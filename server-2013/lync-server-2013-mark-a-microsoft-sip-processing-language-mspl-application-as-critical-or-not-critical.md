﻿---
title: Отметка приложения MSPL как очень важного или или не очень важного
TOCTitle: Отметка приложения MSPL как очень важного или или не очень важного
ms:assetid: df68fdc6-b7e6-4f07-acdc-0cd4c2c888a1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182598(v=OCS.15)
ms:contentKeyID: 49311401
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Отметка приложения MSPL как очень важного или или не очень важного

 

_**Дата изменения раздела:** 2012-11-01_

Приложения сервера MSPL (Microsoft SIP Processing Language) — это основанные исключительно на сценариях приложения, которые вместо API для Microsoft Lync 2010 используют язык сценариев MSPL. Некоторые серверные приложения MSPL указаны как критичные. Если сценарий является критичным, он должен запускаться при включении компьютера для загрузки системы Lync Server 2013. Если во время работы системы Lync Server происходит сбой сценария, сервер не завершает работу, а прекращает отправлять трафик в этот сценарий и записывает ошибки в журнал событий.

Вы можете использовать панель управления Lync Server , чтобы помечать серверные приложения MSPL как критичные или отменять такую пометку.

Данную возможность поддерживают не все сценарии. Например, сценарий DefaultRouting помечен как критичный, и изменить этот параметр для сценария DefaultRouting нельзя.

## Пометка серверного приложения MSPL как критичного и отмена пометки

1.  Войдите на любой компьютер, подключенный к сети, где развернут Lync Server 2013, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsServerAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Topology** (Топология), а затем **Server Application** (Серверное приложение).

4.  На странице **Server Application** (Серверное приложение) при необходимости щелкните заголовок столбца для сортировки приложений, а затем щелкните серверное приложение, которое хотите изменить.

5.  Щелкните элемент **Action** (Действие).

6.  Щелкните элемент **Mark as critical** (Пометить как критичный) или **Unselect as critical** (Отменить пометку) (если сценарий поддерживает эту возможность).

## См. также

#### Задачи

[Включение и отключение серверного приложения MSPL](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  

#### Концепции

[Просмотр серверных приложений Microsoft SIP Processing Language (MSPL) в Lync Server 2013](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  

#### Другие ресурсы

[Управление топологией Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)
