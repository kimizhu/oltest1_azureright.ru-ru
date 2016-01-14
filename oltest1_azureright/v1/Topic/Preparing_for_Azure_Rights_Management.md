---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Подготовка к установке службы Azure Rights Management
После подписки на облачную службу и создания учетной записи организации для [!INCLUDE[o365_1](../Token/o365_1_md.md)] или Azure Active Directory можно начинать использовать службу [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

Прежде чем это делать, убедитесь в наличии следующего.

-   Учетные записи пользователей и группы в облаке, которые вы создаете вручную или автоматически и синхронизируете из доменных служб Active Directory.

    При синхронизации локальных учетных записей и групп не все атрибуты нужно синхронизировать. Список атрибутов, которые следует синхронизировать с Azure RMS, см. в разделе [Azure RMS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) в документации по Azure Active Directory. Чтобы упростить развертывание, рекомендуется использовать [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) для подключения локальных каталогов к Azure Active Directory, но вы можете использовать и любой другой способ синхронизации каталогов, который обеспечивает такой же результат.

-   Группы с включенной почтой в облаке, которые вы будете использовать с Rights Management. Это могут быть встроенные или созданные вручную группы, содержащие пользователей, которые будут использовать Rights Management.

    Если вы используете Exchange Online, вы можете создавать и применять группы с поддержкой почты с помощью Центра администрирования Exchange. Если вы используете службы AD DS и включена синхронизация с Azure AD, можно создавать и использовать группы с включенной поддержкой почты, которые представляют собой группы безопасности или группы рассылки.

## Включить Rights Management
По умолчанию [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] отключена, когда пользователем регистрируется учетная запись для [!INCLUDE[o365_2](../Token/o365_2_md.md)] или Azure AD. Чтобы использовать [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации, необходимо активировать службу. Дополнительные сведения см. в [Активация управления правами Azure](../Topic/Activating_Azure_Rights_Management.md).

## См. также
[Настройка службы Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

