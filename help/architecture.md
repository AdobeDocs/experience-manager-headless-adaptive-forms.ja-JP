---
title: ヘッドレスアダプティブフォームのアーキテクチャ
description: AEM Forms ヘッドレスアダプティブFormsのアーキテクチャと、様々なプラットフォーム向けのフォームをすばやく作成する方法について説明します。 この記事では、ヘッドレスアダプティブFormsの仕組みと、様々なアプリケーションと統合してフォーム作成プロセスをシンプルにする方法について説明します。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, アーキテクチャ
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 54%

---


# ヘッドレスアダプティブフォームの仕組み

ヘッドレスアダプティブフォームは基本的に、フォームフィールド（テキストボックス、選択肢、その他多数のフィールド）と、フォームにインタラクティブ動作を追加するための対応するルール（条件付きロジック）で構成される JSON 構造（スキーマ）です。 アプリケーションや web サイトで REST API を使用して、ホストされた JSON 構造をリクエストし、その JSON 構造をアプリまたは web サイトのフォームとしてネイティブにレンダリングできます。1 つのヘッドレスアダプティブフォームで複数の web ページやアプリケーションに対応でき、アプリや web サイトに合わせて変更を加える必要はありません。

![ヘッドレスアダプティブフォームの仕組み](/help/assets/how-headless-adaprive-forms-work.png)

## アーキテクチャ {#architecture}

一般的なヘッドレスアダプティブフォームのアーキテクチャは、ヘッドレスアダプティブフォームをホストするAdobe Experience Manager Forms サーバーを中心としています。 Web、モバイル、JavaScript、チャットボットなどのフロントエンドアプリが、各チャネルのフォームをレンダリングします。

ヘッドレスアダプティブフォームのデプロイメントの一般的なアーキテクチャは次のとおりです。

![アーキテクチャ](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### ヘッドレスアダプティブフォーム実装のコンポーネント

**Adobe Experience Manager Server**：Adobe Experience Manager は、ヘッドレスアダプティブフォームのホストとして機能するだけでなく、次のバックエンド機能も提供します。

* ヘッドレスフォームの送信ステータスをリスト、取得、事前入力、検証、送信およびトラックするための RESTful API
* ヘッドレスアダプティブフォームを簡単に開発するためのビジュアルエディター。
* 様々な種類のデータソースにデータを送受信するためのフォームデータモデル。
* 複雑なタスクを自動化するためのワークフローエンジン。

**ヘッドレスアダプティブフォーム**：ヘッドレスアダプティブフォームは .json ファイルで表されます。JSON 構造は、フォームのコンポーネント、制約および構造を定義します。

**フロントエンドアプリ**：SPA（単一ページアプリケーション）、モバイルアプリ、JavaScript アプリなどのフロントエンドアプリは、クライアントでヘッドレスアダプティブフォーム（JSON 表現のフォーム）を使用しフォームをレンダリングします。ヘッドレスアダプティブフォームに付属の React レンダラーコンポーネントを使用して、アダプティブフォームをレンダリングしたり、独自のカスタムコンポーネントを作成してヘッドレスアダプティブフォームをネイティブにレンダリングしたりできます。

<!-- ### Understanding Headless adaptive forms definition -->



### 開発者ツール

一般的な開発サイクルでは、まず Adobe Experience Manager Forms サーバー上でヘッドレスアダプティブフォームを作成しホストします。次に、UI コンポーネントをマッピングするか、Google マテリアル UI や Chakra UI などの公開 UI コンポーネントライブラリを使用してフォームのスタイルを設定します。最後に、アプリケーション（web サイト、モバイルアプリケーション、JavaScript アプリケーション、チャットアプリケーションなどの様々なサーフェス）でヘッドレスアダプティブフォームを取得し表示します。

ヘッドレスアダプティブフォームを作成してアプリケーションに統合するには、次のツールが役立ちます。

**Forms Web SDK（クライアントサイドランタイム）**：Forms Web SDK は、クライアントサイドの JavaScript ライブラリです。これにより、フォームフィールドにクライアントサイドの検証を適用し、フォームの状態を維持し、フォームを UI レイヤーまたはアダプティブフォームのレンダリングコンポーネントに接続するためのフックを提供することができます。 これにより、顧客はフォームの様々なフィールドに適用される制約を検証し、フォームの JSON 構造を UI フレームワークに接続するためのフックを使用できます。 Forms Web SDK には次のコンポーネントがあります。

* **ビジネスルールプロセッサー**：ビジネスルールプロセッサーはフォームの JSON 構造を入力として受け取り、フォームフィールドの状態を管理し、ルールを実行し、JSON に存在するイベントハンドラーを実行します。
* **React Binder**：フォームコンポーネントにステートを追加するためのフックをコントローラーに提供します。また、フォームの事前入力にも役立ちます。
* **コンポーネントライブラリ**:React スペクトルコンポーネントを提供し、React バインダーモジュールのフックを使用してこれらのコンポーネントに状態を追加します。

Forms Web SDK は、フォームの様々なフィールドに適用された制約を検証する API を提供するだけでなく、ヘッドレスアダプティブフォームを UI フレームワークに接続するためのフックとしても機能します。また、ヘッドレスアダプティブフォーム用の React レンダラーも提供されるので、ヘッドレスアダプティブフォームをアプリケーションに統合するのに役立ちます。 Web SDKの次のコンポーネントを使用できます。

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

これらのコンポーネントはすべて AEM アーキタイプに含まれています。ヘッドレスアダプティブフォーム用にAEM アーキタイプ 37 以降のプロジェクトを作成する場合、上記のライブラリの最新バージョンがプロジェクトに含まれています。

* **コードのプレイグラウンド**:[ コードのプレイグラウンド ](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=ja) は、開発者がヘッドレスアダプティブFormsの機能を試し、学び、テストできるように設計されたインタラクティブな環境です。

**起動済みのアプリケーション**：ヘッドレスアダプティブフォームの使用をすぐに開始するのに役立つ、起動済みのアプリケーションもリリースされています。

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**ストーリーブック**：[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)は、ヘッドレスアダプティブフォームの様々なコンポーネントの概要を示します。また、サポートされているすべてのコンポーネント、対応するプロパティおよび制約のリストも提供します。

**Visual Studio Code 拡張機能**：[Visual Studio Code 拡張機能](visual-studio-code-extension-for-headless-adaptive-forms.md)は、有効な JSON 構造を作成するのに役立ちます。これは、JSON 構造のコンポーネントの追加、削除、名前変更などの一般的な機能に加えて、IntelliSense のサポートやフォームの JSON 構造の検証も提供します。

**HTTP API とJavaScript API**: [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) を使用すると、ヘッドレスフォームの送信ステータスをリスト、取得、検証、送信およびトラッキングできます。<!-- URL is 404!! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

**JSON 式**: JSON 構造のクエリや、ヘッドレスアダプティブフォームのルールの作成に役立つ、フォーム式文法の実装です。 この文法は、スプレッドシートに似た関数と演算子および JSON クエリ言語である [JMESPath](https://jmespath.org/) をマッシュアップしたものです。[プレイグラウンド](https://opensource.adobe.com/json-formula/dist/index.html)を使用して、JSON 式の構文と機能を調べることができます。

**アダプティブFormsバージョン 2.0 仕様**：アダプティブFormsバージョン 2.0 仕様では、ヘッドレスアダプティブフォームの定義に使用できるすべてのコンポーネント、制約、メソッドに関する詳細を提供します。 仕様は [PDF](/help/assets/headless-adaptive-forms-specification.pdf) 形式で入手可能です。

