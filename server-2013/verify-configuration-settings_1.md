﻿---
title: Проверка параметров конфигурации
TOCTitle: Проверка параметров конфигурации
ms:assetid: 41dbf91c-f2e1-4b9a-88cf-959575558cf2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204848(v=OCS.15)
ms:contentKeyID: 49309574
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Проверка параметров конфигурации

 

_**Дата изменения раздела:** 2015-03-09_

После объединения топологии и запуска командлета **Import-CsLegacyConfiguration** убедитесь, что политики и параметры Office Communications Server 2007 R2 были импортированы в Lync Server 2013. В следующей таблице приведены политики и параметры, которые следует проверить.

## Политики и параметры, которые следует проверить после миграции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>При использовании этой нагрузки:</th>
<th>Проверьте следующие политики и параметры:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Мгновенные сообщения и конференц-связь</p></td>
<td><p>Политика присутствия</p>
<p>Политика конференц-связи</p></td>
</tr>
<tr class="even">
<td><p>Конференц-связь с телефонным подключением</p></td>
<td><p>Номера для телефонного подключения</p>
<p>Абонентские группы</p></td>
</tr>
<tr class="odd">
<td><p>Корпоративная голосовая связь</p></td>
<td><p>Политика голосовой связи</p>
<p>Маршруты голосовых вызовов</p>
<p>Абонентские группы</p>
<p>Параметры использования ТСОП</p></td>
</tr>
<tr class="even">
<td><p>Communicator Web Access</p></td>
<td><p>Простые URL-адреса</p></td>
</tr>
<tr class="odd">
<td><p>внешние пользователи;</p></td>
<td><p>Политики внешнего доступа</p></td>
</tr>
<tr class="even">
<td><p>Архивация</p></td>
<td><p>Политика архивации</p></td>
</tr>
</tbody>
</table>


## Чтобы проверить политики и параметры

1.  В среде Office Communications Server 2007 R2 запишите имена абонентских групп (которые ранее назывались профилями расположений), номера доступа по телефону (номера доступа по телефону и регионы для помощника по конференц-связи), маршруты голосовой связи и политики, приведенные в предыдущей таблице, а также URL-адреса, используемые для Communicator Web Access.

2.  На интерфейсном сервере Lync Server 2013 откройте оснастку управления Lync Server.

3.  Чтобы проверить импортированные политики конференц-связи, на левой панели щелкните пункт **Конференц-связь** , щелкните **Политика конференц-связи** , затем проверьте, что все политики конференц-связи в среде Office Communications Server 2007 R2 включены в приведенный список.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Политика <strong>Собрание</strong> из предыдущих версий Office Communications Server не является политикой конференц-связи в Lync Server 2013. Кроме того, параметр <strong>Анонимные участники</strong> в предыдущих версиях Office Communications Server теперь является параметром в политике конференц-связи Lync Server 2013.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если в Office Communications Server 2007 R2 политика конференц-связи не задана как <strong>для пользователя</strong> , импортируется только параметры глобальной политики. В этом случае никакие другие политики конференц-связи не импортируются.</td>
    </tr>
    </tbody>
    </table>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если для <strong>анонимных участников</strong> в политике конференц-связи Office Communications Server 2007 R2 выставлено значение <strong>Применять к пользователю</strong> , при миграции создаются две политики конференц-связи: одна со значением параметра <strong>AllowAnonymousParticipantsInMeetings</strong> равным <strong>True</strong> и вторая со значением параметра <strong>AllowAnonymousParticipantsInMeetings</strong> равным <strong>False</strong> .</td>
    </tr>
    </tbody>
    </table>


4.  Чтобы проверить импортированные абонентские группы, щелкните **Маршрутизация голосовой связи** , щелкните **Абонентская группа** , затем убедитесь, что все абонентские планы из среды Office Communicator 2007 R2 включены в список.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>В Lync Server 2013<strong>профили расположений</strong> теперь называются <strong>абонентскими группами</strong> .</td>
    </tr>
    </tbody>
    </table>


5.  Чтобы проверить импортированные политики голосовой связи, щелкните **Маршрутизация голосовой связи** , щелкните **Политика голосовой связи** , затем убедитесь, что все политики голосовой связи из среды Office Communicator 2007 R2 включены в список.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если в Office Communications Server 2007 R2 политика голосовой связи не задана как <strong>для пользователя</strong> , импортируется только параметры глобальной политики. В этом случае никакие другие политики голосовой связи не импортируются.</td>
    </tr>
    </tbody>
    </table>


6.  Чтобы проверить импортированные маршруты голосовой связи, щелкните **Маршрутизация голосовой связи** , щелкните **Маршрут** , затем убедитесь, что все маршруты голосовой связи из среды Office Communicator 2007 R2 включены в список.

7.  Чтобы проверить импортированные параметры использования ТСОП, щелкните **Маршрутизация голосовой связи** , щелкните **Использование ТСОП** , затем убедитесь, что параметры использования ТСОП из среды Office Communicator 2007 R2 включены в список.

8.  Чтобы проверить импортированные политики внешнего доступа, щелкните **Федерация и внешний доступ** , щелкните **Политика внешнего доступа** , затем убедитесь, что все политики внешнего доступа из среды Office Communicator 2007 R2 включены в список.

9.  Чтобы проверить политики архивации, щелкните **Мониторинг и архивация** , щелкните **Политика архивации** , затем убедитесь, что все политики архивации из среды Office Communications Server 2007 R2 включены в список.

10. Откройте Командная консоль Lync Server.

11. Чтобы проверить политики присутствия, введите в командной строке следующую команду:
    
        Get-CsPresencePolicy
    
    Проверив имя в параметре **Identity** , убедитесь, что политики присутствия были импортированы из среды Office Communications Server 2007 R2.

## Чтобы проверить политики и параметры с помощью командлетов

1.  Откройте Командная консоль Lync Server.

2.  Запустите командлеты в следующей таблице для проверки политик и параметров.
    
    Синтаксис этих командлетов аналогичен следующему примеру:
    
        Get-CsConferencingPolicy
    
    Для получения дополнительных сведений об этих командлетах, выполните следующую команду:
    
        Get-Help <cmdlet name> -Detailed


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Для этой политики или параметра:</th>
<th>Используйте следующий командлет:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Политика присутствия</p></td>
<td><p><strong>Get-CsPresencePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Политика конференц-связи</p></td>
<td><p><strong>Get-CsConferencingPolicy</strong></p></td>
</tr>
<tr class="odd">
<td><p>Номера для телефонного подключения</p></td>
<td><p><strong>Get-CsDialInConferencingAccessNumber</strong></p></td>
</tr>
<tr class="even">
<td><p>Абонентские группы</p></td>
<td><p><strong>Get-CsDialPlan</strong></p></td>
</tr>
<tr class="odd">
<td><p>Политика голосовой связи</p></td>
<td><p><strong>Get-CsVoicePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Маршруты голосовых вызовов</p></td>
<td><p><strong>Get-CsVoiceRoute</strong></p></td>
</tr>
<tr class="odd">
<td><p>Использование ТСОП</p></td>
<td><p><strong>Get-CsPstnUsage</strong></p></td>
</tr>
<tr class="even">
<td><p>URL-адреса</p></td>
<td><p><strong>Get-CsSimpleUrlConfiguration</strong></p></td>
</tr>
<tr class="odd">
<td><p>Политики внешнего доступа</p></td>
<td><p><strong>Get-CsExternalAccessPolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Политика архивации</p></td>
<td><p><strong>Get-CsArchivingPolicy</strong></p></td>
</tr>
</tbody>
</table>
