﻿---
title: Мониторинг производительности для мобильных устройств в Lync Server 2013
TOCTitle: Мониторинг производительности для мобильных устройств в Lync Server 2013
ms:assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh690033(v=OCS.15)
ms:contentKeyID: 49310654
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Мониторинг производительности для мобильных устройств в Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-14_

Служба Lync Server Mobility Service увеличивает нагрузку на серверы переднего плана и пулы серверов переднего плана. Мобильные устройства, поддерживающие подключение к серверу, даже когда приложение свернуто, например устройства Android и Nokia, создают большую нагрузку, чем устройства, которые прерывают подключение к серверу, когда приложение сворачивается. По мере роста использования мобильных устройств необходимо наблюдать за производительностью, чтобы определить, когда потребуется увеличить мощность.

Некоторые ограничения, влияющие на производительность мобильности:

  - доступная память;

  - ограничение очереди запросов;

  - одновременные подключения;

  - длина очереди IIS.

Кроме того, на производительность мобильности могут влиять следующие ограничения на серверах: не более двенадцати одновременных входов, проверок подлинности, а также возобновлений и прекращений сеансов. В большинстве развертываний эти максимальные значения не нуждаются в изменении.

## Содержание

  - [Отслеживание границ объема памяти сервера](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

  - [Отслеживание использования службы Mobility Service и UCWA](lync-server-2013-monitoring-mobility-service-and-ucwa-usage.md)

  - [Настройка высокой производительности службы Mobility Service](lync-server-2013-configuring-mobility-service-for-high-performance.md)

  - [Мониторинг файлов журнала трассировки запросов IIS](lync-server-2013-monitoring-iis-request-tracing-log-files.md)

  - [Счетчики производительности мобильной работы](lync-server-2013-mobility-performance-counters.md)
