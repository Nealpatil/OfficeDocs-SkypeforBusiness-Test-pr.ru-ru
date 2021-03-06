﻿---
title: 'Lync Server 2013: поддержка IP и сетевого протокола'
TOCTitle: Поддержка IP и сетевого протокола
ms:assetid: b0cffb10-3478-445c-89c7-8cb8b5027424
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412848(v=OCS.15)
ms:contentKeyID: 49310871
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Поддержка IP и сетевого протокола в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Lync Server 2013 поддерживает следующие протоколы IP и сетевые протоколы:

  - **Протоколы IP.**    Lync Server 2013 поддерживает IP версии 4 (IPv4) или IP версии 6 (IPv6) для сети сервера.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Lync Server 2013 может работать в сети с включенным двойным стеком IP.</td>
    </tr>
    </tbody>
    </table>


  - **Транспортные протоколы SIP.**   SIP может использовать как минимум 3 типа транспортных протоколов: UDP, TCP и TLS. В конфигурации SIP по умолчанию TLS запускается поверх TCP. TLS используется в сети Lync Server 2013. На границе сети Lync Server 2013 может работать поверх TCP. Lync Server 2013 не поддерживает UDP для транспорта SIP, поскольку он не соответствует минимальным требованиям безопасности, надежности и масштабируемости для предприятий. Дополнительные сведения см. в записи блога NextHop «UDP или не UDP — вот в чем вопрос» по адресу [http://go.microsoft.com/fwlink/p/?linkId=185369](http://go.microsoft.com/fwlink/p/?linkid=185369).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Содержимое всех блогов и их URL-адреса могут быть изменены без уведомления.</td>
    </tr>
    </tbody>
    </table>

