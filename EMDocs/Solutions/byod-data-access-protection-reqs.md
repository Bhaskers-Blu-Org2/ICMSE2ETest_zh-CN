---
title: "データ アクセスと保護の要件"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29eddc34-5ca5-4169-89b6-8137b03ab7f0
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 163d60c44009628bd32daac0a5f0149a97678009
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>データ アクセスと保護の要件

ユーザーが自分のデバイスから企業のリソースにアクセスできるようにするための最重要要素の 1 つは、企業のデータと情報を保護することです。企業は、場合によっては、場所に関係なくデータを保護するために、さまざまなコンプライアンス要件を設定する必要があります。次の図は、データにアクセスするときのユーザーとデバイスの間のやり取りと、このサブドメインについて考慮するべきコンポーネントをまとめたものです。

![データ アクセスと保護の要件](./media/BYOD_Figure3.png)

次のセクションは、ソリューションを設計するための要件を考えるために答える、データ アクセスと保護に関する質問をまとめたものです。

## <a name=""></a>質問

データ アクセスと保護の要件に関する質問は 6 つのカテゴリに分類されます。

- 記憶域
- ネットワーク
- へのアクセス
- 承認
- ポリシーとコンプライアンス

### <a name=""></a>記憶域

- データをデータ センターに保存するとき、暗号化を有効にしますか。
- 企業はデータセンターのストレージに保存されているデータに対するオフライン アクセスを提供しますか （つまり、データをユーザーのデバイスに同期しますか）。
    - 提供している場合、企業はユーザーのデバイスで同じデータ形式 （暗号化または平文） を維持しますか。
- 現在、ユーザーごとにシステムにストレージ クォータを導入していますか。
    - 導入している場合、自分のデバイスを持ち込むことが認められたユーザーのクォータを増やす予定ですか。
- 企業のポリシーでは、企業のコンピューターで外付け記憶域デバイスを使用することが許可されていますか。
    - 許可されていない場合、自分のデバイスからデータにアクセスするユーザーにもそのポリシーを適用する予定ですか。
- 企業のポリシーでは、企業のコンピューターからクラウドベースの記憶域を使用することが許可されますか。
    - 許可されていない場合、自分のデバイスからデータにアクセスするユーザーにもそのポリシーを適用する予定ですか。

### <a name=""></a>ネットワーク

- 何らかの種類のネットワーク暗号化を社内で導入していますか。
    - 導入している場合、それはサーバー間の通信に限られていますか、それともネットワーク全体が暗号化されますか。
- ユーザーが物理的に企業ネットワークの外にいる場合と中にいる場合では、データ アクセスの要件は異なりますか。
    - 異なる場合、その要件とは何ですか。
- 企業ネットワークで自分のデバイスを使用することをユーザーに許可した場合、ネットワーク活動の増加を予測していますか。
    - 予測している場合、増加したトラフィックを現在のネットワーク能力で処理できますか。
- 企業はネットワーク検査メカニズムを利用していますか。
    - 利用している場合、自分のデバイスを持ち込み、企業ネットワークに接続するユーザーにそれを適用する予定ですか。

### <a name=""></a>へのアクセス

- 企業はユーザー ディレクトリを 1 つ使用しますか。それとも、複数のプロバイダーが存在しますか。
- 企業のディレクトリは社内にありますか。クラウド内ですか。両方の場所 （ハイブリッド） にありますか。
- ユーザーが自分のデバイスからアプリにアクセスするとき、どのディレクトリで認証されますか。
- 企業は社内サービスとクラウド サービスの間で認証をフェデレーションしますか。

### <a name=""></a>認証

- 環境では現在、どのような種類の認証が使用されていますか。
- その認証方法は維持する予定ですか。あるいは、ユーザーが自分のデバイスから企業のリソースにアクセスできるようにする前に認証方法を強化しますか。
- 現在の環境には多要素認証を設定していますか。
- ユーザーのデバイスまたはユーザーのみを認証する予定ですか。
- ユーザーのデバイスからアクセスされるアプリにシングル サインオンを有効にする予定ですか。
- クラウドのリソースを活用し、リモート ユーザーの認証レベルを追加する予定ですか。

### <a name=""></a>承認

- 現在の環境では、ユーザーが承認された後、他にも制御を置き、要求している情報にアクセスする許可がユーザーに与えられているかどうかを検証していますか？
- リモート ユーザーに事前定義されている一連のルールに基づいて条件付きのアクセスを与える予定ですか。
- 企業は社内またはクラウド内に置かれているデータに承認を強制しますか。
- 企業はデータ アクセスを許可するために[需要知道 （知る必要がある人だけ知る） の原則](http://en.wikipedia.org/wiki/Need_to_know)を使用しますか。

### <a name=""></a>ポリシーとコンプライアンス

- 企業はデータ アクセスの分類方法を定義するためのポリシーを定めていますか。
- 企業はデータ処理とプライバシーに関する何らかの規制に準拠する必要がありますか。
    - 必要がある場合、そのような規制は社内リソースの現在のデータ アクセス ポリシーをどのように推進しますか。
- 企業は[モバイル デバイス管理 (MDM)](mdm-design-considerations-guide.md)と[モバイル アプリケーションの管理 (MAM)](https://blogs.technet.microsoft.com/cbernier/2016/01/05/microsoft-intune-mobile-application-management-mam-standalone/)のポリシーを定めていますか。
- 企業は訴訟または犯罪調査でデバイスが押収されるときのポリシーを定めていますか。