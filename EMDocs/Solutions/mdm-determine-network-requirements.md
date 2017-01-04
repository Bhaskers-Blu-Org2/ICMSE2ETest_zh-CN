---
title: "ネットワーク要件の決定"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77e7cab9-2fae-4857-be5d-2b6f57e981be
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 10d12f62d7ac5f3d22f469d171538f616eac46c1
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>ネットワーク要件の決定

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

モバイル デバイスによる広範な企業リソースへの安全で管理されたアクセスを可能にすることは、モバイル デバイス管理ソリューションの重要な機能です。一般に、これらのリソースはオンプレミスのネットワークに配置されていますが、現在では、クラウド ベースの Web サービスおよび外部ネットワーク上でさらにリソースをホストする方がより一般的です。</para><para>企業の電子メール プラットフォーム、仮想プライベート ネットワーク (VPN)、および企業のワイヤレス (Wi-fi) ネットワークにモバイル デバイスが接続する方法はすべて、企業のデータおよび他のリソースを承認されていないアクセスから保護する上で重要な役割を果たします。一方で、ユーザーがもっと便利ではあってもリソースの格納やアクセスに関して安全ではない方法を使わないように、モバイル デバイス ユーザーによるリソースへの安全なアクセスを便利かつ簡単にすることも同じように重要です。</para></content>


## <a name=""></a>電子メール管理
通常、会社の電子メールは、ほとんどのユーザーが個人所有または会社所有のモバイル デバイスからアクセスする必要のある企業ネットワーク上の主要なデータ リソースです。また、普通は、電子メールへのアクセスは、モバイル デバイスの初期登録をトリガーする接続です。既存の非モバイル デバイス管理ソリューションとモバイル デバイス管理ソリューションの両方でモバイル デバイスの電子メール アクセスを管理できることは、デバイス カバレッジのギャップを防ぎ、電子メール サーバーに格納されているデータの保護を強化します。

ほとんどのモバイル デバイス管理ソリューションは、次のどちらか一方または両方の機能を使用して、電子メール アクセスを保護します。

- 
            **電子メール プロファイル︰**電子メール プロファイルを設定して展開することにより、管理者は、ユーザーが電子メール メールボックスに接続できるように、適切な電子メール サーバー情報で自動的にモバイル デバイスを構成できます。ユーザーは、電子メール サーバーの正しいエンドポイント名またはネットワーク アドレスを覚えておかなくても、正しい電子メール サーバーに接続できます。さらに、電子メール プロファイルを削除することで、管理者はデバイスのリセットまたは選択的消去のプロセスの一部としてデバイスから電子メールを削除できます。電子メール プロファイルの管理は、非モバイル デバイス管理ソリューションの機能であるか、またはモバイル デバイス管理ソリューションと統合できます。
- 
            **条件付き電子メール アクセス︰**条件付き電子メール アクセス （"管理された"電子メール アクセス） では、通常、モバイル デバイスが接続するエンドポイントではなく、モバイル デバイスでの電子メールへのアクセスに関するセキュリティとコンプライアンスに重点を置きます。条件付き電子メール アクセスでは、コンプライアンス ポリシーが定義されて、個々のユーザーやデバイスまたはユーザーやデバイスのグループに割り当てられます。ポリシーは、モバイル デバイスが電子メール リソースに接続できるために必要な前提条件を示します (例︰ デバイスには 针 が必要)。ポリシーは、通常はデバイスの初期登録時に適用されますが、モバイル デバイスがモバイル デバイス管理システムに登録されている限り、アクティブな状態を維持し適用され続けます。

###<a name=""></a>電子メール管理の計画に関する確認事項

 電子メール管理の計画について、次の点を確認します。

- モバイル デバイスは既存のオンプレミスの電子メール システムまたはクラウド ホスト型電子メール システムにどのような方法で接続しますか。
- 電子メール システムへのモバイル デバイスの接続は、管理者またはユーザー （または両方の組み合わせ） が責任を持って行いますか。ユーザーが電子メール システムにモバイル デバイスを接続する場合、次のことをどのようにして行いますか。
 - 電子メール メールボックスにアクセスするための適切な接続ポイントを選択する。
 - 適切な接続プロトコルまたは接続方法を選択する。
- モバイル デバイスは、電子メール システムに接続する前および接続中に、セキュリティおよびコンプライアンスに関する特定の標準を満たす必要がありますか。
- カスタムの電子メール セキュリティ ポリシーおよびコンプライアンス接続ポリシーを作成できる必要がありますか。必要な場合、具体的にはどのような要件がありますか。
- 電子メール セキュリティ ポリシーおよびコンプライアンス接続ポリシーをインポートまたはエクスポートできる必要がありますか。
- 電子メール システムへの接続をどのように管理する必要がありますか。
 - デバイス ユーザーごと。
 - デバイスの種類ごと。
 - デバイスの OS ごと。
 - ユーザーのグループまたは役割ごと。
- モバイル デバイスを電子メール システムから切断する必要があるとき、どのようにしてモバイル デバイスから電子メール データを削除しますか。
- 管理者とユーザーの両方が、電子メール データまたは電子メール システムへの接続を削除できる必要がありますか。
- 電子メール データの削除をどのようにして検証または確認しますか。
- オンプレミスの電子メール システムとクラウド ベースの電子メール システムの両方を使用している場合、どのようにしてそれらをモバイル デバイス管理ソリューションと統合しますか。 
- IT 担当者から見て、電子メール プロファイルまたは管理されたアクセス ポリシーの管理方法は同じですか、または異なりますか。メールボックスがホストされている場所によって、ユーザーの電子メール接続のエクスペリエンスは、同じですか、または異なりますか。

## <a name=""></a>ネットワーク接続の管理

通常、モバイル デバイスは、次のアクセス テクノロジを使用して企業ネットワークおよびリソースに接続します。

- 
            **Wi-Fi:**通常、企業リソースへのワイヤレス アクセスは、オンプレミス ネットワークに物理的に近接しているデバイスに対して、オンプレミス ネットワークの拡張サービスとして提供されます。これには通常、ユーザーが、会議室、他のオフィス、その他の社内の場所など、社内を移動しているときに、モバイル デバイスがネットワーク リソースに接続できる機能が含まれます。また、ユーザーのホーム ネットワークや公共のワイヤレス アクセス ポイントなど、企業が管理していないワイヤレス ネットワーク アクセス ポイントによるリモートの場所からのワイヤレス アクセスも含まれます。ワイヤレス ネットワークへの接続を簡素化するため、管理者は通常、モバイル デバイスがワイヤレス ネットワークに接続するために持つ必要のある固有の設定が示されているワイヤレス プロファイルを使用して、これらの接続を管理します。これには、カスタム ネットワーク名、ネットワークのサービス セット識別子 (SSID)、セキュリティ設定、ネットワーク プロキシ、およびデバイスが範囲内のときに自動的にワイヤレス ネットワークに接続する必要があるかどうかの、自動構成が含まれることがあります。
- 
            **仮想プライベート ネットワーク (VPN):**多くの場合、企業リソースへのセキュリティで保護されたリモート アクセスでは、モバイル デバイスから定義済みの VPN 接続が使用されます。これは多くの場合ベンダー固有であり、モバイル デバイスへの VPN アプリケーションのインストールが含まれます。さらに、これらの VPN アプリケーションは通常、デジタル証明書または別に管理されているユーザー アカウント資格情報を使用して、VPN 接続を認証します。VPN への接続を簡単にするため、管理者は通常、VPN ソリューションに含まれる VPN プロファイルまたは VPN 管理ツールを使用してこれらの接続を管理できます。統合のサポートによっては、モバイル デバイス管理ソリューションでの VPN 接続の管理が、特定の VPN プラットフォームでのオプションである場合とない場合があります。

>[!NOTE]
>安全套接字层 (SSL) または 传输层安全性 (TLS) によるセキュア アクセスを利用する他の 网站 ベース リソース (SharePoint など) がある場合があります。これらのリソースまたは別の やセキュアなアクセス方法を持つリソースにモバイル VPN デバイスがアクセスする方法を理解してください。

### <a name=""></a>ネットワーク接続管理の計画に関する確認事項

ネットワーク接続管理の計画について、次の点を確認します。
 
- どの種類の VPN プラットフォームをオンプレミスのネットワークに展開しますか。
- VPN 的 プラットフォームはサポートされていますか、またはモバイル デバイス管理ソリューションと統合できますか。
- VPN 的 プラットフォームが既存の非モバイル デバイス管理ソリューションによって既に統合またはサポートされている場合、モバイル デバイス管理ソリューションを両方のシステムと統合しますか。
- 増加したデバイス接続および増加した帯域幅需要に対応するために、Wi Fi インフラストラクチャを更新する必要がありますか。
- モバイル デバイスは既存のオンプレミスのワイヤレスまたは VPN プラットフォームにどのような方法で接続しますか。
- モバイル デバイスが既存のワイヤレスまたは VPN プラットフォームに既に接続されている場合、デバイスはどのような接続種類またはプロトコルを使用して接続していますか。
- デバイスをモバイル デバイス管理ソリューションに登録する場合、これらの接続を変更する必要がありますか。
- ワイヤレスまたは VPN プラットフォームへのモバイル デバイスの接続は、管理者またはユーザー （または両方の組み合わせ） が責任を持って行いますか。ユーザーがワイヤレスまたは プラットフォームにモバイル VPN デバイスを接続する場合、次のことをどのようにして行いますか。
 - 企業ネットワークにアクセスするための適切な接続ポイントを選択する。
 - 適切な接続プロトコルまたは接続方法を選択する。
 - 接続方法に適したデジタル証明書を選択する。
- ユーザーのモバイル デバイスでワイヤレスおよび VPN 接続のプロパティと設定を自動的に構成しますか。
 - ユーザー、デバイス、デバイスのオペレーティング システム、またはユーザーのグループおよび役割の異なる種類に対し、異なるワイヤレス ネットワーク構成またはセキュリティ設定を提供する必要がありますか。
 - ワイヤレスおよび VPN の構成やセキュリティ接続ポリシーをインポートまたはエクスポートする機能が必要ですか。

## <a name=""></a>証明書管理

デジタル証明書 （自己署名または第三者証明機関 (CA) による発行） を使用して、ネットワーク接続または特定のネットワーク リソースに対してモバイル デバイスを認証できます。デジタル証明書の管理を簡素するため、通常、管理者は証明書プロファイルを使用して証明書を管理します。これにより、統一された一元的な方法で、証明書が作成、発行、更新される方法などを管理できます。また、企業のリソースに接続するユーザーは、証明書を要求して手動でインストールしたり、承認されていないセキュリティ プロセスを使用したりする必要がなくなります。</para><para>ただし、この種の認証に証明書を使用する場合は、通常、追加のオンプレミス インフラストラクチャ要件が必要になります。モバイル デバイス管理ソリューションでサポートされる統合レベルに応じて、これには、次のネットワーク コンポーネントの全部または一部が含まれます。

- 
            **ディレクトリ サービス︰**他のすべてのネットワーク コンポーネントを安全に接続および管理するには、通常、Microsoft Active Directory などのディレクトリ サービスが必要です。
- 
            **証明機関 (CA) サーバー︰**自己署名証明書を組織に発行する場合、デジタル証明書を作成、発行、管理、更新する証明機関が必要です。
- 
            **ネットワーク デバイス登録サービス (NDES) サーバー︰**このサーバーにより、ソフトウェアとモバイル デバイスは SCEP （简单证书注册协议） に基づいて証明書を取得できるようになります。
- 
            **プロキシ サーバー︰**オンプレミス ネットワークの構成によっては、モバイル デバイスが企業内部ネットワークに直接接続せずに、インターネット接続を使用して証明書を受け取ることができるように、プロキシ サーバーが必要になる場合があります。

### <a name=""></a>証明書管理の計画に関する確認事項

証明書管理の計画について、次の点を確認します。

- 組織は既に、ネットワーク リソースへのアクセスを認証するためのデジタル証明書を要求または使用していますか。
- 既にエンタープライズ公開キー基盤 (PKI) がありますか。
- モバイル デバイスにデジタル証明書を自動的に発行する必要がありますか。
- どのような方法でモバイル デバイスのデジタル証明書を作成、発行、更新、失効しますか。
- (CA) デジタル証明書はオンプレミスまたは第三者の証明機関 によって一元的に管理されていますか。
- 異なるネットワーク サービスにアクセスするために異なる証明書を割り当てる必要がありますか。それは、ネットワークにアクセスするモバイル デバイスの種類に依存しますか。

>[!TIP]
>各回答をメモし、答えの裏側にある論理的根拠を理解します。後の作業で、利用可能なオプションと各オプションの長所と短所を確認します。 これらのことを確認しておくと、ビジネス ニーズに最適なオプションを選択できます。