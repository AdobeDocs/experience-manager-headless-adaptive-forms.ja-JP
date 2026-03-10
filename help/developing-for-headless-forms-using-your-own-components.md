---
title: カスタムコンポーネントを使用したヘッドレスフォームのレンダリング
description: カスタムコンポーネントを作成し、ヘッドレスアダプティブFormsのフィールドにマッピングする方法を説明します。 このガイドでは、カスタムレンダリングと動作を実現するために、フィールドタイプとリソースタイプでコンポーネントをマッピングする方法について説明します。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# カスタムコンポーネントを使用したヘッドレスフォームのレンダリング {#developing-for-headless-forms-using-your-own-components}

ヘッドレスアダプティブ Formsでは、カスタムコンポーネントを作成および実装して、フォームのアピアランスと機能を定義できます。 デフォルトのコンポーネントは標準的な動作を提供しますが、場合によっては、特定の UI 要素やインタラクション（カスタムの「通知」コンポーネントや専用の「手書き署名」フィールドなど）が必要になることがあります。

この記事では、カスタム React コンポーネントを作成し、ヘッドレスアダプティブフォームにマッピングする手順について説明します。

## &#x200B;1. カスタム React コンポーネントの作成

まず、フォームフィールドをレンダリングする React コンポーネントを作成します。 このコンポーネントは任意の React ライブラリ（マテリアル UI、Ant デザイン、独自のカスタムスタイルなど）を使用できます。

例えば、特定のスタイル設定を持つ読み取り専用メッセージをレンダリングするカスタム **アナウンス** コンポーネントを作成してみましょう。

1. React プロジェクトのコンポーネントディレクトリ（例：`src/components`）に移動します。
2. コンポーネント用に新しいフォルダーおよびファイル（例：`Announcement/index.tsx`）を作成します。
3. コンポーネントを実装します。 ヘッドレス Forms ランタイム（通常はフィールドのステートを受け取る）と互換性のある `props` を使用する必要があります。

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

カスタムコンポーネントを使用するには、`mappings.ts` ファイルにマッピングする必要があります。 ヘッドレス Forms ランタイムは、このマッピングを使用して、フォーム JSON の各フィールドに対してレンダリングする React コンポーネントを決定します。

コンポーネントをマッピングする主な方法には、**フィールドタイプ** または **リソースタイプ** の 2 つがあります。

### フィールドタイプ別マッピング

標準マッピングは、フォーム JSON の `fieldType` プロパティ（`text-input`、`checkbox`、`button` など）に基づいています。 これは、標準コンポーネントの *すべて* のインスタンスをカスタムバージョンで置き換える場合に便利です。

1. `src/utils/mappings.ts` （またはマッピングが定義されている任意の場所）を開きます。
2. カスタムコンポーネントを読み込みます。
3. `fieldType` をキーとして使用して、マッピング オブジェクトに追加します。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### リソースタイプ別のマッピング（カスタムコンポーネント）

AEMでカスタムコンポーネント（標準テキストコンポーネントを拡張する「アナウンス」コンポーネントなど）を作成し、その特定のコンポーネントを React アプリで異なる方法で *のみ* レンダリングする場合は、その **リソースタイプ** または一意の ID でマッピングする必要があります。

このアプローチを使用すると、標準のテキストコンポーネントを通常どおりにレンダリングしながら、カスタムの「アナウンス」コンポーネントで専用の React 実装を使用できます。

1. コンポーネントの一意の ID を識別します。 ヘッドレスフォーム JSON では、多くの場合、`:type` プロパティやカスタム `fieldType` （設定されている場合）で見つかります。
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

> **メモ：** AEM フォームモデルで、`mappings.ts` で使用するキーに一致する正しい `:type` または ID を書き出していることを確認してください。

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

これらの手順に従うと、特定の設計および機能要件に合致するコンポーネントでヘッドレスアダプティブFormsの機能を拡張できます。
