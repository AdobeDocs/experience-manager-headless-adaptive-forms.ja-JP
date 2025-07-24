---
title: ヘッドレスアダプティブフォームのトラブルシューティング
description: ヘッドレスアダプティブフォームのトラブルシューティング
keywords: ヘッドレス, アダプティブフォーム, トラブルシューティング
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 58%

---

# トラブルシューティング

## アーキタイププロジェクトをローカル開発環境にデプロイできない

### 問題

`mvn -PautoInstallPackage clean install` または同様のコマンドを使用してAEM アーキタイププロジェクトをデプロイすると、プロジェクトのデプロイに失敗します。

### 理由

これは、サポートされていないバージョンか、`node.js` または `NPM` のインストールが破損していることが原因で発生する可能性があります。

### 解決策

1. [現在インストールされている Node.js](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) を環境から完全に削除します。

1. `node.JS 16.13.0` 以降を `NPM` と共にインストールします。

1. コンピューターを再起動します。


## `mvn clean install` コマンドの実行に失敗する

### 問題

`mvn clean install` または同様のコマンドを使用してAEM アーキタイププロジェクトをデプロイすると、コマンドが実行できません。

### 理由

この問題は、Git がインストールされていない場合に発生する可能性があります。

### 解決策

[Git の最新リリース](https://git-scm.com/downloads)をダウンロードしてインストールします。Git を初めて使用する場合は、[Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) を参照してください。
