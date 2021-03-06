﻿---
title: 'Lync Server 2013: удаление проверки подлинности Kerberos для сайта'
TOCTitle: Удаление проверки подлинности Kerberos для сайта
ms:assetid: 93171b02-bb36-42dc-943d-86d9dde45b59
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398749(v=OCS.15)
ms:contentKeyID: 49310549
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# В Lync Server 2013 удаление проверки подлинности Kerberos для сайта

 

_**Дата изменения раздела:** 2012-01-16_

Чтобы успешно выполнить данную процедуру, необходимо войти в систему с учетной записью пользователя, являющегося членом группы RTCUniversalServerAdmins.

Если необходимо удалить проверку подлинности Kerberos с узла или прекратить использование узла, необходимо удалить назначение учетной записи проверки подлинности Kerberos с узла с помощью командлета **Remove-CsKerberosAccountAssignment**. Используйте следующую процедуру для удаления назначения учетной записи проверки подлинности Kerberos, что приводит к удалению назначения со всех компьютеров узла.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если необходимо безвозвратно прекратить использование учетной записи с поддержкой Kerberos, следует использовать раздел «Пользователи и компьютеры Active Directory» для удаления из Доменные службы Active Directory после удаления назначения. Если вы планируете использовать данный объект в дальнейшем, возможно, потребуется сохранить объект Active Directory.</td>
</tr>
</tbody>
</table>


## Удаление проверки подлинности Kerberos с узла

1.  Используя учетную запись члена группы RTCUniversalServerAdmins, выполните вход в систему компьютера в домене, в котором выполняется Lync Server 2013, или в систему компьютера, на котором установлены средства администрирования.

2.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

3.  В командной строке выполните следующие две команды:
    
        Remove-CsKerberosAccountAssignment -Identity "site:SiteName"
    
        Enable-CsTopology
    
    Например:
    
        Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
    
        Enable-CsTopology
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>После внесения любых изменений в систему проверку подлинности Kerberos (например, после добавления или удаления учетной записи) необходимо выполнить <strong>Enable-CsTopology</strong> в командной строке Командная консоль Lync Server.</td>
    </tr>
    </tbody>
    </table>

