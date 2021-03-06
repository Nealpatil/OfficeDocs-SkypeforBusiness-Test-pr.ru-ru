﻿---
title: 'Lync Server 2013: обход сервера-посредника и контроль допуска звонков'
TOCTitle: Обход сервера-посредника и контроль допуска звонков
ms:assetid: 120b2a2b-5f97-4735-a2ee-0f849feb8c1d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398203(v=OCS.15)
ms:contentKeyID: 49308997
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обход сервера-посредника и контроль допуска звонков в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-05_

Обход сервера-посредника и контроль допуска звонков (CAC) взаимодействуют для управления полосой пропускания для мультимедиа данных звонков. Обход сервера-посредника обеспечивает поток мультимедиа по каналам с хорошей связью; CAC управляет трафиком на каналах с ограниченной пропускной полосой. Так как обход сервера-посредника и CAC являются взаимоисключающими, необходимо быть осторожным при планировании использования этих компонентов. Поддерживаются следующие комбинации.

  - CAC и обход сервера-посредника включены. Для обхода сервера-посредника должно быть задано значение **Использовать сведения об узлах и областях** . Эти сведения совпадают с данными, которые используются для CAC.
    
    Если включить CAC, вы не сможете выбрать параметр **Всегда обходить** , и наоборот, так как эти две конфигурации являются взаимоисключающими. Т. е. только одна из них будет применима к любому звонку через ТСОП. Во-первых, выполняется проверка, чтобы определить, применяется ли обход сервера-посредника к вызову. Если это так, CAC не используется. Это имеет смысл, так как если вызов имеет право на обход, он по определению использует подключение, где CAC не требуется. Если обход не может применяться к вызову (т. е. идентификаторы обхода клиента и шлюза не совпадают), к звонку применяется CAC.

  - CAC не включен и для обхода сервера-посредника задано значение **Всегда обходить** .
    
    В этой конфигурации как к клиентские так и магистральные подсети сопоставляются с одним-единственным идентификатором обхода, который вычисляется системой.

  - CAC не включен и для обхода сервера-посредника задано значение **Использовать сведения об узлах и областях** .
    
    Если указан параметр **Использовать сведения об узлах и областях** , определение необходимости обхода работает, в принципе, так же независимо от того, включен или нет CAC. Т. е. для любого звонка через ТСОП подсети клиента сопоставляются с определенным узлом, при этом извлекается идентификатор обхода для этой подсети. Аналогично подсеть шлюза сопоставляется с определенным узлом, при этом извлекается идентификатор обхода для этой подсети. Только если два идентификатора обхода идентичны, для этого звонка будет применяться обход. Если они не совпадают, обход не будет выполняться.
    
    Даже если CAC отключен глобально, необходимо задать политику полосы пропускания для каждого узла и каждой связи, если вы хотите использовать конфигурацию узла и области для управления применением обхода. Фактическое значение ограничения пропускной полосу или ее модальность не имеет значения. Конечная цель состоит в том, чтобы система автоматически вычисляла разные идентификаторы обхода для связи с различными региональными стандартами с плохой связью. Определение ограничения полосы пропускания по определению означает, что связь не очень хорошая.

  - CAC включен, а обход сервера-посредника не включен. Эта конфигурация применима, только если все шлюзы и IP-УАТС подключены по нестабильным каналам или не соответствуют другим требованиям для обхода сервера-посредника. Дополнительные сведения о требованиях обхода сервера-посредника см. в разделе [Технические требования для сервера-посредника в Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md).

## См. также

#### Концепции

[Обзор обхода сервера-посредника в Lync Server 2013](lync-server-2013-overview-of-media-bypass.md)  
[Режимы обхода сервера-посредника в Lync Server 2013](lync-server-2013-media-bypass-modes.md)  
[Технические требования для сервера-посредника в Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md)

