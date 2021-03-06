﻿---
title: 'Lync Server 2013: установка пограничных серверов'
TOCTitle: Установка пограничных серверов
ms:assetid: 1655ab69-3899-4ee4-a1cc-8243bc1bfa0f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398230(v=OCS.15)
ms:contentKeyID: 49309053
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Установка пограничных серверов для Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-08_

Lync Server 2013 устанавливается на пограничные серверы с помощью развертывания Lync Server. Запуская мастер развертывания на каждом пограничном сервере, вы можете выполнить большинство задач, необходимых для пограничного сервера. Для развертывания Lync Server 2013 на пограничном сервере необходимо сначала запустить топологий, чтобы определить и опубликовать топологию пограничного сервера, и экспортировать ее на посредник, доступный с пограничного сервера. Дополнительные сведения см. в разделах [Сценарии доступа внешних пользователей в Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) и [Экспорт топологии Lync Server 2013 и ее копирование на внешние носители для установки в пограничной топологии](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md).

После использования мастера развертывания для установки каждого пограничного сервера, установки и назначения необходимых сертификатов и запуска нужных служб вы можете завершить настройку, используя сведения из раздела [Настройка поддержки доступа внешних пользователей в Lync Server 2013](lync-server-2013-configuring-support-for-external-user-access.md), чтобы включить и настроить доступ внешних пользователей, и сведения из раздела [Проверка развертывания пограничного сервера в Lync Server 2013](lync-server-2013-verifying-your-edge-deployment.md), чтобы проверить установку, в том числе возможности подключения серверов и клиентов.

## Установка пограничного сервера

1.  Войдите в систему на компьютере, на котором требуется установить пограничный сервер, в качестве члена группы "Локальные администраторы" или с учетной записью с с эквивалентными правами и разрешениями.

2.  Убедитесь, что файл конфигурации топологии, созданный с помощью топологий и затем экспортированный и скопированный на внешнего посредника, доступен на пограничном сервере (например, откройте USB-диск, на который вы скопировали файл конфигурации топологии или проверьте доступ к общему сетевому ресурсу, в который вы скопировали файл).

3.  Запустите мастер развертывания.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если отображается сообщение о том, что необходимо установить распространяемый компонент Microsoft Visual C + +, нажмите кнопку <strong>Да</strong> . В следующем диалоговом окне можно принять значения по умолчанию для параметра <strong>Папка установки</strong> или нажать кнопку <strong>Обзор</strong> , чтобы выбрать другое расположение. Затем нажмите кнопку <strong>Установить</strong> . В следующем диалоговом окне установите флажок <strong>Я принимаю условия лицензионного соглашения</strong> и нажмите кнопку <strong>ОК</strong> .</td>
    </tr>
    </tbody>
    </table>


4.  В мастере развертывания выберите **Установить или обновить систему Lync Server** .

5.  После того, как мастер определит состояние развертывания (на **Шаге 1. Установка локального хранилища конфигурации** ), нажмите кнопку **Выполнить** и выполните следующие действия:
    
      - В диалоговом окне **Настройка локальной реплики центрального хранилища управления** щелкните **Импортировать из файла (рекомендуется для пограничных серверов)** , перейдите к местоположению экспортированного файла конфигурации топологии, выберите ZIP-файл, нажмите кнопку **Открыть** , а затем нажмите **Далее** .
    
      - Мастер развертывания прочитает сведения о конфигурации из файла конфигурации и запишет XML-файл конфигурации на локальный компьютер.
    
      - После завершения процесса **выполнения команд** нажмите кнопку **Готово** .

6.  В мастере развертывания щелкните **Шаг 2. Установка и удаление компонентов Lync Server** чтобы установить компоненты пограничного сервера Lync Server 2013, указанные в XML-файле конфигурации, который хранится на локальном компьютере.

7.  После завершения установки воспользуйтесь сведениями из раздела [Настройка сертификатов пограничного сервера для Lync Server 2013](lync-server-2013-set-up-edge-certificates.md) для установки и назначения необходимых сертификатов перед запуском служб.

