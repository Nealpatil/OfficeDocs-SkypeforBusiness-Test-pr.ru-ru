﻿---
title: 'Lync Server 2013: отработка отказа для пограничного пула, используемого для федерации Lync Server или федерации XMPP'
TOCTitle: Отработка отказа для пограничного пула, используемого для федерации Lync Server или федерации XMPP
ms:assetid: d40097a1-1bed-44dc-aeb6-0871927ab2b9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ721897(v=OCS.15)
ms:contentKeyID: 49888205
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Отработка отказа для пограничного пула, используемого для федерации Lync Server или федерации XMPP в Lync Server 2013

 

_**Дата изменения раздела:** 2012-11-01_

После возврата пограничного пула, который используется для размещения федерации, в рабочий режим после сбоя используйте следующую процедуру для восстановления маршрутизации федерации сервера Lync Server и/или маршрутизации федерации XMPP, чтобы снова использовать этот восстановленный пограничный пул.

## Восстановление федерации на восстановленном пограничном пуле

1.  Запустите службы пограничного сервера на пограничном пуле, который снова доступен.

2.  Если необходимо восстановить маршрутизацию федерации Lync Server для использования восстановленного пограничного сервера, выполните следующие действия:
    
      - На сервере переднего плана откройте построитель топологий. Разверните **пограничные пулы** , затем щелкните правой кнопкой пограничный сервер или пул пограничного сервера, который в настоящее время настроен для федерации. Выберите **Edit properties** (Изменить свойства).
    
      - В поле **Edit Properties** (Изменить свойства) раздела **General** (Общие) снимите флажок **Enable federation for this Edge pool (Port 5061)** (Разрешить федерацию для этого пограничного пула (порт 506)). Нажмите кнопку **ОК** .
    
      - Разверните **пограничные пулы** , затем щелкните правой кнопкой исходный пограничный сервер или пул пограничного сервера, который необходимо снова использовать для федерации. Выберите **Edit properties** (Изменить свойства).
    
      - В поле **Edit Properties** (Изменить свойства) раздела **General** (Общие) установите флажок **Enable federation for this Edge pool (Port 5061)** (Разрешить федерацию для этого пограничного пула (порт 506)). Нажмите кнопку **ОК** .
    
      - Щелкните **Action** (Действие), выберите **Topology** (Топология), выберите **Publish** (Опубликовать). При появлении запроса на **публикацию топологии** щелкните **Next** (Далее). По завершении публикации щелкните **Finish** (Готово).
    
      - На пограничном сервере откройте мастер развертывания сервера Lync Server. Щелкните **Install or Update Lync Server System** (Установить или обновить систему сервера Lync Server), щелкните **Setup or Remove Lync Server Components** (Установить или удалить компоненты сервера Lync Server). Щелкните **Run Again** (Повторить).
    
      - В разделе установки компонентов Lync Server щелкните **Next** (Далее). На экране сводных данных отображаются действия по мере их выполнения. По завершении развертывания щелкните **View Log** (Просмотреть журнал) для просмотра доступных файлов журнала. Щелкните **Finish** (Готово) для завершения развертывания.

3.  Если необходимо восстановить маршрутизацию федерации XMPP для использования восстановленного пограничного сервера, выполните следующие действия:
    
      - Выполните следующий командлет, чтобы повторно указать маршрут федерации XMPP к пограничному пулу, в котором теперь будет размещаться федерация XMPP (в данном примере – EdgeServer1):
        
            Set-CsSite Site1 -XmppExternalFederationRoute EdgeServer1.contoso.com
        
        В данном примере Site1 – это сайт, содержащий пограничный пул, в котором теперь размещается маршрут федерации XMPP, а EdgeServer1.contoso.com – это полное доменное имя пограничного сервера в этом пуле.
    
      - Если у вас пока нет записи DNS SRV для федерации XMPP, которая разрешается в пограничный пул, где будет размещаться федерация XMPP, вы должны добавить ее, как указано в следующем примере. Для этой записи SRV необходимо указать значение порта 5269.
        
            _xmpp-server._tcp.contoso.com
    
      - На внешнем DNS-сервере измените запись DNS A для федерации XMPP таким образом, чтобы она указывала на EdgeServer2.contoso.com.
    
      - Убедитесь, что порт 5269 пограничного пула, в котором теперь будет размещаться федерация XMPP, открыт на внешнем уровне.

4.  Если пулы переднего плана продолжают функционировать на сайте, содержащем пограничный пул, который был восстановлен после сбоя, следует обновить службу веб-конференций и службу аудио-/видеоконференций на этих пулах переднего плана, чтобы снова использовать пограничные пулы на локальном сайте. Для получения более подробной информации см. [Изменение пограничного пула, связанного с пулом переднего плана в Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md).

5.  Если происходит сбой пула переднего плана на том же сайте, где располагается отказавший пограничный пул, можно использовать Invoke–CsPoolFailback для восстановления пула переднего плана.

## См. также

#### Задачи

[Отработка отказа для пограничного пула, используемого для федерации Lync Server в Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-lync-server-federation.md)  
[Отработка отказа для пограничного пула, используемого для федерации XMPP в Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)  

#### Концепции

[Аварийное восстановление пограничного сервера в Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)
