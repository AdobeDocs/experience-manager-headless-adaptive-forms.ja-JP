---
title: モバイルフォームのベストプラクティス
description: モバイルとオフラインのフォームのユースケースでは、独自のネイティブアプリを構築し、ヘッドレスアダプティブForms APIを介してフォーム定義を取得します。 ネイティブモバイルアプリケーション向けの推奨アプローチ。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: モバイルフォーム、ネイティブアプリ、オフラインフォーム、ヘッドレス API
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
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
source-wordcount: '330'
ht-degree: 8%
---
# モバイルフォームのベストプラクティス {#mobile-forms-best-practices}

モバイルフォームとオフラインフォームのユースケースの場合は、独自のネイティブアプリを構築し、ヘッドレスアダプティブForms APIを介してフォーム定義を取得することをお勧めします。 これにより、モバイル体験を完全に制御でき、モバイルプラットフォームの進化に伴う継続的なサポートを確保できます。

## 推奨アプローチ {#recommended-approach}

次のことを実現するネイティブモバイルアプリケーション（iOSまたはAndroid）を構築します。

1. **ヘッドレスフォーム定義を取得します** - [ ヘッドレスアダプティブForms API](https://opensource.adobe.com/aem-forms-af-runtime/api/)を使用して、必要に応じてフォーム JSONを取得します（例えば、ユーザーがフォームを開いたり、アプリでフォームに移動したりする場合）。 使用可能なフォームを一覧表示し、IDでフォーム定義を取得できます。

2. **アプリ内でフォームをレンダリングします** – 好みのUI フレームワーク（React Nativeやネイティブビューなど）を使用して、JSONからフォームをレンダリングします。 Forms Web SDKと既存のヘッドレスアダプティブフォーム React コンポーネントを、スタックに合わせて使用したり、同じJSON構造を使用する独自のレンダラーを構築したりできます。

3. **オプションでオフラインをサポート** - アプリにローカルストレージと同期を実装します。 たとえば、オンライン時にはフォーム定義をキャッシュし、ローカルにドラフトを保存し、デバイスがオンラインになったときにデータを送信または同期します。

このアプローチにより、AndroidやiOSの変更に伴うアプリの保守が可能になり、サポートされているヘッドレスアダプティブForms プラットフォームを使用して、フォームのオーサリング、検証、送信が行われます。

## 概要 {#getting-started}

* [AEM ヘッドレスアダプティブフォームの概要](overview.md) – 機能と概念。
* [ ヘッドレスアダプティブフォーム API](https://opensource.adobe.com/aem-forms-af-runtime/api/) - フォームのリスト、取得、検証、送信をプログラムで行います。
* [ アーキテクチャ ](architecture.md) - ヘッドレスアダプティブフォームの仕組みとフロントエンドアプリでの利用方法。

ステップバイステップの統合については、[ ヘッドレスフォームの作成と公開](create-and-publish-a-headless-form.md)および[開発者ポータル ](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=ja)を参照してください。
