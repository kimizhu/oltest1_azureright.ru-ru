---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Расширение служб Active Directory Rights Management для мобильных устройств
Расширение Active Directory Rights Management Services (AD RMS) для мобильных устройств работает на базе существующего развертывания AD RMS. Это дает возможность пользователям мобильных устройств защищать и использовать конфиденциальные данные, если их устройства поддерживают последний клиент RMS и используют информированные приложения RMS. Например, пользователи таких устройств могут выполнять следующее:

-   с помощью приложения для управления доступом RMS использовать защищенные текстовые файлы в различных форматах (включая TXT, CSV и XML);

-   с помощью приложения для управления доступом RMS использовать защищенные графические файлы (включая JPG, GIF и TIF);

-   с помощью приложения для управления доступом RMS открывать любой файл, защищенный с помощью универсальной защиты (в формате PFILE);

-   с помощью приложения для управления доступом RMS защищать графические файлы на устройстве;

-   использовать информированное RMS средство просмотра PDF для мобильных устройств или другое информированное приложение RMS для открытия PDF-файлов, защищенных с помощью приложения для управления доступом RMS для Windows;

-   использовать другие приложения от поставщиков программного обеспечения, предоставляющих информированные приложения RMS, которые поддерживают типы файлов со встроенной поддержкой в RMS;

-   использовать информированные приложения RMS собственной разработки, созданные с помощью пакета SDK RMS.

> [!NOTE]
> Вы можете загрузить приложение для управления доступом RMS со страницы [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) на веб-сайте Майкрософт.
> 
> Дополнительные сведения о различных типах файлов, поддерживаемых RMS, см. в разделе [Поддерживаемые типы файлов и расширения имен файлов](http://technet.microsoft.com/library/dn339003.aspx) руководства администратора по приложению для управления доступом Rights Management.

Расширение для мобильных устройств не требуется для использования или создания защищенных сообщений электронной почты на устройствах, если они используют почтовые приложения, поддерживающие Exchange ActiveSync IRM. Эта встроенная поддержка RMS и мобильных устройств впервые появилась в пакете обновления 1 для Exchange 2010.

Используйте следующие разделы для развертывания расширения Active Directory Rights Management Services (AD RMS) для мобильных устройств:

-   [Необходимые условия для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Настройка AD FS для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Настройка AD FS для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Указание записей SRV DNS для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Развертывание расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Необходимые условия для расширения AD RMS для мобильных устройств
Перед установкой расширения AD RMS для мобильных устройств убедитесь, что соблюдены следующие требования.

|Требование|Дополнительные сведения|
|--------------|---------------------------|
|Существующее развертывание AD RMS в Windows Server 2012 R2 или Windows Server 2012. **Note:** AD RMS необходимо использовать полную базу данных Microsoft SQL Server на отдельном сервере, а не внутреннюю базу данных Windows, которая часто используется для тестирования на том же сервере.|Документацию по AD RMS см. в статье [Службы управления правами Active Directory](http://technet.microsoft.com/library/hh831364.aspx) в библиотеке Windows Server.|
|AD FS, развернутые в Windows Server 2012 R2.|Документацию по AD FS см. в [руководстве по развертыванию AD FS Windows Server 2012 R2](http://technet.microsoft.com/library/dn486820.aspx) в библиотеке Windows Server.<br /><br />AD FS должны быть настроены для расширения для мобильных устройств. Инструкции см. в разделе [Настройка AD FS для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) этой статьи.|
|Записи SRV в DNS|Создайте одну или несколько записей SRV в домене или доменах компании:<br /><br />-   по одной записи для каждого суффикса домена электронной почты, который пользователи будут использовать;<br />-   по одной записи для каждого FQDN, используемого кластерами RMS для защиты контента.<br /><br />Когда пользователи вводят свои адреса электронной почты со своих мобильных устройств, суффикс домена используется для определения того, должны они использовать инфраструктуру AD RMS или Azure RMS. Когда запись SRV обнаруживается, клиенты перенаправляются на сервер AD RMS, который отвечает на этот URL-адрес.<br /><br />Если пользователи используют защищенный контент с помощью мобильного мобильного устройства, клиентское приложение ищет в DNS запись, соответствующую FQDN в URL-адресе кластера, который защищает контент. Затем это устройство направляется в кластер AD RMS, указанный в записи DNS, и получает лицензию для открытия контента. В большинстве случаев этот кластер RMS совпадает с кластером RMS, который защитил контент.<br /><br />Сведения о том, как можно создавать записи SRV, см. в разделе [Указание записей SRV DNS для расширения AD RMS для мобильных устройств](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) этой статьи.|
|В настоящее время поддерживаются следующие клиенты.<br /><br />-   Устройства Android, использующие последнюю версию приложения для управления доступом RMS для Android|Версия Android не ниже 4.0.3.<br /><br />Загрузите приложение для управления доступом RMS для Android с [веб-сайта Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) и передайте его на это устройство.|

### <a name="BKMK_ADFS"></a>Настройка AD FS для расширения AD RMS для мобильных устройств
Вы должны сначала настроить AD FS, а затем авторизовать приложение для управления доступом RMS для Android.

##### Шаг 1. Настройка AD FS

-   Вы можете запустить скрипт Windows PowerShell, чтобы  автоматически настроить AD FS для поддержки расширения AD RMS для мобильных устройств, или вручную задать параметры конфигурации и значения.

    -   Чтобы автоматически настроить AD FS, скопируйте и вставьте следующее в файл скрипта Windows PowerShell, а затем запустите его.

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Чтобы вручную настроить AD FS, используйте следующие параметры:

        |Параметр|Значение|
        |------------|------------|
        |**Отношение доверия с проверяющей стороной**|api.rms.rest.com|
        |**Правило утверждения**|**Хранилище атрибутов**:  Active Directory<br /><br />**Адреса электронной почты**:  адрес электронной почты<br /><br />**Имя участника-пользователя**:  имя участника-пользователя<br /><br />**Прокси-адрес**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Шаг 2. Авторизация приложения для управления доступом RMS  для Android

-   Чтобы добавить поддержку устройств Android, выполните следующую команду Windows PowerShell:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Указание записей SRV DNS для расширения AD RMS для мобильных устройств
Вы должны создать записи SRV DNS для каждого домена электронной почты, используемого вашими пользователями. Если все пользователи используют дочерние домены из одного родительского домена и все пользователи из этого непрерывного пространства имен используют один кластер RMS, то можно использовать только одну запись SRV в родительском домене и RMS найдет соответствующие записи DNS.

Записи SRV имеют следующий формат: _rmsdisco._http._tcp. *&lt;суффикс_электронной_почты&gt;**&lt;номер_порта&gt;**&lt;FQDN_кластера_RMS&gt;*

Например, если в организации имеются пользователи со следующими адресами электронной почты:

-   user@contoso.com,

-   user@sales.contoso.com,

-   user@fabrikam.com,

и нет других дочерних доменов для contoso.com, использующих кластер RMS, отличный от **rmsserver.contoso.com**, создайте две записи SRV DNS, имеющие следующие значения:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Помимо этих записей SRV DNS для доменов электронной почты, вы должны создать другую запись SRV DNS в этих пользовательских доменах. Эта запись должна указывать URL-адреса кластера RMS, который защищает контент. Каждый файл, защищенный RMS, включает URL-адрес кластера, защитившего этот файл. Мобильные устройства используют запись SRV DNS и полное доменное имя URL-адреса, указанное в записи, для поиска соответствующего кластера RMS, который может поддерживать мобильные устройства.

Например, если используется кластер RMS **rmsserver.contoso.com**, создайте запись SRV DNS, которая имеет следующие значения: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Развертывание расширения AD RMS для мобильных устройств
Перед установкой расширения AD RMS для мобильных устройств убедитесь, что, во-первых, все необходимые компоненты из предыдущего раздела на месте, а во-вторых, что вы знаете URL-адрес сервера AD FS. Затем выполните следующие действия.

1.  Загрузите расширение AD RMS для мобильных устройств с [веб-сайта Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Запустите Setup.exe, чтобы запустить мастер настройки расширения Active Directory Rights Management Services для мобильных устройств.

3.  При появлении запроса введите URL-адрес сервера AD FS, настроенный ранее.

4.  Завершите работу мастера.

Запустите этот мастер на всех узлах кластера RMS.

