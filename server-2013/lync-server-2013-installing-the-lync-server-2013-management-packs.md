﻿---
title: Установка пакетов управления Lync Server 2013
TOCTitle: Установка пакетов управления Lync Server 2013
ms:assetid: b800d4ab-fdc8-4c72-a76a-b78932779fe3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205202(v=OCS.15)
ms:contentKeyID: 49310972
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Установка пакетов управления Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Без дополнительных средств System Center Operations Manager может отслеживать только небольшую часть операционной системы Windows. Однако вы можете существенно расширить возможности System Center Operations Manager, установив пакеты управления. Пакет управления — это программное обеспечение, которое добавляет компоненты, доступные System Center Operations Manager для мониторинга, а также задает способы мониторинга этих компонентов и параметры создания и регистрации оповещений. В состав Microsoft Lync Server 2013 входит 2 пакета управления System Center Operations Manager, которые предоставляют следующие возможности.

  - Пакет управления для компонентов и пользователей (Microsoft.LS.2013.Monitoring.ComponentAndUser.mp) отслеживает ошибки Lync Server, которые записываются в журналы событий, базы данных функции регистрации вызовов или качества взаимодействия и регистрируются счетчиками производительности. Вы можете настроить System Center Operations Manager для уведомления администраторов о критических ошибках по электронной почте, с помощью мгновенных сообщений или SMS-сообщений. (SMS или Short Message Service — это технология, которая используется для отправки текстовых сообщений с одного мобильного устройства на другое.)
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Дополнительные сведения о настройке уведомлений Operations Manager см. в статье &quot;Настройка уведомлений&quot; библиотеки TechNet по адресу <a href="http://go.microsoft.com/fwlink/?linkid=268785%26clcid=0x419" class="uri">http://go.microsoft.com/fwlink/?linkid=268785&amp;clcid=0x419</a>.</td>
    </tr>
    </tbody>
    </table>


  - Активный пакет управления (Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp) выполняет профилактическую проверку основных компонентов Lync Server, например возможности входа в систему, обмена мгновенными сообщениями или выполнения звонков на телефоны, расположенные в телефонной сети общего пользования (ТСОП). Для выполнения этих проверок используются командлеты искусственных транзакций Lync Server. Например, командлет **Test-CsIM** имитирует сеанс обмена мгновенными сообщениями между двумя тестовыми пользователями. Если тестовый сеанс заканчивается с ошибкой, то создается оповещение.

Два пакета управления, входящие в состав Lync Server 2013, отличаются от пакетов управления Microsoft Lync Server 2010 большим числом улучшений. Например, пакет управления для компонентов Lync Server 2013 выполняет мониторинг не только Lync Server. Помимо мониторинга журналов событий и счетчиков производительности Lync Server он также отслеживает производительность следующих критически важных компонентов и создает для них оповещения.

  - **Службы IIS**. Оповещения создаются при отключении служб IIS. Это важно, поскольку веб-службы Lync Server используют службы IIS.

  - **Загрузка процессора**. Оповещения создаются при нехватке системных ресурсов (например, доступной памяти). Оповещения будут создаваться даже в том случае, если Lync Server не настроен для обеспечения высокой нагрузки.

  - **Сбои компьютера**. Оповещения создаются при возникновении сбоев оборудования или программного обеспечения, которые угрожают устойчивости сервера. Например, если серверу угрожает сбой жесткого диска, администраторы Lync Server получат оповещения.

В новых пакетах управления также были расширены функции создания отчетов. Для Lync Server 2013 доступны следующие отчеты:

  - **Сквозной отчет о доступности**. Этот отчет содержит сведения о доступности или периоде безотказной работы основных служб Lync Server, например службы регистрации или присутствия.

  - **Отчет об использовании системы**. Этот отчет использует данные счетчиков производительности для предоставления сведений о тенденциях использования компонентов системы, например объеме доступной памяти и загрузке процессора.

  - **Отчет по компонентам**. Этот отчет содержит сведения об основных источниках оповещений, сгруппированные по компонентам Lync Server.

Помимо предоставления встроенных отчетов пакеты управления Lync Server 2013 автоматически создают оповещения для показателя стабильности звонков (измеряемого функцией регистрации вызовов) и состояний качества взаимодействия. Если вы включили функцию регистрации вызовов, то для просмотра оповещений о стабильности звонков выполните в консоли System Center Operations Manager следующие действия.

  - Последовательно разверните узлы **Monitoring**, **Microsoft Lync Server 2013 Health** (Работоспособность Microsoft Lync Server 2013), **Call Reliability and Media Quality** (Стабильность звонков и качество медиаданных) и щелкните **Call Reliability** (Стабильность звонков).

Чтобы просмотреть оповещения системы качества взаимодействия, выполните в консоли System Center Operations Manager следующие действия:

  - Последовательно разверните узлы **Monitoring**, **Microsoft Lync Server 2013 Health**, **Call Reliability and Media Quality** и **Media Quality** (Качество медиаданных).

Вместо механизма центрального обнаружения, используемого в Microsoft Lync Server 2010, пакеты управления Lync Server 2013 используют обнаружение на уровне компьютера. Это означает, что каждый агент System Center обнаруживает себя и сообщает о своем существовании управления. Использование обнаружения на уровне компьютера упрощает администрирование инфраструктуры System Center и позволяет совместно использовать разные версии пакетов управления Lync Server (например, пакеты управления для Lync Server 2010 и Lync Server 2013).

