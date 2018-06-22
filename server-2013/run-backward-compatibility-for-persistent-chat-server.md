﻿---
title: Организация обратной совместимости для сервера сохраняемого чата
TOCTitle: Организация обратной совместимости для сервера сохраняемого чата
ms:assetid: 53f1a706-3104-4a94-8b4e-8badd9a066d6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204901(v=OCS.15)
ms:contentKeyID: 49309790
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Организация обратной совместимости для сервера сохраняемого чата

 

_**Дата изменения раздела:** 2013-02-21_

Конечная точка сервера Lync Server 2013, сохраняемого сеанса беседы предоставляет способ создания простого URL-адреса, указывающего на пул серверов сохраняемого сеанса беседы. Это полезно для устаревших клиентов (Microsoft Office Communications Server 2007 R2групповой беседы или групповой беседы Lync Server 2010), так как пользователи могут вводить простой URL-адрес для конфигурации вручную, пытаясь указать устаревшему клиенту компьютер, на котором работает сервер Lync 2013, сохраняемый сеанс беседы. Эта конечная точка не используется сохраняемый сеанс беседы и необходима только для устаревших клиентов. Это оказывается полезным в промежуточный период, когда может происходить миграция комнат, однако клиенты Lync 2013 еще не развернуты в организации. Пользователи, использующие клиента Lync 2010бесед могут подключаться к внутреннему серверу сохраняемого сеанса беседывнутренний сервер.

Не требуется создавать несколько конечных точек сервера сохраняемого сеанса беседы – достаточно создать по одной для каждого пула серверов сохраняемого сеанса беседы. Администраторы могут создавать несколько конечных точек (по одной на пул), но устаревшие клиенты могут быть настроены для подключения только к одному пулу в каждый момент времени. В обычном или основном сценарии устаревшее развертывание представляет собой только один пул. В новом развертывании этот пул обычно переносится на новый сервер Lync Server 2013, и могут быть добавлены некоторые новые дополнительные серверов сохраняемого чата.

Этот основной сценарий обычно придерживается следующего шаблона.

  - Администрирование пользователей выполняется с помощью одного пула серверов групповой беседы Lync Server 2010, и клиенты Lync 2010 подключаются к этому пулу с помощью какого-либо широко известного пользователя (либо установленного по умолчанию sip:ocschat@ *\<domainName\>* .com, либо аналогичного). Эти пользователи являются доменными службами Доменные службы Active Directory с поддержкой SIP, и служба поиска регистрируется в них, чтобы получать входящие запросы.

  - Далее в сервере Lync Server 2013 устанавливается сервер сохраняемого сеанса беседы и пул серверов сохраняемого сеанса беседы.

  - В течение того времени, когда пользователи в сети отсутствуют (например, в выходные дни), выполняются следующие действия.
    
      - Отключается сервер групповой беседы Lync Server 2010.
    
      - Выполняется миграция данных из сервера групповой беседы Lync Server 2010 в пул серверов сохраняемого сеанса беседы сервера Lync Server 2013.
    
      - Широко известный пользователь удаляется из доменных служб Доменные службы Active Directory.
    
      - Создается новая *конечная точка устаревшего развертывания* с тем же самым SIP URI, что и у ранее удаленного широко известного пользователя.
    
      - Запускаются серверы сохраняемого чата сервера Lync Server 2013.

  - Пользователи снова входят с помощью своего Lync 2010 (клиента) и подключаются к своим данным без необходимости каких-либо изменений конфигурации.

  - Позднее можно вывести из эксплуатации сервер групповой беседы Lync Server 2010, а затем развернуть сервер Lync Server 2013сохраняемого сеанса беседы и установить новые серверов сохраняемого чата сервера Lync Server 2013.

Дополнительные сведения о миграции от сервера групповой беседы Lync Server 2010 на сервер сохраняемого сеанса беседы в сервере Lync Server 2013 см. в статье [Миграция с групповой беседы в Lync Server 2010 или Office Communications Server 2007 R2 на сервер сохраняемого сеанса беседы в Lync Server 2013](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md).

Для запуска обратной совместимости (создания конечной точки сервера сохраняемого сеанса беседы, указывающей на пул серверов сохраняемого сеанса беседы, который может использоваться устаревшими клиентами пула групповых бесед) выполните следующую команду:

    New-CsPersistentChatEndpoint -SipAddress <CO name, ex. persistentchat@contoso.com> -PersistentChatPoolFqdn <pool FQDN, like pcpool.contoso.com>

Затем настройте клиентов сохраняемый сеанс беседы, чтобы они использовали этот SIP-адрес в качестве своего контактного объекта. SIP-адрес создается с помощью командлета **New-CsPersistentChatEndpoint**t для конкретного пула серверов сохраняемого сеанса беседы.

Чтобы добавить конечную точку сервера сохраняемого сеанса беседы с помощью командной консоли командной строки Windows PowerShell, рассмотрите следующий пример. В этом случае настраивается контактный объект с именем "persistentchat" в топологии contoso.com", где полное доменное имя пула – "pcpool.contoso.com".

    New-CsPersistentChatEndpoint -SipAddress sip:persistentchat@contoso.com -PersistentChatPoolFqdn pcpool.contoso.com

## См. также

#### Концепции

[Миграция с групповой беседы в Lync Server 2010 или Office Communications Server 2007 R2 на сервер сохраняемого сеанса беседы в Lync Server 2013](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)
