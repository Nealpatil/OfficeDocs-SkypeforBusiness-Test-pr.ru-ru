﻿---
title: 'Lync Server 2013: развертывание устройства или сервера обеспечения связи в филиалах'
TOCTitle: Развертывание устройства или сервера обеспечения связи в филиалах
ms:assetid: cb780c14-dc5f-41ba-8092-f20ae905bd16
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398849(v=OCS.15)
ms:contentKeyID: 49311196
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание устройства или сервера обеспечения связи в филиалах с Lync Server 2013

 

_**Дата изменения раздела:** 2014-12-10_

Устойчивая система корпоративной голосовой связи означает устойчивость узлов филиалов, т. е. возможность обеспечить непрерывную работу корпоративной голосовой связи для пользователей узлов филиалов, если канал до центрального узла станет недоступным.

Для небольших и средних узлов филиала (от 25 до 1000 пользователей) рекомендуется развернуть для обеспечения связи в филиалах для терминирования вызовов по ТСОП с использованием встроенного шлюза ТСОП ил SIP-магистрали до поставщика услуг телефонии. для обеспечения связи в филиалах – это устройство стороннего производителя с сервером Blade Server под управлением Операционная система Windows Server 2008 R2, Lync Server 2013 Registrar, посредник и со шлюзом ТСОП – в одном корпусе.

Для сайтов филиала с 1000–5000 пользователей и без устойчивого канала глобальной сети мы рекомендуем использовать для обеспечения связи в филиалах с подключением к шлюзу PSTN или SIP-магистрали до поставщика услуг телефонии. для обеспечения связи в филиалах – это компьютер на основе Windows Server с установленным регистратором и программным обеспечением посредник.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для узлов филиалов более чем с 5000 пользователями и выделенными администраторами Lync Server мы рекомендуем использовать полное развертывание Lync Server 2013 отдельно от центрального узла.<br />
Сведения о выборе лучшего решения обеспечения устойчивости для сайтов филиалов в вашей организации, включая предварительные требования и рекомендации по планированию, см. в разделе <a href="lync-server-2013-branch-site-resiliency-requirements.md">Требования к устойчивости для сайтов филиала для Lync Server 2013</a> документации по планированию.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Развертывание устройства или сервера для обеспечения связи в филиалах с помощью Lync Server 2013 — задачи центрального сайта](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md)

  - [Развертывание устройства или сервера для обеспечения связи в филиалах с помощью Lync Server 2013 — задача сайта филиала](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)

  - [Настройка пользователей для организации устойчивости на сайтах филиалов в Lync Server 2013](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

  - [Пользователи, работающие дома на устройстве или сервере для обеспечения связи в филиалах, в Lync Server 2013](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md)

  - [Приложения: устройства и серверы для обеспечения связи в филиалах в Lync Server 2013](lync-server-2013-appendices-survivable-branch-appliances-and-servers.md)

## См. также

#### Другие ресурсы

[Развертывание Lync Server 2013](lync-server-2013-deploying-lync-server.md)
