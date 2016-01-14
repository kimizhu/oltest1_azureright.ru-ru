---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Стратегия развертывания Azure Rights Management
Для подготовки, реализации и обслуживания Azure Rights Management (Azure RMS) в организации выполните следующие действия.

Если требуется быстро попробовать Azure RMS для себя, а не разворачивать службу в рабочей среде, см. раздел [Учебник по быстрому запуску для Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Перед выполнением этих действий ознакомьтесь с разделом [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Шаг 1. Подтвердите наличие подписки, которая включает Azure Rights Management
Существует несколько типов подписок, которые включают [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Ознакомьтесь с разделом [Поддерживающая Azure RMS облачная подписка](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) статьи [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) и убедитесь, что ваша подписка включает функциональность, которую требуется использовать в организации. Для этого используйте таблицу в [Сравнении служб управления правами (RMS)](https://technet.microsoft.com/dn858608).

## Шаг 2. Подготовка учетной записи клиента для использования Rights Management
Перед началом использования [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] выполните следующие подготовительные действия.

1.  Убедитесь, что клиент Azure или Office 365 содержит учетные записи пользователей и групп, которые будут использоваться в Azure RMS для проверки подлинности пользователей в вашей организации. При необходимости создайте эти учетные записи и группы или синхронизируйте их из локального каталога. Дополнительные сведения см. в [Подготовка к установке службы Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Примите решение, будет ли Майкрософт управлять ключом клиента (по умолчанию), или вы хотите создать ключ клиента и управлять им самостоятельно (сценарий BYOK). Обратите внимание, что в настоящее время нельзя использовать BYOK при использовании Exchange Online. Дополнительные сведения см. в [Планирование и реализация ключа клиента службы Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Установите модуль Windows PowerShell для [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] по меньшей мере на одном из компьютеров, имеющих доступ в Интернет. Это действие можно выполнить сейчас или позднее. Дополнительные сведения см. в [Установка Windows PowerShell для Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Если уже используются локальные службы Rights Management: Выполните миграцию для перемещения ключей, шаблонов и URL-адресов в облако. Дополнительные сведения см. в [Переход от AD RMS к Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Активируйте Rights Management, чтобы можно было начать использовать эту службу. В случае необходимости поэтапного развертывания настройте элементы управления переносом для ограничения доступа пользователей. Дополнительные сведения см. в [Активация управления правами Azure](../Topic/Activating_Azure_Rights_Management.md).

Дополнительно подумайте, следует ли настроить следующие объекты.

-   Настраиваемые шаблоны, если шаблонов политики прав по умолчанию недостаточно для организации. Это действие можно выполнить сейчас или позднее. Дополнительные сведения см. в [Настройка настраиваемых шаблонов для службы Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Журнал использования, чтобы можно было отслеживать использование организацией службы Rights Management. Это действие можно выполнить сейчас или позднее. Дополнительные сведения см. в [Ведение журнала и анализ использования Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Шаг 3. Настройка приложений и служб для Rights Management
Настройка приложений может включать установку приложения для управления доступом Rights Management и включение поддержки функций управления правами на доступ к данным (IRM) в SharePoint Online или Exchange Online. Дополнительные сведения см. в [Настройка приложений для службы Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Если у вас есть ИТ-службы, которым нужно проверять файлы, защищаемые с помощью Azure RMS, например решения по предотвращению утечек данных (DLP), шлюзы шифрования содержимого (CEG) и продукты для защиты от вредоносных программ, настройте учетные записи таких служб в качестве суперпользователей для Azure RMS. Дополнительные сведения см. в [Настройка суперпользователей для Azure Rights Management и служб обнаружения или восстановления данных](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Если имеются локальные службы, которые планируется использовать с Azure Rights Management, установите и настройте соединитель Rights Management. Дополнительные сведения см. в [Развертывание соединителя службы Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Шаг 4. Публикация и использование защищенного контента
Теперь все готово для публикации и использования защищенного содержимого и ведения журнала использования Rights Management в вашей организации. Дополнительные сведения см. в [Использование службы Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Шаг 5. Администрирование Rights Management для учетной записи клиента в соответствии с потребностями
Начав использовать [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], вы сможете убедиться, что модуль [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для Windows PowerShell помогает создавать скрипты и автоматизировать административные изменения. Дополнительные сведения см. в [Администрирование Azure Rights Management с помощью Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## См. также
[Настройка службы Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

