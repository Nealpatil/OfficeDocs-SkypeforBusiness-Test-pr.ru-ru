﻿---
title: 'Lync Server 2013: пользовательские модели'
TOCTitle: Пользовательские модели Lync Server 2013
ms:assetid: c551371c-d740-4372-bada-f0d713ec0d33
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398811(v=OCS.15)
ms:contentKeyID: 49888181
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Пользовательские модели в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Описываемые здесь пользовательские модели предоставляют основу для параметров и рекомендаций по планированию мощности, которые приводятся в статье [Планирование мощности для Lync Server 2013 с помощью моделей пользователя](lync-server-2013-capacity-planning-using-the-user-models.md).

## Пользовательские модели Lync Server 2013

В следующей таблице дается описание пользовательской модели для регистрации, контактов, обмена мгновенными сообщениями и присутствия в Lync Server 2013.

### Пользовательская модель среды и регистрации

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Размер и распределение развертывания</p></td>
<td><p>Мы моделируем большое развертывание с тремя центральными сайтами и с одним интерфейсным пулом на каждом сайте.</p></td>
</tr>
<tr class="even">
<td><p>Процент пользователей Active Directory</p></td>
<td><p>Мы предполагаем, что для 70% всех пользователей Active Directory включена поддержка Lync Server. 80% из этих пользователей входят в Lync Server каждый день (параллелизм 80%). На основе количества параллельных пользователей рассчитываются числа в оставшейся части этого раздела.</p></td>
</tr>
<tr class="odd">
<td><p>Изменения Active Directory</p></td>
<td><p>Мы предполагаем, что каждую неделю 0,5% всех пользователей создается в Active Directory и активируется для Lync, и 0,5% всех пользователей отключается от Active Directory и от Lync. Для 5% пользователей каждую неделю изменяется по крайней мере один атрибут Active Directory.</p></td>
</tr>
<tr class="even">
<td><p>Группы рассылки Active Directory</p></td>
<td><p>Мы предполагаем, что число групп рассылки Active Directory в организации втрое больше количества всех пользователей в Active Directory. Эти группы рассылки имеют следующие размеры:</p>
<ul>
<li><p>64% имеют от 2 до 30 пользователей;</p></li>
<li><p>13% имеют от 31 до 50 пользователей;</p></li>
<li><p>10% имеют от 51 до 100 пользователей;</p></li>
<li><p>13% имеют от 101 до 500 пользователей.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Пользователи протокола VoIP</p></td>
<td><p>Для 60% пользователей Lync Server включена поддержка объединенных коммуникаций (т. е. их номера телефонов принадлежат Lync Server).</p></td>
</tr>
<tr class="even">
<td><p>Распределение зарегистрированных клиентов</p></td>
<td><p>65% клиентов используют программное обеспечение Lync 2013, включая Lync и Lync Phone Edition.</p>
<p>30% клиентов используют клиентское программное обеспечение из предыдущей версии Lync.</p>
<p>5% клиентов используют Lync Web App.</p>
<p>Мы предполагаем, что если мобильность включена, то 40% пользователей используют эту функцию параллельно с другими вышеуказанными зарегистрированными клиентами. В этом случае коэффициент нескольких точек подключения клиента (MPOP) составляет 1:1,9. Если мобильность отключена, то коэффициент MPOP составляет 1:1,5.</p></td>
</tr>
<tr class="odd">
<td><p>Распределение удаленных пользователей</p></td>
<td><p>70% пользователей подключается внутренним образом.</p>
<p>30% пользователей подключается через пограничный сервер и Директор.</p></td>
</tr>
<tr class="even">
<td><p>Распределение контактов</p></td>
<td><p>Пользователь имеет не более 1000 контактов. Менее 1% пользователей имеет 1000 контактов. Менее 25% пользователей имеет как минимум 100 контактов.</p>
<p>Пользователи с подключением к общедоступному облаку в среднем имеют по 80 контактов. Для этих пользователей:</p>
<ul>
<li><p>50% контактов находятся внутри организации; 10% пользователей являются удаленными, подключающимися извне через брандмауэр;</p></li>
<li><p>40% контактов являются пользователями общедоступного облака (например, пользователями AOL, Yahoo!, MSN или Google Talk);</p></li>
<li><p>10% контактов приходятся на федеративных партнеров.</p>
<div class="alert">
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>С 1 сентября 2012 г. прекращена продажа лицензий пользовательских подписок на подключение к общедоступным службам обмена мгновенными сообщениями Microsoft Lync (PIC USL) по новым или продляемым соглашениям. Клиенты с активными лицензиями смогут продолжать использование федерации с Yahoo! Messenger до отключения службы. Поддержка служб AOL и Yahoo! завершается в июне 2014 г. Дополнительные сведения см. в статье <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Поддержка подключения к общедоступным службам обмена мгновенными сообщениями в Lync Server 2013</a>.</p></li>
<li><p>Лицензия подписки пользователя на возможность подключения к общедоступным службам обмена мгновенными сообщениями представляет собой лицензию подписки на пользователя в месяц, которая необходима для того, чтобы Lync Server или Office Communications Server могли образовывать федерацию с Yahoo! Messenger. Корпорация Майкрософт смогла предоставлять данную услугу благодаря поддержке со стороны компании Yahoo!, однако соответствующий базовый договор расторгается.</p></li>
<li><p>Сейчас, более чем когда-либо раньше, Lync представляет собой эффективное средство для объединения организаций и отдельных пользователей по всему миру. Федерация с Windows Live Messenger не требует никаких дополнительных лицензий на пользователя/устройство, кроме Lync Standard CAL. В этот список будет добавлена федерация Skype, позволяя пользователям Lync взаимодействовать с сотнями миллионов людей посредством мгновенных сообщений и голосовой связи.</p></li>
</ul></td>
</tr>
</tbody>
</table>

</div></li>
</ul>
<p>Пользователи без возможности подключения к общедоступному облаку в среднем имеют по 50 контактов. Для этих пользователей:</p>
<ul>
<li><p>80% контактов находятся внутри организации; 10% пользователей являются удаленными, подключающимися извне через брандмауэр;</p></li>
<li><p>20% контактов приходятся на федеративных партнеров.</p>
<p>Каждый пользователь имеет одну группу рассылки в своем списке контактов. Для тестирования производительности мы предполагаем, что группы рассылки всегда расширенные.</p></li>
</ul>
<p>25% контактов пользователей используют XMPP.</p></td>
</tr>
<tr class="odd">
<td><p>Время сеанса</p></td>
<td><p>Среднее время сеанса входа пользователя в систему составляет 12 часов. Все пользователи выполняют вход в течение 120 минут после начала сеанса.</p></td>
</tr>
</tbody>
</table>


### Пользовательская модель обмена мгновенными сообщениями и присутствия

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Одноранговые сеансы обмена мгновенными сообщениями</p></td>
<td><p>Каждый пользователь в среднем имеет по шесть одноранговых сеансов обмена мгновенными сообщениями в день.</p>
<p>10 мгновенных сообщений на сеанс.</p>
<p>Каждое сообщение сопровождается двумя сообщениями SIP INFO и двумя сообщениями SIP 200 OK (для индикаторов состояния, таких как “Вводится &lt;имя&gt;”)</p></td>
</tr>
<tr class="even">
<td><p>Опрос присутствия</p></td>
<td><p>В основном для опроса присутствия мы предполагаем по 60 опросов на каждого пользователя в час. Для каждого пользователя предполагаются следующие средние значения.</p>
<ul>
<li><p>Один опрос в день присутствия пользователей со вкладки &quot;Организация&quot; пользователя (но не из списка контактов). В среднем на вкладке &quot;Организация&quot; пользователя имеется 15 пользователей, не являющихся контактами. В день выполняется две операции просмотра карточки контакта.</p></li>
<li><p>Оценивается, что один опрос присутствия каждый раз, когда пользователь щелкает другого пользователя для начала беседы, выполняется раз в час.</p></li>
<li><p>Выполняется по шесть поисков пользователей в час. При каждом выполнении поиска пакетный опрос отправляется каждому в списке результатов поиска. Мы предполагаем, что средний размер результатов поиска – 20. Если результаты поиска остаются на экране, то пакетный опрос обновляется каждые 5 минут; мы предполагаем, что будет два таких обновления в час.</p></li>
<li><p>Когда пользователь открывает или предварительно просматривает электронное письмо в Outlook, выполняется опрос присутствия пользователей, указанных в полях &quot;Кому&quot; и &quot;Копия&quot;. Оценивается, что просматривается по пять электронных писем в час, и в каждом письме указывается по пять пользователей.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Подписки на сведения о присутствии</p></td>
<td><p>Когда пользователь добавляет другого пользователя в качестве контакта, он <em>подписывается</em> на пять категорий сведений об этом пользователе. Обновления этих категорий сведений автоматически отправляются первому пользователю.</p>
<p>Для каждого клиента отправляется один пакетный запрос подписки, чтобы получить сведения о присутствии в среднем 40 контактов, с дополнительными 40 диалогами, чтобы получить сведения о присутствии для федеративных контактов.</p>
<p>Сведения о присутствии для членов расширенной группы рассылки извлекаются с помощью постоянных подписок на сведения о присутствии, а не опросов, и моделируются как 1 расширение на пользователя каждые 2 часа.</p>
<p><em>Краткие подписки</em> происходят, когда пользователь входит, выполняется пакетная подписка для всех контактов этого пользователя, и вскоре он выходит. Мы предполагаем 6 кратких подписок на пользователя в час, при этом каждая подписка продолжается 10 минут.</p></td>
</tr>
<tr class="even">
<td><p>Публикация сведений о присутствии</p></td>
<td><p>Состояние присутствия публикуется в среднем 4 раза на пользователя в час, максимально 6 раз на пользователя в час.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Размер документа сведений о присутствии</p></td>
<td><p>Средний размер полного документа сведений о присутствии оценивается в 4 КБ, максимальный размер – 25 КБ.</p></td>
</tr>
</tbody>
</table>


В следующей таблице описывается пользовательская модель для использования адресной книги.

### Пользовательская модель использования адресной книги

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Режим поиска в адресной книге</th>
<th>Использование</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Только веб-запрос к адресной книге (все запросы выполняются службой веб-запросов к адресной книге)</p></td>
<td><p>Четыре запроса префикса на пользователя в день.</p>
<p>60 запросов точного поиска на пользователя в день. 40% этих запросов являются пакетными, имеющими в среднем по 20 контактов на запрос. Остальные 60% запросов имеют по одному контакту.</p>
<p>25 запросов фотографий на пользователя в день. 24 являются запросами одной фотографии, один является пакетным запросом, в среднем имеющим 20 контактов.</p>
<p>Один запрос поиска по всей организации на пользователя в день.</p></td>
</tr>
<tr class="even">
<td><p>Смешанный режим, в котором используются как файл адресной книги, так и веб-запросы. Это режим по умолчанию.</p></td>
<td><p>В сеть приходят только два типа запросов: запрос фотографий и запрос поиска по всей организации.</p>
<p>25 запросов фотографий на пользователя в день. 24 являются запросами одной фотографии, один является пакетным запросом, в среднем имеющим 20 контактов.</p>
<p>Один запрос поиска по всей организации на пользователя в день.</p></td>
</tr>
</tbody>
</table>


В следующей таблице описывается модель конференций.

### Модель конференций

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Запланированные собрания и собрания в режиме &quot;Провести собрание&quot;</p></td>
<td><p>60% запланированных, 40% незапланированных.</p>
<p>Мы предполагаем, что среди запланированных собраний 80% составляют назначенные конференции, которые являются случаями повторяющихся конференций; 10% составляют однократные открытые собрания, 8% составляют однократные анонимные собрания и 2% составляют однократные закрытые собрания.</p></td>
</tr>
<tr class="even">
<td><p>Распределение клиентов конференций</p></td>
<td><p>Для запланированных собраний:</p>
<ul>
<li><p>65% пользователей конференций используют Lync 2013;</p></li>
<li><p>5% пользователей конференций используют Microsoft Lync Web App.</p></li>
<li><p>30% пользователей конференций используют клиенты предыдущих версий, включая Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007 и Microsoft Office Communicator Web Access (выпуск 2007).</p></li>
</ul>
<p>Для незапланированных собраний:</p>
<ul>
<li><p>70% пользователей конференций используют Lync 2013;</p></li>
<li><p>30% пользователей конференций используют клиенты предыдущих версий, включая Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007 и Microsoft Office Communicator Web Access (выпуск 2007).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Параллелизм собраний</p></td>
<td><p>5% пользователей будут принимать участие в конференциях в рабочее время. Следовательно, в пуле из 80 000 пользователей в любое время могут принимать участие в конференции 4 000 пользователей одновременно.</p></td>
</tr>
<tr class="even">
<td><p>Распределение собраний по использованию звука</p></td>
<td><p>40% смешанных конференций, использующих звук по протоколу VoIP и по телефонному подключению, с отношением 3:1 пользователей протокола VoIP к пользователям с телефонным подключением.</p>
<p>35% конференций только со звуком по протоколу VoIP.</p>
<p>15% конференций только со звуком по телефонному подключению.</p>
<p>10% конференций без звука (конференции только с обменом мгновенными сообщениями, в среднем по пять отправленных сообщений на пользователя).</p></td>
</tr>
<tr class="odd">
<td><p>Комбинирование средств представления для конференций</p></td>
<td><p>75% конференций являются веб-конференциями, включающими звук и некоторые другие способы совместной работы.</p>
<p>Для таких конференций другие способы совместной работы используются следующим образом.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Эти значения добавляют более 100%, поскольку в одной конференции может использоваться несколько способов совместной работы.</td>
</tr>
</tbody>
</table>

</div>
<ul>
<li><p>50% добавляет общий доступ к приложениям. Мы предполагаем, что один пользователь отправляет данные с максимальной скоростью 1,1 МБ в секунду.</p></li>
<li><p>50% вносит обмен мгновенными сообщениями (в среднем по 2 сообщения на пользователя).</p></li>
<li><p>20% добавляет совместная работа с данными, включая использование PowerPoint или доски. Мы предполагаем, что в каждой конференции представляется 2 файла PowerPoint со средним размером в 10 МБ (без внедренного видео) или 30 МБ (с внедренным видео). В среднем используется 20 заметок на доску.</p></li>
<li><p>20% добавляет видео. Для 70% из этих пользователей включена поддержка видео MultiView, и каждый пользователь получает 2-3 видеопотока.</p></li>
<li><p>15% добавляют общие заметки.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Распределение участников собраний</p></td>
<td><p>50% внутренних, прошедших проверку пользователей.</p>
<p>25% удаленных, прошедших проверку пользователей.</p>
<p>15% анонимных пользователей.</p>
<p>10% федеративных пользователей.</p></td>
</tr>
<tr class="odd">
<td><p>Распределение присоединений к собраниям</p></td>
<td><p>Моделируется присоединение пользователей к собраниям в течение первых 5 минут.</p></td>
</tr>
</tbody>
</table>


В обычных интерфейсных пулах Lync Server 2013 поддерживает максимальный размер собрания в 250 пользователей. В каждом пуле в каждый момент времени может быть размещено одно собрание в 250 пользователей. Во время проведения такого большого собрания в пуле также могут размещаться другие небольшие конференции. Кроме того, можно поддерживать собрания до 1000 пользователей, настраивая выделенный пул для размещения таких собраний. Дополнительные сведения см. в статье [Поддержка больших собраний в Lync Server 2013](lync-server-2013-support-for-large-meetings.md).

Конференции моделировались следующим образом:

  - 85% конференций имели четырех участников;

  - 10% конференций имели шесть участников;

  - 5% конференций имели одиннадцать участников;

  - одна большая конференция с 250 участниками.

В следующей таблице приводятся подробные сведения о пользовательской модели конференций, в которых участвовали пользователи с телефонным подключением.

### Пользовательская модель конференции с телефонным подключением

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Прошедшие проверку и анонимные участники</p></td>
<td><p>70% участников присоединяются как анонимные, и им предлагается указать записанное имя. 30% присоединяются как прошедшие проверку пользователи.</p></td>
</tr>
<tr class="even">
<td><p>Продолжительность вызова и музыка при удержании</p></td>
<td><p>Средняя продолжительность вызова без воспроизведения музыки при удержании: 50 секунд.</p>
<p>50% звонящих пользователей прослушивают музыку при удержании в среднем 5 минут.</p></td>
</tr>
<tr class="odd">
<td><p>Двухтональный многочастотный набор (DTMF)</p></td>
<td><p>15% конференций с подключением по телефону имеют ведущих по телефону. 10% смешанных конференций, включающих пользователей с телефонным подключением, также имеют ведущих по телефону.</p>
<p>20% ведущих по телефону используют по 2 команды DTMF на конференцию.</p></td>
</tr>
<tr class="even">
<td><p>Языки оповещений</p></td>
<td><p>При моделировании в качестве языка оповещений использовался английский.</p></td>
</tr>
</tbody>
</table>


В следующей таблице предоставляются сведения по пользовательской модели "залов ожидания" конференций.

### Пользовательская модель "залов ожидания" конференций

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Количество пользователей в &quot;зале ожидания&quot;</p></td>
<td><p>5% пользователей с телефонным подключением и 25% других пользователей проходят через &quot;зал ожидания&quot;</p></td>
</tr>
<tr class="even">
<td><p>Приглашение из &quot;зала ожидания&quot;</p></td>
<td><p>При моделировании все пользователи приглашались выступающим до истечения времени ожидания клиента.</p></td>
</tr>
</tbody>
</table>


В следующей таблице описывается пользовательская модель для прочих одноранговых сеансов.

### Пользовательская модель одноранговых сеансов

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Общий доступ к приложениям</p></td>
<td><p>Каждый пользователь участвует в 5 одноранговых сеансах общего доступа к приложениям в месяц, в среднем по 0,25 сеанса в день.</p></td>
</tr>
<tr class="even">
<td><p>Передача файлов</p></td>
<td><p>Каждый пользователь участвует в 1 одноранговом сеансе передачи файлов в месяц (в качестве части сеанса обмена мгновенными сообщениями), в среднем по 0.05 сеанса в день. Средний размер передаваемого файла в сеансе составляет 1 МБ.</p></td>
</tr>
</tbody>
</table>


В следующей таблице описывается пользовательская модель для политик.

### Пользовательская модель политик

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Категория</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Политики конференц-связи, присутствия и архивации</p></td>
<td><p>Мы предполагаем, что существует одна глобальная политика, 10 помеченных политик конференц-связи, 4 политики архивации и 10 помеченных политик присутствия.</p></td>
</tr>
<tr class="even">
<td><p>Политика голосовой связи</p></td>
<td><p>Мы предполагаем, что существует одна глобальная политика и по 2 помеченные политики на сайт. 100% сайтов имеют политику сайта, и 30% пользователей имеют назначенную политику на уровне пользователя. Мы предполагаем также по одной абонентской группе и по два маршрута на сайт.</p></td>
</tr>
</tbody>
</table>


## Период максимальной нагрузки

Для одноранговых сеансов пиковая нагрузка вычисляется с помощью попыток вызовов в час наибольшей нагрузки (BHCA). Этот термин из сферы голосовой связи предполагает, что 50% всех вызовов в день будут выполняться в 20% времени. Это значение вычисляется по следующей формуле:

`BHCA=(total calls * 0.5) / 1.6`

При тестировании производительности период максимальной нагрузки моделируется путем запуска сеансов VoIP и других одноранговых сеансов с уровнем максимальной нагрузки по крайней мере 1,6 часов в день.

Пиковая нагрузка конференц-связи предполагает, что 75% всех конференций для восьмичасового дня происходит в 4 часа максимальной нагрузки. В эти часы нагрузка в полтора раза выше средней нагрузки конференц-связи.

## Вызовы из системы корпоративной голосовой связи в ТСОП

Следующие предположения относятся к вызовам корпоративной голосовой связи.

  - Для 50% пользователей включена поддержка корпоративной голосовой связи, и 60% этих пользователей разрешены звонки в ТСОП.

  - Каждый из пользователей, которым разрешены звонки в ТСОП, выполняет 4 звонка в ТСОП в течение часов максимальной нагрузки. Каждый звонок длится 3 минуты.

  - В 65% этих голосовых звонков в ТСОП используется обход сервера-посредника.

## Мобильность

Предполагается. что для 40% зарегистрированных пользователей включена поддержка мобильности. Для каждого из пользователей с поддержкой мобильности предполагается, что использование мобильного клиента является дополнительным к использованию других экземпляров MPOP для этого пользователя, за исключением взаимодействий в конференциях, в которых мобильный клиент является просто еще одним типом клиента, используемым для участия в конференциях.

## сохраняемый сеанс беседы

Мы предполагаем, что 25% зарегистрированных пользователей будут принимать участие в сеансах сохраняемого чата со следующими характеристиками:

  - в среднем по 1,5 комнат чата на пользователя;

  - каждая комната чата приводит к выполнению 12 запросов опроса в час, и каждый из опросов в среднем выполняется для 10 пользователей.

## Группа ответа и парковка вызовов

Мы предполагаем, что 0,15% зарегистрированных пользователей входят в группы ответа. Мы также предполагаем, что в каждый момент времени 0,02% зарегистрированных пользователей имеют запаркованные вызовы.
