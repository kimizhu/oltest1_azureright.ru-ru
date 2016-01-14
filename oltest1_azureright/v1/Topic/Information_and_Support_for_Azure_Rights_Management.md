---
description: na
keywords: na
title: Information and Support for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cc73d92-27d6-49ff-a8ab-2fae73519b4b
---
# Информация и поддержка Azure Rights Management
Для получения дополнительных сведений о Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) могут использоваться следующие ресурсы.

|Для выполнения этого …|.. сделайте следующее:|
|--------------------------|--------------------------|
|… прочитать последнюю версию документации по продукту [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] →|используйте библиотеку документации TechNet для [Azure Rights Management](../Topic/Azure_Rights_Management.md)|
|… предоставить отзывы о документации или задать вопрос о документации →|Отправить сообщение [askipteam](mailto:%20askipteam@microsoft.com?subject=Documentation%20feedback) по электронной почте|
|… получение твитов о Rights Management и уведомлений об обновлении документации от группы разработчиков продукта →|Обратиться к Дэну Пластина, который помогает вести группу Microsoft Rights Management. См. [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy)|
|… … получить пробную версию [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] →|[Зарегистрироваться для получения бесплатной 30-дневной пробной версии](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)|
Дополнительные сведения о [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] приводятся в указанных ниже разделах.

-   [Поиск в библиотеке документации](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_SearchTips)

-   [Доступная для загрузки документация](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_Download)

-   [Блог группы разработчиков продукта Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_ProductGroupBlog)

-   [Средства поддержки и ресурсы сообщества](../Topic/Information_and_Support_for_Azure_Rights_Management.md#BKMK_SupportOptions)

## <a name="BKMK_SearchTips"></a>Поиск в библиотеке документации
[Используйте запрос для поиска в данной области](http://www.bing.com/search?q=%28"Rights%20Management"%29%20site:technet.microsoft.com/library%20meta:search.MSCategory%28jj619159%29), чтобы найти документацию в библиотеке TechNet, которая предназначена только для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Результаты поиска для данного запроса не включают результаты для Active Directory Rights Management Services (AD RMS), Windows Rights Management или ресурсов сообщества. Количество результатов поиска можно уменьшить путем замены строки «Rights Management» (управление правами) в URL-адресе собственной строкой поиска.

### Пример поиска
[Используйте этот запрос поиска](http://www.bing.com/search?q=%28"Rights%20Management"%29%20site:technet.microsoft.com/library%20meta:search.MSCategory%28jj619159%29), а затем настройте поиск, используя следующие примеры.

-   Единственная строка поиска: для поиска разделов, содержащих строку поиска **RMS connector**, замените **“Rights Management”** на **“RMS connector”**:

    ```
    ("RMS connector") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Объединение строк поиска: для поиска разделов, содержащих строки поиска **Exchange** и **SharePoint**, используйте оператор **AND** (и):

    ```
    ("Exchange") AND ("SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Альтернативные строки поиска: для поиска разделов, содержащих строки поиска **Exchange** или **SharePoint**, используйте оператор **OR** (или):

    ```
    ("Exchange" OR "SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

-   Исключение строк поиска: для поиска разделов, содержащих строку поиска **Exchange**, и исключения разделов о **SharePoint** используйте оператор **NOT** (не):

    ```
    ("Exchange)" NOT ("SharePoint") site:technet.microsoft.com/library meta:search.MSCategory(jj619159)
    ```

### Советы по поиску
Использование приведенных ниже советов по поиску поможет найти необходимую информацию.

-   При поиске официальной документации вместо неофициальных терминов или сокращений из контента от сообщества следует использовать поисковые термины из интерфейса пользователя (ИП) и документации TechNet. Например: для поиска следует искать «Azure Rights Management», а не «AADRMS» или другое неофициальное сокращение для этой облачной службы. Хотя часто и используется «RMS», полным названием является Rights Management service, поэтому при поиске официальной документации следует использовать «rights management», а не «RMS». Можно использовать [Терминология для Azure Rights Management](../Topic/Terminology_for_Azure_Rights_Management.md) для определения официальных терминов для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

-   При поиске на странице в TechNet (следует нажать клавиши Ctrl-F и ввести поисковые термины в поле **Find** (найти)), в результаты поиска не будет включен текст в свернутых разделах. Для поиска текста в свернутых разделах перед выполнением поиска на странице разделы необходимо развернуть. Для этого следует щелкнуть по кнопке **Expand All** (развернуть все) вверху страницы или дважды щелкнуть по свернутому разделу. После разворачивания всех разделов поиск будет производиться во всех разделах на странице.

-   По возможности следует использовать библиотеку TechNet в сети, а не скачивать документацию. Библиотека TechNet в сети содержит самые свежие данные, в загруженной на жесткий диск компьютера документации искомая информация может отсутствовать, так как в сетевой библиотеке могли быть выполнены изменения или добавлены дополнительные данные.

-   Если поиск будет выполнять проще и быстрее при хранении документации на локальном диске, можно выбрать несколько разделов TechNet и сохранить их на своем компьютере. Дополнительные сведения приводятся в следующем разделе.

## <a name="BKMK_Download"></a>Доступная для загрузки документация
Страницы из TechNet могут быть сохранены локально, например в файле формата PDF, для последующего чтения на ноутбуке, планшетном компьютере или телефоне, когда отсутствует подключение к Интернету. Или могут быть добавлены примечания и выполнена печать информации. При использовании этого метода можно эффективно создавать собственные технические документы или проектную документацию, группируя необходимые для выполнения определенных задач или сквозного сценария разделы.

Этот метод может использоваться для всех библиотек документации в TechNet, а не только для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

#### Чтобы загрузить документы из TechNet:

1.  Войти в TechNet.

2.  В верхней части страницы, которую необходимо сохранить локально, щелкните **Экспорт** (рядом с кнопкой **Печать**).

    После этого появится баннер **Export multiple sets of pages** (экспортировать несколько наборов страниц), позволяющий добавлять и удалять подлежащие сохранению страницы.

3.  Щелкните**Управление страницами**, чтобы их экспортировать.

Для получения дополнительных сведений необходимо щелкнуть по **Help** (справка) на баннере.

> [!NOTE]
> Информация по TechNet часто обновляется, поэтому желательно использовать сетевую версию, чем будет гарантироваться доступность самой последней информации.
> 
> Можно использовать ежемесячные уведомления об обновлении документации в [Блоге группы Microsoft Rights Management (RMS) и тег документации](http://blogs.technet.com/b/rms/archive/tags/docs/) для проверки, были ли изменены загруженные ранее разделы для [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] и какие изменения были сделаны.

## <a name="BKMK_ProductGroupBlog"></a>Блог группы разработчиков продукта Rights Management
Группа продукта Rights Management использует[Блог группы Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) для предоставления технических сведений и новостей о[!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], AD RMS и связанных технологиях. В статьях этого блога публикуются дополнения к документации по продукту и сведения о поддержке.

> [!TIP]
> При разработке приложений для Azure RMS или AD RMS вас может заинтересовать [Блог разработчиков службы управления правами Active Directory (AD RMS)](http://blogs.msdn.com/b/rms/).

## <a name="BKMK_SupportOptions"></a>Средства поддержки и ресурсы сообщества
Дополнительные сведения о средствах поддержки, устранении неполадок и ресурсах сообщества могут быть получены по указанным ниже ссылкам.

-   [Анализатор соответствия RMS](http://www.microsoft.com/en-us/download/details.aspx?id=46437)

-   [Yammer: Microsoft Rights Management (RMS)](http://www.yammer.com/AskIPTeam)

-   [Форум: Microsoft RMS (облако)](https://social.technet.microsoft.com/Forums/en-US/home?forum=rmscloud)

-   [Форум: RMS для пользователей (приложения)](https://social.technet.microsoft.com/Forums/en-US/home?forum=rmsapps)

-   [Центр справки и поддержки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=243064)

Кроме того, посетите[портал служб Microsoft Rights Management](http://www.microsoft.com/rms), чтобы найти другие вспомогательные ресурсы о[!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

## См. также
[Начало работы со службой Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

