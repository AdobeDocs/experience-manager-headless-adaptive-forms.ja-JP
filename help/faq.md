---
title: ヘッドレスアダプティブフォームに関するよくある質問
description: よくある質問
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, FAQ
index: true
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
TQID: https://experienceleague.adobe.com/GqYwqgwHe82HXLvljMyGW4PDOkmi7Xg2MKjYxibsFnY
product_v2: id: e8f6de9b-cf88-4405-8d10-15efa08c230eid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: f013e6ab-27b8-4645-b5a7-31ffa474d04f
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 837
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

<!-- 
## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. 
-->

## ヘッドレスアダプティブフォームのプレビューはどこで入手できますか？ {#storybook-example}

スターターアプリを使用して、カスタムのヘッドレスアダプティブフォームをレンダリングしプレビューできます。 [ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)の例を変更して、ヘッドレスアダプティブフォームをプレビューすることもできます。

![](/help/assets/storybook-example.png)

## カスタムフレームワークでヘッドレスアダプティブフォームを使用することはできますか？

ヘッドレスアダプティブフォームは[標準仕様](/help/assets/headless-adaptive-forms-specification.pdf)に基づいています。 仕様を拡張して、カスタムコンポーネントの構築に使用できます。 例えば、Chakra UI、Vue.js などのコンポーネントです。

## ヘッドレスアダプティブフォームはカスケードフィールドをサポートしていますか？

カスケードフィールドでは、2 番目のフィールドの内容は、最初のフィールドで選択された内容に依存します。 カスケードフィールドの例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)に含まれています。

## ヘッドレスアダプティブフォームでは、パーソナライズされたデータをフォームに事前入力できますか？

ヘッドレスアダプティブフォームを使用すると、パーソナライズされたデータをフォームに事前入力できます。 ヘッドレスアダプティブフォームに事前入力する方法の例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)に含まれています。

<!--
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  
-->

## Angular SPA でヘッドレスアダプティブフォームを使用できますか？

Web SDK を使用して、ヘッドレスアダプティブフォームを Angular SPA と統合できます。 どのようなフレームワークにも依存しません。 React SDK を参照用に使用できます。

<!--
## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 
-->

## ヘッドレス AF を開発しやすくなるプラグインはありますか？

はい - Visual Studio Code 拡張機能を使用すると、JSON でヘッドレスアダプティブフォームを手動で作成できます。

## モバイルフォームとオフラインフォームに推奨されるアプローチは何ですか？ {#mobile-offline-forms}

独自のネイティブアプリを構築し、ヘッドレスアダプティブForms APIを使用してフォーム定義を取得します。 オプションで、オフラインサポート（ローカルストレージや同期など）を実装できます。 推奨されるアプローチとAPIへのリンクについては、[ モバイルフォームのベストプラクティス ](mobile-forms-best-practices.md)を参照してください。

## GraphQLやヘッドレス APIをAEM Formsでどのように使用しますか？

AEM ヘッドレスアダプティブ Formsでは、GraphQLではなく&#x200B;**HTTP/REST API**&#x200B;を使用します。 アプリはこれらのAPIを呼び出して、フォームのリスト、フォーム定義（JSON）の取得、検証、送信、送信ステータスの追跡を行います。 完全な参照には、[ ヘッドレスアダプティブフォーム HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)を使用します。 フォームの取得およびレンダリング方法については、[ アーキテクチャ ](architecture.md)および[ ヘッドレスフォームについて](understanding-headless-forms.md)を参照してください。

## Adobe AEM FormsでReact コンポーネントを使用してヘッドレスフォームを実装し、スタイルを設定するにはどうすればよいですか？

独自のReact コンポーネントとCSS （またはマテリアル UIなどのUI ライブラリ）を使用して、ヘッドレスフォームを実装し、スタイルを設定します。 フォームロジック（ステート、検証、ルール）は、Forms Web SDKおよびフォーム JSONから取得されます。アプリは、それをレンダリングするUIを提供します。

* React UI ライブラリを使用してヘッドレスフォームのスタイルを設定するには、[ カスタム react ライブラリを使用してヘッドレスフォームをレンダリングする](use-google-material-ui-react-components-to-render-a-headless-form.md)を参照してください。
* カスタム React コンポーネントを構築してフォームフィールドにマッピングするには、[ カスタムコンポーネントを使用してヘッドレスフォームをレンダリングする](developing-for-headless-forms-using-your-own-components.md)を参照してください。

ヘッドレスフォームを使用するタイミング、状態管理、検証などの概念については、[ ヘッドレスフォームについて](understanding-headless-forms.md)を参照してください。

## カスタム CSS、テーマ、ルールエディター、ヘッドレスフォームを使用して、AEM Formsを実装およびカスタマイズするにはどうすればよいですか？

**ヘッドレスフォーム：** スタイル設定とルックアンドフィールは完全にユーザーの管理下にあります。 独自のReact （または他の）コンポーネントと独自のCSSを使用します。組み込みのテーマはありません。 [ カスタム react ライブラリを使用してヘッドレスフォームをレンダリング ](use-google-material-ui-react-components-to-render-a-headless-form.md)および[ カスタムコンポーネントを使用してヘッドレスフォームをレンダリング ](developing-for-headless-forms-using-your-own-components.md)し、ヘッドレスフォームを実装およびスタイル設定するを参照してください。

**Classic AEM Forms（テーマ、ルールエディター、ビジュアルエディター）:** カスタム CSS、テーマエディター、ルールエディターは、従来の（ヘッドレスではない）アダプティブ Forms オーサリングエクスペリエンスに適用されます。 これらのトピックについては、Experience Leagueの[AEM Forms ドキュメント ](https://experienceleague.adobe.com/docs/experience-manager-forms.html)を参照してください。

## ヘッドレスアダプティブフォームを CRM に接続してデータを読み書きできますか？

Microsoft Dynamics や Salesforce を使用して、ヘッドレスアダプティブフォームを送信または事前入力できます。 CRM とは別に、ヘッドレスアダプティブフォームでは、REST エンドポイント、メールおよびカスタム送信アクションを使用した送信または事前入力をサポートしています。
