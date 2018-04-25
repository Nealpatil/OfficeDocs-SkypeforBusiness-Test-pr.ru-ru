﻿---
title: 'Lync Server 2013: конфигурация маршрутизации на основе расположения для конференций'
TOCTitle: Конфигурация маршрутизации на основе расположения для конференций
ms:assetid: d8c708cc-a1b1-48b1-808c-a64df15f7701
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn362846(v=OCS.15)
ms:contentKeyID: 56270627
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Конфигурация маршрутизации на основе расположения для конференций в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Приложение для конференций с маршрутизацией на основе расположения использует конфигурацию маршрутизации на основе расположения Lync Server 2013. Основные конфигурации описаны ниже.

  - Местоположение участников, присоединяющихся к собранию, определяется на основе их сетевого сайта. Для включения маршрутизации на основе расположения сетевой сайт и сопоставленные с ним подсети должны быть определены в Lync Server.

  - Для обеспечения маршрутизации на основе расположения для собраний необходимо включить поддержку маршрутизации на основе расположения для участников Lync.

  - Чтобы включить маршрутизацию на основе расположения для конечных точек ТСОП, присоединяющихся к собранию, магистральная сеть SIP, используемая для подключения конечных точек ТСОП, должна быть настроена для маршрутизации на основе расположения.

Дополнительные сведения о развертывании и настройке маршрутизации на основе расположения для Lync Server 2013 см. в статье [Настройка маршрутизации на основе расположения](lync-server-2013-configuring-location-based-routing.md).

## Включение приложения для конференций с маршрутизацией на основе расположения

Приложение для конференций с маршрутизацией на основе расположения по умолчанию отключено. Перед включением приложения необходимо определить и назначить для него правильное значение приоритета. Чтобы определить приоритет, выполните в Командная консоль Lync Server следующий командлет:

Get-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>

Значение \<Pool FQDN\> в этом командлете — это пул, в котором необходимо включить приложение для конференций с маршрутизацией на основе расположения.

Этот командлет вернет список приложений, размещенных в Lync Server, а также значения приоритета для каждого из них. Для приложения для конференций с маршрутизацией на основе расположения необходимо назначить такое значение приоритета, которое будет больше значения приоритета для приложения "UdcAgent", но меньше, чем значение приоритета для приложений "DefaultRouting", "ExumRouting"и "OutboundRouting". Рекомендуется назначать для приложения для конференций с маршрутизацией на основе расположения такое значение приоритета, которое будет на один пункт выше значения приоритета для приложения "UdcAgent".

Например, если приложение "UdcAgent"имеет значение приоритета "2", приложение "DefaultRouting"имеет значение приоритета "8", приложение "ExumRouting"имеет значение приоритета "9", а приложение "OutboundRouting"имеет значение приоритета "10", необходимо назначить для приложения для конференций с маршрутизацией на основе расположения значение приоритета "3". В этом случае приоритет приложений будет выстроен в следующем порядке: другие приложения (приоритеты: от 0 до 1), "UdcAgent"(приоритет: 2), приложение для конференций с маршрутизацией на основе расположения (приоритет: 3), другие приложения (приоритеты: от 4 до 8), "DefaultRouting"(приоритет: 9), "ExumRouting"(приоритет: 10) и "OutboundRouting"(приоритет: 11).

Когда правильное значение приоритета для приложения для конференций с маршрутизацией на основе расположения определено, введите для каждого интерфейсного пула или сервера Standard Edition, на котором размещены пользователи с включенной поддержкой маршрутизации на основе расположения, следующий командлет:

New-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>/LBRouting -Priority \<Application Priority\> -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

Например:

New-CsServerApplication -Identity Service:Registrar:LS2013CU2LBRPool.contoso.com/LBRouting -Priority 3 -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

После выполнения командлета перезапустите все серверы переднего плана в пуле или серверы Standard Edition, для которых было включено приложение для конференций с маршрутизацией на основе расположения.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Включение маршрутизации на основе расположения для конференций или передачи после консультации произойдет только после перезагрузки всех серверов переднего плана в соответствующих пулах и серверов Standard Edition. При указании значения <strong>$true</strong> для <strong>–Critical</strong> в предшествующих командлетах ваши службы Lync будут незамедлительно перезапущены. Если вы не хотите осуществлять перезапуск данных служб, сначала укажите значение <strong>$false</strong> для <strong>–Critical</strong>, а затем воспользуйтесь <strong>Set-CsServerApplication</strong>, чтобы после перезапуска служб снова изменить значение на <strong>$true</strong> для <strong>-Critical</strong>.</td>
</tr>
</tbody>
</table>


После включения приложения для конференций с маршрутизацией на основе расположения и перезапуска всех соответствующих серверов Lync все конференции, организованные в Lync пользователями с поддержкой маршрутизации на основе расположения, будут отслеживаться для предотвращения обхода платных звонков ТСОП.
