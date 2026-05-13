---
title: ヘッドレスアダプティブフォームのトラブルシューティング
description: ヘッドレスアダプティブフォームのトラブルシューティング
keywords: ヘッドレス, アダプティブフォーム, トラブルシューティング
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
TQID: https://experienceleague.adobe.com/yjO3VhNmqIAyfnD7daHB7eAEUNmaAjnUgEm0fHc1ArY
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 152
ht-degree: 100%

---

# トラブルシューティング

## アーキタイププロジェクトをローカル開発環境にデプロイできない

### 問題

`mvn -PautoInstallPackage clean install` または同様のコマンドを使用して AEM アーキタイププロジェクトをデプロイしようとすると、プロジェクトのデプロイに失敗します。

### 理由

この問題が発生する原因としては、`node.js` または `NPM` がサポートされていないバージョンであるか、インストールが破損していることが考えられます。

### 解決策

1. [現在インストールされている Node.js](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) を環境から完全に削除します。

1. `node.JS 16.13.0` 以降を `NPM` と共にインストールします。

1. コンピューターを再起動します。


## `mvn clean install` コマンドの実行に失敗する

### 問題

`mvn clean install` または同様のコマンドを使用して AEM アーキタイププロジェクトをデプロイしようとすると、コマンドの実行に失敗します。

### 理由

この問題は、Git がインストールされていない場合に発生する可能性があります。

### 解決策

[Git の最新リリース](https://git-scm.com/downloads)をダウンロードしてインストールします。 Git を初めて使用する場合は、[Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) を参照してください。
