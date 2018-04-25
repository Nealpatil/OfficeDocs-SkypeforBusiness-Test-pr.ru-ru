﻿---
title: 'Lync Server 2013: сводка по DNS — масштабируемая консолидированная пограничная топология с аппаратными балансировщиками нагрузки'
TOCTitle: Сводка по DNS — масштабируемая консолидированная пограничная топология с аппаратными балансировщиками нагрузки
ms:assetid: 8453297c-da1d-4b9e-a37e-6721458c6feb
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398670(v=OCS.15)
ms:contentKeyID: 49310395
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по DNS — масштабируемая консолидированная пограничная топология с аппаратными балансировщиками нагрузки в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Требования к записям DNS для удаленного доступа к Lync Server 2013 довольно просты, по сравнению с требованиями для сертификатов и портов. Кроме того, многие записи являются необязательными и зависят от настройки клиентов, на которых выполняется Lync 2013 и того, включена ли федерация.

Дополнительные сведения о требованиях Lync 2013 к DNS см. в статье [Определение требований DNS для Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Дополнительные сведения о параметрах автоматической настройки клиентов Lync 2013, если не настроена DNS с двумя ведущими элементами, см. в разделе "Автоматическая настройка без DNS с двумя ведущими элементами" статьи [Определение требований DNS для Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Следующая таблица содержит сводку записей DNS, необходимых для поддержки топологии масштабированной и консолидированной среды пограничных серверов (с аппаратной балансировкой нагрузки). Обратите внимание, что некоторые записи DNS требуются только для автоматической настройки клиентов Lync. Если для настройки клиентов Lync вы планируете использовать объекты групповой политики, эти записи не требуются.

## Важно. Требования сервер к сетевым адаптерам

Чтобы избежать проблем с маршрутизацией, убедитесь, что серверы сервер оборудованы по крайней мере двумя сетевыми адаптерами и что шлюз по умолчанию задан только на сетевом адаптере, связанном с внешним интерфейсом. Например, как показано на рис. «Сценарий масштабируемого консолидированного пограничного сервера» в статье [Масштабируемая консолидированная пограничная топология с аппаратными балансировщиками нагрузки в Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md), шлюз по умолчанию указывает на внешний брандмауэр.

Можно настроить два сетевых адаптера для каждого сервера сервер следующим образом.

  - **Сетевой адаптер 1 (внутренний интерфейс)**
    
    Внутренний интерфейс с назначенным адресом 172.25.33.10.
    
    Шлюз по умолчанию не определен.
    
    Убедитесь в наличии маршрута между сетью, содержащей внутренний интерфейс сервера сервер, и любыми сетями, содержащими клиенты Lync Server или серверы Lync Server (например, от 172.25.33.0 до 192.168.10.0).

  - **Сетевой адаптер 2 (внешний интерфейс)**
    
    Данному сетевому адаптеру назначаются три общедоступных IP-адреса, например 131.107.155.10 для доступа, 131.107.155.20 для веб-конференций и 131.107.155.30 для аудио- и видеоконференций.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>IP-адреса, назначаемые фактическим внешним сетевым интерфейсам пограничного сервера, могут зависеть от выбранного устройства балансировки нагрузки. Обратитесь к документации по своему устройству балансировки нагрузки, чтобы понять фактически требования к IP-адресам.<br />
    Возможно, но не рекомендуется использовать единый IP-адрес для всех трех интерфейсов пограничных служб. Хотя происходит сохранение IP-адресов, для каждой службы требуются разные номера портов. Номер порта по умолчанию – 443/TCP, это гарантирует, что большинство удаленных брандмауэров сможет пропускать трафик. Изменение значение портов (например) на 5061/TCP для доступа, на 444/TCP для веб-конференций и на 443/TCP для аудио- и видеоконференций может вызвать проблемы у удаленных пользователей, если брандмауэр, который они используют не разрешает прохождение трафика через порты 5061/TCP и 444/TCP. Кроме того, использование трех определенных IP-адресов упрощает устранение неполадок, благодаря возможности фильтрации на IP-адресе.</td>
    </tr>
    </tbody>
    </table>
    
    IP-адрес доступа доступа является основным адресом, для которого в качестве шлюза по умолчанию задан маршрутизатор с выходом в Интернет (131.107.155.1).
    
    IP-адреса веб-конференций и аудио- и видеоконференций являются дополнительными.


> [!TIP]
> Настройка сервер с двумя сетевыми адаптерами – это один из двух возможных вариантов. Другой вариант – использование одного сетевого адаптера для внутренней части и трех сетевых адаптеров – для внешней части сервера сервер. Основное преимущество этого варианта – выделенный сетевой адаптер на службу сервер и сбор потенциально более кратких данных при необходимости поиска и устранения неполадок.



### Записи DNS, необходимые для масштабированной и консолидированной среды пограничных серверов с аппаратной балансировкой нагрузки (пример)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Местоположение/тип/порт</th>
<th>Полное доменное имя/DNS-запись</th>
<th>IP-адрес/полное доменное имя</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>131.107.155.10</p></td>
<td><p>Внешний интерфейс доступа (Contoso). Повторите для всех доменов SIP, в которых имеются пользователи, использующие Lync.</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Внешний интерфейс веб-конференций</p></td>
</tr>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>Внешний интерфейс аудио- и видеоконференций</p></td>
</tr>
<tr class="even">
<td><p>Внешние DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Внешний интерфейс доступа. Требуется для автоматической настройки клиентов Lync 2013 и Lync 2010 для работы во внешней среде. Повторите для всех доменов SIP, в которых имеются пользователи, использующие Lync.</p></td>
</tr>
<tr class="odd">
<td><p>Внешние DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Внешний интерфейс доступа SIP. Требуется для автоматического обнаружения DNS федеративных партнеров, в совокупности называемых &quot;разрешенный домен SIP&quot; (&quot;расширенная федерация&quot; в предыдущих выпусках). Повторите для всех доменов SIP, в которых имеются пользователи, использующие Lync, и клиенты Microsoft Lync Mobile, использующие служба push-уведомлений или Apple Push Notification Service.</p></td>
</tr>
<tr class="even">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Внутренний интерфейс консолидированного пограничного сервера</p></td>
</tr>
</tbody>
</table>
