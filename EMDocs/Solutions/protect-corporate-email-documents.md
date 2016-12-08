---
title: "Proteção de 电子 e documentos da empresa"
description: "Permitir 汉阳 apenas dispositivos compatíveis acessem 电子邮件 da sua empresa e protejam o conteúdo e anexos de 电子邮件。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 78d8368e-1bfe-4ac4-991d-467321a76ed7
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: d2d2b5254267af54b9c3f3243104f9bbb3066976
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="proteo-de-emails-e-documentos-corporativos"></a>Proteção de 发电子邮件 e documentos corporativos
Proteção de 电子邮件 corporativo envolve dois objetivos principais:

-   Permitir somente dispositivos compatíveis acessar o 电子邮件 da empresa

-   Proteção 执行 conteúdo de 电子 e anexos

## <a name="permitir-somente-a-dispositivos-compatveis-acessar-o-email-da-empresa"></a>Permitir somente dispositivos compatíveis acessar o 电子邮件 da empresa
Uma etapa importante para proteger dados corporativos é restringir o acesso dispositivos 汉阳 não usem uma senha 彩云，não estejam desbloqueado ou não estejam criptografados。 O Microsoft Intune oferece 与 condições 汉阳 os usuários devem cumprir para obter acesso aos recursos da empresa capacidade de definir。 Isso é conhecido como acesso condicional。

Acesso condicional é determinado por dois tipos de políticas 汉阳 podem ser definidas 没有 Intune:


            **Políticas de conformidade** determinam a conformidade de um dispositivo. Elas avaliam as configurações e as condições, como:

-   
            **针脚 e senhas**: sua TI pode criar regras para exigir senhas 的 antes de desbloquear um dispositivo，como complexidade da senha，expiração de senha e outras configurações de senha。

-   
            **Criptografia**: sua TI pode restringir o acesso dispositivos criptografados。

-   
            **O dispositivo não está desbloqueado ou enraizado**: o Intune pode detectar se um e sua TI pode definir política para bloquear o acesso esses dispositivos-desbloqueado dispositivo registrado está。


            **Políticas de acesso condicional** são configuradas para um serviço específico como o Exchange Online ou no SharePoint Online. Para cada serviço, você pode definir a quais grupos de usuários essas políticas devem ser aplicadas. Por exemplo, você pode garantir que todos no departamento financeiro possam acessar apenas email de dispositivos registrados e compatíveis.

## <a name="experincia-de-alto-nvel-do-usurio-final"></a>Experiência de 市 nível do usuário 最终
Após solução ser implementada，os usuários finais só poderão acessar o 电子邮件 da empresa em dispositivos gerenciados e compatíveis。 没有 ecossistema do aplicativo e ficarão disponíveis apenas 段 os usuários pretendidos，Quando eles tiverem capacidade de acessar o 电子邮件 nos dispositivos，os dados da empresa ficarão protegidos e contidos。 O acesso pode ser revogado incompatível qualquer momento se o dispositivo。

作为 políticas de acesso condicional definidas Especificamente，没有 Intune garantem 汉阳 os dispositivos possam acessar o 电子邮件 somente se forem compatíveis políticas de conformidade 汉阳 você definir 作为 com。 Ações como copiar e colar ou salvar em serviços pessoais de armazenamento na nuvem podem ser restringidas usando políticas de gerenciamento de aplicativos móveis。 O Serviço de gerenciamento de direitos 做 Azure pode ser usado para garantir 汉阳 os dados confidenciais de 邮件，bem como os anexos encaminhados，somente possam ser lidos pelos destinatários pretendidos。 Experiência 执行 usuário 最终 é descrita com mais detalhes em [Experiência 执行 usuário 最终 de acesso condicional](end-user-experience-conditional-access.md)。


Assista [este](https://www.youtube.com/watch?feature=player_embedded&v=lYx3YIezccg) vídeo de quatro minutos para ver como acesso condicional afeta os usuários finais。

## <a name="por-que-a-arquitetura-importante"></a>Por 汉阳 arquitetura é importante
Os diferentes componentes 实现 EMS e o Office 365 圣保罗 criados e projetados para execução na nuvem。 Isso traz todos os benefícios 汉阳 nuvem oferece: escalabilidade，flexibilidade e facilidade de gerenciamento。

Uma vez 汉阳 diferentes empresas têm requisitos diferentes，o EMS foi projetado para integrar se com infraestrutura 的本地 existente，como o Active Directory，o Exchange Server ou o 系统中心配置管理器。 Isso permite 汉阳 você credenciais já estabelecidas em sua para seus recursos locais e na nuvem 作为使用。

作为 seções seguir descrevem arquitetura conforme projetada 段 ser executada na nuvem e falam brevemente sobre opção 本地。

### <a name="fluxo-de-acesso-de-email"></a>Fluxo de acesso de 电子邮件
Dependendo 执行 tipo de aplicativo de 电子邮件汉阳 você 美国 para acessar o Exchange 联机，o caminho para estabelecer acesso seguro ao 电子邮件 pode ser ligeiramente diferente。 没有 entanto，os componentes principais︰ 广告 do Azure (Active Directory do Azure)，Office 365/Exchange 联机电子 Microsoft Intune 圣保罗 os mesmos。 Experiência de TI e experiência do usuário 最终 também 圣保罗 semelhantes。 O EMS atualmente dá suporte aplicativos de 电子邮件 nativos e ao aplicativo Microsoft Outlook para iOS e Android。

### <a name="fluxo-de-controle-de-acesso-para-aplicativos-de-email-nativos"></a>Fluxo de controle de acesso para aplicativos de 电子邮件 nativos
Os clientes seguintes propriedades 作为执行 Exchange ActiveSync (EAS) 汉阳 estiverem tentando acessar 电子邮件没有 Exchange Online 的 serão avaliados 段︰

-   O dispositivo é gerenciado pelo Intune 吗？

-   O dispositivo está registrado com o Active Directory Azure？

-   O dispositivo é compatível？

-   ID EA 做 cliente está mapeada 段 um dispositivo registrado？

Para obter um estado compatível，o dispositivo em 汉阳 o cliente EAS está em execução precisa:

-   注册器 com o Intune

-   Registre se com o [Azure Active Directory](https://msdn.microsoft.com/6a14cb1f-a058-4453-8ede-d9f4a66a7073.aspx)段落

-   Estar em conformidade com políticas de dispositivo definidas por seu administrador de 作为 TI。

Na maioria da plataformas，o registro de dispositivo 不要 Active Directory 做 Azure ocorre automaticamente durante o registro。 Os estados de dispositivo 圣保罗 gravados pelo Intune 没有 Active Directory 不要 Azure e então lidos pelo Exchange Online na próxima vez 汉阳 o cliente EAS tenta obter 电子邮件。 Se o dispositivo não estiver registrado，o usuário receberá uma mensagem na caixa de entrada com instruções sobre como 注册 (também conhecido como registro)。 对于 compatível Se o dispositivo não，o usuário receberá um 电子邮件 diferente 汉阳 o redireciona 段 o 门户的 Web 执行 Intune 全身汉阳 ele poderá obter mais informações sobre o problema de conformidade e da como corrigi-lo。

**Azure AD**autentica o usuário e O o dispositivo Microsoft Intune gerencia 与 políticas de acesso condicional，enquanto o **Exchange Online** gerencia o acesso ao conformidade e 电子基 com 没有 estado do dispositivo。

![Gráfico 汉阳 mostra o fluxo de controle de acesso para aplicativos de 电子邮件 nativos em dispositivos com Android 电子 iOS](./media/ProtectEmail/Access-Control-Flow-For-Native-Email-Apps.png)

### <a name="fluxo-de-controle-de-acesso-para-aplicativos-do-outlook"></a>Fluxo de controle de acesso para aplicativos 不要 Outlook
Semelhante ao cliente EA，o aplicativo de 电子邮件做 Outlook 汉阳 estiver tentando acessar o 电子邮件没有 Exchange Online 的 será avaliado para seguintes propriedades:

-   O dispositivo é gerenciado pelo Intune 吗？

-   O dispositivo está registrado com o Active Directory Azure？

-   O dispositivo é compatível？

Conformidade 执行 dispositivo é estabelecida quase da mesma 预计，conforme descrito 没有 fluxo de controle de acesso de cliente do EAS。 没有 entanto，para aplicativos 做 Outlook，o fluxo entre os componentes é levemente diferente。 Quando o aplicativo Outlook tenta obter o 电子邮件、 ele é redirecionado ao Azure 的广告。 O Azure AD emite um 标记为 avaliado com sucesso como estando registrado e em conformidade de segurança se o dispositivo。 O 标记 de segurança então é usado para obter 电子邮件 corporativo 执行 Exchange 联机。 Sincronização de 电子邮件、 na verdade，é orientada por meio do serviço de nuvem do Outlook、 汉阳 obtém um 令牌 de acesso do serviço EAS em nome do usuário 段 concluir autenticação e entrega o 发送电子邮件。

![Gráfico 汉阳 mostra o fluxo de controle de acesso do aplicativo 不要 Outlook](./media/ProtectEmail/Access-Control-Flow-For-Outlook-App.png)

## <a name="a-experincia-de-administrao-de-ti"></a>Experiência de administração de TI:
Não há necessidade de uma configuração de infraestrutura complexa 段 o Azure AD ou o 交换 para 汉阳 isso aconteça。 Seus administradores de TI:

-   配置为 políticas de conformidade usadas para avaliar o 状态 de conformidade do dispositivo e implante。

-   Configurar política de acesso condicional do 在线交换 e especificar quais grupos de segurança 做广告做 Azure serão afetados por ela ou estão isentos dela。

-   Escolha permitir ou bloquear dispositivos 汉阳 não 圣保罗 capazes de se 注册没有 Intune。 可变 de sistemas operacionais com suporte para dispositivos móveis é apresentada mais adiante。

Pode ser necessária uma etapa de configuração opcional。 O relatório usado para gerenciar e monitorar o 状态 e o acesso ao dispositivo requer configuração do 连接器 de serviços 执行 Microsoft Intune。

## <a name="a-experincia-do-usurio-final"></a>最终的 experiência do usuário:
Quando o usuário tenta acessar 电子邮件没有 dispositivo pela primeira vez ou sincronizar posteriormente，dispositivo é verificado o 状态 de conformidade e de registro。 O 处理器 de 注册 ou corrigir problemas de conformidade é uma experiência guiada。 圣保罗 mostradas ao usuário etapas necessárias 段注册 o dispositivo e torná 作为最终的 lo compatível sem necessidade de chamar o suporte técnico da TI:

-   
            **Se o dispositivo não estiver registrado**，página de 登录 mostrará o acesso negado e solicitará o registro。 没有 registro、 o dispositivo é registrado automaticamente 没有 Active Directory 不要 Azure。 作为 etapas de solução 段解析器 quaisquer problemas de não conformidade O Intune verifica o dispositivo 段片 de conformidade e apresenta。 Depois 汉阳 o dispositivo estiver em conformidade，o Intune 定义 o 状态 de conformidade do dispositivo com o Active Directory 做 Azure。

-   
            **Se o dispositivo estiver registrado、 mas não estiver em conformidade**，将 com etapas para corrigir os problemas é enviado ao dispositivo um 链接。 Quando o usuário 最终 corrige o problema （por exemplo，definir senha，criptografia），作为 políticas de conformidade atualiza o 状态 de conformidade o Intune 汉阳 gerencia 执行 dispositivo 没有 Azure 广告。

Quando o dispositivo é avaliado como registro e em conformidade，sincronização de 电子邮件 deve acontecer dentro de alguns minutos。

## <a name="onde-ir-daqui"></a>红外线 （ir) daqui Onde
Agora 汉阳 você sabe como proteger 电子邮件 e documentos corporativos，pode ler sobre como [proteger anexos de 电子邮件](protect-email-attachments.md)。 Ou，se você estiver pronto，saiba mais sobre [como implementar uma solução para proteger seu 电子邮件 corporativo](implement-solution.md)。
