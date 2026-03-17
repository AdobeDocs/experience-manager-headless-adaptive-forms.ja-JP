---
title: Mobile forms のベストプラクティス
description: モバイルおよびオフラインフォームのユースケースでは、独自のネイティブアプリを作成し、ヘッドレスのアダプティブ Forms API を介してフォーム定義を取得します。 ネイティブモバイルアプリケーションに推奨されるアプローチ。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: モバイルフォーム，ネイティブアプリ，オフラインフォーム，ヘッドレス API
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 8%

---

# Mobile forms のベストプラクティス {#mobile-forms-best-practices}

モバイルおよびオフラインフォームのユースケースでは、独自のネイティブアプリを作成し、ヘッドレスアダプティブ Forms API を介してフォーム定義を取得することをお勧めします。 これにより、モバイルエクスペリエンスを完全に制御でき、モバイルプラットフォームの進化に合わせて継続的なサポートを確実に行えます。

## 推奨アプローチ {#recommended-approach}

次の機能を備えたネイティブモバイルアプリケーション（iOSまたはAndroid）を作成します。

1. **ヘッドレスフォーム定義を取得します** - [&#x200B; ヘッドレスアダプティブ Forms API](https://opensource.adobe.com/aem-forms-af-runtime/api/) を使用して、フォームの JSON をオンデマンドで取得します（例えば、ユーザーがフォームを開いたり、アプリ内でフォームに移動したりする場合）。 使用可能なフォームを一覧表示し、ID でフォーム定義を取得できます。

2. **アプリでフォームをレンダリング** – 好みの UI フレームワーク（React Native、ネイティブビューなど）を使用して、JSON からフォームをレンダリングします。 スタックに適合するForms Web SDKと既存のヘッドレスアダプティブフォーム React コンポーネントを使用することも、同じ JSON 構造を使用する独自のレンダラーを構築することもできます。

3. **オプションでオフラインをサポート** - アプリにローカルストレージと同期を実装します。 例えば、オンライン時にフォーム定義をキャッシュし、ローカルでドラフトを保存し、デバイスがオンラインに戻ったときにデータを送信または同期します。

このアプローチは、AndroidとiOSの変更に合わせてアプリを保守でき、フォームのオーサリング、検証、送信には、サポートされているヘッドレスのアダプティブ Forms プラットフォームを使用します。

## 概要 {#getting-started}

* [AEM ヘッドレスアダプティブフォームの概要 &#x200B;](overview.md) – 機能と概念。
* [&#x200B; ヘッドレスアダプティブフォーム API](https://opensource.adobe.com/aem-forms-af-runtime/api/) - フォームをプログラムによってリスト化、取得、検証および送信します。
* [&#x200B; アーキテクチャ &#x200B;](architecture.md) - ヘッドレスアダプティブフォームの仕組みと、フロントエンドアプリによるヘッドレスアダプティブフォームの消費方法。

統合の手順については、[&#x200B; ヘッドレスフォームの作成と公開 &#x200B;](create-and-publish-a-headless-form.md) および [&#x200B; 開発者ポータル &#x200B;](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=ja) を参照してください。
