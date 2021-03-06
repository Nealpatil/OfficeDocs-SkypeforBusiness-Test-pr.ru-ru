﻿---
title: Резервное копирование основных данных и параметров
TOCTitle: Резервное копирование основных данных и параметров
ms:assetid: 278bc95a-7b8d-4e01-a872-a844830459de
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh202170(v=OCS.15)
ms:contentKeyID: 52058197
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Резервное копирование основных данных и параметров

 

_**Дата изменения раздела:** 2014-04-23_

В следующих процедурах командлеты командной консоли Командная консоль Lync Server используются с целью создания файлов резервных копий для параметров и данных основных служб. Дополнительные сведения о тех средствах, которые применяются в данном разделе, и их расположении см. в статье [Требования к резервному копированию и восстановлению: средства и разрешения](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md). Дополнительные сведения о резервном копировании данных архивирования и мониторинга см. в статье [Резервное копирование баз данных архивации и мониторинга](lync-server-2013-backing-up-archiving-and-monitoring-databases.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Описанный в данном разделе этап резервного копирования центрального хранилища управления содержит параметры и конфигурацию для архивирования и мониторинга.</td>
</tr>
</tbody>
</table>


Указанные в этом разделе командлеты можно запускать как локально, так и удаленно.

## Резервное копирование основных данных и параметров

1.  Выполните вход на любой компьютер из внутреннего развертывания с использованием учетной записи пользователя, являющейся членом группы RTCUniversalServerAdmins.

2.  Для хранения создаваемых резервных копий создайте новую общую папку и обновите путь, на который ссылается **$Backup**, на эту новую общую папку.

3.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

4.  Выполните резервное копирование файла конфигурации центрального хранилища управления. В командной строке введите следующее:
    
        Export-CsConfiguration -FileName <path and file name for backup>
    
    Например:
    
        Export-CsConfiguration -FileName "C:\Config.zip"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>В данном шаге выполняется экспорт топологии, политик и параметров конфигурации Lync Server в файл. Иные действия для резервного копирования данных топологии не требуются.</td>
    </tr>
    </tbody>
    </table>


5.  Скопируйте файл резервной копии конфигурации центрального хранилища управления в папку $Backup\\.

6.  Выполните резервное копирование данных службы информирования о местонахождении. В командной строке введите следующее:
    
        Export-CsLisConfiguration -FileName <path and file name for backup>
    
    Например:
    
        Export-CsLisConfiguration -FileName "C:\E911Config.zip"

7.  Скопируйте файл резервной копии конфигурации службы информирования о местонахождении в папку $Backup\\.

8.  Выполните резервное копирование пользовательских данных из каждой серверной базы данных пула переднего плана и каждого сервера Сервер Standard Edition. В командной строке введите следующее:
    
        Export-CsUserData -PoolFQDN <Fqdn> -FileName <String>
    
    Например:
    
        Export-CsUserData -PoolFQDN "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

9.  Скопируйте файл резервной копии пользовательских данных в папку $Backup\\.

10. В каждом пуле, где выполняется приложение "Группа ответа", выполните резервное копирование конфигурации группы ответа. Выполните следующие действия:
    
    1.  Введите в командной строке следующее:
        
            Export-CsRgsConfiguration -Source "service:ApplicationServer:<pool FQDN>" -FileName <path and file name for backup>
        
        Например:
        
            Export-CsRgsConfiguration -Source ApplicationServer:pool01.contoso.com -FileName C:\RgsConfiguration.zip

11. Скопируйте файл резервной копии конфигурации группы ответа в папку $Backup\\.

