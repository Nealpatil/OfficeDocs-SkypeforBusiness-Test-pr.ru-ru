﻿---
title: 'Lync Server 2013: обзор приложения "Оповещение"'
TOCTitle: Обзор приложения "Оповещение"
ms:assetid: 2abee804-2599-48bb-90b2-15df0bae5e20
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204757(v=OCS.15)
ms:contentKeyID: 49309275
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обзор приложения \"Оповещение\" в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-13_

При развертывании приложения "Объявление" вам необходимо настроить таблицу неназначенных номеров, которая определяет действие, выполняемое при наборе неназначенного номера. Таблица неназначенных номеров содержит диапазоны номеров телефонов, допустимых для организации, и указывает, какое приложение "Объявление" обрабатывает каждый из этих диапазонов. Когда звонящий набирает номер телефона, который допустим для вашей организации и не назначен никому, Lync Server выполняет поиск этого номера в таблице маршрутизации неназначенных номеров, определяет, к какому диапазону он относится, и перенаправляет звонок в приложение "Объявление", указанное для этого диапазона. Приложение "Объявление" отвечает на звонок и воспроизводит звуковое сообщение (если вы настроили его соответствующим образом), а затем отключает звонок или переводит его в предварительно заданное назначение, например оператору. Вы можете использовать командлеты командной консоли Командная консоль Lync Server для настройки нескольких звуковых сообщений или для перевода назначений.

Способ настройки таблица неназначенных номеров зависит от ее последующего использования. Если у вас имеются определенные номера, которые больше не используются, и вы хотите воспроизводить для каждого номера индивидуальные сообщения, то можете ввести эти номера в таблицу неназначенных номеров. Например, если вы изменили номер отдела обслуживания клиентов, вы можете ввести старый номер обслуживания клиентов и сопоставить его с оповещением, в котором указывается новый номер. Если вы хотите воспроизвести сообщение общего характера любому человеку, позвонившему по неназначенному номеру, например номеру уволившегося сотрудника, то можете ввести диапазоны для всех допустимых добавочных номеров в организации. Таблица неназначенных номеров вызывается при наборе звонящим номера, который в данный момент не назначен.

В системе Lync Server 2013 приложение "Объявление" автоматически устанавливается с приложением "Группа ответа". Приложения "Объявление" и "Группа ответа" являются стандартными компонентами развертывания корпоративной голосовой связи: при развертывании корпоративной голосовой связи оба этих приложения развертываются автоматически.

