---
title: "Usando Políticas de Gerenciamento de Aplicativos Móveis 没有 Intune"
description: "Crie e implante um aplicativo 没有 Intune com uma política de gerenciamento de aplicativos móveis。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d7c4104-b85f-407e-8832-0e6bbac934f5
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 24e3953f0625da90dc42c68703ee2433429efbf8
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="usar-polticas-de-gerenciamento-de-aplicativos-mveis-no-intune"></a>Usar Políticas de Gerenciamento de Aplicativos Móveis 没有 Intune
嗯 dos motivos principais pelos quais muitas empresas usam o Microsoft Intune é implantar aplicativos 汉阳 os usuários precisam 段 realizar seu trabalho。 Antes de implantar aplicativos，você precisará [tornar dispositivos seus gerenciados](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)。

Por exemplo，se sua empresa 美国 o Microsoft Word 中，há versões disponíveis 段 Windows、 iOS 和 Android 的 e outros。 O desafio 汉阳 você como um administrador de TI enfrenta é gerenciar variedade de aplicativos disponíveis，em muitas plataformas diferentes de computador e de dispositivo com o objetivo de permitir 汉阳 os usuários façam seu trabalho e simultaneamente，garantir segurança dos seus dados corporativos。

Se estiver usando o Intune com o 配置管理器中，consulte[如何控制应用程序使用移动应用程序管理策略在配置管理器](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396)(Como controlar aplicativos usando políticas de gerenciamento de aplicativos móveis 没有配置管理器)。

为 políticas de MAM (gerenciamento de aplicativos móveis) dão suporte:
- Dispositivos 汉阳 executam o posterior Android 4 e。
- Dispositivos 汉阳 executam o iOS 7 e posterior。

> [!NOTE]
> 作为 políticas de MAM dão suporte dispositivos registrados com o Intune。 段落剑齿虎 mais sobre como criar políticas de gerenciamento de aplicativos para dispositivos 汉阳 não 圣保罗 gerenciados pelo Intune， [Proteger os dados 执行 aplicativo usando políticas de gerenciamento de aplicativos móveis com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)veja。

Diferente de outras políticas 做 Intune，você não implanta uma política de MAM diretamente。 Em vez disso，você associa política ao aplicativo 汉阳 deseja restringir。 Quando o aplicativo é implantado e instalado em dispositivos，configurações especificadas entrarão em 积极作为。

Para aplicar restrições um aplicativo，o aplicativo deve incorporar o SDK （软件开发工具包） 执行 aplicativo Microsoft Intune。 Há dois métodos de obter esse tipo de aplicativo:

- 
            **Usar um aplicativo gerenciado por política** – tem o SDK interno 执行 aplicativo。 Para adicionar este tipo de aplicativo，especifique um 链接段落-o aplicativo de uma loja de aplicativos，como iTunes 商店 ou o Google 播放。 Nenhum processamento adicional é necessário 段 este tipo de aplicativo。 段落 ver lista completa de aplicativos da Microsoft com suporte、 vá 段 galeria de aplicativos móveis 执行 Microsoft Intune na página de [parceiros de aplicativos 执行 Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)。 Clique 没有 aplicativo 段 ver os cenários e plataformas com suporte e se o aplicativo dá suporte várias identidades ou não。
- 
            **Usar um aplicativo"encapsulado"** -aplicativos 汉阳圣保罗 empacotados novamente para incluir o SDK 进行 aplicativo usando Ferramenta de Encapsulamento de Aplicativos do Microsoft Intune。 Normalmente，essa ferramenta é usada para processar aplicativos da empresa criados internamente。 Ele não pode ser usado para processar aplicativos 汉阳 foram baixados da loja de aplicativos。 Consulte:
  - [Preparar aplicativos iOS para o gerenciamento de aplicativos móveis com Ferramenta de disposição de aplicativos 执行 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
  - [Preparar aplicativos Android para o gerenciamento de aplicativos móveis com Ferramenta de Encapsulamento de Aplicativos do Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

Alguns aplicativos gerenciados，como o aplicativo 做 Outlook para iOS e Android，dão suporte**多 identidade**。 作为 configurações de gerenciamento somente dados ou contas corporativas Isso significa 汉阳 Intune aplica 不 aplicativo。

Por exemplo usando o aplicativo 执行 Outlook:
- Se o usuário configurar uma conta de 电子邮件 pessoal e uma corporativa，作为 configurações de gerenciamento apenas à conta corporativa e não gerencia a conta pessoal o Intune aplicará。
- 对于 desativado ou seu registrado cancelado Se o dispositivo，somente dados corporativos 操作系统执行 Outlook serão removidos do dispositivo。
- Conta corporativa usada deve ser mesma conta 汉阳 foi usada 段注册 o dispositivo 没有 Intune。

Word、 Excel 电子 PowerPoint também dão suporte várias identidades，exceto restrições de política 汉阳 se aplicam somente ao gerenciar e editar dados de identificação empresarial de 为 um serviço，como OneDrive ou SharePoint。

## <a name="criar-e-implantar-um-aplicativo-no-intune-com-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Criar e implantar um aplicativo 没有 Intune com uma política de gerenciamento de aplicativos móveis

- Etapa 1: obter o 链接段落 um aplicativo gerenciado por política ou criar um aplicativo encapsulado。
- Etapa 2: publicar o aplicativo em seu espaço de armazenamento de nuvem。
- Etapa 3: criar uma política de gerenciamento de aplicativos móveis。
- Etapa 4: implantar o aplicativo，selecionando opção 的 para associar o aplicativo uma política de gerenciamento de aplicativos móveis。
- Etapa 5: monitorar implantação 进行 aplicativo。

### <a name="etapa-1-obter-o-link-para-um-aplicativo-gerenciado-por-poltica-ou-criar-um-aplicativo-encapsulado"></a>Etapa 1: obter o 链接段落 um aplicativo gerenciado por política ou criar um aplicativo encapsulado
- 
            **Para obter um 链接段落 um aplicativo gerenciado por política** -na Windows 应用商店，encontre e anote URL 执行 aplicativo gerenciado por política 汉阳 você deseja implantar。
Por exemplo URL 执行 aplicativo 执行 Microsoft Word para iPad é [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- 
            **Para criar um aplicativo encapsulado**︰ 用作 informações nos tópicos [Preparar aplicativos iOS para o gerenciamento de aplicativos móveis com Ferramenta de Disposição 执行 Aplicativo 执行 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) e [Preparar aplicativos Android para o gerenciamento de aplicativos móveis com Ferramenta de Disposição 执行 Aplicativo 不要 Intune](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) para criar um aplicativo encapsulado。 Ferramenta cria um aplicativo processado 汉阳 será usado quando você publica o aplicativo 没有 espaço de armazenamento de nuvem。

### <a name="etapa-2-carregar-o-aplicativo-em-seu-espao-de-armazenamento-de-nuvem"></a>Etapa 2: Carregar o aplicativo em seu espaço de armazenamento de nuvem
Quando você publica um aplicativo gerenciado，os procedimentos diferem se você estiver publicando um aplicativo gerenciado por política ou um aplicativo 汉阳 foi processado usando ferramenta de disposição de aplicativos 执行 Microsoft Intune para iOS。

Veja [Adicionar aplicativos para dispositivos móveis 没有 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune#add-the-app) para obter etapas completas necessárias para carregar 为 um aplicativo em seu espaço de armazenamento de nuvem。

### <a name="etapa-3-criar-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Etapa 3: criar uma política de gerenciamento de aplicativos móveis
O 门户执行 Azure é o 控制台 de administração recomendado para criar políticas de MAM。 O 门户执行 Azure dá suporte aos seguintes cenários MAM 操作︰
- Dispositivos registrados 没有 Intune
- Dispositivos gerenciados por uma solução MDM terceirizada
- Dispositivos 汉阳 não 圣保罗 gerenciados por uma solução MDM (BYOD)。

Veja [Criar e implantar políticas de gerenciamento de aplicativo móvel com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) para 剑齿虎 mais sobre o uso 做门户执行 Azure para criar uma política de MAM。

Se 不 momento você estiver usando o 控制台 de administração do Intune para gerenciar seus dispositivos，poderá criar uma política MAM 汉阳 dê suporte aplicativos para dispositivos registrados [de administração 控制台执行 Intune](https://docs.microsoft.com/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console#-step-3-create-a-mobile-application-management-policy)没有 Intune usando o。


### <a name="etapa-4-implantar-o-aplicativo-selecionando-a-opo-para-associar-o-aplicativo-a-uma-poltica-de-gerenciamento-de-aplicativos-mveis"></a>Etapa 4: implantar o aplicativo，selecionando opção 的 para associar o aplicativo uma política de gerenciamento de aplicativos móveis
Se você estiver usando o 门户做 Azure， [implante política de MAM para usuários](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune#deploy-a-policy-to-users)。

Se você estiver usando o 门户执行 Intune， [implante o aplicativo](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune#deploy-an-app)，garantindo 汉阳 você selecione política de gerenciamento de aplicativo móvel na página de Gerenciamento de Aplicativo Móvel para associar política ao aplicativo。

Se o dispositivo tiver o registro 没有 Intune desfeito，políticas não serão removidas dos aplicativos 作为。 Quaisquer aplicativos 汉阳 tiverem políticas aplicadas manterão configurações de política，mesmo depois de ser desinstalado e reinstalado 作为。

#### <a name="o-que-fazer-quando-um-aplicativo-j-est-implantado-em-dispositivos"></a>O 汉阳 fazer quando um aplicativo já está implantado em dispositivos

Pode haver situações em 汉阳 você implantar um aplicativo e um dos usuários ou dispositivos de destino já tem uma versão não gerenciada 执行 aplicativo instalada，por exemplo o usuário instalou o Microsoft Word da loja de aplicativos。

Nesse caso，você deve pedir ao usuário para desinstalar manualmente versão não gerenciada 段汉阳 possa ser instalada versão gerenciada 汉阳 você configurou。

没有 entanto，para dispositivos 汉阳 executam o iOS 9 e versões posteriores，o Intune automaticamente solicitará ao usuário permissão para assumir o gerenciamento do aplicativo existente。 Se eles concordarem，o aplicativo será gerenciado pelo Intune e qualquer política de MAM associada ao aplicativo também será aplicada。


### <a name="etapa-5-monitorar-a-implantao-do-aplicativo-com-a-poltica-de-mam"></a>Etapa 5: monitorar implantação 执行 aplicativo com política de MAM
使用 os procedimentos seguir para monitorar implantação do aplicativo por meio 执行控制台执行 Intune e 解析器 conflitos de política。

1. 没有[控制台 de administração Microsoft Intune](https://manage.microsoft.com/)，团全身**Grupos**。
2. 执行 uma das seguintes etapas:
  -  Clique 全身**Todos os Usuários** e duas vezes 团没有 usuário cujos dispositivos você deseja examinar。 Na página Propriedades 做 Usuário，团 em **Dispositivos** e 团 duas vezes 没有 dispositivo 汉阳 você deseja examinar。
  -  团 em **Todos os Dispositivos > Todos os Dispositivos Móveis**。 Na página Propriedades 做 Grupo de Dispositivos，团 em **Dispositivos** e 团 duas vezes 没有 dispositivo 汉阳 você deseja examinar。
3. Na página Propriedades 不做任何 dispositivo 的 Dispositivo Móvel，团 em **Política**段 ver uma lista das políticas de MAM 汉阳 foram implantados。
4. Selecione política de MAM cujo 状态 você deseja exibir。 Você pode ver detalhes da política configurações 作为没有 painel 劣质 e expandir o nó para exibir。
5.  Na coluna 状态 de cada uma das políticas de MAM，Compatível，Compatível (Pendente) ou 错误 será exibido。 Se política selecionada tiver uma ou mais configurações conflitantes，错误 será exibido nesse campo。
6.  Após ter identificado um conflito，você pode revisar configurações de política conflitantes 段 usar mesma configuração ou 的 implantar apenas uma política 段 o aplicativo e o usuário 作为。

> [!NOTE]
> Você pode 剑齿虎 mais informações gerais sobre monitoramento de aplicativos por meio 做[门户执行 Azure](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) ou usando o[控制台执行 Intune](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune)。

## <a name="onde-ir-daqui"></a>红外线 （ir) daqui Onde

Depois de criar e implantar um aplicativo associado uma política de MAM，você pode 剑齿虎 mais sobre o [experiência 执行 usuário 最终 de MAM](end-user-experience-mam.md)。 Isso ajudará se preparar para problemas 汉阳 possam surgir。
