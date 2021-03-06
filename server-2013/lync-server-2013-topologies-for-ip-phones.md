﻿---
title: Топологии для IP-телефонов
TOCTitle: Топологии для IP-телефонов
ms:assetid: 26ebffcf-43ff-4e70-847d-0fbc90e94e57
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425740(v=OCS.15)
ms:contentKeyID: 49309241
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Топологии для IP-телефонов

 

_**Дата изменения раздела:** 2012-06-21_

В этом разделе приводится обзор процесса подключения и рассматриваются различия в способах подключения IP-телефона во внутренней и внешней сетях.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server обеспечивает поддержку следующих IP-телефонов: телефон общего пользования Aastra 6721ip, стационарный телефон Aastra 6725ip, IP-телефон HP 4110 (телефон общего пользования), IP-телефон HP 4120 (стационарный телефон), стационарный IP-телефон Polycom CX600, стационарный IP-телефон Polycom CX700, IP-телефон общего пользования Polycom CX500 и IP-телефон для конференц-связи Polycom CX3000. На всех этих телефонах, кроме Polycom CX700, может работать Lync Phone Edition.</td>
</tr>
</tbody>
</table>


На следующей схеме показаны все компоненты, используемые для связи между устройствами в корпоративной среде.

**Внутренняя топология**

![Устройства внутри сети](images/Gg425740.3d88893e-df57-46e3-855a-a1d24589030a(OCS.15).jpg "Устройства внутри сети")

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Выше представлена логическая схема, которая не отражает особенности физического размещения. Например, доменные службы Active Directory (AD DS) редко располагаются на том же компьютере, что и другие компоненты Lync Server. Хранилище пользователя может располагаться на тыловом сервере или на сервере архивации и наблюдения. Командная консоль Lync Server, веб-сервер и службы обновления входят в роль сервера переднего плана.</td>
</tr>
</tbody>
</table>


На следующей схеме приводится обзор компонентов, используемых в том случае, если устройство находится за пределами корпоративной сети.

**Внешняя топология**

![Устройства снаружи сети](images/Gg425740.8ce6bb8e-b89c-4c4e-ac6d-41ac6c68f6f3(OCS.15).jpg "Устройства снаружи сети")

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Веб-служба обновления устройств предоставляет внешний и внутренний веб-сайты, но здесь показан только внешний веб-сайт.<br />
Если планируется включать внешний доступ, в DNS необходимо опубликовать расположение Регистратора и URL-адрес веб-службы обновления устройств для организации. Кроме того, для обеспечения внешних подключений устройств к корпоративной среде и наоборот нужно развернуть и правильно настроить пограничный сервер. На предыдущей схеме этот компонент не показан, поскольку развертывание пограничного сервера не является необходимым для подключения устройств.</td>
</tr>
</tbody>
</table>

