﻿---
title: 'Lync Server 2013: высокая доступность внутреннего сервера'
TOCTitle: Высокая доступность внутреннего сервера
ms:assetid: c559aacb-4e1d-4e78-9582-41f966ad418d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205248(v=OCS.15)
ms:contentKeyID: 49311095
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Высокая доступность внутреннего сервера в Lync Server 2013

 

_**Дата изменения раздела:** 2013-08-12_

Для обеспечения высокой доступности внутренних серверов можно использовать синхронное зеркальное отображение SQL или кластеризацию SQL. Применение этих решений не является обязательным, но рекомендуется для поддержания устойчивости функционирования организации. Асинхронное зеркальное отображение SQL для обеспечения высокой доступности внутренних серверов в Lync Server 2013 не поддерживается. Далее в этом документе под зеркальным отображением SQL будет пониматься синхронное зеркальное отображение SQL, если явно не будет указано иное.

Зеркальное отображение SQL можно легко настроить с помощью топологий. Для настройки отказоустойчивой кластеризации SQL необходимо использовать SQL Server.

Если вы применяете зеркальное отображение SQL или кластеризацию SQL в пуле, который сопряжен с другим интерфейсным пулом для аварийного восстановления, необходимо использовать одинаковые серверные решения для обеспечения высокой доступности в обоих пулах. Не следует сопрягать пул, использующий зеркальное отображение SQL, с пулом, использующим кластеризацию SQL.

При развертывании инфраструктуры зеркального отображения SQL создаются зеркальные копии всех баз данных Lync Server в пуле, включая управления, если она находится в этом пуле, а также базы данных приложения группы ответа и приложения парковки вызовов, если эти приложения работают в пуле.

При зеркальном отображении SQL нет необходимости использовать общее хранилище для серверов. Каждый сервер хранит свою копию баз данных в локальном хранилище.

Развернуть зеркальное копирование SQL можно со следящим сервером или без него. Рекомендуется использовать следящий сервер, поскольку он обеспечивает автоматическую отработку отказа внутренним сервером. В противном случае администратор должен запускать отработку отказа вручную. Обратите внимание, что даже если следящий сервер развернут, администратор все равно при необходимости может запустить отработку отказа внутренним сервером вручную.

Одни следящий сервер можно использовать для нескольких пар внутренних серверов. Строгого взаимно-однозначного соответствия между следящими серверами и парами внутренних серверов нет. Развертывания с одним следящим сервером для нескольких пар внутренних серверов менее отказоустойчивы, чем топологии с отдельным следящим сервером для каждой пары внутренних серверов.

Подробнее о поддержке кластеризации SQL: [Поддержка программного обеспечения баз данных в Lync Server 2013](lync-server-2013-database-software-support.md). Подробнее о развертывании кластеров SQL: [Настройка кластеризации SQL Server в Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md).

## Время восстановления при автоматической отработке отказа внутренним сервером в условиях зеркального отображения SQL

При автоматической отработке отказа внутренним сервером в условиях зеркального отображения SQL плановое время восстановления (RTO) составляет 5 минут. Использование синхронного зеркального отображения SQL позволяет рассчитывать на отсутствие потери данных при отработке отказа внутренним сервером (за исключением редких случаев, когда одновременно происходит отказ и серверов переднего плана, и внутреннего сервера во время передачи данных между ними). Техническая плановая целевая точка восстановления (RPO) составляет 5 минут.

## Сбой внутреннего сервера со стороны пользователя в условиях зеркального отображения SQL

То, каким образом отказ отразится на пользователе, зависит от природы отказа и топологии.

Если в инфраструктуре с зеркальным отображением SQL и следящим сервером происходит отказ основного сервера, отработка отказа внутренним сервером происходит автоматически и очень быстро. Активные пользователи не должны заметить особых пауз в своих текущих сеансах.

Если следящий сервер на настроен, администратору потребуется некоторое время для проведения отработки отказа вручную. В этот период активные пользователи могут заметить последствия. Они продолжат свои сеансы как обычно в течение 30 минут. Если основной сервер к этому времени еще не восстановится, или администратор не выполнит отработку отказа на резервный сервер, то пользователи будут переключены в режим устойчивости, то есть не смогут выполнять задачи, требующие сохранения изменений в Lync Server (например, добавлять контакты).

При отказе и главного, и внутреннего зеркальных серверов или при отказе одного из них и следящего сервера внутренний сервер становится недоступным (даже если это основной сервер, продолжающий работать). В этом случае активные пользователи переключаются в режим устойчивости через некоторое время.
