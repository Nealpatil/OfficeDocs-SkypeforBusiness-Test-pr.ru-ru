﻿---
title: 'Lync Server 2013: изменение параметров ПИН-кодов по умолчанию для конференц-связи с телефонным подключением'
TOCTitle: Изменение параметров ПИН-кодов по умолчанию для конференц-связи с телефонным подключением
ms:assetid: 2d110e94-ad29-4755-b17f-d8c2da9b78a4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425780(v=OCS.15)
ms:contentKeyID: 49309304
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Изменение параметров ПИН-кодов по умолчанию для конференц-связи с телефонным подключением в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-18_

Глобальная политика ПИН-кодов определяет правила для ПИН-кодов конференц-связи с телефонным подключением на уровне лесов. Выполните приведенные действия, чтобы изменить политику ПИН-кодов для конференц-связи с телефонным подключением. Дополнительные сведения о создании или изменении политики ПИН-кодов для конференц-связи с телефонным подключением на уровне сайтов или пользователей см. в разделе [оздание или изменение параметров ПИН-кода для конференц-связи с телефонным подключением в Lync Server 2013 для сайта или группы пользователей](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md).

## Изменение глобальной политики ПИН-кодов

1.  Войдите на любой компьютер, подключенный к сети, где развернут Lync Server 2013, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsServerAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Conferencing** (Конференц-связь), а затем щелкните элемент **PIN Policy** (Политика ПИН-кодов).

4.  На странице **PIN Policy** (Политика ПИН-кодов) щелкните политику **Global** (Глобальная), нажмите кнопку **Edit** (Изменить) и затем щелкните **Show details** (Показать сведения).

5.  В окне **Изменение политики ПИН-кода** введите или выберите в поле **Минимальная длина ПИН-кода** минимальную длину ПИН-кода. Минимальная длина по умолчанию составляет пять цифр.

6.  Чтобы иметь возможность задать максимальное число попыток входа перед блокированием пользователя, установите флажок **Задать максимальное число попыток входа** . Если этот параметр не выбран, максимальное число разрешенных попыток входа автоматически определяется в зависимости от длины ПИН-кода. По умолчанию максимальное число попыток определяется автоматически.

7.  Если установлен флажок **Задать максимальное число попыток входа** , в поле **Максимальное число попыток входа** введите или выберите максимальное число попыток входа, которое требуется разрешить.

8.  Чтобы ПИН-коды имели конечный срок действия, установите флажок **Включить конечный срок действия ПИН-кодов** . Если этот параметр не выбран, ПИН-коды не будут иметь ограничений по сроку действия. По умолчанию ПИН-коды не имеют ограничений по сроку действия.

9.  Если флажок **Включить конечный срок действия ПИН-кодов** установлен, то в поле **Срок действия ПИН-кода (дней)** введите или выберите максимальное число дней, после которых ПИН-коды становятся недействительными.

10. В поле **Число запомненных ПИН-кодов** введите число ПИН-кодов, которое пользователь должен создать перед тем, как он сможет использовать их повторно. По умолчанию пользователи могут повторно использовать ПИН-коды.

11. Чтобы разрешить распространенные последовательности цифр в ПИН-кодах, такие как последовательные номера и повторяющиеся наборы номеров, установите флажок **Разрешить распространенные последовательности** . Если не выбрать этот параметр, будут разрешены только сложные наборы цифр. По умолчанию разрешены только сложные наборы цифр.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Мы рекомендуем не разрешать использование распространенных последовательностей.</td>
    </tr>
    </tbody>
    </table>


12. Щелкните **Исполнить** .
