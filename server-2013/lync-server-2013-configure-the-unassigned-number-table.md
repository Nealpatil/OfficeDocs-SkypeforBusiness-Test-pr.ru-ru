﻿---
title: 'Lync Server 2013: настройка таблицы неназначенных номеров'
TOCTitle: Настройка таблицы неназначенных номеров
ms:assetid: eaa01986-e92f-4328-acf6-4e46c4306a04
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg399053(v=OCS.15)
ms:contentKeyID: 49311553
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка таблицы неназначенных номеров в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-30_

В сервере Lync Server 2013 можно указать, что происходит со входящими вызовами на телефонные номера, которые существуют в организации, но не назначены пользователю или телефону. Можно задать воспроизведение сообщения для вызывающего абонента, или перенаправление в другое место назначения, или и то, и другое.

Настройка таблицы неназначенных номеров зависит от того, как ее планируется использовать. Можно включить в эту таблицу все действительные добавочные номера для организации, только неназначенные добавочные номера или оба типа номеров. Таблица неназначенных номеров может включать как назначенные, так и неназначенные номера, но вызывается только в том случае, если вызывающий абонент набирает номер, который в текущий момент не назначен. Если в таблицу неназначенных номеров включить все действительные добавочные номера, то можно указать действие, которое должно выполняться, когда кто-либо увольняется из организации, и тогда не придется заново настраивать таблицу. Если в таблицу включить неназначенные добавочные номера, то можно настраивать действие, выполняющееся для определенных номеров. Например, если добавочный номер службы поддержки клиентов изменился, то старый номер можно включить в эту таблицу и назначить его объявлению, которое сообщает новый номер.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед настройкой таблицы неназначенных номеров в системе должны уже быть заданы объявления или настроен автосекретарь единой системы обмена сообщениями Exchange.</td>
</tr>
</tbody>
</table>



> [!TIP]
> Когда кто-либо звонит на неназначенный номер, Lync Server выполняет поиск в таблице неназначенных номеров сверху вниз и использует первый соответствующий диапазон. Таким образом, действие, которое должно выполняться последним, должно быть задано для последнего диапазона в таблице.



## Содержание

[Создание или изменение диапазона неназначенных номеров в Lync Server 2013](lync-server-2013-create-or-modify-an-unassigned-number-range.md) [Создание объявления в Lync Server 2013](lync-server-2013-create-an-announcement.md)
