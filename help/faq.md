---
title: ヘッドレスアダプティブフォームに関するよくある質問
description: よくある質問
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 58%

---

# よくある質問（FAQ） {#headless-adaptive-forms-faq}

## ヘッドレスアダプティブフォームを使用するには React.js の知識が必要ですか？

任意のフレームワーク、ライブラリまたは言語を使用してヘッドレスアダプティブフォームをレンダリングし、アドビの REST API を使用してフォームを検証および送信できます。 標準提供の AF コアライブラリは、フレームワークに依存しません。 また、標準提供の React Render および React コンポーネントライブラリも、参考までに提供されています。 独自のコンポーネントを作成でき、提供のライブラリには限定されません。


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## ヘッドレスアダプティブフォームを使用するには、Forms as a Cloud Service サンドボックスが必要ですか？

スターターアプリを使用して、ヘッドレスアダプティブフォームの開発とスタイル設定を開始できます。 バックエンドのフォーム機能とともにヘッドレスアダプティブフォームをホストし提供するには、Forms as a Cloud Service が必要です。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## ヘッドレスアダプティブフォームのプレビューはどこで入手できますか？ {#storybook-example}

スターターアプリを使用して、カスタムのヘッドレスアダプティブフォームをレンダリングしプレビューできます。 [ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)の例を変更して、ヘッドレスアダプティブフォームをプレビューすることもできます。

![](/help/assets/storybook-example.png)

## カスタムフレームワークでヘッドレスアダプティブフォームを使用することはできますか？

ヘッドレスアダプティブフォームは[標準仕様](/help/assets/headless-adaptive-forms-specification.pdf)に基づいています。 仕様を拡張して、カスタムコンポーネントの構築に使用できます。 例えば、Chakra UI、Vue.js などのコンポーネントです。

## ヘッドレスアダプティブフォームはカスケードフィールドをサポートしていますか？

カスケードフィールドでは、2 番目のフィールドの内容は、最初のフィールドで選択された内容に依存します。 カスケードフィールドの例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)に含まれています。

## ヘッドレスアダプティブフォームでは、パーソナライズされたデータをフォームに事前入力できますか？

ヘッドレスアダプティブフォームを使用すると、パーソナライズされたデータをフォームに事前入力できます。 ヘッドレスアダプティブフォームに事前入力する方法の例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)に含まれています。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Angular SPA でヘッドレスアダプティブフォームを使用できますか？

Web SDK を使用して、ヘッドレスアダプティブフォームを Angular SPA と統合できます。 どのようなフレームワークにも依存しません。 React SDK を参照用に使用できます。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## ヘッドレス AF を開発しやすくなるプラグインはありますか？

はい - Visual Studio Code 拡張機能を使用すると、JSON でヘッドレスアダプティブフォームを手動で作成できます。

## モバイルフォームとオフラインフォームで推奨されるアプローチを教えてください。 {#mobile-offline-forms}

独自のネイティブアプリを作成し、ヘッドレスなアダプティブ Forms API を介してフォーム定義を取得します。 オプションで、オフラインサポート（ローカルストレージや同期など）を実装できます。 推奨されるアプローチと API へのリンクについては、[ モバイルフォームのベストプラクティス ](mobile-forms-best-practices.md) を参照してください。

## AEM FormsでGraphQLやヘッドレス API を使用する方法

AEM ヘッドレスアダプティブFormsは、GraphQLではなく、**HTTP/REST API** を使用します。 アプリはこれらの API を呼び出し、フォームの一覧表示、フォーム定義（JSON）の取得、送信ステータスの検証、送信および追跡を行います。 完全なリファレンスには [ ヘッドレスアダプティブフォーム HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) を使用します。 フォームの取得とレンダリングの方法については、[ アーキテクチャ ](architecture.md) および [ ヘッドレスフォームについて ](understanding-headless-forms.md) を参照してください。

## Adobe AEM Formsで React コンポーネントを使用してヘッドレスフォームを実装し、スタイルを設定する方法を教えてください。

独自の React コンポーネントおよび CSS （または Material UI などの UI ライブラリ）を使用して、ヘッドレスフォームを実装し、スタイルを設定します。 フォームロジック（ステート、検証、ルール）は、Forms Web SDKとフォーム JSON から取得されます。アプリによって、それをレンダリングする UI が提供されます。

* React UI ライブラリを使用してヘッドレスフォームのスタイルを設定するには、[ カスタム React ライブラリを使用してヘッドレスフォームをレンダリングする ](use-google-material-ui-react-components-to-render-a-headless-form.md) を参照してください。
* カスタム React コンポーネントを作成してフォームフィールドにマッピングするには、[ カスタムコンポーネントを使用したヘッドレスフォームのレンダリング ](developing-for-headless-forms-using-your-own-components.md) を参照してください。

ヘッドレスフォームを使用するタイミング、状態の管理、検証などの概念については、[ ヘッドレスフォームについて ](understanding-headless-forms.md) を参照してください。

## カスタム CSS、テーマ、ルールエディター、ヘッドレスフォームを使用してAEM Formsを実装およびカスタマイズする方法を教えてください。

**ヘッドレスフォーム：** スタイル設定とルックアンドフィールは、完全に自分で制御できます。 独自の React （または他の）コンポーネントと独自の CSS を使用します。組み込みのテーマはありません。 [ カスタム React ライブラリを使用したヘッドレスフォームのレンダリング ](use-google-material-ui-react-components-to-render-a-headless-form.md)、および [ カスタムコンポーネントを使用したヘッドレスフォームのレンダリング ](developing-for-headless-forms-using-your-own-components.md) を参照して、ヘッドレスフォームの実装とスタイル設定を行います。

**クラシック AEM Forms（テーマ、ルールエディター、ビジュアルエディター）:** カスタム CSS、テーマエディターおよびルールエディターは、クラシック（ヘッドレス以外）のアダプティブ Formsのオーサリングエクスペリエンスに適用されます。 これらのトピックについては、Experience Leagueの [AEM Forms ドキュメント ](https://experienceleague.adobe.com/docs/experience-manager-forms.html) を参照してください。

## ヘッドレスアダプティブフォームを CRM に接続してデータを読み書きできますか？

Microsoft Dynamics や Salesforce を使用して、ヘッドレスアダプティブフォームを送信または事前入力できます。 CRM とは別に、ヘッドレスアダプティブフォームでは、REST エンドポイント、メールおよびカスタム送信アクションを使用した送信または事前入力をサポートしています。
