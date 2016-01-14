---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Администрирование Azure Rights Management с помощью Windows PowerShell
Хотя Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) можно активировать с помощью центра администрирования [!INCLUDE[o365_2](../Token/o365_2_md.md)] или классического портала Azure, в этих целях можно также использовать модуль Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (AADRM).

После активации [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] дальнейшее администрирование этой службы может не потребоваться. Однако некоторые сценарии расширенной конфигурации могут потребовать использовать модуль Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. В следующей таблице приведены некоторые сценарии расширенной конфигурации, использующие Windows PowerShell. Полный список доступных командлетов с дополнительными сведениями о каждой из них см. в разделе[Командлеты Azure Rights Management](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Если требуется установить модуль Windows PowerShell для [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], см. раздел [Установка Windows PowerShell для Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Имеется также дополнительный модуль Windows PowerShell, **RMSProtection**, который поддерживает Azure RMS и AD RMS. Этот модуль поддерживает защиту и снятие защиты нескольких файлов, чтобы, например, массово защитить все файлы в папке. Дополнительные сведения см. в подразделе [Параметры создания скриптов для суперпользователей](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) раздела [Настройка суперпользователей для Azure Rights Management и служб обнаружения или восстановления данных](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

|Если требуется…|...используйте следующие командлеты|
|-------------------|---------------------------------------|
|Миграция из локальной службы Rights Management (AD RMS или Windows RMS) в [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Командлет Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Подключение к службе [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации или отключение от нее|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Создание собственного ключа клиента и управление им — сценарий BYOK|[Add-AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Активация или деактивация службы [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Включение и отключение сайта отслеживания документов в Azure Rights Management.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Настройка элементов управления адаптацией для поэтапного развертывания Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Создание шаблонов политик прав для организации и управление ими|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Настройка максимального числа дней доступности содержимого, защищенного организацией, без подключения к Интернету (срок действия лицензии на использование).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Управление функцией суперпользователя [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации|[Командлет Enable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Командлет Disable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Командлет Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Командлет Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Командлет Remove-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Управление пользователями и группами, авторизованными для администрирования службы [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] в организации|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Командлет Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Командлет Remove-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Получение журнала задач администрирования [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Ведение журналов и анализ использования для [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Enable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Set-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Disable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|Отображение текущей конфигурации службы [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] для организации|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Перенос организации из [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] в локальное развертывание AD RMS|[Set-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Командлет Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## См. также
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

