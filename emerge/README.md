Установка и простое использование

Добавьте в элемент <head> на странице:

<script src="/путь/к/jquery.js"></script>
<script src="/путь/к/emerge.js"></script>
Теперь элементы, у которых class="emerge" , будут проявляться только после загрузки их содержимого:

<div class="emerge">
  ... Покажется после загрузки ...
</div>
Эмёрдж ждёт загрузки картинок в тегах <img /> и подключенных через ЦСС (фоны, маркеры списка и т. д.), а также видеороликов в теге <video /> .

Если подключаете скрипт в конце документа, в <head> добавьте:

<style>.emerge { opacity: 0; }</style>
Индикаторы загрузки

Пропишите data-spin="true" в элементах, которым нужен индикатор загрузки:

<div class="emerge" data-spin="true">
  ... Будет индикатор загрузки ...
</div>
Встроенный спиннер выглядит так: 

Эти атрибуты управляют индикатором:

data-spin-size="24" 
Диаметр в пикселях. По умолчанию 24.
data-spin-color="#000" 
Цвет. По умолчанию чёрный.
data-spin-direction="clockwise" 
Направление вращения. Варианты: clockwise (по умолчанию) и counter-clockwise
Чтобы использовать свой индикатор, заверните его код в скрытый див:

<div id="custom-spinner" style="display: none">
  ... Код своего индикатора загрузки ...
</div>
И привяжите его к нужному Эмёрдж-элементу:

data-spin-element="custom-spinner" 
Использовать содержимое дива с id="custom-spinner" в качестве индикатора загрузки
Эмёрдж клонирует этот див для каждого элемента и выставит соответствующие размеры. Поэтому если вы хотите, чтобы индикатор отображался по центру, вам нужно самостоятельно добиться этого, например:

<div id="custom-spinner" style="position: relative; display: none">
  <img src="data:image..." width="24" height="24"
    style="position: absolute; left: 50%; top: 50%; margin: -12px"
  />
</div>
Чтобы использовать spin.js, «заведите» его внутри вашего дива (см. пример в блоге).

Эффекты

Эти атрибуты управляют анимационными эффектами:

data-effect="slide" 
Использовать такой встроенный эффект. Встроенные эффекты: relax, slide, zoom и screw.
data-duration="500" 
Длительность анимации в миллисекундах. По умолчанию 500 мс.
data-up="20px" or data-down="5em" 
Для эффекта slide указывает, насколько элемент должен скользить вверх или вниз. По умолчанию 20 пикселей вверх. Использование одновременно обоих атрибутов не имеет смысла.
data-left="10%" or data-right="5cm" 
Для эффекта slide указывает, насколько элемент должен скользить влево или вправо. По умолчанию ноль (т. е. без горизонтального скольжения). Использование одновременно обоих атрибутов не имеет смысла.
data-scale="0.5" 
Для эффектов relax, zoom и screw исходный масштаб. По умолчанию 0,92 для эффекта relax и 0,5 для эффектов zoom и screw.
data-angle="90" 
Для эффекта screw исходных угол в градусах. По умолчанию 90°. Используйте знак для изменения направления вращения.
data-origin="top" 
Для эффектов relax, zoom и screw точка, относительно которой происходит трансформация. По умолчанию «top» для эффекта relax и «center center» для эффектов zoom и screw.
data-opaque="true" 
Все встроенные эффекты включают переход из полностью прозрачного в полностью непрозрачное состояние. Этот атрибут делает элемент изначально полностью непрозрачным. Полезно, например, если вы хотите, чтобы элемент прилетел из-за края экрана.
data-style-1 
data-style-2 
Использовать указанный ЦСС для анимационных эффектов (см. пример ниже). Эти атрибуты игнорируются, если используется data-effect .
Пример:

<div class="emerge" data-effect="slide">
  ... Появится со скольжением ...
</div>
Использование data-атрибутов для изменения параметров анимации:

<div class="emerge"
  data-effect="relax" data-scale=".5" data-origin="bottom"
>
  ... Вырастет вертикально от половины высоты ...
</div>
Использование указанного ЦСС (перепроверьте префиксы):

<div class="emerge"
  data-opaque="true"
  data-style-1="-webkit-transform: rotate3d(1,1,0,90deg)"
  data-style-2="-webkit-transform: rotate3d(0,0,0,0);
    transition: opacity .5s ease-out,
      -webkit-transform 2s cubic-bezier(0.0, 0.0, 0.001, 1.0)"
>
  ... Космический эффект ...
</div>
Порядок и время

Иногда нужно, чтобы один элемент дождался другого перед появлением. Следующие атрибуты управляют порядком и временем:

data-await="element-id" 
Ждать, пока элемент с id="element-id" загрузится (но не конца его анимации появления). Ожидаемый элемент должен иметь class="emerge" , иначе атрибут будет проигнорирован. Здесь можно указывать только один элемент, но тот элемент может в свою очередь ждать другого.
data-continue="true" 
Ждать, пока предыдущий элемент class="emerge" (по порядку в ХТМЛ-документе) загрузится (но не конца его анимации появления). Это равносильно использованию data-await со значением id предыдущего элемента, но позволяет не прописывать ему это значение (проще!). Этот атрибут игнорируется, если используется data-await .
data-hold="500" 
Задержаться на столько миллисекунд (хотя бы столько времени должно пройти с тех пор, как готов элемент, которого ждёт данный).
data-expose="true" 
Задержаться до тех пор, пока пользователь не доскролит до элемента. Если установлена временная задержка, она будет отсчитывать только после появления элемента в области видимости.
Пример:

<div class="emerge">
  ... Тра-ля-ля...
</div>
<div class="emerge" data-continue="true">
  ... Дождётся предыдущего элемента ...
</div>
Чуть сложнее:

<div class="emerge" data-await="thing" data-hold="500">
  ... Дождётся элемента thing, появится через 500 мс ...
</div>
<div class="emerge" id="thing">
  ... Появится первым ...
</div>
Чтобы элементы появились одновременно независимо от того, какой загрузится первым, их нужно заставить ждать друг друга:

<div class="emerge" id="one" data-await="two">
  ... Появится одновременно со следующим ...
</div>
<div class="emerge" id="two" data-await="one">
  ... Появится одновременно со предыдущим ...
</div>
Событие готовности видео

По умолчанию Эмёрдж ждёт полной загрузки видеороликов перед тем, как их показать (событие canplaythrough ). С помощью аттрибута data-emerge-event у видеоролика это событие можно изменить, например:

<video ... data-emerge-event="loadedmetadata">
  ...
</video>
См. документацию по медиасобытиям в МДН.

Повтор

Добавьте class="emerge-replay" любому элементу, и по клику на нём все анимации страницы будут воспроизведены заново:

<a href="#" class="emerge-replay">Replay</a>
Полезно для отладки процесса появления страницы.

Требования к браузерам и Джейквери
Полностью поддерживаются последние браузеры на Вебките и Фаерфокс. В неподдерживаемых браузерах страница загрузится как если бы Эмёрджа не было. Аналогично с выключенными скриптами.

Эмёрдж создан с Джейквери версии 1.10.1. Возможно, он заработает с более старыми.