---
title: カスタムコンポーネントを使用したヘッドレスフォームのレンダリング
description: カスタムコンポーネントを作成し、ヘッドレスアダプティブForms フィールドにマッピングする方法について説明します。 このガイドでは、カスタムレンダリングと動作を実現するために、フィールドタイプとリソースタイプごとにコンポーネントをマッピングする方法について説明します。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%
---

# カスタムコンポーネントを使用したヘッドレスフォームのレンダリング {#developing-for-headless-forms-using-your-own-components}

ヘッドレスアダプティブFormsでは、カスタムコンポーネントを作成および実装して、フォームの外観と機能を定義できます。 デフォルトコンポーネントは標準的な動作を提供しますが、カスタムの「お知らせ」コンポーネントや専用の「手書き署名」フィールドなど、特定のUI要素やインタラクションが必要になる場合があります。

この記事では、カスタム React コンポーネントを作成し、ヘッドレスアダプティブフォームにマッピングする方法を説明します。

## &#x200B;1. カスタム React コンポーネントの作成

まず、フォームフィールドをレンダリングするReact コンポーネントを作成します。 このコンポーネントでは、任意のReact ライブラリ（マテリアル UI、Ant デザイン、独自のカスタムスタイルなど）を使用できます。

例えば、特定のスタイルを持つ読み取り専用メッセージをレンダリングするカスタム **通知** コンポーネントを作成します。

1. React プロジェクトのコンポーネントディレクトリ（例：`src/components`）に移動します。
2. コンポーネントの新しいフォルダーとファイル（例：`Announcement/index.tsx`）を作成します。
3. コンポーネントを実装します。 ヘッドレス Forms ランタイムと互換性のある`props`を受け入れる必要があります（通常はフィールドのステートを受け取ります）。

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. カスタムコンポーネントのマッピング

カスタムコンポーネントを使用するには、`mappings.ts` ファイルにマッピングする必要があります。 ヘッドレス Forms ランタイムは、このマッピングを使用して、フォーム JSON内の各フィールドに対してレンダリングするReact コンポーネントを決定します。

コンポーネントをマッピングする方法は、主に&#x200B;**フィールドタイプ**&#x200B;または&#x200B;**リソースタイプ**&#x200B;の2つがあります。

### フィールドタイプ別マッピング

標準マッピングは、フォーム JSONの`fieldType` プロパティ （例：`text-input`、`checkbox`、`button`）に基づいています。 これは、標準コンポーネントの&#x200B;*all* インスタンスをカスタムバージョンに置き換える場合に便利です。

1. `src/utils/mappings.ts` （またはマッピングが定義されている場所）を開きます。
2. カスタムコンポーネントを読み込みます。
3. キーとして`fieldType`を使用して、マッピング オブジェクトに追加します。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### リソースタイプ別マッピング（カスタムコンポーネント）

AEMでカスタムコンポーネント（標準テキストコンポーネントを拡張する「お知らせ」コンポーネントなど）を作成し、その特定のコンポーネントをReact アプリで異なる方法で&#x200B;*のみ* レンダリングする場合は、**リソースタイプ**&#x200B;または一意のIDを使用してマッピングする必要があります。

この方法では、標準のテキストコンポーネントを通常どおりにレンダリングし、カスタムの「お知らせ」コンポーネントでは専用のReact実装を使用できます。

1. コンポーネントの一意のIDを識別します。 ヘッドレスフォーム JSONでは、設定されている場合、`:type` プロパティまたはカスタム `fieldType`に多くあります。
2. この識別子を使用してマッピングを追加します。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **注：** AEM フォーム モデルが、`mappings.ts`で使用するキーに一致する正しい`:type`または識別子を書き出していることを確認してください。

## &#x200B;3. マッピングの適用

最後に、ヘッドレスフォームインスタンスでこれらのカスタムマッピングが使用されていることを確認します。

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

次の手順に従うことで、特定のデザインおよび機能要件に一致するコンポーネントを使用して、ヘッドレスアダプティブFormsの機能を拡張できます。
