---
description: na
keywords: na
title: Configuring Applications for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
---
# Настройка приложений для службы Azure Rights Management
> [!NOTE]
> Эта информация предназначена для ИТ-администраторов и консультантов, развернувших службу Azure Rights Management. Если вам нужна информация об использовании службы Rights Management с определенным приложением или о том, как открыть файл с защитой прав, обратитесь к справке и документации по этому приложению.
> 
> Например, в случае с программами Office щелкните значок справки и введите поисковый запрос, такой как **Rights Management** или **IRM**. Информацию о приложении для управления доступом RMS можно найти в [соответствующем руководстве пользователя](http://technet.microsoft.com/library/dn339006.aspx).

После развертывания Azure Rights Management (Azure RMS) для вашей организации используйте следующие сведения, чтобы настроить приложения и службы для поддержки службы Azure RMS. Сюда входят приложения Office, например Word 2013 и Word 2010, и службы, например Exchange Online (правила транспорта, предотвращение потери данных, отсутствие пересылки и шифрование сообщений) и SharePoint Online (защищенные библиотеки). Сведения о поддержке Rights Management этими приложениями и службами см. в разделе [Поддержка приложениями Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

> [!IMPORTANT]
> Сведения о поддерживаемых версиях и других требованиях см. в разделе [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

-   [Office 365: настройка для клиентов и веб-служб](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365)

    -   [Exchange Online: настройка службы управления правами на доступ к данным](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline)

    -   [SharePoint Online и OneDrive для бизнеса: настройка службы управления правами на доступ к данным](#BKMK_SharePointOnline)

-   [Office 2016 и Office 2013: настройка для клиентов](#BKMK_Office2013Configuration)

-   [Office 2010: настройка для клиентов](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_Office2010Configuration)

-   [Приложение для управления доступом Rights Management: установка и настройка для клиентов](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp)

    -   [Приложение для управления доступом RMS для Windows: установка и настройка](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppforWindows)

    -   [Приложение для управления доступом RMS для мобильных платформ: Установка](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppMovileDevices)

-   [Другие приложения, которые поддерживают API RMS: установка и настройка](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_RMSAPIs)

Сведения о настройке локальных серверов, таких как Exchange Server и SharePoint Server, см. в разделе [Развертывание соединителя службы Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!TIP]
> Высокоуровневые примеры и снимки экрана приложений, настроенных для использования с Azure RMS, см. в разделе [Azure RMS в действии: что видят администраторы и пользователи?](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) статьи [Что такое управление правами Azure?](../Topic/What_is_Azure_Rights_Management_.md).

## <a name="BKMK_O365"></a>Office 365: настройка для клиентов и веб-служб
Поскольку Office 365 изначально поддерживает службу Azure RMS, настройка клиентского компьютера для поддержки функций управления правами на доступ к данным для таких приложений, как Word, Excel, PowerPoint, Outlook и Outlook Web App, не требуется. Все, что пользователям необходимо сделать — войти в приложения Office с учетными данными [!INCLUDE[o365_1](../Token/o365_1_md.md)], после чего они смогут защищать файлы и электронные сообщения, а также использовать файлы и электронные сообщения, защищенные другими пользователями.

Однако, чтобы пользователи смогли воспользоваться преимуществами надстройки Office, рекомендуется дополнительно использовать приложение управления доступом Rights Management. Для получения дополнительных сведений см. раздел [Приложение для управления доступом Rights Management: установка и настройка для клиентов](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) в этой статье.

### <a name="BKMK_ExchangeOnline"></a>Exchange Online: настройка службы управления правами на доступ к данным
Чтобы настроить Exchange Online для поддержки Azure RMS, необходимо настроить службу управления правами на доступ к данным для Exchange Online. Для этого используйте Windows PowerShell (нет необходимости устанавливать отдельный модуль) и выполните [команды PowerShell для Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Сейчас невозможно настроить в Exchange Online поддержку Azure RMS, если для Azure RMS используется ключ клиента, который управляется клиентом (BYOK), а не конфигурация по умолчанию, где ключ клиента управляется корпорацией Майкрософт. Для получения дополнительных сведений см. раздел [Цены и ограничения BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) в статье [Планирование и реализация ключа клиента службы Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).
> 
> При попытке настроить Exchange Online, когда для Azure RMS используется BYOK, команда для импорта ключа (шаг 5 в следующей процедуре) выдает сообщение об ошибке **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

Ниже приведен типичный набор команд, которые необходимо выполнить для включения Exchange Online для использования Azure RMS:

1.  Если Windows PowerShell для Exchange Online впервые используется на компьютере, необходимо настроить Windows PowerShell для выполнения подписанных скриптов. Начните сеанс Windows PowerShell с помощью команды **Запуск от имени администратора**, а затем введите следующее:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  В сеансе Windows PowerShell войдите в Exchange Online, используя учетную запись, у которой включен удаленный доступ к оболочке. По умолчанию для всех учетных записей, созданных в Exchange Online, включен удаленный доступ к оболочке, но его можно отключить (и включить) с помощью команды [Set-User &lt;удостоверение_пользователя&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx).

    Чтобы войти, введите следующее:

    ```
    $Cred = Get-Credential
    ```
    В диалоговом окне **Запрос учетных данных Windows PowerShell** введите имя пользователя Office 365 и пароль.

3.  Подключитесь к службе Exchange Online, выполнив следующие две команды:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Укажите расположение ключа клиента Azure RMS в зависимости от региона:

    Для Северной Америки (и государственных подписок):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Для Европы:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Для Азии:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Для Южной Америки:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Импортируйте конфигурационные данные из Azure RMS в Exchange Online в виде доверенного домена публикаций (TPD). Сюда входят ключ клиента Azure RMS и шаблоны Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    В этой команде мы использовали имя **RMS Online** в качестве базового имени TPD для Azure RMS в Exchange Online. После импорта TPD он получает имя **RMS Online - 1** в Exchange Online.

6.  Включите функциональность Azure RMS, чтобы функции управления правами на доступ к данным (IRM) стали доступны для Exchange Online:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    После выполнения этой команды Rights Management автоматически включается для клиента Outlook, Outlook Web App и Exchange ActiveSync.

7.  При необходимости проверьте успешность конфигурации с помощью следующей команды:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Например: **Test-IRMConfiguration -Sender  adams@contoso.com**

    Эта команда выполняет серию проверок, включая проверку подключения к службе, получение конфигурации, получение URI, лицензий и шаблонов. В сеансе Windows PowerShell вы увидите результаты каждой проверки в конце, если все эти проверки будут пройдены: **ОБЩИЙ РЕЗУЛЬТАТ: ПРОЙДЕНО**

8.  Отключение удаленного сеанса PowerShell:

    ```
    Remove-PSSession $Session
    ```

Пользователи теперь могут защитить свои сообщения электронной почты с помощью Azure RMS. Например, в Outlook Web App в расширенном меню (**...**) выберите **Задать разрешения** и затем выберите **Не пересылать** или один из доступных шаблонов, чтобы применить защиту информации к сообщению электронной почты и вложениям. Так как Outlook Web App кэширует пользовательский интерфейс в течение суток, дождитесь окончания этого периода времени, прежде чем пытаться применить защиту информации к сообщениям электронной почты после выполнения этих команд конфигурации. Пока пользовательский интерфейс не обновится, чтобы отобразить новую конфигурацию, меню **Задать разрешения** отображаться не будет.

> [!IMPORTANT]
> При создании новых [настраиваемых шаблонов](https://technet.microsoft.com/library/dn642472.aspx) для Azure RMS или обновлении шаблонов каждый раз необходимо запускать следующую команду Exchange Online PowerShell (при необходимости выполните сначала шаги 2 и 3) для синхронизации этих изменений в Exchange Online: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Администратор Exchange теперь может настраивать компоненты, которые применяют защиту информации автоматически, например [правила транспорта](https://technet.microsoft.com/library/dd302432.aspx), [политики защиты от потери данных (DLP)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) и [защищенную голосовую почту](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (в рамках единой системы обмена сообщениями).

Подробные инструкции по настройке Exchange Online для включения функциональности IRM см. в документации в библиотеке Exchange. Например:

-   [Подключение к Exchange Online с помощью удаленного PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.160%29.aspx)

-   [Настройка IRM для использования Azure Rights Management](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)

#### Шифрование сообщений Office 365
Выполните те же действия, что описаны в предыдущем разделе. Если не нужно, чтобы отображались шаблоны, выполните до шага 6 следующую команду, чтобы сделать шаблоны IRM недоступными в клиенте Outlook и Outlook Web App: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

После этого все будет готово к настройке [правил транспорта](https://technet.microsoft.com/library/dd302432.aspx) для автоматического изменения уровня безопасности сообщений, если получатели находятся за пределами организации. Выберите параметр **Применить шифрование сообщений Office 365**.

Дополнительные сведения о шифровании сообщений см. в разделе [Шифрование в Office 365](https://technet.microsoft.com/library/dn569286.aspx) в библиотеке Exchange.

### <a name="BKMK_SharePointOnline"></a>SharePoint Online и OneDrive для бизнеса: настройка службы управления правами на доступ к данным
Чтобы настроить SharePoint Online и OneDrive для бизнеса с поддержкой Azure RMS, сначала необходимо настроить службу управления правами на доступ к данным для SharePoint Online в центре администрирования SharePoint. Затем владельцы сайтов смогут защитить с помощью IRM свои списки и библиотеки документов SharePoint, а пользователи смогут защитить свою библиотеку OneDrive для бизнеса, чтобы документы, которые в ней сохраняются и используются совместно с другими пользователями, были автоматически защищены Azure RMS.

Чтобы включить службу управления правами на доступ к данным (IRM) для SharePoint Online, см. следующие инструкции на веб-сайте Office:

-   [Настройка службы управления правами на доступ к данным в центре администрирования SharePoint](http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Эта настройка выполняется администратором Office 365.

#### Настройка IRM для библиотек и списков
После включения службы IRM для SharePoint владельцы сайтов смогут защитить с помощью IRM свои библиотеки документов и списки SharePoint. Инструкции см. в следующих разделах на веб-сайте Office:

-   [Применение службы управления правами на доступ к данным к списку или библиотеке](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Эта настройка выполняется администратором сайта SharePoint.

#### <a name="BKMK_OneDrive"></a>Настройка IRM для OneDrive для бизнеса
После включения службы IRM для SharePoint Online к библиотеке документов OneDrive для бизнеса пользователей можно применить защиту Rights Management.  Пользователи могут настроить это самостоятельно, щелкнув значок **Параметры** в OneDrive. Хотя администраторы не могут настроить Rights Management для OneDrive для бизнеса пользователей в Центре администрирования SharePoint, вы можете сделать это с помощью Windows PowerShell.

> [!NOTE]
> Дополнительные сведения о настройке OneDrive для бизнеса см. в документации по Office [Настройка OneDrive для бизнеса в Office 365](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

##### Настройка для пользователей
Эти инструкции помогут пользователям настроить OneDrive для бизнеса и защитить рабочие файлы с помощью IRM.

1.  в OneDrive щелкните значок **Параметры**, чтобы открыть меню параметров, и щелкните **Содержимое сайта**.

2.  Наведите указатель мыши на плитку **Документы**, выберите многоточие (**...**) и нажмите **Параметры**.

3.  На странице **Параметры** в разделе **Разрешения и управление** щелкните **Управление правами на доступ к данным**.

4.  На странице **Параметры управления правами на доступ к данным** установите флажок **Ограничить разрешения для этой библиотеки при скачивании**, укажите имя и описание для разрешений и при необходимости щелкните **ПОКАЗАТЬ ПАРАМЕТРЫ**, чтобы настроить необязательные параметры, а затем нажмите кнопку **ОК**.

    Дополнительные сведения о параметрах конфигурации см. в инструкциях раздела [Применение управления правами на доступ к данным к списку или библиотеке](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) в документации по Microsoft Office.

Поскольку конфигурация зависит в большей степени от пользователей, чем от администратора в плане защиты библиотеки OneDrive для бизнеса с помощью IRM, расскажите пользователям о преимуществах защиты файлов и о том, как ее применить. Например, объясните им, что когда документ в OneDrive для бизнеса используется совместно, доступ к этому документу будут иметь только указанные ими пользователи с теми ограничениями, которые они сами настроят, даже если файл будет переименован и скопирован в другое место.

##### Настройка для администраторов
Хотя вы и не можете настроить IRM для OneDrive для бизнеса пользователей в Центре администрирования SharePoint, вы можете сделать это с помощью Windows PowerShell. Чтобы включить IRM для этих библиотек, выполните следующие действия.

1.  Скачайте и установите [Пакет SDK для клиентских компонентов SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=42038).

2.  Скачайте и установите [Оболочку управления SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=35588).

3.  Скопируйте содержимое следующего скрипта и назовите файл на компьютере Set-IRMOnOneDriveForBusiness.ps1.

    *&#42;&#42;Заявление об отказе&#42;&#42;* Данный пример скрипта не поддерживается никакой из стандартных программ или служб поддержки корпорации Майкрософт. Этот пример скрипта предоставляется «как есть» без каких-либо гарантий.

    ```
    # Requires Windows PowerShell version 3 <# Description: Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/user3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Set-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List, [parameter(Mandatory=$true)][string]$PolicyTitle, [parameter(Mandatory=$true)][string]$PolicyDescription, [parameter(Mandatory=$false)][switch]$IrmReject, [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate, [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView, [parameter(Mandatory=$false)][switch]$AllowPrint, [parameter(Mandatory=$false)][switch]$AllowScript, [parameter(Mandatory=$false)][switch]$AllowWriteCopy, [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays, [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays, [parameter(Mandatory=$false)][string]$GroupName ) process { Write-Verbose "Applying IRM Configuration on '$($List.Title)'" # reset the value to the default settings $list.InformationRightsManagementSettings.Reset() $list.IrmEnabled = $true # IRM Policy title and description $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription # Set additional IRM library settings # Do not allow users to upload documents that do not support IRM $list.IrmReject = $IrmReject.IsPresent $parsedDate = Get-Date if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate)) { # Stop restricting access to the library at <date> $list.IrmExpire = $true $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate } # Prevent opening documents in the browser for this Document Library $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent # Configure document access rights # Allow viewers to print $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent # Allow viewers to run script and screen reader to function on downloaded documents $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent # Allow viewers to write on a copy of the downloaded document $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent if($DocumentAccessExpireDays) { # After download, document access rights will expire after these number of days (1-365) $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays } # Set group protection and credentials interval if($LicenseCacheExpireDays) { # Users must verify their credentials using this interval (days) $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays } if($GroupName) { # Allow group protection. Default group: $list.InformationRightsManagementSettings.EnableGroupProtection = $true $list.InformationRightsManagementSettings.GroupName             = $GroupName } } end { if($list) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() # **************  ADMIN INSTRUCTIONS  ************** # If necessary, modify the following Set-IrmConfiguration parameters to match your required values # The supplied options and values are for example only # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90 Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  Просмотрите скрипт и внесите следующие изменения.

    1.  Найдите `$sharepointAdminCenterUrl` и замените пример значения собственным URL-адресом Центра администрирования SharePoint.

        Это значение будет базовым URL-адресом при переходе в Центр администрирования SharePoint и вводится в следующем формате: https://*&lt;имя_клиента&gt;*-admin.sharepoint.com.

        Например, если имя клиента — contoso, следует указать **https://contoso-admin.sharepoint.com**.

    2.  Найдите `$tenantAdmin` и замените пример значения собственной полной учетной записью глобального администратора Office 365.

        Это значение аналогично тому, которое вы используете для входа на портал администрирования Office 365 в качестве глобального администратора и имеет следующий формат: имя_пользователя@*&lt;доменное имя клиента&gt;*.com

        Например, если имя пользователя глобального администратора Office 365 — admin для домена клиента contoso.com, следует указать **admin@contoso.com**.

    3.  Найдите `$webUrls` и замените примеры значений URL-адресами OneDrive для бизнеса пользователей, добавляя или удаляя столько записей, сколько требуется.

        Кроме того, см. комментарии в скрипте о том, как заменить этот массив путем импорта CSV-файла, который содержит все URL-адреса, которые нужно настроить.  Мы предоставили другой пример скрипта для автоматического поиска и извлечения URL-адресов, чтобы заполнить этот CSV-файл. Когда вы будете готовы сделать это, разверните раздел [Дополнительный скрипт для вывода всех URL-адресов OneDrive для бизнеса в CSV-файл](#BKMK_Script_OD4B_URLS) сразу же после этих шагов.

        URL-адрес для OneDrive для бизнеса пользователя указан в следующем формате: https://*&lt;имя клиента&gt;*-my.sharepoint.com/personal/*&lt;имя_пользователя&gt;*_*&lt;имя клиента&gt;*_com.

        Например, если пользователь в клиенте contoso имеет имя rsimone, следует указать **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**.

    4.  Так как мы используем скрипт для настройки OneDrive для бизнеса, не изменяйте значение **Documents** для переменной `$listTitle`.

    5.  Найдите `ADMIN INSTRUCTIONS`. Если вы не внесете изменения в этот раздел, OneDrive для бизнеса пользователя будет настроен с использованием IRM с названием политики Protected Files (Защищенные файлы) и описанием "This policy restricts access to authorized users" (Эта политика предоставляет доступ только авторизованным пользователям).  Другие параметры IRM не будут заданы, что, возможно, подойдет для большинства сред. Однако вы можете изменить предложенные название политики и описание, а также добавить любые другие параметры IRM, подходящие для вашей среды. См. пример с комментариями в скрипте, чтобы создать собственный набор параметров для команды Set-IrmConfiguration.

5.  Сохраните скрипт и подпишите его. Если вы не подпишите скрипт (что обеспечивает дополнительную безопасность), следует настроить на компьютере запуск неподписанных скриптов Windows PowerShell. Для этого запустите сеанс Windows PowerShell с параметром **Запуск от имени администратора** и введите: **Set-ExecutionPolicy Unrestricted**. Но учтите, что эта конфигурация позволяет запускать все неподписанные скрипты (что снижает уровень безопасности).

    Дополнительные сведения о подписывании скриптов Windows PowerShell см. в статье [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) библиотеки документации по PowerShell.

6.  Запустите скрипт и при запросе укажите пароль учетной записи администратора Office 365. Если вы измените скрипт и запустите его в том же сеансе Windows PowerShell, вас не будут просить указать учетные данные.

> [!TIP]
> Вы можете также использовать скрипт для настройки IRM в библиотеке SharePoint Online. Для этой конфигурации вам, скорее всего, потребуется включить дополнительный параметр **Запретить пользователям отправлять документы, не поддерживающие управление правами на доступ к данным**, чтобы гарантировать, что в библиотеке будут присутствовать только защищенные элементы.    Для этого добавьте параметр `-IrmReject` в команду Set-IrmConfiguration в скрипте.
> 
> Необходимо также изменить переменную `$webUrls` (например, **https://contoso.sharepoint.com**) и переменную `$listTitle` (например, **$Reports**).

Если вам нужно отключить IRM для библиотек OneDrive для бизнеса пользователя, см. статью [Скрипт для отключения IRM для OneDrive для бизнеса](#BKMK_Script_OD4B_DisableIRM).

###### <a name="BKMK_Script_OD4B_URLS"></a>Дополнительный скрипт для вывода всех URL-адресов OneDrive для бизнеса в CSV-файл
В рамках шага 4c выше вы можете использовать следующий скрипт Windows PowerShell для извлечения URL-адресов всех библиотек OneDrive для бизнеса пользователей, которые вы можете проверить, изменить при необходимости, а затем импортировать в основной скрипт.

Для этого скрипта также требуется [Пакет SDK для клиентских компонентов SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=42038) и [Оболочка управления SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Следуйте тем же инструкциям, чтобы скопировать и вставить его, сохранить файл локально (например, как "Report-OneDriveForBusinessSiteInfo.ps1"), изменить значения `$sharepointAdminCenterUrl` и `$tenantAdmin` на нужные, а затем запустить скрипт.

*&#42;&#42;Заявление об отказе&#42;&#42;* Данный пример скрипта не поддерживается никакой из стандартных программ или служб поддержки корпорации Майкрософт. Этот пример скрипта предоставляется «как есть» без каких-либо гарантий.

```
# Requires Windows PowerShell version 3 <# Description: Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites. Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv"). Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.onmicrosoft.com" $reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv" $oneDriveForBusinessSiteUrls= @() $resultsProcessed = 0 function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # establish the client context and set the credentials to connect to the site $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl) $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs do { # build the query object $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext) $query.TrimDuplicates        = $false $query.RowLimit              = 500 $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site" $query.StartRow              = $resultsProcessed $query.TotalRowsExactMinimum = 500000 # run the query $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext) $queryResults = $searchExecutor.ExecuteQuery($query) $clientContext.ExecuteQuery() # enumerate the search results and store the site URLs $queryResults.Value[0].ResultRows | % { $oneDriveForBusinessSiteUrls += $_.Path $resultsProcessed++ } } while($resultsProcessed -lt $queryResults.Value.TotalRows) $oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

###### <a name="BKMK_Script_OD4B_DisableIRM"></a>Скрипт для отключения IRM для OneDrive для бизнеса
Используйте следующий пример скрипта, если вам нужно отключить IRM для OneDrive для бизнеса пользователя.

Для этого скрипта также требуется [Пакет SDK для клиентских компонентов SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=42038) и [Оболочка управления SharePoint Online](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Скопируйте и вставьте содержимое, сохраните файл локально (например, как "Disable-IRMOnOneDriveForBusiness.ps1") и измените значения `$sharepointAdminCenterUrl` и `$tenantAdmin`. Вручную укажите URL-адреса OneDrive для бизнеса или используйте скрипт из предыдущего раздела, чтобы импортировать их, а затем запустите скрипт.

*&#42;&#42;Заявление об отказе&#42;&#42;* Данный пример скрипта не поддерживается никакой из стандартных программ или служб поддержки корпорации Майкрософт. Этот пример скрипта предоставляется «как есть» без каких-либо гарантий.

```
# Requires Windows PowerShell version 3 <# Description: Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/person3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Remove-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List ) process { Write-Verbose "Disabling IRM Configuration on '$($List.Title)'" $List.IrmEnabled = $false $List.IrmExpire  = $false $List.IrmReject  = $false $List.InformationRightsManagementSettings.Reset() } end { if($List) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() Remove-IrmConfiguration -List $list } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
```

## <a name="BKMK_Office2013Configuration"></a>Office 2016 и Office 2013: настройка для клиентов
Поскольку эти более поздние версии Office изначально поддерживают службу Azure RMS, настройка клиентского компьютера для поддержки функций управления правами на доступ к данным для таких приложений, как Word, Excel, PowerPoint, Outlook и Outlook Web App, не требуется. Все, что пользователям необходимо сделать — войти в приложения Office с учетными данными [!INCLUDE[o365_1](../Token/o365_1_md.md)], после чего они смогут защищать файлы и электронные сообщения, а также использовать файлы и электронные сообщения, защищенные другими пользователями.

Однако, чтобы пользователи смогли воспользоваться преимуществами надстройки Office, рекомендуется дополнительно использовать приложение управления доступом Rights Management. Для получения дополнительных сведений см. раздел [Приложение для управления доступом Rights Management: установка и настройка для клиентов](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) в этой статье.

## <a name="BKMK_Office2010Configuration"></a>Office 2010: настройка для клиентов
Чтобы использовать службу Azure RMS с Office 2010 на клиентских компьютерах, необходимо установить приложение для управления доступом Rights Management для Windows. Дальнейшая конфигурация не требуется. Пользователям необходимо будет войти по учетным данным [!INCLUDE[o365_1](../Token/o365_1_md.md)], после чего они смогут защищать файлы и использовать файлы, защищенные другими пользователями.

Дополнительные сведения о приложении управления доступом Rights Management см. в разделе [Приложение для управления доступом Rights Management: установка и настройка для клиентов](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) этой статьи.

## <a name="BKMK_SharingApp"></a>Приложение для управления доступом Rights Management: установка и настройка для клиентов
Приложение для управления доступом Rights Management необходимо для клиентских компьютеров, чтобы использовать Azure RMS с Office 2010, и рекомендуется для всех компьютеров и мобильных устройств, которые поддерживают Azure RMS. Приложение для управления доступом RMS интегрируется с приложениями Office путем установки надстройки Office, чтобы пользователи могли легко защищать файлы и электронные письма ленты. Кроме того, предоставляется универсальная защита для типов файлов, которые изначально не поддерживаются Azure RMS, и сайт отслеживания документов, на котором пользователи могут отслеживать и отзывать защищенные ими файлы.

### <a name="BKMK_SharingAppforWindows"></a>Приложение для управления доступом RMS для Windows: установка и настройка
Чтобы установить и настроить приложение управления доступом RMS для корпоративного развертывания Windows, см. раздел [Руководство администратора приложения управления доступом Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

> [!TIP]
> Если вы хотите быстро установить и протестировать приложение управления доступом RMS для одного компьютера, см. раздел [Загрузка и установка приложения управления доступом Rights Management](http://technet.microsoft.com/library/dn574734.aspx) в [Руководстве пользователя приложения управления доступом Rights Management](http://technet.microsoft.com/library/dn339006.aspx).

### <a name="BKMK_SharingAppMovileDevices"></a>Приложение для управления доступом RMS для мобильных платформ: Установка
Чтобы установить приложение для управления доступом RMS для мобильных платформ, скачайте нужное приложение, используя ссылки на [странице службы Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970). Для использования Azure RMS с этим приложением конфигурация не требуется.

## <a name="BKMK_RMSAPIs"></a>Другие приложения, которые поддерживают API RMS: установка и настройка
В эту категорию входят бизнес-приложения, созданные локально с помощью RMS SDK, и приложения от поставщиков программного обеспечения, созданные с помощью RMS SDK. Для использования этих приложений следуйте инструкциям, предоставленным с приложением.

## Дальнейшие шаги
После настройки приложений для поддержки Azure Rights Management используйте [Стратегия развертывания Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md), чтобы проверить, есть ли другие шаги настройки, которые стоит выполнить перед развертыванием [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] для пользователей и администраторов. Если их нет, перейдите к разделу [Использование службы Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) для выполнения следующих действий.

## См. также
[Настройка службы Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

