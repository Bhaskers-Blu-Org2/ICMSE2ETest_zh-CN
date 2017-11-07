---
title: "Intune と 配置管理器 による条件付きアクセスの使用"
description: "配置管理器 ソリューションで Intune を展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e65a0662-33ff-4e8c-9305-a21e80ea0f69
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: db5c3899deebf3e85142a653673bf9b0c3a20af5
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="intune-configuration-manager-"></a>Intune と 配置管理器 による条件付きアクセスの使用
このトピックは、電子メールへのアクセスを管理するために、社内でオンプレミスの 系统中心配置管理器 と Microsoft Exchange Server、Exchange Online、または両方のハイブリッド展開を既に使用していることを前提としています。このソリューションでは、場所に関係なくあらゆる種類のデバイスで電子メールへのアクセスを安全に管理するために、既存の 配置管理器環境と Intune を組み合わせて使用します。

> [!TIP]
> このトピック全体のダウンロード可能なコピーは、 [TechNet ギャラリー](https://gallery.technet.microsoft.com/Deploying-Enterprise-16499404)から入手できます。

## <a name=""></a>始める前に
条件付きアクセスの使用を開始する前に、次の該当する要件を満たしていることを確認してください。

## <a name="exchange-online-"></a>Exchange 的联机 の場合
Exchange 的联机 への条件付きのアクセスでは、次を実行するデバイスがサポートされます。

-   Windows 8.1 以降 (Intune に登録されている場合)

-   Windows 7.0 以降 （ドメインに参加している場合）

-   Windows Phone 8.1 以降

-   iOS 7.1 以降

-   Android 的 4.0 版以降、Samsung Knox 标准 4.0 以降

さらに、デバイスを Azure Active Directory 设备注册服务 (AAD DRS) に登録する必要があります。

AAD DRS は、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。ADFS 设备注册服务 をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。

-   交换在线 を含む Office 365 サブスクリプション (E3 など) を使用する必要があります。ユーザーには 交换在线 のライセンスが必要です。

-   オプションの**Microsoft Intune 服务到服务接口**は、Intune を Microsoft Exchange Online に接続します。これにより、Intune コンソールを使用してデバイス情報を管理できるようになります （「[Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)」を参照してください）。コンプライアンス ポリシーまたは条件付きアクセス ポリシーを使用するうえでコネクタを使用する必要はありませんが、条件付きアクセスの影響を評価するためのレポートの実行に必要です。

    コネクタを構成すると、Intune の一部の Exchange ActiveSync ポリシーが 办公室 コンソールに表示される場合がありますが、既定のポリシーとして設定されないため、デバイスへの影響はありません。

    > [!IMPORTANT]
    > 交换到服务接口的在线 と 交换内部 の両方で条件付きアクセスを使用する場合は、Service を構成しないでください。

    これで、[Intune を使用して Exchange 在线 を展開する](conditional-access-intune-exchange-online.md)方法を学習する準備が整いました。

## <a name="-exchange-server-"></a>オンプレミスの Exchange Server の場合
交换内部 への条件付きアクセスでは、次のデバイスをサポートします。

-   Windows 8 以降 (Intune に登録されている場合)

-   Windows Phone 8 以降

-   Exchange ActiveSync (EAS) 電子メール クライアントを使用する iOS デバイス

-   Android 的 4 以降

補足︰

-   Exchange のバージョンは、Exchange 2010 以降である必要があります。Exchange Server クライアント アクセス サーバー (CAS) 構成がサポートされています。

    > [!TIP]
    > 交换環境が CA サーバー構成の場合は、CAS サーバーのいずれかを指すようにオンプレミスの Exchange 连接器 を構成する必要があります。

-   Exchange ActiveSync は、証明書ベースの認証またはユーザーの資格情報のエントリで構成できます。

-   Intune をオンプレミスの Microsoft Exchange Server に接続する**オンプレミスの 交换连接器**を使用する必要があります。これにより、Intune コンソールからデバイスを管理できるようになります （「[Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)」を参照してください）。

  > [!IMPORTANT]
> 最新バージョンのオンプレミス Exchange 连接器 を使用していることを確認します。Intune コンソールで利用可能なオンプレミスの Exchange 连接器 は、Intune テナントに固有であり、他のテナントでは使用できません。また、テナントの 交换连接器 は複数ではなく 1 台のコンピューターにのみインストールされるようにしてください。

  これで、[Intune Exchange Server を使用してオンプレミスの を展開する](conditional-access-intune-exchange.md)方法を学習する準備が整いました。

環境に 交换在线 と 交换内部 の両方が含まれている場合は、[Microsoft Intune と 配置管理器 を使用した Exchange 联机 と Exchange 部署 の展開](conditional-access-intune-configmgr-coexist.md)についてお読みください。
