﻿---
title: Обновление серверов переднего плана в Lync Server 2013
TOCTitle: Обновление серверов переднего плана в Lync Server 2013
ms:assetid: 20fa39ae-ecfb-4c72-9cc4-8e183d3c752f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204736(v=OCS.15)
ms:contentKeyID: 49309167
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обновление серверов переднего плана в Lync Server 2013

 

_**Дата изменения раздела:** 2013-06-28_

Серверы переднего плана в пуле Enterprise Edition объединены в *домены обновления*. Такие домены обновления представляют собой подмножество серверов переднего плана в пуле. Домены обновления создаются топологий автоматически.

При обновлении серверов следует выполнять обновление каждого сервера по отдельности. Необходимо после обновления перезагрузить сервер, перед тем как приступить к обновлению следующего. Обязательно запоминайте, для каких серверов уже выполнялось обновление.

![Обновление блок-схемы серверов](images/JJ204736.42ed59a4-1c26-49f7-ade4-a5a788457ab9(OCS.15).jpg "Обновление блок-схемы серверов")

## Установка обновления на серверы переднего плана в пуле

1.  Выполните следующий командлет на сервере переднего плана в пуле:
    
    **Get-CsPoolUpgradeReadinessState**
    
    Если для параметра *PoolUpgradeState* отображается значение **Занято**, необходимо подождать 10 минут и повторно выполнить командлет **Get-CsPoolUpgradeReadiness**. Если значение **Занято** отобразится три раза подряд после 10-минутного перерыва перед каждой попыткой или отображаются какие-либо результаты выполнения команды **InsufficientActiveFrontEnds** для параметра **PoolUpgradeState,**, это говорит о наличии неполадок в пуле. Если этот пул сопряжен с другим интерфейсным пулом в топологии аварийного восстановления, необходимо аварийно завершить работу пула и перейти в резервный пул, после чего обновить серверы в этом пуле. Дополнительные сведения см. в разделе [Отработка отказа для пула в Lync Server 2013](lync-server-2013-failing-over-a-pool.md).
    
    Когда для параметра *PoolUpgradeState* отобразится значение **Готово**, перейдите к шагу 2.

2.  Командлет **Get-CsPoolUpgradeReadiness** также возвращает данные о каждом домене обновления в пуле и обо всех серверах переднего плана в каждом из доменов обновления. Если параметр **ReadyforUpgrade** содержит значение **True** для домена обновления, где размещены серверы, требующие обновления, значит, можно выполнить их безопасное обновление. Для этого выполните следующие действия:
    
    1.  Остановите все новые подключения к серверам переднего плана с помощью командлета `Stop-CsWindowsService -Graceful -Verbose`.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>При обновлении серверов во время их запланированного простоя можно выполнять этот командлет без параметра ‘-<strong>Graceful</strong>‘: <strong>Stop-CsWindowsService</strong>. После этого службы будут остановлены, не дожидаясь завершения обработки всех существующих запросов.</td>
        </tr>
        </tbody>
        </table>
    
    2.  Обновление серверов, связанных с доменом обновлений.
    
    3.  Перезагрузите серверы и убедитесь в том, что для них разрешены новые подключения.

3.  Повторите действия 1 и 2 для каждого домена обновлений в пуле до полного обновления переднего плана .

