---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Настройка суперпользователей для Azure Rights Management и служб обнаружения или восстановления данных
Функция суперпользователя Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) гарантирует, что авторизованные пользователи и службы всегда смогут прочитать и проверить данные вашей организации, которые защищает служба Azure RMS. И, при необходимости, вы сможете удалить или изменить уровень защиты, который был настроен ранее. У суперпользователя всегда полные права владельца для всех лицензий, которые были выданы клиенту RMS организации. Данная возможность иногда называется "обоснование на основе данных" и является ключевым элементом при обеспечении контроля за данными вашей организации. Например, эта функция будет использоваться в следующих сценариях.

-   Сотрудник увольняется из организации, и вам нужно прочитать файлы, которые были им защищены.

-   ИТ-администратор должен удалить текущую политику защиты, настроенную для файлов, и применить новую политику.

-   Exchange Server необходимо индексировать почтовые ящики индекса для операций поиска.

-   Вы используете ИТ-службы для решений защиты от потери данных, шлюзов шифрования содержимого и продуктов защиты от вредоносных программ, которым необходимо проверять файлы, которые уже защищены.

-   Вам требуется выполнить массовую расшифровку файлов для аудита, в юридических или других целях.

По умолчанию функция суперпользователя не включена и не назначена пользователям. Она включается автоматически при настройке соединителя Rights Management для Exchange и не требуется для стандартных служб под управлением Exchange Online, SharePoint Online или SharePoint Server.

Если вам необходимо вручную включить функцию суперпользователя, выполните командлет Windows PowerShell [Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), а затем назначьте пользователей (или учетные записи служб) с помощью командлета [Add-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx). В вашей организации может быть один или несколько суперпользователей, но при этом необходимо добавить отдельных пользователей, так как группы не поддерживаются.

> [!NOTE]
> Если вы еще не установили модуль Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], см. раздел [Установка Windows PowerShell для Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Рекомендации по безопасности для функции суперпользователя:

-   Ограничьте и отслеживайте администраторов, которым назначена роль глобального администратора для вашего клиента Office 365 или Azure RMS или которым назначена роль GlobalAdministrator с помощью командлета [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx). Эти пользователи могут включить функцию суперпользователя, назначить себя в качестве суперпользователей и потенциально расшифровать все файлы, которые защищает ваша организация.

-   Чтобы узнать, какие пользователи и учетные записи служб назначены как суперпользователи, выполните командлет [Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Как и все действия администрирования, включение или отключение функции суперпользователя, а также добавление и удаление суперпользователей записываются в журнал. Эти операции можно просмотреть с помощью команды [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx). Если суперпользователи расшифровывают файлы, это действие записывается в журнал и может быть проверено в [журнале использования](https://technet.microsoft.com/library/dn529121.aspx).

-   Если функция суперпользователя не требуется для повседневных служб, включайте ее, когда она необходима, и отключайте ее с помощью командлета [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx).

В следующем фрагменте журнала показаны некоторые примеры записей, отображаемых командлетом Get-AadrmAdminLog. В этом примере администратор Contoso Ltd убеждается, что функция суперпользователя отключена, добавляет Ричарда Симоне как суперпользователя, проверяет, что Ричард — единственный суперпользователь, настроенный для Azure RMS, и затем включает функцию суперпользователя, чтобы Ричард мог расшифровать некоторые файлы, которые были защищены сотрудником, уволившимся из компании.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Параметры создания скриптов для суперпользователей
Часто тем, кто назначается суперпользователем для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], будет необходимо удалить защиту для нескольких файлов в различных местах. Хотя это можно сделать вручную, более эффективно (и часто более надежно) использовать для этого скрипт. Для этого [скачайте средство защиты RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Затем выполните командлеты [Unprotect-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) и [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx).

> [!IMPORTANT]
> Хотя средство защиты RMS предназначено для массовой отмены защиты файлов суперпользователями для восстановления, текущая версия средства не поддерживает проверку подлинности пользователя для Azure RMS. Пока это ограничение не будет устранено, для отмены защиты файлов необходимо использовать учетную запись участника службы для проверки подлинности в службе Azure RMS.  Дополнительные сведения и инструкции см. в разделе [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Дополнительные сведения об этих командлетах см. в разделе [Командлеты защиты RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Модуль RMSProtection Windows PowerShell, который поставляется со средством защиты RMS, отличается от главного [модуля Windows PowerShell для Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx) и дополняет его. Он поддерживает Azure RMS и AD RMS.

## См. также
[Настройка службы Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

