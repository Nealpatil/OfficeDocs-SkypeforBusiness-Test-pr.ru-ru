﻿---
title: 'Lync Server 2013: делегирование административного управления Lync Server'
TOCTitle: Делегирование административного управления Lync Server 2013
ms:assetid: 0f378eff-8ef4-4c60-9fd2-67d7ee259ef8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520951(v=OCS.15)
ms:contentKeyID: 49308952
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Делегирование административного управления Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-22_

В Lync Server 2013 административные задачи делегируются пользователям с помощью нового компонента управления доступом на основе ролей. Когда вы устанавливаете систему Lync Server, создается несколько ролей управления доступом на основе ролей. Они соответствуют универсальным группам безопасности в Доменные службы Active Directory. Например, роль управления доступом CsHelpDesk соответствует группе CsHelpDesk, расположенной в контейнере Users доменных служб Active Directory. Кроме того, каждая роль управления доступом на основе ролей сопоставлена с набором командлетов Lync ServerWindows PowerShell. Эти командлеты представляют собой задачи, которые могут выполнять пользователи с соответствующей ролью управления доступом на основе ролей. Например, роли CsHelpDesk были назначены командлеты Lock-CsClientPin и UnlockCsClientPin; это значит, что пользователи, которым назначена роль CsHelpDesk, могут блокировать и разблокировать ПИН-коды пользователей. Однако роли CsHelpDesk не был назначен командлет New-CsVoicePolicy. Это значит, что пользователи с ролью CsHelpDesk не могут создавать новые политики голосовой связи.

## Просмотр сведений о ролях RBAC

Вы можете получить базовую информацию о ролях управления доступом на основе ролей, выполнив следующую команду из командной консоли Командная консоль Lync Server:

    Get-CsAdminRole

Помните о том, что удостоверение роли управления доступом на основе ролей (например, CsVoiceAdministrator) имеет прямую связь с группой безопасности, расположенной в контейнере Users в Active Directory.

Чтобы просмотреть список командлетов, которые были назначены роли, используйте команду, аналогичную приведенной ниже:

    Get-CsAdminRole -Identity "CsHelpDesk" | Select-Object -ExpandProperty Cmdlets

## Назначение роли RBAC пользователю

Чтобы назначить роль управления доступом на основе ролей пользователю, вам следует добавить этого пользователя в соответствующую группу безопасности Active Directory. Например, чтобы назначить роль CsLocationAdministrator пользователю, его нужно добавить в группу CsLocationAdministrator. Это можно сделать посредством следующей процедуры:

**Назначение пользователя в группу безопасности**

1.  Используя учетную запись с разрешением на изменение членства группы Active Directory, выполните вход на компьютер, где был установлен компонент «Пользователи и компьютеры Active Directory».

2.  Нажмите кнопку **Пуск** , выберите **Все программы** , **Администрирование** и затем **Пользователи и компьютеры Active Directory** .

3.  В окне «Пользователи и компьютеры Active Directory» разверните имя своего домена и щелкните контейнер **Users** .

4.  Щелкните группу безопасности **CsLocationAdministrator** правой кнопкой мыши и выберите **Свойства** .

5.  В диалоговом окне **Свойства** на вкладке **Члены** нажмите кнопку **Добавить** .

6.  В диалоговом окне **Выбор: Пользователи, Компьютеры, Контакты или Группы** введите имя пользователя или отображаемое имя для пользователя, добавляемого в группу, (например, **Ken Myer** ) в поле **Введите имена выбираемых объектов** и нажмите кнопку **ОК** .

7.  В диалоговом окне **Свойства** нажмите кнопку **ОК** .

Чтобы убедиться, что роль управления доступом на основе ролей была назначена, используйте командлет [Get-CsAdminRoleAssignment](get-csadminroleassignment.md), передавая в него SamAccountName (имя для входа Active Directory) пользователя. Например, запустите следующую команду из командной консоли Командная консоль Lync Server:

    Get-CsAdminRoleAssignment  -Identity "kenmyer"
