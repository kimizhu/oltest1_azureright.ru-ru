---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Активация управления правами Azure
После активации [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) организация может начать защищать важные данные, используя приложения и службы, которые поддерживают это решение для защиты информации. Администраторы могут также управлять и отслеживать защищенные файлы и электронные сообщения, которыми владеет организация. Перед тем как начать использовать функции службы управления правами на доступ к данным в Office, SharePoint и Exchange, необходимо включить [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] и защитить все важные и конфиденциальные файлы.

Если вы хотите узнать подробнее об управлении правами Azure Rights Management перед активацией службы (например, о бизнес-задачах, которые позволяет решать эта служба, о типовых примерах ее внедрения и принципах работы), см. раздел [Что такое управление правами Azure?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Перед активацией [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] убедитесь, что в вашей организации имеется план обслуживания, который включает службы [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. В противном случае вы не сможете активировать Azure RMS.
> 
> Для получения дополнительных сведений см. раздел [Поддерживающая Azure RMS облачная подписка](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) в статье [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

После активации Azure RMS все пользователи в организации могут применять защиту информации к своим файлам и открывать (использовать) файлы, которые были защищены с помощью Azure RMS. При желании можно ограничить список пользователей, которые могут применять защиту информации, с помощью элементов управления переносом для проведения поэтапного развертывания. Для получения дополнительных сведений см. раздел [Настройка элементов управления переносом для поэтапного развертывания](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) в этой статье.

## Активация службы Rights Management
Используйте одну из следующих процедур, чтобы активировать [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Также можно использовать командлет Windows PowerShell [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), чтобы активировать [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Активация службы Rights Management из центра администрирования Office 365

1.  После подписки на план Office 365, включающий Rights Management, [войдите в Office 365 с рабочей или учебной учетной записью](https://portal.office.com/), которая является администратором развертывания Office 365.

2.  Если центр администрирования Office 365 не отображается автоматически, щелкните значок запуска приложений в левом верхнем углу и выберите **Администратор**. Плитка **Администратор** появляется только у администраторов Office 365.

    > [!TIP]
    > Справку центра администрирования см. в разделе [Сведения о центре администрирования Office 365 - справка администратора](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  На левой панели разверните элемент **ПАРАМЕТРЫ СЛУЖБЫ**.

4.  Щелкните **Rights Management**.

    > [!NOTE]
    > Если вы не видите этого варианта, возможно, ваш план службы или версия продукта не поддерживают службу Rights Management или еще не обновлен для ее поддержки.
    > 
    > Чтобы проверить поддержку, используйте сведения в разделе [Поддерживающая Azure RMS облачная подписка](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) статьи [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Если ваш план службы или версия продукта поддерживаются, но вы не видите варианта Rights Management, возможно, служба еще не обновлена. Для получения справки по этой проблемы отправьте сообщение электронной почты команде [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  На странице **RIGHTS MANAGEMENT** щелкните **Управление**.

6.  На странице **RIGHTS MANAGEMENT** щелкните **Активировать**.

7.  При запросе **Вы хотите активировать службу Rights Management?** щелкните **активировать**.

Теперь должна отображается надпись **Rights Management включена** и параметр для ее деактивации.

#### Активация Rights Management на классическом портале Azure

1.  После регистрации для получения учетной записи Azure [войдите на классический портал Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  На левой панели щелкните **ACTIVE DIRECTORY**.

3.  На странице **active directory** щелкните **RIGHTS MANAGEMENT**.

4.  Выберите управляемый каталог для [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], щелкните **АКТИВИРОВАТЬ**, а затем подтвердите свое действие.

    > [!NOTE]
    > Если появляется ошибка активации, возможно, ваш план службы или версия продукта не поддерживают [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Чтобы проверить поддержку RMS, используйте сведения в разделе [Поддерживающая Azure RMS облачная подписка](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) статьи [Требования для службы Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Для получения справки по этой проблемы отправьте сообщение электронной почты команде [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

**Состояние RIGHTS MANAGEMENT** должно отображаться как **Активно**, а параметр **АКТИВИРОВАТЬ** заменяется на **ДЕАКТИВИРОВАТЬ**.

### Значения и описания состояний Rights Management на классическом портале Azure
В дополнение к состоянию **Активно**, которое указывает, что служба Rights Management включена и готова к использованию, также может отображаться состояние **Неактивно**, **Недоступно** или **Несанкционировано**.

|Значение состояния|Описание|
|----------------------|------------|
|**Активно**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] включена и готова к работе.|
|**Неактивно**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] отключена и должна быть активирована для того, чтобы ваша организация могла защитить файлы.|
|**Недоступна**|Служба [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] не работает. Повторите попытку позднее.|
|**Не санкционировано**|У вас нет разрешений на просмотр состояния службы [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Например, ваша учетная запись заблокирована, или вы не являетесь глобальным администратором для выбранного клиента.|

## <a name="BKMK_OnboardingControls"></a>Настройка элементов управления переносом для поэтапного развертывания
Если вы не хотите, чтобы все пользователи сразу же получили возможность защищать файлы с помощью Azure RMS, можно настроить пользовательские элементы переноса с помощью команды Windows PowerShell [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx). Вы можете выполнить эту команду до или после активации Azure RMS.

> [!IMPORTANT]
> Чтобы использовать эту команду, необходимо иметь по меньшей мере версию **2.1.0.0**[модуля Azure RMS Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Чтобы проверить установленную вами версию, выполните следующую команду: **(Get-Module aadrm –ListAvailable).Version**.

Например, если изначально требуется, чтобы только администраторы в группе "ИТ-отдел" (с идентификатором объекта fbb99ded-32a0-45f1-b038-38b519009503) смогли защищать содержимое для тестирования, используйте следующую команду:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Обратите внимание, что для этого варианта настройки необходимо указать группу; вы не можете указать отдельных пользователей.

Если же необходимо гарантировать, что только пользователи, которые имеют соответствующие лицензии для использования Azure RMS, могли защищать содержимое:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
При использовании этого варианта все пользователи в организации всегда смогут использовать защищенный контент, который был защищен неким подмножеством пользователей, но при этом не смогут самостоятельно применять механизмы защиты информации из клиентских приложений. Например, они не увидят в клиентах Office шаблонов по умолчанию, которые публикуются автоматически при активации Azure RMS, или настроенных вами шаблонов.  Серверные приложения, такие как Exchange, могут реализовывать собственные механизмы управления, действующие на уровне отдельных пользователей, для интеграции с RMS и достижения того же результата.

## Дальнейшие шаги
После активации [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] для организации используйте статью [Стратегия развертывания Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md), чтобы проверить, есть ли другие шаги настройки, которые стоит выполнить перед развертыванием [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] для пользователей и администраторов. Например, может потребоваться использовать [пользовательские шаблоны](http://technet.microsoft.com/library/dn642472.aspx), чтобы упростить пользователям применение защиты информации к файлам, подключить локальные серверы для использования [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] с помощью установки [соединителя RMS](http://technet.microsoft.com/library/dn375964.aspx) и развернуть [приложение управления доступом Rights Management](http://technet.microsoft.com/library/jj585031.aspx), поддерживающее защиту файлов всех типов на всех устройствах. Для служб Office, таких как Exchange Online и SharePoint Online, требуется дополнительная настройка перед тем, как вы сможете использовать их функции управления правами на доступ к данным (IRM). Если же вы уже полностью выполнили настройку, ознакомьтесь со статьей [Использование службы Azure Rights Management](../Topic/Using_Azure_Rights_Management.md). В ней представлены рекомендации по эксплуатации, которые помогут вам успешно использовать развертывание в организации.

Дополнительные сведения о работе приложений с [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] см. в разделе [Поддержка приложениями Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## См. также
[Настройка службы Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

