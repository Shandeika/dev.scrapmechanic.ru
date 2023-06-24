---
title: GameClass
description: Класс, который определяет режим игры.
published: false
date: 2023-06-24T11:45:45.228Z
tags: class, gameclass, класс
editor: markdown
dateCreated: 2023-06-24T08:14:21.565Z
---

# GameClass
Класс, который определяет режим игры. Создается только один экземпляр этого класса.

Это первый скрипт, который будет запущен.

Игровой скрипт отвечает за создание [миров](TODO:link_to_type) и управление ими.

Может получать события, отправленные с помощью [sm.event.sendToGame](TODO:link_to_func).
## Переменные
|              Тип              |    Имя    |                                                      Описание                                                      |
|-------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------|
| [Storage](TODO:link_to_type)| storage | (Только на стороне сервера.) Объект [хранения](TODO:link_to_type), который может быть использован для хранения данных при следующей загрузке этого объекта после выгрузки.                              |
| [Network](TODO:link_to_type)  |  network  | [Сетевой](TODO:link_to_type) объект, который может использоваться для отправки сообщений между клиентом и сервером.|
|              any              |   data    | Данные о начале игры.                                                                      |
{.dense}
## Переменные
- [defaultInventorySize](#defaultInventorySize)
- [enableAggro](#enableAggro)
- [enableAmmoConsumption](#enableAmmoConsumption)
- [enableFuelConsumption](#enableFuelConsumption)
- [enableLimitedInventory](#enableLimitedInventory)
- [enableRestrictions](#enableRestrictions)
- [enableUpgrade](#enableUpgrade)
## Общие события
- [server_onCreate](#server_onCreate)
- [client_onCreate](#client_onCreate)
- [server_onDestroy](#server_onDestroy)
- [client_onDestroy](#client_onDestroy)
- [server_onRefresh](#server_onRefresh)
- [client_onRefresh](#client_onRefresh)
- [server_onFixedUpdate](#server_onFixedUpdate)
- [client_onFixedUpdate](#client_onFixedUpdate)
- [client_onUpdate](#client_onUpdate)
- [client_onClientDataUpdate](#client_onClientDataUpdate)
## События класса
- [server_onPlayerJoined](#server_onPlayerJoined)
- [server_onPlayerLeft](#server_onPlayerLeft)
- [server_onReset](#server_onReset)
- [server_onRestart](#server_onRestart)
- [server_onSaveLevel](#server_onSaveLevel)
- [server_onTestLevel](#server_onTestLevel)
- [server_onStopTest](#server_onStopTest)
- [client_onLoadingScreenLifted](#client_onLoadingScreenLifted)
- [client_onLanguageChange](#client_onLanguageChange)
## События
<h3 id="server_onCreate">server_onCreate(self) <i>serverEventCallback</i></h3>

Вызывается при создании скриптового объекта. Это происходит, когда ставится или загружается из файла сохранения новая деталь.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onCreate">client_onCreate(self) <i>clientEventCallback</i></h3>

Вызывается при создании скриптового объекта. Это происходит, когда ставится или загружается из файла сохранения новая деталь.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onDestroy">server_onDestroy(self) <i>serverEventCallback</i></h3>

Вызывается, когда интерактивная деталь уничтожается.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onDestroy">client_onDestroy(self) <i>clientEventCallback</i></h3>

Вызывается, когда интерактивная деталь уничтожается.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onRefresh">server_onRefresh(self) <i>serverEventCallback</i></h3>

Вызывается, если Lua-скрипт, прикрепленный к интерактивной детали, изменяется во время работы игры.

> Для этого события требуется, чтобы Scrap Mechanic был запущен с флагом '-dev'. Это позволит скриптам автоматически обновляться при внесении изменений.
{.is-info}

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onRefresh">client_onRefresh(self) <i>clientEventCallback</i></h3>

Вызывается, если Lua-скрипт, прикрепленный к интерактивной детали, изменяется во время работы игры.

> Для этого события требуется, чтобы Scrap Mechanic был запущен с флагом '-dev'. Это позволит скриптам автоматически обновляться при внесении изменений.
{.is-info}

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onFixedUpdate">server_onFixedUpdate(self, timeStep) <i>serverEventCallback</i></h3>

Вызывается каждый игровой тик – в одной секунде 40 тиков. Если частота кадров ниже 40 кадров в секунду, это событие может быть вызвано дважды.

Во время фиксированного обновления, обновляются физика и логика взаимодействия между интерактивными объектами.

Аргументы:
| Тип  |   Имя  |                            Описание                             |
|------|--------|-----------------------------------------------------------------|
|table |  self  |Экземпляр класса.                                                |
|number|timeStep|Период времени в тике. (Всегда равно 0.025, или же 1/40 секунды.)|
{.dense}
<h3 id="client_onFixedUpdate">client_onFixedUpdate(self, timeStep) <i>clientEventCallback</i></h3>

Вызывается каждый игровой тик – в одной секунде 40 тиков. Если частота кадров ниже 40 кадров в секунду, это событие может быть вызвано дважды.

Во время фиксированного обновления, обновляются физика и логика взаимодействия между интерактивными объектами.

Аргументы:
| Тип  |   Имя  |                            Описание                             |
|------|--------|-----------------------------------------------------------------|
|table |  self  |Экземпляр класса.                                                |
|number|timeStep|Период времени в тике. (Всегда равно 0.025, или же 1/40 секунды.)|
{.dense}
<h3 id="client_onUpdate">client_onUpdate(self, deltaTime) <i>clientEventCallback</i></h3>

Вызывается каждый кадр.
Во время обновления кадра обновляются графика, анимация и эффекты.

> Из-за того, как часто вызывается это событие, количество выполняемого здесь кода сильно влияет на частоту кадров игры.
Для любого кода, не связанного с графикой, рассмотрите возможность использования [client_onFixedUpdate](#client_onfixedupdateself-timestep-clienteventcallback) вместо этого.
Если событие не используется, рассмотрите возможность удаления его из сценария. (Обратные вызовы событий, которые не реализованы, вызываться не будут.)
{.is-warning}

Аргументы:
|  Тип |   Имя   |                    Описание                   |
|------|---------|-----------------------------------------------|
|table |   self  |Экземпляр класса.                              |
|number|deltaTime|Разность во времени с момента последнего кадра.|
<h3 id="client_onClientDataUpdate">client_onClientDataUpdate(self, data, channel) <i>clientEventCallback</i></h3>

Вызывается, когда клиент получает новые обновления клиентских данных с сервера, установленных с помощью [Network.setClientData](TODO:link_to_func).

Данные, установленные таким образом, являются постоянными, и последние данные будут автоматически отправляться новым клиентам.

Данные поступят после client_onCreate в течение того же тика.

Канал 1 будет получен раньше канала 2, если оба будут обновлены.

Аргументы:
|  Тип  |  Имя  |                                      Описание                                     |
|-------|-------|-----------------------------------------------------------------------------------|
| table |  self |Экземпляр класса.                                                                  |
|  any  |  data |Любой объект Lua, отправленный с помощью [Network.setClientData](TODO:link_to_func)|
|integer|channel|Клиентский канал передачи данных, 1 или 2. (по умолчанию: 1)                       |
{.dense}
<h3 id="server_onPlayerJoined">server_onPlayerJoined(self, player, newPlayer) <i>serverEventCallback</i></h3>

Вызывается, когда [игрок](TODO:link_to_type) присоединяется к игре.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Player](TODO:link_to_type)|player|Присоединившийся игрок|
|boolean|newPlayer|True, если игрок раньше не присоединялся к этой игре.|
{.dense}
<h3 id="server_onPlayerLeft">server_onPlayerLeft(self, player) <i>serverEventCallback</i></h3>

Вызывается, когда [игрок](TODO:link_to_type) отключается от игры.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Player](TODO:link_to_type)|player|Отключившийся игрок|
{.dense}
<h3 id="server_onReset">server_onReset(self) <i>serverEventCallback</i></h3>

> Только для Challenge Mode!
{.is-info}

Вызывается, когда пользователь хочет сбросить уровень.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onRestart">server_onRestart(self) <i>serverEventCallback</i></h3>

> Только для Challenge Mode!
{.is-info}

Вызывается, когда пользователь хочет перезапустить уровень.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onSaveLevel">server_onSaveLevel(self) <i>serverEventCallback</i></h3>

> Только для редактора Challenge Mode!
{.is-info}

Вызывается, когда пользователь хочет сохранить испытание.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onTestLevel">server_onTestLevel(self) <i>serverEventCallback</i></h3>

> Только для редактора Challenge Mode!
{.is-info}

Вызывается, когда пользователь хочет сохранить и протестировать испытание.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onStopTest">server_onStopTest(self) <i>serverEventCallback</i></h3>

> Только для редактора Challenge Mode!
{.is-info}

Вызывается, когда пользователь хочет прекратить тестирование испытания.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onLoadingScreenLifted">client_onLoadingScreenLifted(self) <i>clientEventCallback</i></h3>

Вызывается, когда показывается экран загрузки при входе в игру.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onLanguageChange">client_onLanguageChange(self, language) <i>clientEventCallback</i></h3>

Вызывается, когда игрок меняет язык в игровых настройках.

Возможные языковые значения:
- Russian
- Brazilian
- Chinese
- French
- German
- Italian
- Japanese
- Korean
- Polish
- Spanish
- English

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|string|language|Установленный язык.|
{.dense}