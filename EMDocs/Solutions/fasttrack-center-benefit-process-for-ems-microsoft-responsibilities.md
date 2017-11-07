---
title: "企业移动套件用 FastTrack センター特典のプロセス-Microsoft の責任範囲"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: ccb750d2bc1cfe59875ec46517114378b991e08b
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="enterprise-mobility-suite-fasttrack---microsoft-"></a>企业移动套件用 FastTrack センター特典のプロセス-Microsoft の責任範囲
次のセクションでは、[企业移动套件 (EMS) 用の FastTrack センター特典](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md)を使用して Azure Active Directory Premium、Microsoft Intune、および Azure 权限管理 を準備している組織に対して、Microsoft が提供するサービスについて説明します。

FastTrack オンボーディング プロセスの他の部分については、「[FastTrack 中心福利企业移动套件 (EMS) 的流程 (企业移动套件 (EMS) 用 FastTrack センター特典のプロセス)](fasttrack-center-benefit-process-for-enterprise-mobility-suite-ems.md)」を参照してください。


## <a name=""></a>全般

-   必要な構成アクティビティのための遠隔サポート アシスタンスを提供します。その内容については、フェーズの詳細な説明で一覧表示しています。

-   構成タスクを軽減または省略するために、利用可能な説明書およびソフトウェア ツール、管理コンソール、およびスクリプトを提供します。

## <a name=""></a>開始フェーズ

-   新規テナントの対象ライセンスのご購入から 30 日以内にご連絡します。

-   お客様と連携してオンボーディングを開始します。

-   オンボーディングする対象のサービスを選定します。

## <a name=""></a>評価フェーズ

-   管理上の概要を示します。

-   次の点に関するガイダンスを行います。

    -   DNS、ネットワーク、およびインフラストラクチャのニーズ。

    -   クライアントのニーズ （インターネット ブラウザー、クライアント オペレーティング システム、およびサービスのニーズ）。

    -   ユーザー ID およびプロビジョニング。

    -   購入済みでオンボーディングの一部として規定されている対象サービスの有効化。

-   修復アクティビティのタイムラインの設定。

-   修復チェックリストの提供。

## <a name=""></a>修復フェーズ

-   修復アクティビティの進捗状況を確認するために、あらかじめ合意したスケジュールに従って電話会議を行います。

-   問題を特定および修復するツールの実行、およびその結果の分析を支援します。

## <a name=""></a>有効化フェーズ
次の点に関するガイダンスを行います。

-   Microsoft 在线服务 テナントのアクティブ化。

-   TCP/IP プロトコルとファイアウォール ポートの構成。

-   対象サービスの DNS の構成。

-   Microsoft 在线服务 への接続の検証。

-   フォレスト環境が 1 つの場合︰ 

    -   Active Directory ドメイン サービス (AD DS) と対象の Microsoft 在线服务 との間のディレクトリ同期サーバーの設置 （必要な場合）。

    -   Azure 的 Active Directory 连接 ツールを使用した Microsoft Intune (Azure Active Directory) へのパスワード同期 （パスワードのハッシュ） の構成。

        > [!NOTE]
        > カスタム ルール拡張機能の開発と実装は対象外です。

-   フォレストが 1 つで、フェデレーション ID を対象とする場合:単一サイトのフォールト トレラント構成における Microsoft Intune を使用したローカル ドメイン認証用に Active Directory フェデレーション サービス (AD FS) のインストールおよび構成 （必要な場合）。

    > [!NOTE]
    > フォレストが複数あるすべての構成において、AD FS の展開は対象外です。

-   シングル サインオン (SSO) 機能のテスト （展開されている場合）。

### <a name="---azure-active-directory-premium"></a>有効化フェーズ-Azure Active Directory 津贴

次の点に関するガイダンスを行います。

-   Microsoft Azure Active Directory 特优 テナントの有効化。

-   ファイアウォール ポートの構成。

-   対象サービスの DNS の構成。

-   Microsoft Azure Active Directory 特优 サービスへの接続の検証。

-   フォレスト環境が 1 つの場合︰ 

    -   Active Directory ドメイン サービス (AD DS) と Azure Active Directory 连接 との間のディレクトリ同期サーバーの設置 （必要な場合）。

    -   Azure 目录连接 ツールを使用したパスワード同期の構成。

-   複数のフォレスト環境の場合︰

    -   Azure 的 Active Directory 连接同期のインストールと複数フォレストのシナリオのための設定。パスワード ハッシュ同期とパスワード書き戻しは複数のフォレストに対応しています。 ただし、その他の書き戻しシナリオはサポートされていません。

    -   オンプレミスの 活动目录 フォレストと Microsoft Azure Active Directory 津贴 (Azure Active Directory) ディレクトリ の間の同期の構成。

        > [!NOTE] 
        > カスタム ルール拡張機能の開発と実装は対象外です。

-   フォレストが 1 つで、フェデレーション ID を対象とする場合︰ 単一サイトのフォールト トレラント構成における Microsoft Azure AD 特优 を使用したローカル ドメイン認証用の Active Directory フェデレーション サービス (AD FS) のインストールおよび構成 （必要な場合）。

    > [!NOTE] 
    > フォレストが複数あるすべての構成において、AD FS の展開は対象外です。

-   シングル サインオン (SSO) 機能のテスト （展開されている場合）。

### <a name="---azure-active-directory-premium--azure-active-directory-connect-active-directory-ad-fs-"></a>有効化フェーズ-Azure Active Directory 特优 — Azure Active Directory 连接 と Active Directory フェデレーション サービス (AD FS) を使用

設定に関するガイダンスを提供します。

-   ライセンシングを含む、ユーザー プロビジョニング。

-   Azure 的 Active Directory 连接 ディレクトリ同期 （パスワード書き戻しとパスワード ハッシュ同期あり）。

-   Active Directory フェデレーション サービス (AD FS)。

- セルフサービスのパスワード リセット (SSPR)。

- Azure 多要素認証 (MFA)。

- SaaS アプリケーションのシングル サインオンを含めることのできる 1 つの統合アプリケーション。

- 管理者への使用方法とセキュリティの報告。

- セルフサービスのグループ管理 (SSGM)。

- アプリケーション プロキシ。

- 管理者通知。

- ロゴ、テキスト、画像を含む、カスタマイズされたログオン画面。
 
### <a name="-microsoft-intune"></a>有効化フェーズ – Microsoft Intune
次の点に関してガイダンスを提供します。

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

        -   電子メール プロファイルの展開。

        -   適用対象となる場合の Microsoft Intune Exchange 连接器 の設定。

    -   サポートされているプラットフォームごとに最大 2 つのテスト デバイスを Microsoft Intune サービスで Microsoft Intune または に登録。 配置管理器

    -   ハードウェアとソフトウェアのインベントリ レポートの使用。

-   モバイル アプリケーション管理 (MAM) がスコープ内にある場合、または MAM ポリシーで既存のサードパーティ製 MDM ソリューションを補完しようとする場合は、次の点に関するガイダンスを提供します。

    -   サポートされているプラットフォームごとの MAM ポリシーの構成。

    -   管理対象アプリの条件付きアクセス ポリシーの構成。

    -   上記の MAM ポリシーを使用した適切なユーザー グループのターゲット設定。

    -   マネージ アプリケーションの使用状況レポートの使用。

-   PC 管理がスコープ内にある場合は、次の点に関してガイダンスを提供します。

    -   必要に応じた Intune クライアント ソフトウェアのインストール。

    -   Intune で利用できるソフトウェアとハードウェアのレポートの使用。

### <a name="---azure-right-management-premium"></a>有効化フェーズ-Azure 的适当管理津贴

次の点に関するガイダンスを行います。

-   Azure RMS テナントのアクティブ化。

-   テンプレートを管理する情報セキュリティ管理者の追加。

-   Azure RMS へのスーパー ユーザー アカウントの割り当て。

-   Azure RMS の 2 人のパイロット ユーザーのライセンシング。

-   ポリシーを検証するための 2 つのテスト配布グループの構成。

-   ディレクトリ用の 1 つのカスタム Azure RMS テンプレートの構成。

-   次を含む、Azure RMS との SharePoint 在线 および Exchange 在线 の統合の設定に関するガイダンス。

    -   Azure RMS と Exchange 在线 の統合の構成および検証。

    -   組織外の受信者に送信する機密性の高いメッセージを暗号化する 1 つのテスト メール フロー ルールの設定。

    -   Azure RMS で保護する 1 つのテスト ライブラリの SharePoint 在线保護の構成および検証。

-   RMS コネクタを使用した 1 台のオンプレミス サーバーの構成 （適用対象となる場合）。

    -   Azure RMS Exchange 2013 2010-の統合の構成および検証。 とオンプレミスの

    -   コネクタを使用した組織外の受信者に送信する機密性の高いメッセージを暗号化する 1 つのテスト メール フロー ルールの設定。

    -   Azure RMS で保護する 1 つのテスト ライブラリのオンプレミスの SharePoint 2013 2010-保護の構成および検証。

-   Windows デバイスおよび Windows 以外のデバイス用の RMS 共有アプリケーションの設定。

FastTrack のオンボーディング プロセスの次のパート「[お客様の責任](fasttrack-center-benefit-process-for-ems-your-responsibilities.md)」を参照してください。

### <a name=""></a>詳細な情報をご希望ですか？
「[企业移动套件](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。。

