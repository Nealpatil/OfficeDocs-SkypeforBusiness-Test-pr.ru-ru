﻿---
title: 'Lync Server 2013: включение службы безопасности'
TOCTitle: Включение службы безопасности
ms:assetid: 4b1d9125-7488-419b-85dd-a8dd3ab5add3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398299(v=OCS.15)
ms:contentKeyID: 49309685
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение службы безопасности в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-02_

Вашей компании может потребоваться, чтобы в обработке экстренного звонка принимала участие служба безопасности. Чтобы облегчить принятие решения о способе интеграции службы безопасности с развертыванием E9-1-1, вам следует ответить на следующие вопросы.

  - **Вы хотите оповещать службу безопасности об экстренном звонке?**  
    Вы можете настроить политику определения местоположения, чтобы продукт Lync Server отправлял предупреждения в виде мгновенных сообщений на SIP-адреса Lync одного или нескольких сотрудников службы безопасности. Эти предупреждения содержат имя, номер и расположение сотрудника, выполняющего экстренный звонок, и упрощают своевременное реагирование службы безопасности на экстренную ситуацию.

<!-- end list -->

  - **Вы хотите подключать службу безопасности в каждому экстренному звонку в режиме конференции?**  
    Если это поддерживается поставщиком услуг экстренных служб, вы можете настроить политику определения местоположения, чтобы включить в каждый экстренный звонок номер обратного вызова. Этот номер используется поставщиком, чтобы подключить службу безопасности вашей организации к экстренному вызову в режиме конференции. В политике определения местоположения эту конференцию можно настроить как одностороннюю (только прослушивание) или двухстороннюю (двунаправленная связь).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При необходимости вы можете настроить различных сотрудников экстренной службы для каждой политики определения местоположения. Это позволяет настроить ответ для разных областей вашей компании или создать отличную процедуру обработки экстренных звонков, поступающих не извне, изнутри сети. Можно использовать группы распределения для указания сотрудников, которых следует уведомлять.</td>
</tr>
</tbody>
</table>
