﻿---
title: Управление конфигурацией компьютера, сайта и глобальной службы централизованного ведения журналов
TOCTitle: Управление конфигурацией компьютера, сайта и глобальной службы централизованного ведения журналов
ms:assetid: 93b9a354-9aea-4b3a-a4fe-68a89f436196
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ688138(v=OCS.15)
ms:contentKeyID: 49888102
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Управление конфигурацией компьютера, сайта и глобальной службы централизованного ведения журналов

 

_**Дата изменения раздела:** 2014-02-04_

Служба централизованная служба ведения журнала может выполняться в области, включающей один компьютер или пул компьютеров, в области сайта (т. е. на определенном сайте, например на сайте Redmond, который содержит набор компьютеров и пулов развертывания) или в глобальной области (т. е. на всех компьютерах и во всех пулах в развертывании).

Для настройки области централизованная служба ведения журнала с помощью Командная консоль Lync Server необходимо быть членом группы безопасности управления доступом на основе ролей CsAdministrator или CsServerAdministrator или участником пользовательской роли RBAC, содержащей одну из этих групп. Чтобы получить список всех ролей RBAC, которым назначен этот командлет (включая пользовательские роли RBAC, созданные самостоятельно), выполните следующую команду из командной строки Командная консоль Lync Server или Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "<Lync Server 2013 cmdlet>"}

Пример:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Windows PowerShell предоставляет дополнительные возможности и параметры конфигурации, недоступные при использовании средства CLSController.exe. CLSController предлагает быстрый способ выполнения команд, однако набор этих команд ограничен. Система Windows PowerShell не ограничена командами, доступными командному процессору CLSController, и предоставляет более широкий набор команд и параметров. Например, средство CLSController.exe предоставляет параметры области для компьютеров (–computers) и пулов (–pools). С помощью Windows PowerShell можно указывать компьютеры или пулы в большинстве команд, а при определении новых сценариев (CLSController имеет ограниченное количество сценариев, которые пользователь не может изменить) можно задать область сайта или глобальную область. Эта полезная возможность Windows PowerShell позволяет определить сценарий для области сайта или глобальной области, но ограничить ведение журнала компьютером или пулом.<br />
Существуют принципиальные различия между командами командной строки, которые можно выполнить в Windows PowerShell, и командами CLSController. Windows PowerShell предоставляет полнофункциональный метод для настройки и определения сценариев, а также для повторного использования этих сценариев и их отладки. Хотя CLSController позволяет быстро и эффективно выполнять команды и получать результаты, набор команд этого средства ограничен командами, доступными из командной строки. В отличие от командлетов Windows PowerShell, CLSController не может определять новые сценарии, управлять областью на уровне сайта и на глобальном уровне, а также имеет другие ограничения конечного набора команд, который не подлежит динамической настройке. Средство CLSController предлагает возможность быстрого выполнения, тогда как система Windows PowerShell позволяет использовать возможности централизованная служба ведения журнала, недоступные при использовании CLSController.</td>
</tr>
</tbody>
</table>


Область одного компьютера можно определить при выполнении команд [Search-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Search-CsClsLogging), [Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging), [Start-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Start-CsClsLogging), [Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging), [Sync-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Sync-CsClsLogging) и [Update-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Update-CsClsLogging) с помощью параметра –Computers. Параметр –Computers принимает разделенный запятой список полных доменных имен для целевого компьютера.


> [!TIP]
> С помощью параметра –Pools можно задать разделенный запятой список пулов, в которых должны выполняться команды ведения журнала.



Область сайта и глобальная область определяются в командлетах **New-**, **Set-** и **Remove-**централизованная служба ведения журнала. В следующих примерах показано, как задать область сайта и глобальную область.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Показанные команды могут содержать параметры и концепции, описанные в других разделах. Команды в примерах предназначены для демонстрации использования параметра <strong>–Identity</strong> для определения области, а другие параметры включены для полноты и для указания области. Дополнительные сведения о командлетах <strong>Set-CsClsConfiguration</strong> см. в описании командлета <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration">Set-CsClsConfiguration</a> в документации по применению.</td>
</tr>
</tbody>
</table>


## Получение текущей конфигурации централизованная служба ведения журнала

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Get-CsClsConfiguration

Используйте командлеты **New-CsClsConfiguration** и **Set-CsClsConfiguration** для создания новой конфигурации или для обновления существующей.

При выполнении командлета **Get-CsClsConfiguration** отображаются сведения, подобные показанным на следующем снимке экрана. В этом примере в развертывании имеется глобальная конфигурация по умолчанию, а конфигурации сайтов не определены:

![Выход выборки из Get-CsClsConfiguration.](images/JJ688138.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Выход выборки из Get-CsClsConfiguration.")

## Получение текущей конфигурации централизованная служба ведения журнала из локального хранилища компьютера

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Get-CsClsConfiguration -LocalStore

При использовании первого примера, в котором для командлета **Get-CsClsConfiguration** не указаны параметры, команда обращается за данными к управления. Если указать параметр –LocalStore, команда обратится к локальному хранилищу компьютера, а не к управления.

## Получение листинга сценариев, определенных в текущий момент

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Get-CsClsConfiguration -Identity <scope and name> | Select-Object -ExpandProperty Scenarios
    
    Например, для получения сценариев, определенных в глобальной области, выполните следующую команду.
    
        Get-CsClsConfiguration -Identity "global" | Select-Object -ExpandProperty Scenarios

Командлет **Get-CsClsConfiguration** всегда отображает сценарии, которые являются частью конфигурации заданной области. В большинстве случаев отображаются не все сценарии, кроме того, отображаемые сценарии сокращаются. Используемая здесь команда отображает список всех сценариев и частичные сведения об используемых поставщиках, настройках и флагах.

## Обновление глобальной области для централизованная служба ведения журнала с помощью Windows PowerShell

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Set-CsClsConfiguration -Identity <scope> -EtlFileRolloverSizeMB <size for logging file in megabytes>
    
    Пример:
    
        Set-CsClsConfiguration -Identity "global" -EtlFileRolloverSizeMB 40

При выполнении этой команды CLSAgent на каждом компьютере и в каждом пуле развертывания задает для размера переключения на новый файл трассировки значение 40 МБ. Эта команда влияет на компьютеры и пулы на всех сайтах и задает в качестве размера переключения на новый журнал трассировки значение 40 МБ.

## Обновление области сайта для централизованная служба ведения журнала с помощью Windows PowerShell

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Set-CsClsConfiguration -Identity <scope/site name> -EtlFileRolloverSizeMB <size for logging file in megabytes> -EtlFileFolder <default location %TEMP%\Tracing>
    
    Пример:
    
        Set-CsClsConfiguration -Identity "site/Redmond" -EtlFileRolloverSizeMB 40 -EtlFileFolder "C:\LogFiles\Tracing" 
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Как отмечено в примере, расположением файлов журнала по умолчанию является каталог %TEMP%\Tracing. Однако, так как фактически файл записывает CLSAgent, который выполняется как сетевая служба, переменная %TEMP% расширяется до %WINDIR%\ServiceProfiles\NetworkService\AppData\Local.</td>
    </tr>
    </tbody>
    </table>


При выполнении этой команды CLSAgent на каждом компьютере и в каждом пуле сайта Redmond задает для размера переключения на новый файл трассировки значение 40 МБ. Эта команда не повлияет на компьютеры и пулы на других сайтах, которые продолжат использовать текущее значение размера переключения на новый журнал трассировки, определенное либо по умолчанию (20 МБ), либо во время запуска сеанса ведения журнала.

## Создание новой конфигурации централизованная служба ведения журнала

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        New-CsClsConfiguration -Identity <scope and name> [CsClsConfiguration options for this site]
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Командлет New-CsClsConfiguration предоставляет доступ к большому количеству необязательных параметров конфигурации. Дополнительные сведения о параметрах конфигурации см. в описании командлета <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsConfiguration">Get-CsClsConfiguration</a> и в разделе <a href="lync-server-2013-understanding-centralized-logging-service-configuration-settings.md">Понимание параметров конфигурации службы централизованного ведения журналов</a>.</td>
    </tr>
    </tbody>
    </table>
    
    Например, для создания новой конфигурации, которая определяет сетевую папку для файлов кэша, а также период и размер переключения для файлов журнала, введите следующую команду:
    
        New-CsClsConfiguration -Identity "site:Redmond" -CacheFileNetworkFolder "\\fs01.contoso.net\filestore\logfiles" -EtlFileRolloverMinutes 120 -EtlFileRolloverSizeMB 40

Следует тщательно планировать создание новых конфигураций и определение новых свойств для централизованная служба ведения журнала. Необходимо проявлять осторожность при изменениях и учитывать их влияние на возможность правильного ведения журналов в проблемных сценариях. В конфигурацию следует вносить такие изменения, которые улучшат возможности управления журналами и позволят задать такие значения размера и периода переключения, которые помогут устранить возможные проблемы.

## Удаление существующей конфигурации централизованная служба ведения журнала

1.  Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**.

2.  Введите следующую команду в командной строке:
    
        Remove-CsClsConfiguration -Identity <scope and name>
    
    Например, чтобы удалить конфигурацию централизованная служба ведения журнала, созданную для увеличения времени переключения на новый файл журнала, увеличьте размер переключения на новый файл журнала и задайте в качестве расположения кэша файла журнала сетевую папку, как показано ниже:
    
        Remove-CsClsConfiguration -Identity "site:Redmond"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Это новая конфигурация, которая была создана в процедуре &quot;Создание новой конфигурации централизованная служба ведения журнала&quot;.</td>
    </tr>
    </tbody>
    </table>


Если удалить конфигурацию уровня сайта, сайт будет использовать глобальные параметры.

## См. также

#### Концепции

[Обзор службы централизованного ведения журналов](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### Другие ресурсы

[Управление параметрами конфигурации службы централизованного ведения журналов с помощью PowerShell](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)  
[Set-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration)  
[Get-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsConfiguration)  
[New-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsConfiguration)  
[Remove-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsConfiguration)

