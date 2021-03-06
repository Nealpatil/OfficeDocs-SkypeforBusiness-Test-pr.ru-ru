﻿---
title: 'Lync Server 2013: корпоративная голосовая связь'
TOCTitle: Корпоративная голосовая связь
ms:assetid: c9da8099-6f4f-4346-ac67-f041bb96072c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg417163(v=OCS.15)
ms:contentKeyID: 49311175
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Корпоративная голосовая связь в Lync Server 2013

 

_**Дата изменения раздела:** 2015-04-08_

Благодаря корпоративной голосовой связи Lync Server обеспечивает отдельное решение VoIP для улучшения или замены традиционных систем УАТС. Пользователи корпоративной голосовой связи могут звонить коллегам в сети VoIP организации или на УАТС, а также они могут звонить на традиционные телефонные номера, находящиеся за пределами организации. Решение корпоративной голосовой связи включает общие функции совершения звонков, такие как ответ, переадресация, переключение, удержание, отклонение, освобождение и приостановка звонков, а также вызовы Enhanced 9-1-1 (E9-1-1). (E9-1-1 – доступна только в США.) Корпоративная голосовая связь также поддерживает широкий диапазон современных и старых IP- и USB-устройств.

## Совершение и прием звонков

С помощью Lync пользователи могут совершать звонки, набирая имя или номер телефона на клавиатуре или используя панель набора номера, отображаемую на экране. Пользователи могут также инициировать звонки напрямую из списка контактов. Администраторы могут развернуть устройства Lync Phone Edition, которые являются отдельными IP-телефонами, поставляемыми партнерами Майкрософт.

Пользователи могут иметь несколько телефонных устройств, зарегистрированных в Lync Server, и могут легко переключаться между ними.

Пользователи предупреждаются о входящих звонках через все свои устройства одновременно. На IP-телефонах при этом используются настраиваемые мелодии и уведомления, как в системе обмена мгновенными сообщениями на ПК.

Пользователи могут настроить единый телефонный номер, который связывает их настольный телефон, ПК и мобильный телефон, чтобы быть доступными вне зависимости от своего местонахождения.

## Базовые функции звонков

Во время звонка пользователь может отвечать на другие входящие звонки или инициировать исходящие звонки, а существующий активный звонок автоматически ставится на удержание. Звонки могут переадресовываться от одного пользователя другому либо напрямую, либо после предварительной частной беседы первого пользователя со вторым. Пользователи могут переключать звонки на другое устройство; например, они могут переключить активный звонок на свой мобильный телефон, если выходят из офиса.

## Дополнительный возможности связи

Разговаривая с другим пользователем с помощью Lync, пользователи могут легко добавлять в звонок текст, видео или общий доступ к рабочему столу. Функция "Не беспокоить" встроена в параметры присутствия в Lync.

При помощи обмена сообщениями Exchange происходит интеграция Lync и Lync Server с Microsoft Exchange Server 2013 и Microsoft Outlook 2013. Пользователи могут видеть, есть ли у них новая голосовая почта, в окне Lync и в программе электронной почты. Находясь в программе электронной почты, они могут нажать кнопку, чтобы воспроизвести звук голосового сообщения в сообщении электронной почты, или просмотреть запись разговора из сообщения голосовой почты.

## Расширенные функции звонков

Корпоративная голосовая связь включает несколько расширенных функций телефонии, таких как делегирование, групповые звонки, групповой ответ на звонки и группы ответа.

Делегирование позволяет пользователям передавать обработку звонков одному или нескольким помощникам. Делегат может выполнять несколько задач по работе со звонками от имени пользователя, включая отбор звонков, совершение звонков и инициирование конференций.

Групповые звонки обеспечивают одновременную подачу звукового сигнала о входящем звонке на телефоны коллег, чтобы любой из них мог ответить на вызов.

Групповой ответ на звонки, новая функция, представленная в накопительном обновлении для Lync Server 2013 (февраль 2013 г.), позволяет пользователям отвечать на входящие звонки, поступающие на телефоны их коллег, используя собственный телефон. Функция группового ответа на звонок отличается от функции группового звонка главным образом тем, что звонок поступает только на телефон получателя, однако любой из пользователей группы может ответить на него, набрав номер группового ответа.

Группы ответа можно настроить для создания очередей и интеллектуальной маршрутизации звонков назначенным агентам. Обычно эта функция применяется в службах IT-поддержки, горячих линиях отделов кадров и других внутренних контактных центрах.

## Администрирование корпоративной голосовой связи

Lync Server использует стандарты и опубликованные интерфейсы для взаимодействия с существующей инфраструктурой. Сервер поддерживает варианты подключения через шлюз и SIP (например, магистраль SIP) для соединения с системами IP-УАТС и сетями ТСОП, поэтому можно постепенно перемещать пользователей в систему корпоративной голосовой связи, минимизируя нарушения в работе. Lync Server поддерживает традиционные кодеки, такие как G.711, G.722 и G.723.1 для взаимодействия с традиционными решениями VoIP.

С помощью функции контроля допуска звонков (CAC) администраторы могут настраивать пределы на объем голосового и видеотрафика Lync Server, передаваемого через ограниченные сетевые подключения, и задавать действие, которое должно выполняться, если новый звонок превышает предел. Действием может быть маршрутизация по альтернативному пути или отклонение звонка.

Lync Server работает со сторонними устройствами для обеспечения связи в филиалах, предоставляющими локальные телефонные службы и подключение к ТСОП в офисах филиалов в случае сбоя глобальной сети в центральном офисе.

