﻿---
title: Связанные отчеты по отслеживанию с зеркальной базой данных
TOCTitle: Связанные отчеты по отслеживанию с зеркальной базой данных
ms:assetid: 42b797c6-8db8-4ad7-886e-8ddf8deb06f9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ945624(v=OCS.15)
ms:contentKeyID: 52058204
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Связанные отчеты по отслеживанию с зеркальной базой данных

 

_**Дата изменения раздела:** 2014-02-07_

Если для базы данных мониторинга настроена зеркальная база данных, то в случае отказа зеркальная база данных примет на себя функции основной базы данных. Но если вы используете Отчеты о мониторинге Lync Server и происходит отказ, возможно, что отсутствует связь между вашими Отчетами о мониторинге и зеркальной базой данных. Причиной этого является то, что при установке Отчетов о мониторинге вы указываете только местоположение основной базы данных, но не указываете местоположение зеркальной базы данных.

Для того, чтобы Отчеты о мониторинге автоматически переключались на зеркальную базу данных, необходимо добавить зеркальную базу данных как "партнера по обеспечению отработки отказа" к двум базам данных, используемым в Отчетах о мониторинге (одна база данных – сбор данных и создание отчетов для детализации звонков, другая база - для сбора данных и создания отчетов о качестве взаимодействия (QoE)). (Обратите внимание, что этот шаг должен выполняться только после установки Отчетов о мониторинге.) You can add the failover partner information by manually editing the connection string values used by these two databases. Для этого выполните следующие действия:

1.  В браузере Internet Explorer откройте главную страницу служб **SQL Server Reporting Services**. URL-адрес главной страницы служб Reporting Services состоит из следующих частей:
    
      - Префикс **http:**.
    
      - Полное доменное имя (FQDN) компьютера, на который устанавливаются службы Reporting Services (например,**atl-sql-001.litwareinc.com**).
    
      - Строка символов **/Reports\_**.
    
      - Имя экземпляра базы данных, в которой устанавливаются Отчеты о мониторинге (например,**archinst**).
    
    Например, если служба SQL Server Reporting Services была установлена на компьютере atl-sql-001.litwareinc.com, а в Отчетах о мониторинге используется экземпляр базы данных с именем archinst, то URL-адрес главной страницы будет выглядеть следующим образом:
    
    **http://atl-sql-001.litwareinc.com/Reports\_archinst**

2.  Выполнив переход на главную страницу службы Reporting Services, щелкните ссылку **LyncServerReports**, затем - **Reports\_Content**. Будет выполнен переход на страницу **Reports\_Content** к Отчетам о мониторинге Lync Server.

3.  На странице **Reports\_Content** выберите источник данных **CDRDB**.

4.  На странице **CDRDB**, на вкладке **Свойства**, найдите текстовое окно с именем **Строка подключения**. Текущая строка подключения будет выглядеть следующим образом:
    
    **Data source=(local)\\archinst;initial catalog=LcsCDR**

5.  Добавьте в эту строку подключения имя сервера и экземпляр базы данных для зеркальной базы данных. Например, если имя сервера atl-mirror-001, а зеркальная база данных представлена экземпляром archinst, то для указания зеркальной базы данных применяется следующий синтаксис:
    
    **Партнер по обеспечению отработки отказа=atl-mirror-001\\archinst**
    
    Отредактированная строка подключения будет выглядеть следующим образом:
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=LcsCDR**

6.  После внесения изменений в строку подключения нажмите кнопку **Применить**.

7.  На странице **CDRDB** щелкните ссылку **Reports\_Content**. Выберите источник данных **QMSDB**, затем отредактируйте строку подключения для базы данных о качестве взаимодействия (QoE). Например:
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=QoEMetrics**

8.  Нажмите кнопку **Применить**.

## См. также

#### Концепции

[Установка отчетов мониторинга Lync Server 2013](lync-server-2013-installing-lync-server-2013-monitoring-reports.md)  
[Использование отчетов мониторинга в Lync Server 2013](lync-server-2013-using-monitoring-reports.md)
