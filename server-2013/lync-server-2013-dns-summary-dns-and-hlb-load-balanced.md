﻿---
title: 'Lync Server 2013: сводка по DNS — балансировка нагрузки на DNS и аппаратная балансировка нагрузки'
TOCTitle: Сводка по DNS — балансировка нагрузки на DNS и аппаратная балансировка нагрузки
ms:assetid: d2132695-1956-4190-a98e-cd7255cbded6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205273(v=OCS.15)
ms:contentKeyID: 49311254
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по DNS — балансировка нагрузки на DNS и аппаратная балансировка нагрузки в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

В следующей таблице приведена сводка DNS-записей, которые требуются для поддержки балансировки нагрузки DNS и Директор с аппаратной балансировкой нагрузки. Роль Директор требует использования DNS-записей, аналогичных используемым ролью переднего плана. Число необходимых записей отображается в дополнительных именах сертификатов, обязательных для сертификата Директор. В отличие от переднего плана в пуле Директоров не размещаются учетные записи пользователей или службы Mobility Service.

### DNS-записи, обязательные для пула каталогов, использующего балансировщик нагрузки DNS и аппаратный балансировщик нагрузки

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Местоположение/тип/порт</th>
<th>Полное доменное имя/DNS-запись</th>
<th>IP-адрес/полное доменное имя</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Директор</p></td>
<td><p>Директор содержит запись, которая использовалась для репликации передачи данных с сервера на сервер</p></td>
</tr>
<tr class="even">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>Директоров</p></td>
<td><p>Содержит запись Директоров с балансировкой нагрузки DNS для передачи данных с сервера на сервер</p></td>
</tr>
<tr class="odd">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Директоров</p></td>
<td><p>Входящий протокол SIP для передачи данных от внутреннего интерфейса сервер</p></td>
</tr>
<tr class="even">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Виртуальный IP-адрес HLB Директоров</p></td>
<td><p>Аппаратный балансировщик нагрузки, опубликованный веб-службами dialin с обратного прокси-сервера</p></td>
</tr>
<tr class="odd">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Виртуальный IP-адрес HLB Директоров</p></td>
<td><p>Аппаратный балансировщик нагрузки, опубликованный веб-службами meet с обратного прокси-сервера</p></td>
</tr>
<tr class="even">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>Виртуальный IP-адрес HLB Директоров</p></td>
<td><p>Аппаратный балансировщик нагрузки, опубликованный и определенный внешними службами веб-билетов обратного прокси-сервера для пула директора</p></td>
</tr>
</tbody>
</table>

