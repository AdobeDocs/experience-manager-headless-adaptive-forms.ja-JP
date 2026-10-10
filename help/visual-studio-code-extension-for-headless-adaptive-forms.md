---
title: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
description: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, Visual Studio Code 拡張機能
index: true
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
TQID: 'https://experienceleague.adobe.com/sf8qkVgbwMf2CGDsATHRYzq6idFQNFv3Os89oiCoiLU'
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
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
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%
---
# ヘッドレスアダプティブフォーム用の Microsoft Visual Studio Code 拡張機能

Microsoft® Visual Studio Code を IDE（統合開発環境）として使用する場合は、Microsoft Visual Studio Code 用のアダプティブフォーム拡張機能を使用できます。 この拡張機能の特長は次のとおりです。

* Visual Studio Code にアダプティブフォーム用の IntelliSense 機能を追加します。
* ヘッドレスアダプティブフォームコンポーネントの JSON 構文の検証とオートコンプリートに役立ちます。
* パネルを通じてヘッドレスアダプティブフォームの構造を簡単に移動します。
* ヘッドレスアダプティブフォームの翻訳に役立ちます。

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 前提条件

* [Microsoft Visual Studio Code 1.62.0 以降](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version)をダウンロードしてインストールします。 古いバージョンがある場合や、どのバージョンもインストールされていない場合は、[Microsoft web サイト](https://code.visualstudio.com/docs/setup/setup-overview)から最新バージョンをダウンロードしてください。 Apple macOS のコマンドラインから Visual Studio を使用するには、[コマンドラインからの起動](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)を参照してください。
* [アダプティブフォームビルダー拡張機能](/help/assets/adaptive-form-builder-0.12.0.vsix)をダウンロードします。

## 拡張機能のインストール

1. コマンドプロンプトを開き、ダウンロードした拡張機能ファイル（*adaptive-form-builder-[version].vsix*）を含んだディレクトリに移動します。

1. 次のコマンドを実行して、拡張機能をインストールします。

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![拡張機能のインストール](/help/assets/install-extension.png)


   .vsix ファイルについては、[Microsoft Visual Studio Code のヘルプ](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix)を参照してください。
