---
title: "企业移动套件用 FastTrack センター特典のプロセス-フェーズ"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e51f030b-8b08-4fea-96c9-d4ded435a264
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: f601be574812c0ca0b64c731324baba73c022abc
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="enterprise-mobility-suite-fasttrack---"></a>企业移动套件用 FastTrack センター特典のプロセス-フェーズ

            [Enterprise Mobility Suite (EMS) 用の FastTrack センター特典](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md)を使用して、Azure Active Directory Premium、Microsoft Intune、および Azure Rights Management を準備する場合、そのプロセスには複数のフェーズがあります。 次のセクションでは、オンボーディング プロセスの各フェーズについて説明します。

FastTrack オンボーディング プロセスの他の部分については、「[FastTrack 中心福利企业移动套件 (EMS) 的流程 (企业移动套件 (EMS) 用 FastTrack センター特典のプロセス)](fasttrack-center-benefit-process-for-enterprise-mobility-suite-ems.md)」を参照してください。


次の図に示すように、オンボーディングには 4 つのプライマリ フェーズがあります。


![FastTrack オンボーディング プロセスの 4 つのフェーズ](./media/ft-2-onboarding-phases.png)


## <a name=""></a>開始フェーズ

適切な数のライセンスを購入した後、購入確認メールのガイダンスに従って、ライセンスを既存または新規のテナントに関連付けます。Microsoft はお客様が FastTrack センター特典の対象かどうかを確認し、対象の方にオンボーディング アシスタンスを提供する旨をお知らせいたします。これらのサービスを組織で展開する準備ができている場合は、 [FastTrack センター](http://fasttrack.microsoft.com/)からサポートをご依頼いただくこともできます。サポートを依頼するには、[FastTrack センター](http://fasttrack.microsoft.com/) (http://fasttrack.microsoft.com) [プラン] にサインインし、ダッシュボードを開き、 タブ、 [Microsoft Intune、Azure Premium、または Azure Active Directory 权限管理津贴 のサポートを依頼] の順にクリックしてください。オンボーディング サポートが開始したなら、オンライン会議のスケジュールを立てることになります。

このフェーズで、お客様といっしょにオンボーディング プロセスについて話し合い、データを検証し、キックオフ ミーティングの日付を設定します。

![オンボーディングの開始フェーズ](./media/ft-3-initiate-phase.png)

## <a name=""></a>評価フェーズ

オンボーディング プロセスが開始すると、Microsoft はお客様といっしょにソース環境および要件を評価します。ツールを実行してデータを収集した後、Microsoft はオンプレミス 活动的 Directory、インターネット ブラウザー、クライアント デバイスのオペレーティング システム、DNS、ネットワーク、インフラストラクチャ、および ID システムを評価して、オンボーディングを行うために変更の必要があるかどうかを判断します。

また、対象サービスの導入を成功に導く方法に関するガイダンスも紹介します。

現在のセットアップ環境に基づいて、ご使用のソース環境を EMS またはその個別のクラウド サービスへと正常にオンボーディングするために必要な最低要件を満たすような修復プランを提供します。また、修復フェーズのための適切なチェックポイント電話会議を設定します。

![オンボーディングの評価フェーズ](./media/ft-4-assess-phase.png)

## <a name=""></a>修復フェーズ
必要であれば、ソース環境で修復プランの作業を行い、各サービスのオンボーディングと導入を行うための要件を満たすことができます。

![オンボーディングの修復フェーズ](./media/ft-5-remediate-phase.png)

有効化フェーズを開始する前に、修復アクティビティの結果をいっしょに検証して、先に進む準備ができているかを確認します。

## <a name=""></a>有効化フェーズ
すべての修復アクティビティが完了すると、プロジェクトはサービス利用のためのコア インフラストラクチャの構成、および対象となる各 EMS クラウド サービスのプロビジョニングへとシフトします。

**有効化フェーズ-コア機能**

コア オンボーディングには、サービスのプロビジョニングおよびテナントと ID の統合が含まれます。これには、Azure Premium、Microsoft Intune、Azure Active Directory 权限管理津贴 など、オンライン サービスをオンボーディングするための基礎を提供するステップも含まれます。

![オンボーディングの有効化フェーズ-コア機能](./media/ft-6-enable-phase-core.png)

###<a name="---azure-active-directory-premium"></a>有効化フェーズ-Azure Active Directory 津贴

Azure 的 Active Directory 特优環境は、必要に応じて、Azure Active Directory 连接 ツール ディレクトリ同期と Active Directory フェデレーション サービス (AD FS) を使用してセットアップできます。

オンプレミス ID をクラウドに同期する Azure Active Directory 特优 シナリオの場合、IT 管理者とユーザーのサブスクリプションへの追加、管理前提条件の構成、Azure Active Directory 特优 の設定、Azure Active Directory 连接 ツールによるディレクトリ同期の設定、Azure 活动目录连接 ツールによる Active Directory フェデレーション サービス (AD FS) の設定、テスト ユーザーの構成、サービスのコア ユース ケースの検証を Microsoft が支援します。

Azure 的 Active Directory 特优設定では、次の機能を有効化します。

-   セルフサービスのパスワード リセット (SSPR)

-   Azure 多要素認証 (MFA)

-   サービスとしてのソフトウェア (SaaS) アプリケーション- [Azure Active Directory 市场](https://azure.microsoft.com/marketplace/active-directory/)からの 1 つの SaaS アプリケーションのセットアップ

-   セルフサービスのグループ管理 (SSGM)

-   管理レポート

![オンボーディングの有効化フェーズ-AADP](./media/ft-7-enable-phase-aadp.png)

###<a name="-microsoft-intune"></a>有効化フェーズ – Microsoft Intune

Microsoft Intune の場合、モバイル デバイスとモバイル アプリケーション管理のニーズに基づき、Microsoft Intune を使用してデバイスを管理できるようにする手順をご案内します。そのために行う実際のステップは、ご使用のソース環境によって異なりますが、一般に以下の作業が含まれます。

-   エンド ユーザーのライセンシング。必要に応じて、Microsoft クラウド サービス テナントのボリューム ライセンスをアクティブ化する方法のサポートも提供します。

-   オンプレミスの 活动目录 ID またはクラウド ID のいずれかを活用した、Microsoft Intune で使用される ID の構成。

-   Microsoft Intune サブスクリプションへのユーザーの追加、IT 管理者ロールの定義、およびユーザーとデバイスのグループの作成。

-   管理ニーズに基づいたモバイル デバイス管理機関の構成︰

    -   Microsoft Intune が唯一の MDM ソリューションであるか、Office 365 のモバイル デバイス管理と併用される場合は、Microsoft Intune を MDM 機関として設定します。

    -   系统中心配置管理器 の既存の実装があり、Microsoft Intune を使用した管理機能を拡張しようとする場合は、Configuration 管理器 を MDM 機関として設定します。

        > [!NOTE]
        > エンドユーザー所有のデバイス、共有デバイス、またはキオスク型デバイス全体でモバイル アプリケーション管理のみを活用しようとする場合は、MDM 機関を設定する必要はありません。

-   モバイル デバイス管理がスコープ内にある場合は、次の点に関してガイダンスを提供します。

    -   MDM 管理ポリシーの検証に使用するテスト グループの構成。

    -   次のような MDM 管理ポリシーとサービスの構成。

        -   网站 リンクまたはディープ リンクでサポートされているプラットフォームごとのアプリケーション展開。

        -   条件付きアクセス ポリシー。

        -   メール、Wi Fi、VPN プロファイルの展開。

        -   適用対象となる場合の Microsoft Intune Exchange 连接器 の設定。

    -   
            [サポートされているプラットフォーム](https://technet.microsoft.com/library/dn600287.aspx)ごとにデバイスを Microsoft Intune サービスで Microsoft Intune または に登録。 配置管理器

-   モバイル アプリケーション管理 (MAM) がスコープ内にある場合、または MAM ポリシーで既存の Microsoft ソリューションまたはサードパーティ製 MDM ソリューションを補完しようとする場合は、次の点に関するガイダンスを提供します。

    -   サポートされているプラットフォームごとの MAM ポリシーの構成。

    -   管理対象アプリの条件付きアクセス ポリシーの構成。

    -   上記の MAM ポリシーを使用した適切なユーザー グループのターゲット設定。

    -   マネージ アプリケーションの使用状況レポートの使用。

-   PC 管理がスコープ内にある場合は、次の点に関してガイダンスを提供します。

    -   必要に応じた Intune クライアント ソフトウェアのインストール。

    -   Intune で利用できるソフトウェアとハードウェアのレポートの使用。

また、対象サービスの導入を成功に導く方法に関するガイダンスも紹介します。

![オンボーディングの有効化フェーズ-Intune](./media/ft-8-enable-phase-intune.png)

###<a name="---azure-right-management-premium"></a>有効化フェーズ-Azure 的适当管理津贴

Azure 的适当管理津贴環境は、必要に応じて、Azure Active Directory 连接 ディレクトリ同期と Active Directory フェデレーション サービス (AD FS) を使用してセットアップできます。

オンプレミス ID をクラウドに同期する AzRMS シナリオの場合、IT 管理者とユーザーのサブスクリプションへの追加、管理前提条件の構成、Azure 正确的管理增值 の設定、Azure Active Directory 连接 ツールによるディレクトリ同期の設定、Azure 活动目录连接 による Active Directory フェデレーション サービスの設定、テスト ユーザーの構成、サービスのコア ユース ケースの検証を Microsoft が支援します。

AzRMS 設定では、次の機能を有効にします。

-   AzRMS サービスの有効化

-   Exchange 联机 と Sharepoint 在线 の IRM 構成

-   オンプレミスの 交换 およびオンプレミスの Sharepoint との 权限管理 コネクタ

-   Windows デバイスおよび Windows 以外のデバイス用の RMS 共有アプリケーション

![オンボーディングの有効化フェーズ-Azure RMS](./media/ft-7-enable-phase-aadp.png)

FastTrack のオンボーディング プロセスの次のパート「[Microsoft の責任](fasttrack-center-benefit-process-for-ems-microsoft-responsibilities.md)」を参照してください。

### <a name=""></a>詳細な情報をご希望ですか？
「[企业移动套件](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。。

