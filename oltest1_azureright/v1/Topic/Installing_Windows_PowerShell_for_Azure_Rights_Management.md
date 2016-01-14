---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Установка Windows&#160;PowerShell для Azure Rights Management
Следующая информация поможет установить Windows PowerShell для Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

Вы можете использовать этот модуль Windows PowerShell для администрирования [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] из командной строки с помощью любого компьютера, который подключен к Интернету и отвечает требованиям, перечисленным в следующем разделе. Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] поддерживает скрипты для автоматизации, которые могут понадобиться для сложных сценариев конфигурации. Дополнительные сведения о задачах администрирования и конфигурациях, которые поддерживает модуль, см. в разделе [Администрирование Azure Rights Management с помощью Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Предварительные требования
В следующей таблице перечислены обязательные требования для установки и использования Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Требование|Дополнительные сведения|
|--------------|---------------------------|
|Версия Windows, которая поддерживает модуль администрирования [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]|Ознакомьтесь со списком поддерживаемых операционных систем в разделе **Требования к системе**[на странице загрузки средства администрирования Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Минимальная версия Windows PowerShell: 2.0|Поддержка модуля администрирования [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] появилась в Windows PowerShell 2.0.<br /><br />По умолчанию большинство операционных систем Windows устанавливается с Windows PowerShell версии не ниже 2.0.. Если необходимо установить Windows PowerShell 2.0, см. раздел [Установка Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx).<br /><br />Совет. Вы можете проверить используемую версию Windows PowerShell, набрав **$PSVersionTable** в сеансе Windows PowerShell.|
|Минимальная версия Microsoft .NET Framework: 4.5<br /><br />Примечание. Эта версия платформы Microsoft .NET Framework входит в состав более поздних версий операционных систем, поэтому устанавливать ее вручную требуется, только если версия операционной системы клиента ниже, чем Windows 8.0, или версия операционной системы сервера ниже, чем Windows Server 2012.|Если минимальная версия платформы Microsoft .NET Framework еще не установлена, вы можете загрузить [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Минимальная версия платформы Microsoft .NET Framework требуется для некоторых классов, используемых модулем администрирования [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|
|Помощник по входу в Microsoft Online Services версии 7.0|Помощник по входу в Microsoft Online Services требуется для проверки подлинности [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].<br /><br />Дополнительные сведения см. в разделе [Центр загрузки: помощник по службам Microsoft Online Services для ИТ-специалистов (RTW)](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Установка модуля администрирования Rights Management

1.  Перейдите в центр загрузки Майкрософт и [загрузите средство администрирования Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721) которое содержит модуль администрирования [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] для Windows PowerShell.

2.  В локальной папке, в которую был загружен и сохранен файл установщика [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], дважды щелкните исполняемый файл, загруженный для используемой платформы (WindowsAzureADRightsManagementAdministration_x64.exe или WindowsAzureADRightsManagementAdministration_x86.exe), чтобы запустить мастер установки администрирования Azure AD Rights Management.

3.  Выполните указания мастера.

Теперь Windows PowerShell для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] установлен.

## Дальнейшие шаги
Чтобы увидеть список доступных командлетов, запустите Windows PowerShell, используя пункт **Запуск от имени администратора**, и введите следующее:

```
Get-Command -Module aadrm
```
Используйте команду `the Get-Help <cmdlet_name>`, чтобы получить справку по конкретному командлету.

Дополнительные сведения

-   Полный список доступных командлетов: [Командлеты Azure Rights Management](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Список основных сценариев настройки, поддерживаемых Windows PowerShell, см. в статье [Администрирование Azure Rights Management с помощью Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Перед выполнением любых команд для настройки службы [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] необходимо подключиться к службе с помощью командлета [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx). После завершения выполнения команды конфигурации необходимо отключиться от службы с помощью командлета [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx).

> [!NOTE]
> Если активация [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] еще не выполнена, это можно сделать после подключения к службе, воспользовавшись командлетом [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx).

## См. также
[Администрирование Azure Rights Management с помощью Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

