﻿---
title: 'Lync Server 2013: развертывание сервера сохраняемого чата'
TOCTitle: Развертывание сервера сохраняемого чата
ms:assetid: e3b930fb-6855-47f0-b6b3-7dfae386540d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205357(v=OCS.15)
ms:contentKeyID: 49311459
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание сервера сохраняемого чата в Lync Server 2013

 

_**Дата изменения раздела:** 2014-03-31_

Lync Server 2013, сохраняемого сеанса беседы является частью инфраструктуры Lync Server 2013.

Для развертывания сохраняемого сеанса беседы необходимо следующее:

  - использовать топологий для определения или импорта и последующей публикации топологии и компонентов, которые вы хотите развернуть;

  - подготовить среду для развертывания компонентов сохраняемого сеанса беседы;

  - установить и настроить компоненты сохраняемого сеанса беседы для развертывания.

Компонент сохраняемого сеанса беседы доступен с Lync Server 2013Enterprise Edition как отдельный пул (не размещаемый совместно с Enterprise Editionпереднего плана). Для сохраняемого сеанса беседы необходима роль SQL Serverвнутренний сервер в вашем пуле Enterprise Edition для хранения контента комнаты чатов и других важных метаданных. Рекомендуется установить **PersistentChatStore** на выделенном сервере SQL Serverвнутренний сервер, хотя совместное размещение Lync Server 2013внутренний сервер и **PersistentChatStore** на одном экземпляре SQL Server также поддерживается.

сохраняемого сеанса беседы также можно развернуть с Lync Server 2013Standard Edition. В этом случае **PersistentChatService**переднего плана размещается совместно на компьютере Standard Edition, а **PersistentChatStore**внутренний сервер можно развернуть на локальном экземпляре SQL Server, экспресс-выпуск.

Подробные сведения о поддерживаемых конфигурациях совместного расположения см. в разделе [Поддерживаемое совместное размещение серверов в Lync Server 2013](lync-server-2013-supported-server-collocation.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Мы не поддерживаем высокую доступность для сервера сохраняемого сеанса беседыStandard Edition. Производительность и масштабирование будут ограничены. Кроме того, поддерживается только новый сервер сохраняемого сеанса беседыСервер Standard Edition. Мы не поддерживаем обновление Lync Server 2010, групповой беседы до Lync Server 2013сохраняемого сеанса беседыStandard Edition.</td>
</tr>
</tbody>
</table>


Если вашей организации требуется поддержка соответствия требованиям, вы можете явно установить ее с помощью построителя сохраняемого сеанса беседы на сервере сохраняемого сеанса беседыпереднего плана. Для этого требуется отдельная база данных.

Каждой топологии требуется по крайней мере сервер с системой Lync Server 2013 и сервер с установленным программным обеспечением баз данных SQL Server.

Используйте топологий, чтобы добавить сохраняемого сеанса беседы в развертывания Lync Server 2013. Вы можете добавить один или несколько пулов серверов сохраняемого чата с помощью топологий. При развертывании нескольких серверов сохраняемого чата следуйте инструкциям, применяемым для любого пула. Дополнительные сведения см. в разделе [Развертывание Lync Server 2013](lync-server-2013-deploying-lync-server.md) в документации по развертыванию.

Дополнительные сведения о доступных топологиях и требованиях к техническим характеристикам и программному обеспечению для установки сервера сохраняемого сеанса беседы см. в разделе [Планирование сервера сохраняемого чата в Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) в документации по планированию, в разделе [Принципы работы сервера сохраняемого сеанса беседы в Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md) в документации по планированию, развертыванию или использованию, а также в разделе [Поддерживаемое оборудование для Lync Server 2013](lync-server-2013-supported-hardware.md) в документации по поддержке.

Дополнительные сведения о получении сертификатов, создании базы данных SQL Server и хранилища файлов см. в разделе [Развертывание Lync Server 2013](lync-server-2013-deploying-lync-server.md)в документации по развертыванию.

Один сервер сохраняемого сеанса беседыпереднего плана может поддерживать до 20 000 активных пользователей. У вас может быть один пул серверов сохраняемого сеанса беседы с 4 активными серверами переднего плана для поддержки 80 000 пользователей одновременно.

сохраняемого сеанса беседы также поддерживается на виртуальных серверах. Виртуальный сервер может поддерживать до 20 000 пользователей при условии соответствия характеристикам физического сервера.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Необходимо установить сохраняемого сеанса беседы в файловой системе NTFS для помощи в усилении безопасности файловой системы. FAT32 не является поддерживаемой файловой системой для сохраняемого сеанса беседы.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Принципы работы сервера сохраняемого сеанса беседы в Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md)

  - [Контрольный список развертывания для сервера сохраняемого чата в Lync Server 2013](lync-server-2013-deployment-checklist-for-persistent-chat-server.md)

  - [Технические требования для сервера сохраняемого чата в Lync Server 2013](lync-server-2013-technical-requirements-for-persistent-chat-server.md)

  - [Настройка систем и инфраструктуры для сервера сохраняемого чата в Lync Server 2013](lync-server-2013-setting-up-systems-and-infrastructure-for-persistent-chat-server.md)

  - [Добавление сервера сохраняемого сеанса беседы в развертывание в Lync Server 2013](lync-server-2013-adding-persistent-chat-server-to-your-deployment.md)

  - [Установка сервера сохраняемого чата в Lync Server 2013](lync-server-2013-installing-persistent-chat-server.md)

  - [Добавление администратора сохраняемого чата в Lync Server 2013](lync-server-2013-adding-a-persistent-chat-administrator.md)

  - [Настройка сервера сохраняемого чата в Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md)

  - [Настройка сервера сохраняемого сеанса беседы с помощью командлетов Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

  - [Устранение неполадок конфигурации сервера сохраняемого чата с помощью командлетов Windows PowerShell в Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md)

  - [Настройка сервера сохраняемого чата для обеспечения высокой доступности и аварийного восстановления в Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Отработка отказа и восстановление после сбоя сервера сохраняемого чата в Lync Server 2013](lync-server-2013-failing-over-and-failing-back-persistent-chat-server.md)
