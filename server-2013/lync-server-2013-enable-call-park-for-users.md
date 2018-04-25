﻿---
title: 'Lync Server 2013: включение для пользователей приостановки звонков'
TOCTitle: Включение для пользователей приостановки звонков
ms:assetid: 9430763f-3394-467c-9c6d-426bf761604e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398753(v=OCS.15)
ms:contentKeyID: 49310537
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение для пользователей приостановки звонков в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-11_

Чтобы пользователи могли приостанавливать вызовы и возобновлять их, необходимо включить для них функцию Приостановка вызовов в политике голосовой связи.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>По умолчанию функция Приостановка вызовов отключена для всех пользователей.</td>
</tr>
</tbody>
</table>


Функцию Приостановка вызовов можно включить на глобальном уровне, уровне сайта или уровне пользователя. Уровень пользователя имеет приоритет перед уровнем сайта, а тот в свою очередь – перед глобальным уровнем. Если имеется несколько политик голосовой связи, то для включения Приостановка вызовов нужно настроить их все, а не только глобальную политику.

## Использование панели управления Lync Server для включения Приостановка вызовов для пользователей

1.  Войдите на компьютер в качестве члена группы **RTCUniversalServerAdmins** или роли администратора **CsVoiceAdministrator** , **CsServerAdministrator** или **CsAdministrator** .

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой области навигации щелкните элемент **Voice Routing** (Маршрутизация голосовых вызовов).

4.  Перейдите на вкладку **Политика голосовой связи** .

5.  Дважды щелкните существующую политику голосовой связи, чтобы открыть диалоговое окно **Изменение политики голосовой связи** .

6.  В разделе **Функции звонков** установите флажок **Включить Парковку вызовов** .

7.  Чтобы сохранить политику голосовой связи, нажмите кнопку **ОК** .

## Использование командлетов для включения Приостановка вызовов для пользователей

1.  Войдите на компьютер в качестве члена группы RTCUniversalServerAdmins или роли администратора CsVoiceAdministrator, CsServerAdministrator или CsAdministrator.

2.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

3.  Выполните следующую команду:
    
        Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
    
    Например, чтобы включить Приостановка вызовов для глобальной политики голосовой связи по умолчанию, выполните команду:
    
        Set-CsVoicePolicy -EnableCallPark $true

## См. также

#### Задачи

[Создание голосовой политики и настройка записей использования ТСОП в Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)
