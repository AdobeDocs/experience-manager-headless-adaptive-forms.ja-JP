---
title: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
description: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, Visual Studio Code 拡張機能
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 40%

---

# ヘッドレスアダプティブフォーム用の Microsoft Visual Studio Code 拡張機能

Microsoft® Visual Studio Code を IDE （Integrated Development Environment）として使用する場合は、Microsoft Visual Studio Code 用のアダプティブForms拡張機能を使用できます。 この拡張機能の特長は次のとおりです。

* アダプティブFormsの IntelliSense 機能を Visual Studio Code に追加します。
* ヘッドレスアダプティブフォームコンポーネントの JSON 構文の検証とオートコンプリートに役立ちます。
* パネルを使用してヘッドレスアダプティブフォームの構造を簡単に移動します。
* ヘッドレスアダプティブフォームの翻訳に役立ちます。

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 前提条件

* [Microsoft Visual Studio Code 1.62.0 以降](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version)をダウンロードしてインストールします。古いバージョンがある場合やバージョンがインストールされていない場合は、[Microsoft Web サイト ](https://code.visualstudio.com/docs/setup/setup-overview) から最新バージョンをダウンロードしてください。 Apple macOSのコマンドラインから Visual Studio を使用するには、[ コマンドラインからの起動 ](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line) を参照してください。
* [アダプティブフォームビルダー拡張機能](/help/assets/adaptive-form-builder-0.12.0.vsix)をダウンロードします。

## 拡張機能のインストール

1. コマンドプロンプトを開き、ダウンロードした拡張機能ファイル *adaptive-form-builder-[version].vsix* を含むディレクトリに移動します。

1. 次のコマンドを実行して、拡張機能をインストールします。

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![拡張機能のインストール](/help/assets/install-extension.png)


   .vsix ファイルについては、[Microsoft Visual Studio Code のヘルプ](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix)を参照してください。
