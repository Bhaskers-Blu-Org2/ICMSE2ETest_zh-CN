---
title: "Experiência 执行 usuário 最终 para acesso condicional em dispositivos Io"
description: "Experiência 执行最终 de usuário 的注册商 um dispositivo Io。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c641ea8-2c0e-490e-b1de-831336f46d19
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 183e8d9169df969a4667e64fe41f70b389ea4e20
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="ios"></a>iOS

O 处理器 de registro e 作为 telas 汉阳 o usuário vê serão um pouco diferentes dependendo da versão 执行 sistema operacional em execução 最终没有 dispositivo do usuário。 Este tópico descreve experiência 做 usuário 最后段落注册 dispositivos Io。

## <a name="registro"></a>Registro

1.  Se usuário já estiver registrado compatível，ele não verá nenhuma diferença em dispositivos 为没有 Intune e 执行 um iOS: o acesso aos 电子邮件 continuará normalmente。 Se o usuário ainda não estiver registrado，ele verá uma mensagem de quarentena semelhante este quando iniciar seu aplicativo de 电子邮件︰

    ![Captura de tela mostrando o 通过电子邮件发送 em quarentena 汉阳 o usuário recebe em um dispositivo Io](./media/ProtectEmail/EUX-iOS-Get-Started.PNG)

    Usuário clica em **Comece agora mesmo** para começar 注册 seus dispositivos。

2.  É solicitado 汉阳 o usuário instale o aplicativo 做门户 da Empresa do Intune na respectiva loja de aplicativos。

    ![Captura de tela mostrando o 门户 da empresa 的执行 Intune 全身 um dispositivo Io](./media/ProtectEmail/EUX-iOS-intune-Company-Portal.png)

    Depois de instalado，o usuário abre o aplicativo e entra usando suas credenciais da empresa。

3.  Na tela de Configuração de Acesso da Empresa、 o usuário clica em **Iniciar** para começar configurar seu dispositivo e verificar se é ele compatível。

    ![Captura de tela mostrando Configuração de Acesso da Empresa em tela um dispositivo Io](./media/ProtectEmail/EUX-iOS-company-AccessSetup.png)

4.  Na tela de registro 做 dispositivo，o usuário clica em **Registro**段注册 seu dispositivo。

    ![Captura de tela mostrando tela Registro 的执行 Dispositivo em um dispositivo Io](./media/ProtectEmail/EUX-iOS-device-Enrollment.png)

    Durante o registro、 o perfil de Gerenciamento de Dispositivo Móvel é instalado para permitir 汉阳 você o administrador de TI，gerencie remotamente o dispositivo。 O usuário insere sua senha se solicitada。

5.  Na tela de Configuração de Acesso da Empresa，o usuário clica em **Continuar** para iniciar verificação de conformidade do dispositivo。

    ![Captura de tela mostrando 汉阳 o registro de dispositivo foi bem sucedido em um dispositivo iOS e o usuário precisa verificar conformidade](./media/ProtectEmail/EUX-iOS-device-Compliance-Check.png)

    Se houver em **Verificar Conformidade** para continuar um problema de conformidade，será solicitado 汉阳 o usuário resolva o problema (como criar uma senha válida) e，em seguida 团。

    ![Captura de tela mostrando 汉阳 o usuário deve 解析器 problemas de conformidade em um dispositivo Io](./media/ProtectEmail/EUX-iOS-check-Compliance.png)

6.  Depois 汉阳 o dispositivo estiver totalmente compatível，o usuário clica em **Continuar** para continuar。

    ![Captura de tela mostrando 汉阳 o dispositivo iOS é compatível e instalação foi concluída](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    Depois 汉阳 o usuário estiver registrado e verificada，o acesso ao 电子邮件 deverá ficar disponível dentro de alguns minutos 为 conformidade。

Se o usuário seguir essas etapas 段注册 e ficar compatível e ainda não puder acessar seus 发没有 dispositivo móvel，ele poderá seguir estas etapas adicionais para tentar corrigir o problema 电子邮件︰

-   Primeiro，verifique se seu dispositivo está registrado。 Caso contrário，作为 etapas acima o usuário deve seguir。

-   Verifique se o dispositivo é compatível clicando em **Verificar conformidade**。 Se um 错误 de conformidade identificado，instruções específicas 段 seu dispositivo móvel sobre como resolvê-la，tal 作为 o usuário poderá seguir 的 como sua redefinir senha。

-   Ligue para o suporte técnico。

## <a name="problemas-e-solues"></a>Problemas e soluções
Por padrão，cada 8 horas os dispositivos 圣保罗 verificados para verificar se eles ainda 圣保罗 compatíveis。 Se um dispositivo 汉阳时代 anteriormente compatível o usuário pode seguir estas etapas para restaurar conformidade considerado incompatível (por exemplo，devido uma política de conformidade ter sido adicionada ou alterada)，为执行 dispositivo:

1.  O usuário recebe notificação por 电子邮件的 ou 全身 seu dispositivo 汉阳 este é incompatível。 Neste momento，o dispositivo está em quarentena 没有交换。

2.  Se o usuário tentar acessar o 电子邮件、 一 tela ele será redirecionado para de Configuração de Acesso da Empresa do 门户 da Empresa 不要 Intune 全身汉阳 se é mostrado se eles estão de conformidade 的。

    ![Captura de tela mostrando 汉阳 o dispositivo iOS se tornou não compatível](./media/ProtectEmail/EUX-iOS-fallOut-Compliance.png)

3.  Usuário clica em **Continuar** e o problema de conformidade 汉阳 está impedindo 汉阳 ele acesse o 电子邮件 é mostrado。

    ![Captura de tela mostrando 汉阳 o usuário deve 解析器 problemas de conformidade em um dispositivo Io](./media/ProtectEmail/EUX-iOS-check-Compliance.png)

4.  Depois 汉阳 o problema foi corrigido，eles devem clicar em **Verificar Conformidade** para verificar se o problema foi resolvido。

5.  Se o problema estiver corrigido，o usuário clica em **Continuar** para concluir o 处理器。

    ![Captura de tela mostrando 汉阳 o dispositivo iOS é compatível e instalação foi concluída](./media/ProtectEmail/EUX-iOS-compliance-Check-Completed.png)

    O acesso ao 电子邮件 deverá ficar disponível novamente dentro de alguns minutos。

### <a name="onde-ir-daqui"></a>红外线 （ir) daqui Onde
Experiência 执行 usuário 最终 é um pouco diferente em outros dispositivos móveis。 Saiba mais sobre experiência 做 usuário 最后段落[Android](end-user-experience-conditional-access-android.md)电子[Windows Phone](end-user-experience-conditional-access-winphone.md)。
