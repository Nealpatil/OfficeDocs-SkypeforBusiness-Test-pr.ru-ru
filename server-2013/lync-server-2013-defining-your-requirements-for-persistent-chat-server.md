﻿---
title: 'Lync Server 2013: определение своих требований для сервера сохраняемого чата'
TOCTitle: Определение требований организации для сервера сохраняемого чата
ms:assetid: 568674fb-c08a-4170-ac38-e2f8428c69e0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398372(v=OCS.15)
ms:contentKeyID: 49309804
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Определение требований организации для сервера сохраняемого чата в Lync Server 2013

 

_**Дата изменения раздела:** 2014-01-15_

Перед развертыванием сервера сохраняемого сеанса беседы в организации следует учесть ряд ключевых вопросов по оптимизации развертывания.

  - Кто (профиль пользователя) будет использовать сервер сохраняемого сеанса беседы? Сервер сохраняемого сеанса беседы включается политикой, которая может быть задана на глобальном уровне, а также на уровне сайта, пули или пользователя.

  - Сколько пользователей (масштабируемость) может поддерживаться сервером сохраняемого сеанса беседы? Система сохраняемого сеанса беседы поддерживает 150 000 пользователей (включаются политикой), и не более 80000 пользователей должны одновременно использовать систему сохраняемого сеанса беседы. Отдельный сервер сохраняемого сеанса беседы может поддерживать 20 000 подключенных пользователей, а отдельный пул серверов сохраняемого сеанса беседы – до 4 активных серверов, что в совокупности составляет 80000 одновременно подключенных пользователей.

  - Выполняется ли миграция с предыдущей версии сервера групповой беседы или впервые развертывается новая версия сохраняемого сеанса беседы?

  - Существуют ли нормативные требования? сохраняемого сеанса беседы поддерживает соответствие нормам и требованиям. Служба соответствия совмещена с сохраняемого сеанса беседыпереднего плана, что отличается от предыдущих версий сервера групповой беседы, где был необходим отдельный компьютер. Функции соответствия являются дополнительными и, если выбраны, нуждаются в базе данных соответствия, которую следует настроить для хранения данных и событий соответствия. Может понадобиться также настроить адаптер для извлечения данных из базы данных соответствия и преобразования их в другой формат (например, XML-файлы или архивы, размещенные в Exchange).

  - Каким образом можно контролировать сферу применения, этические нормы и права доступа? Можно определить **Категории** для разграничения прав и выбора пользователей, которые могут присутствовать в тех или иных комнатах.

  - Как можно ограничить права на создание комнат? С помощью группы **Авторы** можно дать права пользователям на создание комнат в соответствии с используемыми категориями. Авторы могут назначать других участников в качестве **менеджеров комнат чата** для постоянного управления комнатами (добавление или удаление дополнительных участников) в соответствии с параметром **AllowedMembers/DeniedMembers**, настроенным для той или иной категории.

  - Как можно создавать комнаты? сохраняемого сеанса беседы предоставляет веб-компоненты для создания комнат и управления ими. Их можно запустить в клиенте Lync 2013. Можно определить пользовательское решение (с помощью набора SDK для серверов сохраняемого сеанса беседы), которое будет соответствовать определенным требованиям и рабочим процессам бизнеса. Можно также настроить сервер сохраняемого сеанса беседы для переадресации пользователя к созданному пользовательскому решению.

  - Какие типы надстроек следует предоставлять? **Надстройки** улучшают работу пользователей, задействуя панель расширений в клиенте Lync 2013, на которой предоставляются возможности, имеющие отношение к данной комнате. Можно указать, какие общие надстройки будут наиболее полезными (например, веб-сайт компании, внутренние документы для совместной работы и т. д.). Менеджеры комнат чата могут выбирать зарегистрированные надстройки и сопоставлять их с комнатами.

  - Какие предъявляются требования к высокой доступности и аварийному восстановлению? Сервер сохраняемого сеанса беседы поддерживает зеркалирование SQL Server и кластеризацию SQL Server в качестве средства высокой доступности. Кроме того, поддерживается до 8 серверов (4 активных и 4 пассивных) в расширенном пуле с доставкой журналов SQL Server для аварийного восстановления.

  - Существуют ли нормативные требования? Если компания находится в стране или регионе, где данные должны храниться на уровне страны, может понадобиться развернуть несколько пулов серверов сохраняемого чата по одному для каждого географического региона. Комната, категория или надстройка не могут использоваться совместно несколькими пулами, но принадлежат только одному пулу серверов сохраняемого сеанса беседы. Можно управлять набором категорий, надстройками и комнатами для каждого пула серверов сохраняемого сеанса беседы. Можно дать пользователям доступ к комнатам в одном или нескольких пулах с помощью области действия категории AllowedMembers или области действия членства для комнаты в зависимости от того, как были определены категории.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Наличие нескольких пулов серверов сохраняемого чата не повышает масштабируемость (ко всем пулам серверов сохраняемого чата все так же могут подключиться не более 80 000 пользователей одновременно). Основной причиной для поддержки нескольких пулов серверов сохраняемого чата является необходимость соблюдения нормативных требований.</td>
    </tr>
    </tbody>
    </table>
