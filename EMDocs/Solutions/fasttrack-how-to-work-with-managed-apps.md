---
title: "組織が管理するモバイル アプリケーションを使用する方法"
description: "組織が管理するモバイル アプリを使用する方法"
keywords: 
author: craigcaseyMSFT
manager: jeffgilb
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 174348f0-dbc6-4204-8626-3c6f38b7bbde
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: fcc80a02d32da5ee45fd645448b0d89a19e9bb7c
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>組織が管理するモバイル アプリを使用する方法

## <a name="ios-onedrive-"></a>iOS デバイスでの OneDrive へのアクセス

业务 を使用して、Intune で管理されているアプリケーションと操作方法が少し違う点について説明します。 的 このセクションでは、例として OneDrive

1.  
            **业务的 OneDrive**アプリを起動し、サインイン ページを開きます。

  ![説明文](./media/ft-useMngdApps-1-launchOnedrive.png)
> [!NOTE]
> 個人用デバイスの場合は、通常、エンドユーザーがアプリをダウンロードします。デバイスが MDM ソリューションで管理されている場合は、管理者がアプリをデバイスに展開できます。

2.  自分の作業アカウントのユーザー名を入力します。        **O365 認証**ページにリダイレクトされたら、作業用の資格情報を入力します。

  ![説明文](./media/ft-useMngdApps-2-enterName.png)
3.  Azure AD によって資格情報が正常に認証されると、MAM ポリシーが適用され、**业务的 OneDrive**アプリを再起動するように求められます。

  ![説明文](./media/ft-useMngdApps-3-restart.png)
> [!NOTE]
> [再起動が必要] ダイアログ ボックスは、Intune に登録されていないデバイスにのみ表示されます。

4.  
            **业务的 OneDrive**アプリを再起動します。MAM ポリシーが有効な状態でアプリが起動されます。次に、アプリの**暗証番号 (PIN)**を設定するように求められます。（ポリシーの構成がそうなっている場合）

  ![説明文](./media/ft-useMngdApps-4-enterPIN.png)
5.  暗証番号 (PIN) を設定して確認すると、**业务的 OneDrive**上のファイルにアクセスできるようになります。

  ![説明文](./media/ft-useMngdApps-5-accessFiles.png)
> [!NOTE]
> 展開済みのポリシーを変更すると、次回アプリを開いたときにその変更が適用されます。

## <a name="android-onedrive-"></a>Android 的 デバイスでの OneDrive へのアクセス
业务 を使用して、Intune で管理されているアプリケーションと操作方法が少し違う点について説明します。 的 このセクションでは、例として OneDrive
1.  
            **业务的 OneDrive**アプリを起動し、サインイン ページを開きます。
> [!NOTE]
> 個人用デバイスの場合は、通常、エンドユーザーがアプリをダウンロードします。デバイスが MDM ソリューションで管理されている場合は、管理者がアプリをデバイスに展開できます。

2.  自分の作業アカウントのユーザー名を入力します。O365 認証ページにリダイレクトされたら、作業用の資格情報を入力します。

  ![説明文](./media/ft-useMngdApps-6-enterCreds.png)
3.  Azure AD によって資格情報が正常に認証されると、まだ会社のポータル アプリがデバイスにインストールされていない場合はインストールするよう指示するメッセージが表示されます。        **[アプリの入手]**をタップして続行します。
> [!NOTE]
> Android 的 デバイス上の MAM ポリシーに関連付けられたすべてのアプリでポータル サイト アプリが必要です。Intune に登録されていないデバイスでは、このアプリをデバイスにインストールする必要がありますが、アプリの起動もサインインも実行する必要はありません。

4.  
            **Google 播放**ストアが開かれるので、そこから**会社のポータル**アプリをダウンロードしてインストールします。

  ![説明文](./media/ft-useMngdApps-7-installPortal.png)

 会社のポータル アプリを使うと、データを安全に保護できます。![説明文](./media/ft-useMngdApps-8-intunePortal.png)
5.  インストールが完了したら、**[承認]**を選択して使用条件を承認します。
6.  
            **业务的 OneDrive**アプリが自動的に起動されます。
7.  对于业务 (PIN) を開くと、暗証番号 を設定するプロンプトが表示されます。 ポリシー設定で**业务的 OneDrive**アプリへのアクセスに**暗証番号 (PIN)**が必要な設定になっている場合は、次回 OneDrive

  ![説明文](./media/ft-useMngdApps-9-setNewPIN.png)
8.  暗証番号 (PIN) が設定されて確認されると、アプリのポリシーで管理されるようになった**业务的 OneDrive**を継続して使用できます。

### <a name=""></a>詳細な情報をご希望ですか？
「[企业移动套件](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。。
