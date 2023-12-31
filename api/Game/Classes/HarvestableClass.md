---
title: HarvestableClass
description: Класс, который создается для каждого собираемого объекта в игре.
published: false
date: 2023-06-26T04:26:33.075Z
tags: class, harvestable, harvestableclass, класс
editor: markdown
dateCreated: 2023-06-24T12:03:31.102Z
---

# HarvestableClass
Класс, который создается для каждого [Harvestable](TODO:link_to_type) в игре.

Дерево или растение, которое можно собрать, является типичным примером harvestable.

Может получать события, отправленные с помощью [sm.event.sendToHarvestable](TODO:link_to_func).
## Переменные
|Тип|Имя|Описание|
|---|---|--------|
|[Harvestable](TODO:link_to_type)|harvestable|[Harvestable](TODO:link_to_type), принадлежащий этому экземпляру класса.|
|[Network](TODO:link_to_type)|network|[Сетевой](TODO:link_to_type) объект, который может использоваться для отправки сообщений между клиентом и сервером.|
|[Storage](TODO:link_to_type)|storage|(Только на стороне сервера.) Объект [хранения](TODO:link_to_type), который может быть использован для хранения данных при следующей загрузке этого объекта после выгрузки.|
|any|data|Информация переданная из таблицы data в json.|
{.dense}
## Константы
- [poseWeightCount](#poseWeightCount)
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
- [server_onUnload](#server_onUnload)
- [server_onReceiveUpdate](#server_onReceiveUpdate)
- [client_onCollision](#client_onCollision)
- [server_onCollision](#server_onCollision)
- [client_onProjectile](#client_onProjectile)
- [server_onProjectile](#server_onProjectile)
- [server_onExplosion](#server_onExplosion)
- [client_onMelee](#client_onMelee)
- [server_onMelee](#server_onMelee)
- [server_onRemoved](#server_onRemoved)
- [client_canErase](#client_canErase)
- [server_canErase](#server_canErase)
- [client_onInteract](#client_onInteract)
- [client_canInteract](#client_canInteract)
- [client_onAction](#client_onAction)
## Описание констант
<h3 id="poseWeightCount">poseWeightCount <i>integer</i></h3>

Задает количество поз анимации, которые может использовать модель harvestable.

Значением могут быть целые числа 0-3. (По умолчанию 0, никаких поз)

Значение, большее 0, указывает на то, что "mesh" визуализируемого объекта настроена на смешивание с "pose0", "pose1", "pose2".

Это, например, используется для выращивания растений.
## События
<h3 id="server_onCreate">server_onCreate(self) <i>serverEventCallback</i></h3>

Вызывается при создании скриптового объекта. Это происходит, когда ставится или загружается из файла сохранения новый Shape.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onCreate">client_onCreate(self) <i>clientEventCallback</i></h3>

Вызывается при создании скриптового объекта. Это происходит, когда ставится или загружается из файла сохранения новый Shape.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onDestroy">server_onDestroy(self) <i>serverEventCallback</i></h3>

Вызывается, когда Shape уничтожается.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onDestroy">client_onDestroy(self) <i>clientEventCallback</i></h3>

Вызывается, когда Shape уничтожается.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onRefresh">server_onRefresh(self) <i>serverEventCallback</i></h3>

Вызывается, если Lua-скрипт, прикрепленный к Shape, изменяется во время работы игры.

> Для этого события требуется, чтобы Scrap Mechanic был запущен с флагом '-dev'. Это позволит скриптам автоматически обновляться при внесении изменений.
{.is-info}

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onRefresh">client_onRefresh(self) <i>clientEventCallback</i></h3>

Вызывается, если Lua-скрипт, прикрепленный к Shape, изменяется во время работы игры.

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
<h3 id="server_onUnload">server_onUnload(self) <i>serverEventCallback</i></h3>

Вызывается, когда [Harvestable](TODO:link_to_type) выгружается из игры, потому что ни один [персонаж](TODO:link_to_type) [игрока](TODO:link_to_type) не находится достаточно близко к нему. Также вызывается при выходе из игры.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="server_onReceiveUpdate">server_onReceiveUpdate(self) <i>serverEventCallback</i></h3>

Вызывается время от времени в классе [HarvestableClass](), чтобы указать, что прошло некоторое время.

По соображениям производительности рекомендуется использовать это вместо [HarvestableClass.server_onFixedUpdate](#server_onFixedUpdate) для обновлений, которые не должны происходить часто.

Используйте [sm.game.getCurrentTick](TODO:link_to_func) для расчета времени.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}
<h3 id="client_onCollision">client_onCollision(self, other, position, selfPointVelocity, otherPointVelocity, normal) <i>clientEventCallback</i></h3>

Вызывается, когда [Harvestable](TODO:link_to_type) сталкивается с другим объектом.

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|[Shape](TODO:link_to_type)/[Character](TODO:link_to_type)|other|Другой объект.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которой произошло столкновение.|
|[Vec3](TODO:link_to_type)|selfPointVelocity|Скорость, которую имел [урожай](TODO:link_to_type) в момент столкновения.|
|[Vec3](TODO:link_to_type)|otherPointVelocity|Скорость, которую имел другой объект в момент столкновения.|
|[Vec3](TODO:link_to_type)|normal|Точка соприкосновения между [Harvestable](TODO:link_to_type) и другим объектом.|
{.dense}
<h3 id="client_onProjectile">client_onProjectile(self, position, airTime, velocity, projectileName, shooter, damage, customData, normal, uuid) <i>clientEventCallback</i></h3>

Вызывается, когда в [Harvestable](TODO:link_to_type) попадает снаряд.

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
|[Player](TODO:link_to_type)/[Shape](TODO:link_to_type)/[Harvestable](TODO:link_to_type)/nil|shooter|Стрелок может быть игроком, Shape, Harvestable или nil, если неизвестно. Снаряды, выпущенные юнитом, будут равны nil для клиента.|
|number|damage|Количество нанесённого урона от снаряда.|
|any|customData|Объект Lua, который может быть определен во время выстрела с помощью [sm.projectile.customProjectileAttack](TODO:link_to_func) или другой пользовательской версии.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал снаряд.|
|[Uuid](TODO:link_to_type)|uuid|Uuid снаряда.|
{.dense}
<h3 id="server_onProjectile">server_onProjectile(self, position, airTime, velocity, projectileName, shooter, damage, customData, normal, uuid) <i>serverEventCallback</i></h3>

Вызывается, когда в [Harvestable](TODO:link_to_type) попадает снаряд.

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
|[Player](TODO:link_to_type)/[Shape](TODO:link_to_type)/[Harvestable](TODO:link_to_type)/nil|shooter|Стрелок может быть игроком, Shape, Harvestable или nil, если неизвестно. Снаряды, выпущенные юнитом, будут равны nil для клиента.|
|number|damage|Количество нанесённого урона от снаряда.|
|any|customData|Объект Lua, который может быть определен во время выстрела с помощью [sm.projectile.customProjectileAttack](TODO:link_to_func) или другой пользовательской версии.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал снаряд.|
|[Uuid](TODO:link_to_type)|uuid|Uuid снаряда.|
{.dense}
<h3 id="server_onExplosion">server_onExplosion(self, center, destructionLevel) <i>serverEventCallback</i></h3>

Вызывается, когда [Harvestable](TODO:link_to_type) взрывается.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Vec3](TODO:link_to_type)|center|Эпицентр взырва.|
|integer|destructionLevel|Уровень разрушений, причиненных этим взрывом. Соответствует показателю прочности [Shape](TODO:link_to_type).|
{.dense}
<h3 id="client_onMelee">client_onMelee(self, position, attacker, damage, power, direction, normal) <i>clientEventCallback</i></h3>

> Если атакующий будет уничтожен до того, как произойдет удар, значение attacker будет равно nil.
{.is-info}

Вызывается, когда [Harvestable](TODO:link_to_type) получает удар в ближнем бою.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которую попал удар.|
|[Player](TODO:link_to_type)/nil|attacker|Нападавший. Может быть [игроком](TODO:link_to_type) или nil, если неизвестно. Атаки, предпринятые [юнитом](TODO:link_to_type), будут равны nil для клиента.|
|integer|damage|Количество нанесённого урона от удара.|
|number|power|"Сила" удара|
|[Vec3](TODO:link_to_type)|direction|Направление, в которое был нанесён урон.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал удар.|
{.dense}
<h3 id="server_onMelee">server_onMelee(self, position, attacker, damage, power, direction, normal) <i>serverEventCallback</i></h3>

> Если атакующий будет уничтожен до того, как произойдет удар, значение attacker будет равно nil.
{.is-info}

Вызывается, когда [Harvestable](TODO:link_to_type) получает удар в ближнем бою.

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Vec3](TODO:link_to_type)|position|Позиция, в которую попал удар.|
|[Player](TODO:link_to_type)/[Unit](TODO:link_to_type)/nil|attacker|Нападавший. Может быть [игроком](TODO:link_to_type), [юнитом](TODO:link_to_type) или nil, если неизвестно.|
|integer|damage|Количество нанесённого урона от удара.|
|number|power|"Сила" удара|
|[Vec3](TODO:link_to_type)|direction|Направление, в которое был нанесён урон.|
|[Vec3](TODO:link_to_type)|normal|Точка в которую попал удар.|
{.dense}
<h3 id="server_onRemoved">server_onRemoved(self, player) <i>serverEventCallback</i></h3>

Вызывается, когда [игрок](TODO:link_to_type) убирает [Harvestable](TODO:link_to_type).

> [HarvestableClass]() должен удалять [Harvestable](TODO:link_to_type) с помощью [Harvestable.destroy](TODO:link_to_func).
{.is-info}

Пример:
```lua
self.harvestable:destroy()
```

Аргументы:
|Тип|Имя|Описание|
|---|---|--------|
|table|self|Экземпляр класса.|
|[Player](TODO:link_to_type)|player|[Игрок](TODO:link_to_type), который хочет убрать [Harvestable](TODO:link_to_type).|
<h3 id="client_canErase">client_canErase(self) <i>clientEventCallback</i></h3>

Вызывается, чтобы проверить, можно ли в данный момент удалить [Harvestable](TODO:link_to_type).

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}

Должно вернуть:
| Тип |     Описание    |
|-----|-----------------|
|boolean|Логическое значение, указывающее, можно ли удалить [Harvestable](TODO:link_to_type) или нет. (По умолчанию используется "removable" из json, которое по умолчанию равно false)|
{.dense}
<h3 id="server_canErase">server_canErase(self) <i>serverEventCallback</i></h3>

Вызывается, чтобы проверить, можно ли в данный момент удалить [Harvestable](TODO:link_to_type).

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
{.dense}

Должно вернуть:
| Тип |     Описание    |
|-----|-----------------|
|boolean|Логическое значение, указывающее, можно ли удалить [Harvestable](TODO:link_to_type) или нет. (По умолчанию используется "removable" из json, которое по умолчанию равно false)|
{.dense}
<h3 id="client_onInteract">client_onInteract(self, character, state) <i>clientEventCallback</i></h3>

Вызывается, когда [игрок](TODO:link_to_type) взаимодействует с [Harvestable](TODO:link_to_type) нажатием клавиши "Использовать" (по умолчанию "E").

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|[Character](TODO:link_to_type)|character|[Персонаж](TODO:link_to_type) [игрока](TODO:link_to_type), который взаимодействует с [Harvestable](TODO:link_to_type).|
|boolean|state|Состояние взаимодействия. Всегда true. Класс [HarvestableClass]() получает только событие `key down`.|
{.dense}
<h3 id="client_canInteract">client_canInteract(self, character) <i>clientEventCallback</i></h3>

Вызывается, чтобы проверить, можно ли взаимодействовать с [Harvestable](TODO:link_to_type) в данный момент.

> Этот обратный вызов также отвечает за обновление текста взаимодействия, отображаемого игроку с помощью [sm.gui.setInteractionText](TODO:link_to_func#setInteractionText).
{.is-info}

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|[Character](TODO:link_to_type)|character|[Персонаж](TODO:link_to_type) [игрока](TODO:link_to_type), который смотрит на [Harvestable](TODO:link_to_type).|
{.dense}

Должно вернуть:
|Тип|Описание|
|---|--------|
|boolean|Логическое значение, указывающее, можно ли взаимодействовать с [Harvestable](TODO:link_to_type) или нет. (По умолчанию используется значение true, если реализован [client_onInteract](#client_onInteract), в противном случае значение false)
<h3 id="client_onAction">client_onAction(self, action, state) <i>clientEventCallback</i></h3>

Вызывается, когда урожай получает входные данные от игрока, [персонаж](TODO:link_to_type) которого привязан к [Harvestable](TODO:link_to_type).

Когда [персонаж](TODO:link_to_type) сидит в "сиденье", [персонаж](TODO:link_to_type) также считается привязанным к [Harvestable](TODO:link_to_type).

Аргументы:
| Тип | Имя|     Описание    |
|-----|----|-----------------|
|table|self|Экземпляр класса.|
|integer|action|Действие в виде целочисленного значения. Более подробная информация в [sm.interactable.actions](TODO:link_to_namespace#actions).|
|boolean|state|Значение True при начале действия, значение false при завершении действия.|
{.dense}