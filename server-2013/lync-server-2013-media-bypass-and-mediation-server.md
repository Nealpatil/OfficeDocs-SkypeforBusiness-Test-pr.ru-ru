﻿---
title: 'Lync Server 2013: сервер-посредник и обход сервера посредника'
TOCTitle: Сервер-посредник и обход сервера посредника
ms:assetid: 8ed35f95-05cd-4b5d-8470-442d2323df71
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398719(v=OCS.15)
ms:contentKeyID: 49310487
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сервер-посредник и обход сервера посредника в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-21_

Обход сервера-посредника появился в Lync Server и позволяет администратору настроить маршрутизацию вызовов таким образом, чтобы вызовы проходили напрямую между конечной точкой пользователя и шлюзом ТСОП, без прохода через сервер посредник. Обход сервера-посредника улучшает качество вызова, поскольку уменьшается задержка, потребность в преобразовании, вероятность потери пакетов и число точек вероятного сбоя. Когда удаленный сайт без сервера-посредника посредник подключается к центральному сайту с помощью связей WAN с ограниченной пропускной способностью, обход сервера-посредника понижает требования к пропускной способности, позволяя мультимедиа от клиента на удаленном сайте проходить напрямую к своему локальному шлюзу без предварительного прохода по связи WAN к серверу-посреднику посредник на центральном сайте и обратно. Это сокращение обработки мультимедиа также дополняет возможность сервера-посредника посредник управлять несколькими шлюзами.

Обход сервера-посредника и контроль допуска звонков являются взаимоисключающими функциями. Если для вызова применяется обход сервера-посредника, то для него не применяется контроль допуска звонков. Предполагается, что нет никакой связи с ограниченной пропускной способностью сторон, участвующих в вызове.

## См. также

#### Концепции

[Контроль допуска звонков и сервер-посредник в Lync Server 2013](lync-server-2013-call-admission-control-and-mediation-server.md)  

#### Другие ресурсы

[Планирование обхода серверов-посредников в Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)
