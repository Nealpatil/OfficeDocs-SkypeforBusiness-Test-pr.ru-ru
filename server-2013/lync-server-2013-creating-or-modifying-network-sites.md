﻿---
title: Создание или изменение сетевых узлов
TOCTitle: Создание или изменение сетевых узлов
ms:assetid: 358aa08a-c5bc-45fc-8017-19e6202f88c5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520975(v=OCS.15)
ms:contentKeyID: 49309410
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание или изменение сетевых узлов

 

_**Дата изменения раздела:** 2012-10-08_

Сетевые узлы — это офисы или места, настроенные в каждой области развертывания контроля допуска звонков (CAC) или Enhanced 9-1-1. Панель управления Microsoft Lync Server 2013 позволяет настроить узлы и связать их с областями. Например, сетевую область для Северной Америки можно связать с такими сетевыми узлами, как Чикаго, Редмонд и Ванкувер. Сетевой узел CAC необходимо создать для каждого узла в организации, даже если у этого узла нет ограничений по пропускной способности. Панель управления Lync Server позволяет создавать, изменять и удалять сетевые узлы. Ниже описаны процедуры для создания или изменения сетевого узла. Подробные сведения об удалении существующего сетевого узла см. в разделе [Удаление существующего сетевого узла](lync-server-2013-deleting-an-existing-network-site.md).

## Создание сетевого узла

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните **Конфигурация сети**, а затем щелкните **Узел**.

4.  На странице **Узел** нажмите кнопку **Создать**.

5.  В диалоговом окне **Создание узла** введите имя узла в поле **Имя**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Имена узлов должны быть уникальными в рамках развертывания Lync Server 2013.</td>
    </tr>
    </tbody>
    </table>


6.  В раскрывающемся списке **Область** выберите сетевую область, которую необходимо сопоставить с этим узлом.

7.  (Необязательно) Если нужно наложить ограничения полосы пропускания на аудио- или видеовызовы с данного узла, выберите профиль политики с соответствующими параметрами в раскрывающемся списке **Политика полосы пропускания**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вы можете просмотреть информацию о доступных профилях политики пропускной полосы или создать новый профиль на странице <strong>Профиль политики</strong> группы <strong>Конфигурация сети</strong>. Дополнительные сведения см. в разделе <a href="lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md">Создание или изменение профилей политик пропускной способности</a>.</td>
    </tr>
    </tbody>
    </table>


8.  (Необязательно) Если требуется предоставить параметры местоположения для данного узла, выберите политику расположения в раскрывающемся списке **Политика расположения**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Политика расположения устанавливает определенные параметры системы Enhanced 9-1-1 (E9-1-1) и клиентского расположения для узла. Вы можете просмотреть сведения о доступных политиках или создать новую на странице <strong>Политика расположения</strong> группы <strong>Конфигурация сети</strong>. Дополнительные сведения см. в разделе <a href="lync-server-2013-viewing-location-policy-information.md">Просмотр сведений о политике расположения</a>.</td>
    </tr>
    </tbody>
    </table>


9.  (Необязательно) Введите значение в поле **Описание**, чтобы предоставить дополнительную информацию об этом узле, которую нельзя выразить в имени.

10. Нажмите кнопку **Сохранить**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Таблица <strong>Связанные подсети</strong> не используется при создании нового сетевого узла. Необходимо связать подсеть с узлом при создании или изменении подсети. Дополнительные сведения см. в разделе <a href="lync-server-2013-create-or-modify-network-subnets.md">Создание или изменение подсетей</a>.</td>
    </tr>
    </tbody>
    </table>


## Изменение сетевого узла

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните **Конфигурация сети**, а затем щелкните **Узел**.

4.  На странице **Узел** щелкните узел, который требуется изменить.

5.  В меню **Правка** выберите команду **Показать подробности**.

6.  На странице **Редактирование узла** вы можете изменить описание, область, профиль политики полосы пропускания и политику расположения, связанную с узлом. Дополнительные сведения см. в разделе "Создание сетевого узла" ранее в этом разделе.

7.  Нажмите кнопку **Сохранить**.

Вы не можете изменить таблицу **Связанные подсети** на этой странице. Список связанных подсетей предоставлен для справки, чтобы вы могли узнать, на что повлияет изменение параметров узла.

## Удаление сетевого узла

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните **Конфигурация сети**, а затем щелкните **Узел**.

4.  На странице **Узел** щелкните узел, который требуется удалить.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вы можете удалить несколько узлов за раз. Для этого нажмите клавишу CTRL и выберите несколько узлов, удерживая клавишу CTRL нажатой. Или, чтобы выбрать все узлы, щелкните <strong>Выбрать все</strong> в меню <strong>Правка</strong>.</td>
    </tr>
    </tbody>
    </table>


5.  В меню **Правка** выберите команду **Удалить**.

6.  Нажмите кнопку **ОК**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вы не можете удалить сетевой узел, если он связан с подсетью. При попытке удаления такого узла отображается сообщение об ошибке. Чтобы увидеть, связал ли узел с какой-либо подсетью, щелкните узел и выберите команду <strong>Показать подробности</strong> в меню <strong>Правка</strong>.</td>
    </tr>
    </tbody>
    </table>


## См. также

#### Задачи

[Удаление существующего сетевого узла](lync-server-2013-deleting-an-existing-network-site.md)  

#### Другие ресурсы

[New-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSite)  
[Set-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSite)  
[Remove-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSite)  
[Get-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSite)

