﻿---
title: 'Lync Server 2013: топологии и компоненты для мобильной работы'
TOCTitle: Топологии и компоненты для мобильной работы
ms:assetid: be3cae7a-095d-4785-91ba-6fac99eba92a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh690037(v=OCS.15)
ms:contentKeyID: 49311034
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Топологии и компоненты для мобильной работы в Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-17_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Чтобы обеспечить поддержку мобильных приложений Lync на мобильных устройствах, Lync Server 2013 включает три службы: Lync Server 2013 Mcx Mobility Service, службу автообнаружения Lync Server 2013 и службу push-уведомлений Lync Server 2013. Накопительное обновление для Lync Server 2013 (февраль 2013 г.) включает дополнительную, расширенную службу для мобильных клиентов Lync 2013. Она обеспечивает поддержку мобильности благодаря использованию веб-API объединенных коммуникаций (UCWA). В этом разделе кратко рассматриваются указанные компоненты и определяются топологии Lync Server 2013, поддерживающие мобильность.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Службы мобильной связи также доступны в гибридных развертываниях. Если все пользователи вашей организации подключены к сети, вам не требуется развертывать службы для поддержки возможностей мобильной связи. Чтобы мобильные пользователи могли выполнять поиск своих сетевых удостоверений, вам потребуется задать параметры службы автообнаружения.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если планируется какое-либо подключение внешних пользователей (например, федерация, доступ внешних пользователей или функции мобильности), то необходимо использовать пограничные серверы сервер с серверами Сервер Standard Edition и переднего плана или пулом переднего плана. Серверы Сервер Standard Edition и переднего плана или пул переднего плана не имеют необходимых компонентов для разрешения внешним пользователям доступа к внутреннему или внутреннему развертыванию взаимодействия с внешними пользователями. Для всех сценариев, включающих совместную работу или взаимодействие внешних пользователей с внутренними, в том числе сценариев использования мобильности, необходимо развернуть хотя бы один пограничный сервер сервер и один обратный прокси-сервер.<br />
<em>Push-уведомление</em> использует тип федерации со службами Lync Online, в которых размещается система PNCH. Push-уведомление относится к звуковым предупреждениям, предупреждениям на экране (текстовым) и индикаторам событий, которые отправляются приложениями на Apple iPhone, iPad, iPod и Windows Phone, когда мобильное устройство неактивно. PNCH получает push-уведомления от Lync Server. Когда PNCH получает уведомление о сообщении, то перенаправляет уведомление мобильным клиентам через службы Apple Push Notification Services или службы Push-уведомлений Lync Server 2013, в зависимости от того, для какого мобильного клиента сообщение предназначено. Для установки федерации с Lync Online PNCH использует серверы сервер, сертификаты для обеспечения конфиденциальности и проверки подлинности, политики и правильно настроенные записи DNS. Клиенты Lync Mobile на базе Nokia Symbian и Android не используют PNCH. Подробные сведения о планировании и развертывании сервер см. в статьях <a href="lync-server-2013-planning-for-external-user-access.md">Планирование доступа внешних пользователей в Lync Server 2013</a> и <a href="lync-server-2013-deploying-external-user-access.md">Развертывание доступа внешних пользователей в Lync Server 2013</a>.<br />
Мобильные клиенты Lync 2013 для устройств Apple, на которых установлено накопительное обновление для Lync Server 2013 (февраль 2013 г.), больше не используют push-уведомления или PNCH. Мобильные клиенты Lync 2013 на основе Windows Phone по-прежнему используют push-уведомления и PNCH.</td>
</tr>
</tbody>
</table>


## Компоненты, предназначенные для поддержки мобильной связи

Службы, поддерживающие мобильную связь:

  - Веб-API объединенных коммуникаций **Lync Server 2013 (UCWA)** обеспечивает службы для обмена данными в режиме реального времени между мобильными и веб-клиентами в Lync Server 2013. При развертывании накопительного обновления для Lync Server 2013 (февраль 2013 г.) для ролей серверов " переднего плана" и " Директор" программа установки создает виртуальный каталог во внутренних и внешних веб-службах (Ucwa). Веб-компонент, который является частью виртуального каталога Ucwa, принимает вызовы от клиентов, поддерживающих UCWA. Клиентские приложения обмениваются по интерфейсу REST такими данными, как сведения о присутствии, контакты, сообщения VoIP, мгновенные сообщения, видеоконфереции и совместная работа. UCWA использует канал на основе протокола P-GET для отправки событий, таких как входящие звонки, входящие мгновенные сообщения и сообщения для клиентского приложения.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><em>REST</em> (Representational State Transfer или передача репрезентативного состояния) представляет собой архитектуру программного обеспечения для распределенных систем, которая широко используется в различных формах и хорошо отвечает требованиям веб-служб в общем.</td>
    </tr>
    </tbody>
    </table>


  - Служба **Lync Server 2013 Mobility Service (Mcx)** поддерживает функции Lync, такие как обмен мгновенными сообщениями, сведения о присутствии и контакты, на мобильных устройствах. Служба Mobility Service устанавливается на каждом сервере переднего плана в каждом пуле, который должен поддерживать функции Lync на мобильных устройствах. При установке Lync Server 2013 новый виртуальный каталог (Mcx) создается на внешнем и внутреннем веб-сайте на серверах с ролью " переднего плана".
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Lync Server 2013 с накопительным обновлением для Lync Server 2013 (февраль 2013 г.) поддерживает службу Mobility Service (обычно называемую Mcx), представленную в накопительном обновлении для Lync Server 2010 (ноябрь 2011 г.), а также веб-компонент UCWA. Комбинация двух этих служб обеспечивает взаимодействие и возможность для пользователей работать с мобильными клиентами Lync 2010 Mobile и Lync 2013 в среде Lync Server 2013.</td>
    </tr>
    </tbody>
    </table>


  - **Служба автообнаружения Lync Server 2013** идентифицирует расположение пользователя и позволяет мобильным устройствам и другим клиентам Lync находить ресурсы, такие как внутренние и внешние URL-адреса веб-служб Lync Server 2013 и URL-адрес службы Mcx или UCWA, независимо от расположения в сети. Служба автоматического обнаружения использует жестко заданные имена узлов (lyncdiscoverinternal для пользователей, расположенных в сети организации, и lyncdiscover для пользователей, расположенных за пределами сети организации) и домен SIP пользователя. Для поддержки клиентских подключений служба использует протокол HTTP или HTTPS.
    
    Служба автообнаружения устанавливается на всех переднего плана и на всех Директор каждого пула для поддержки функциональных возможностей Lync на мобильных устройствах. При установке службы автообнаружения на внешнем и внутреннем веб-сайтах переднего плана и Директор создается новый виртуальный каталог (Autodiscover).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Служба автообнаружения указана в этом разделе, так как она по-прежнему является критическим компонентом при предоставлении служб мобильных клиентов. Роль &quot;Автообнаружение&quot; в Lync Server 2013 была расширена для предоставления служб для всех клиентов. Сведения о планировании развертывания службы автообнаружения см. в статье <a href="lync-server-2013-planning-for-autodiscover.md">Планирование автоопределения в Lync Server 2013</a>.</td>
    </tr>
    </tbody>
    </table>


  - **Служба push-уведомлений**   – служба, которая расположена в центре обработки данных Lync Online. Если мобильное приложение Lync на поддерживаемом устройстве Apple iOS или Windows Phone неактивно, оно не сможет отвечать на новые события, такие как приглашение к сеансу обмена мгновенными сообщениями, пропущенное мгновенное сообщение, пропущенный звонок или сообщение голосовой почты, поскольку эти устройства не поддерживают мобильные приложения, запущенные в фоновом режиме. В таком случае на мобильное устройство отправляется уведомление, называемое *push-уведомлением*. Служба мобильной связи отправляет уведомление в облачную службу push-уведомлений, которая затем отправляет уведомление в службу Apple Push Notification Service (APNS) (для устройств Apple iOS) или службу push-уведомлений (Майкрософт) (MPNS) (для Windows Phone), которые, в свою очередь, отправляют его на мобильное устройство. Чтобы активировать приложение, пользователю необходимо коснуться уведомления на мобильном устройстве.
    
    Lync 2010 Mobile на устройствах Apple и Windows Phone использует push-уведомления. Мобильный клиент Lync 2013 для устройств Apple, представленный в накопительном обновлении для Lync Server 2013 (февраль 2013 г.), больше не использует PNCH.

На следующей схеме показано использование службы push-уведомлений в топологии Lync Server 2013, использующей интерфейс UCWA и мобильные клиенты Lync 2013.

![Службы push-уведомлений UCWA](images/Hh690037.166d60fd-ff71-4ffe-9f66-3c8bbde0b5ae(OCS.15).jpg "Службы push-уведомлений UCWA")

Представленная в накопительном обновлении для Lync Server 2010 (ноябрь 2011 г.) служба Mcx обеспечивает службы для клиентов Lync 2010 Mobile. Следующая схема иллюстрирует применение службы Push-уведомлений к топологии, использующей службу Mcx и клиенты Lync 2010 Mobile.

![Службы push-уведомлений MCX](images/Hh690037.3081634e-60e7-4348-b24e-bbbf05a90f5f(OCS.15).jpg "Службы push-уведомлений MCX")

## Поддерживаемые топологии

Применение накопительного обновления для Lync Server 2013 (февраль 2013 г.) включает веб-компоненты UCWA для поддержки мобильности для компонентов мобильных клиентов Lync 2013 в следующих топологиях.

  - Lync Server 2013 Standard Edition

  - Lync Server 2013 Enterprise Edition

В качестве сервер можно использовать Lync Server 2010  сервер.

Развертывание Lync Server 2013 без накопительного обновления для Lync Server 2013 (февраль 2013 г.) будет использовать службу Mcx Mobility Service и сможет предоставлять службы только для Lync 2010 Mobile.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Служба Mobility Service поддерживается на серверах переднего плана, размещаемых совместно с ролью посредник с двумя сетевыми интерфейсами, однако для настройки этих интерфейсов необходимо выполнить определенные действия. Вы должны назначить IP-адреса для конкретного интерфейса, которому будет назначена роль посредник, и IP-адрес сетевого интерфейса, которому будет назначена роль переднего плана. Эти действия выполняются в топологий путем выбора правильного IP-адреса для каждой службы вместо параметра по умолчанию <strong>Использовать все настроенные IP-адреса</strong>.</td>
</tr>
</tbody>
</table>


## См. также

#### Другие ресурсы

[Планирование доступа внешних пользователей в Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Развертывание доступа внешних пользователей в Lync Server 2013](lync-server-2013-deploying-external-user-access.md)  
[Планирование автоопределения в Lync Server 2013](lync-server-2013-planning-for-autodiscover.md)
