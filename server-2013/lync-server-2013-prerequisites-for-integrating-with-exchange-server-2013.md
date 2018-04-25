﻿---
title: Предварительные условия для интеграции Microsoft Lync Server 2013 и Microsoft Exchange Server 2013
TOCTitle: Предварительные условия для интеграции Microsoft Lync Server 2013 и Microsoft Exchange Server 2013
ms:assetid: ea22beb9-c02e-47cb-836d-97a556969052
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ721919(v=OCS.15)
ms:contentKeyID: 49888242
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Предварительные условия для интеграции Microsoft Lync Server 2013 и Microsoft Exchange Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Для интеграции Microsoft Lync Server 2013 и Microsoft Exchange Server 2013 необходимо выполнить все предварительные действия. Как можно было ожидать, интеграция будет невозможна, пока и Exchange 2013, и Lync Server 2013 не будут полностью установлены и запущены. Дополнительные сведения об установке Exchange см. в документации по планированию и развертыванию Exchange 2013 по адресу [http://go.microsoft.com/fwlink/?linkid=268539\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=268539%26clcid=0x419). Дополнительные сведения об установке Lync Server 2013 см. в документации по планированию и развертыванию по адресу [http://go.microsoft.com/fwlink/?linkid=254806\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=254806%26clcid=0x419).

После настройки и запуска серверов необходимо назначить сертификаты серверной проверки подлинности для Lync Server 2013 и Exchange 2013. Они позволяют Lync Server и Exchange обмениваться информацией и взаимодействовать друг с другом. После установки Exchange 2013 самозаверяющий сертификат с именем Microsoft Exchange Server Auth Certificate создается автоматически. Этот сертификат, который можно найти в хранилище сертификатов локального компьютера, следует использовать для проверки подлинности между серверами в Exchange 2013. Дополнительные сведения о назначении сертификатов в Exchange 2013 см. в статье "Настройка потока почты и клиентского доступа" по адресу [http://go.microsoft.com/fwlink/?linkid=268540\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=268540%26clcid=0x419).

Для Lync Server 2013 существующий сертификат Lync Server можно использовать как сертификат проверки подлинности между серверами. Например, сертификат по умолчанию также можно использовать как сертификат OAuthTokenIssuer. Lync Server 2013 позволяет применять любой сертификат веб-сервера как сертификат проверки подлинности между серверами при выполнении следующих условий:

  - этот сертификат содержит имя домена SIP в поле "Тема";

  - тот же сертификат настроен как сертификат OAuthTokenIssuer на всех интерфейсных серверах;

  - длина сертификата составляет не менее 2048 бит.

Дополнительные сведения о проверке подлинности между серверами для Microsoft Lync Server 2013 см. в разделе [Назначение сертификата проверки подлинности между серверами для Microsoft Lync Server 2013](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md).

После назначения сертификатов необходимо настроить службу автообнаружения в Exchange 2013. В Exchange 2013 служба автообнаружения настраивает профили пользователей и предоставляет доступ к службам Exchange при входе пользователей в систему. Пользователи предоставляют службе автообнаружения свой адрес электронной почты и пароль; в свою очередь службы предоставляют пользователю следующую информацию:

  - сведения о внутреннем и внешнем подключении к Exchange 2013;

  - расположение сервера почтовых ящиков пользователя;

  - URL-адреса для компонентов Outlook, таких как сведения о доступности, единой системе обмена сообщениями, а также автономной адресной книге;

  - параметры сервера мобильного Outlook.

Для интеграции Lync Server 2013Exchange 2013 необходимо настроить службу автообнаружения. Вы можете проверить, настроена ли служба автообнаружения, выполнив следующую команду в консоли управления Exchange и проверив значение свойства AutoDiscoverServiceInternalUri:

    Get-ClientAccessServer | Select-Object Name, AutoDiscoverServiceInternalUri | Format-List

Если это значение пусто, необходимо назначить URI службе автообнаружения. Обычно этот URI выглядит следующим образом:

    https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml

URI автообнаружения можно назначить с помощью следующей команды:

    Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri "https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml"

Дополнительные сведения о службе автообнаружения см. в статье "Основные сведения о службе автообнаружения" по адресу [http://go.microsoft.com/fwlink/?linkid=268542\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=268542%26clcid=0x419).

После настройки службы автообнаружения необходимо изменить параметры конфигурации OAuth Lync Server. Так Lync Server будет знать, где искать службу автообнаружения. Чтобы изменить параметры конфигурации OAuth в Lync Server 2013, выполните следующую команду в Командная консоль Lync Server. При выполнении этой команды укажите URI службы автообнаружения, работающей на сервере Exchange и используйте **autodiscover.svc**, чтобы указать расположение службы, вместо **autodiscover.xml** (который указывает на XML-файл, используемый службой):

    Set-CsOAuthConfiguration -Identity global -ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Параметр Identity в предыдущей команде является необязательным. Это связано с тем, что Lync Server позволяет использовать только одну глобальную коллекцию параметров конфигурации OAuth. Помимо прочего это значит, что вы можете настроить URL-адрес службы автообнаружения с помощью этой более простой команды:<br />
Set-CsOAuthConfiguration–ExchangeAutodiscoverUrl &quot;https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc&quot;<br />
Если вы не знакомы с этой технологией, OAuth — это стандартный протокол авторизации, который применяется на различных крупных веб-сайтах. При использовании OAuth учетные данные и пароли пользователей не переносятся с одного компьютера на другой. Вместо этого проверка подлинности и авторизация основаны на обмене маркерами безопасности, которые предоставляют доступ к определенному набору ресурсов в течение определенного промежутка времени.</td>
</tr>
</tbody>
</table>


Помимо настройки службы автообнаружения вы также должны создать запись DNS, которая указывает на ваш сервер Exchange. Например, если служба автообнаружения расположена по адресу autodiscover.litwareinc.com, вам потребуется создать запись DNS для autodiscover.litwareinc.com, которая разрешается в полное доменное имя вашего сервера Exchange (например, atl-exchange-001.litwareinc.com).
