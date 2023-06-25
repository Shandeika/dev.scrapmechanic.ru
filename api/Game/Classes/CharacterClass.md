---
title: CharacterClass
description: Класс, который создается для каждого персонажа в игре.
published: false
date: 2023-06-25T08:41:58.291Z
tags: character, class, класс, персонаж
editor: markdown
dateCreated: 2023-06-24T05:26:00.455Z
---

# CharacterClass
Класс, который создается для каждого [персонажа](TODO:link_to_type) в игре.
[Персонаж](TODO:link_to_type) - это временный "сосуд", управляемый [игроком](TODO:link_to_type) или [юнитом](TODO:link_to_type) (Unit).

Может получать события, отправленные с помощью [sm.event.sendToCharacter](TODO:link_to_func).

## Переменные
|              Тип              |    Имя    |                                                      Описание                                                      |
|-------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------|
| [Character](TODO:link_to_type)| character | Игровой объект [персонажа](TODO:link_to_type), принадлежащий этому экземпляру класса.                              |
| [Network](TODO:link_to_type)  |  network  | [Сетевой](TODO:link_to_type) объект, который может использоваться для отправки сообщений между клиентом и сервером.|
|              any              |   data    | Информация переданная из таблицы data в json.                                                                      |
{.dense}
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
- [client_onProjectile](#client_onProjectile)
- [client_onMelee](#client_onMelee)
- [client_onCollision](#client_onCollision)
- [client_onGraphicsLoaded](#client_onGraphicsLoaded)
- [client_onGraphicsUnloaded](#client_onGraphicsUnloaded)
- [client_onInteract](#client_canInteract)
- [client_canInteract](#client_canInteract)
- [client_onEvent](#client_onEvent)
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
<h3 id="client_onProjectile">client_onProjectile(self, position, airTime, velocity, projectileName, shooter, damage, customData, normal, uuid) <i>clientEventCallback</i></h3>

Вызывается, когда в [персонажа](TODO:link_to_type) попадает снаряд.

> Если стрелок будет уничтожен до того, как произойдет попадание, значение shooter будет равно nil.
{.is-info}

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которую попал снаряд.|
|number|airTime|Время в секундах, которое снаряд потратил на полет до попадания.|
|[Vec3](TODO:link_to_type)|velocity|Скорость снаряда при ударе.|
|string|projectileName|Название снаряда. (Устарело, вместо него используйте uuid)|
|[Player](TODO:link_to_type)/[Shape](TODO:link_to_type)/[Harvestable](TODO:link_to_type)/nil|shooter|Стрелок может быть игроком, деталью, Harvestable или nil, если неизвестно. Снаряды, выпущенные юнитом, будут равны nil для клиента.|
|number|damage|Количество нанесённого урона от снаряда.|
|any|customData|Объект Lua, который может быть определен во время выстрела с помощью [sm.projectile.customProjectileAttack](TODO:link_to_func) или другой пользовательской версии.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал снаряд.|
|[Uuid](TODO:link_to_type)|uuid|Uuid снаряда.|
{.dense}
<h3 id="client_onMelee">client_onMelee(self, position, attacker, damage, power, direction, normal) <i>clientEventCallback</i></h3>

Вызывается, когда [персонаж](TODO:link_to_type) получает удар в ближнем бою.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которую попал удар.|
|[Player](TODO:link_to_type)/nil|attacker|Нападавший. Может быть [игроком](TODO:link_to_type) или nil, если неизвестно. Атаки, предпринятые юнитом, будут равны nil для клиента.|
|integer|damage|Количество нанесённого урона от удара.|
|number|power|"Сила" удара|
|[Vec3](TODO:link_to_type)|direction|Направление, в которое был нанесён урон.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал удар.|
{.dense}
<h3 id="client_onCollision">client_onCollision(self, other, position, selfPointVelocity, otherPointVelocity, normal) <i>clientEventCallback</i></h3>

Вызывается, когда [персонаж](TODO:link_to_type) сталкивается с другим объектом.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Shape](TODO:link_to_type)/[Character](TODO:link_to_type)/[Harvestable](TODO:link_to_type)/[Lift](TODO:link_to_type)/nil|other|Объект, с которым столкулись. nil, если земля.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которой произошло столкновение.|
|[Vec3](TODO:link_to_type)|selfPointVelocity|Скорость, которую имел [персонаж](TODO:link_to_type) в момент столкновения.|
|[Vec3](TODO:link_to_type)|otherPointVelocity|Скорость, которую имел другой объект в момент столкновения.|
|[Vec3](TODO:link_to_type)|normal|Точка соприкосновения между [персонажем](TODO:link_to_type) и другим объектом.|
{.dense}

<h3 id="client_onGraphicsLoaded">client_onGraphicsLoaded(self) <i>clientEventCallback</i></h3>

Вызывается при загрузке графики для персонажа.

После этого могут быть вызваны функции, связанные с графикой, например анимации.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}

<h3 id="client_onGraphicsUnloaded">client_onGraphicsUnloaded(self) <i>clientEventCallback</i></h3>

Вызывается, когда для персонажа выгружается графика.

После этого функции, связанные с графикой, больше не будут работать или завершатся сбоем.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}

<h3 id="client_onInteract">client_onInteract(self, character, state) <i>clientEventCallback</i></h3>

Вызывается, когда игрок взаимодействует с персонажем, нажимая клавишу "Использовать" (по умолчанию "E").

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|[Character](TODO:link_to_type)|character|[Персонаж](TODO:link_to_type) [игрока](TODO:link_to_type), который взаимодействует с этим [персонажем](TODO:link_to_type).|
|boolean|state|Состояние взаимодействия. Всегда true. Класс [CharacterClass](CharacterClass) получает только событие нажатия клавиши.|
{.dense}

<h3 id="client_canInteract">client_canInteract(self, character) <i>clientEventCallback</i></h3>

Вызывается, чтобы проверить, можно ли взаимодействовать с персонажем в данный момент.

> Это событие также отвечает за обновление текста взаимодействия, отображаемого игроку с помощью [sm.gui.setInteractionText](TODO:link_to_func).
{.is-info}

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|[Character](TODO:link_to_type)|character|[Персонаж](TODO:link_to_type) [игрока](TODO:link_to_type), который смотрит на этого [персонажа](TODO:link_to_type).|
{.dense}

Должно вернуть:
|Тип|Описание|
|---|--------|
|boolean|Логическое значение, указывающее, можно ли взаимодействовать с [персонажем](TODO:link_to_type) или нет. (По умолчанию используется значение true, если реализован [client_onInteract](#client_onInteract), в противном случае значение false)|
{.dense}

<h3 id="client_onEvent">client_onEvent(self, event) <i>clientEventCallback</i></h3>

Вызывается, когда [персонаж](TODO:link_to_type) получает событие от [Player.sendCharacterEvent](TODO:link_to_func) или [Unit.sendCharacterEvent](TODO:link_to_func).

Обычно это делается для запуска анимации персонажа.

Для получения более подробной информации о событиях смотрите [sm.event.sendToCharacter](TODO:link_to_func).

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|string|event|Название события.|