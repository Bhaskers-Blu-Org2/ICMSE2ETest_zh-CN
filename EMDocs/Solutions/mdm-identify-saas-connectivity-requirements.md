---
title: Identificar requisitos de conectividade de SaaS
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6afbce4c-7500-4387-a19c-dff52c152097
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 15d896671f7687e017180bca2ca6acbd8dd0b0be
ms.sourcegitcommit: 1b0888e015659ad5d1cb408e4af57f1b916d13a3
translationtype: MT
---
# <a name="identificar-requisitos-de-conectividade-de-saas"></a>Identificar requisitos de conectividade de SaaS

>[!NOTE]
>Este tópico faz parte de guia de considerações sobre um 设计 mais amplo。 Se você quiser começar 做 início do guia，confira o [tópico 主体](mdm-design-considerations-guide.md)。 Para obter uma cópia baixável deste guia inteiro，visite [Galeria 不要 TechNet](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)将。

预计 como você conecta sua infraestrutura 本地 afetará 预计 como identidade de usuário e de dispositivo será gerenciada com todas 与 soluções de MDM: Intune，MDM para Office 365 e implantações híbridas do Intune e 不要 ConfigMgr。 Tanto o Intune quanto o MDM para Office 365 aproveitam arquitetura de serviços de diretório fornecida pelos Serviços 做 Azure 活动目录。 Essa integração com o Azure oferece bastante flexibilidade quando você estiver projetando o suporte de gerenciamento de identidades em sua solução de gerenciamento de dispositivos móveis。

作为 listas abaixo Conforme mostra，conexão dos serviços de diretório locais ao Azure é o 主体 requisito para habilitar o 登录 único e o gerenciamento de contas de diretório unificado。 O 登录 único torna muito mais fácil 段 seus usuários se conectarem aos recursos da empresa 汉阳 estão locais e na nuvem。 Ter um único 本地 para gerenciar contas facilita o trabalho dos administradores。 段落-o acesso móvel，sincronizar atributos e credenciais de conta de diretório entre o Azure e os serviços locais de diretório permite 汉阳 os usuários se autentiquem 全身 seus dispositivos móveis para acessar os recursos 汉阳圣保罗 gerenciados pelo MDM 段 Office 365 ou Intune。

![Visão geral 执行 gerenciamento integrado de identidades](./media/MDM_Figure_15.png)

**Visão geral 执行 gerenciamento integrado de identidades**

Dependendo de como você respondeu às perguntas na Tarefa 2，você precisa conseguir determinar como solução de SaaS precisa se conectar à sua plataforma de gerenciamento 本地 de clientes de sua solução de gerenciamento de dispositivos móveis。 作为 listas abaixo ajudarão você 为 vantagens e desvantagens de conectar sua infraestrutura 本地 uma solução entender de SaaS。

## <a name="intune-autnomo"></a>Intune (autônomo)

**Vantagens**

- Totalmente integrado ao Azure Active Directory para gerenciar identidade e autenticação 执行 usuário do e dispositivo
- Dá suporte ao autogerenciamento de credenciais de usuário e experiências de 登录 único 汉阳 podem aproveitar credenciais existentes de conta 本地作为
- Dá suporte 登录 único para milhares de aplicativos SaaS pré integrados
- Dá suporte à segurança de acesso ao aplicativo com a imposição da MFA (autenticação multifator baseada em regras) para aplicativos locais e na nuvem

**Desvantagens**

- Recursos e funcionalidades avançados de conectividade de serviços de diretório exigem o emparelhamento com o Azure 活动目录津贴

## <a name="mdm-para-o-office-365"></a>MDM para o Office 365

**Vantagens**

- Integrado aos locatários Office 365，汉阳 usam estrutura 不要 Azure Active Directory para gerenciar identidade e autenticação de usuário e dispositivo
- Os serviços locais de diretório podem ser conectados como parte da conexão dos serviços ao Office 365
- Dá suporte ao autogerenciamento e experiências de 登录 único 汉阳 podem aproveitar credenciais existentes de conta 本地作为
- Oferece suporte à autorização de multifator para inscrições de dispositivos usando o serviço 不要 Azure MFA

**Desvantagens**

- Não dá suporte à integração 执行 gerenciamento de aplicativos móveis com outras soluções ou aplicativos de SaaS

## <a name="hbrido-intune-com-configmgr"></a>Híbrido (Intune com ConfigMgr)

**Vantagens**

- 作为 vantagens 的 Todas 执行 Intune autônomo，além da seguintes:
 - Integração direta com serviços locais de diretório por meio da infraestrutura 不要 ConfigMgr

**Desvantagens**

- 作为 organizações 汉阳 não tenham uma infraestrutura 段不要 ConfigMgr atual configurada，será necessário planejá-路易斯安娜州，instalá la e configurá la antes da integração com o Intune
- Exige requisitos de implantação 本地 adicional e alterações de configuração para organizações com o ConfigMgr 作为。
