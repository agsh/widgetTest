# Тестовое задание

## Задание

Нужно написать виджет, который проигрывает определённое видео с youtube на всё окно.

Документация находится в `doc/index.html`

Пример виджета в `widgets/sampleWidget/sampleWidget.js`

Страница примера: `sampleWidget.html`

Создать виджет в окне можно кликнув на меню окна (это три полосочки в верхнем левом углу каждого окна) и в выпадающем
меню выбрать `создать виджет -> Пример виджета`. Потом поводить мышкой, выбрав серой областью место создания, и кликнуть.

Нужно иметь возможность дублировать виджет в этом окне, или соседнем, по выбору. Реализация свободная.

## Конкретика

Новый виджет должен наследоваться от класса `Widget`, как это показано в примере.

События изменения размера окна/виджета сейчас нет, но можно переопределить метод `recalculatePosition`, который
как раз-таки и вызывается при изменении размеров и есть у всех классов наследников класс `Area`, а именно: `Window` и `Widget`.
Как-то так:
``` javascript
NewWidget.prototype.recalculatePosition = function() {
	Widget.prototype.recalculatePosition.apply(this, arguments);
	console.log('resized!');
};
```

Чтобы можно было создавать свой виджет в окне через меню, нужно зарегистрировать свой класс с помощью метода `Window~registerWidget`.
Имя задаётся приватным свойством `_name`.

Метод `afterPlacement` вызывается после того, как виджет будет отрисован в DOM-дереве.

