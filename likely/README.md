# README #

Установка и использование

Добавьте в элемент <head> на странице:

<script src="https://cdn.swiftlead.ru/likely/likely.js"></script>
<link rel="stylesheet" href="https://cdn.swiftlead.ru/likely/likely.css">
Вставьте кнопки в нужное место, расположите в любом порядке, уберите лишние, подпишите как нравится:

<div class="likely">
  <div class="twitter">Твитнуть</div>
  <div class="facebook">Поделиться</div>
  <div class="gplus">Плюсануть</div>
  <div class="vkontakte">Поделиться</div>
  <div class="telegram">Отправить</div>
  <div class="odnoklassniki">Класснуть</div>
  <div class="linkedin">Линкануть</div>
  <div class="whatsapp">Вотсапнуть</div>
  <div class="pinterest" data-media="i/pinnable.jpg">Запинить</div>
</div>

Настройка

Классы, меняющие внешний вид (все примеры выше):

class="likely likely-light" 
Скин, который хорошо смотрится на тёмном и фотографическом фоне. Если фотография слишком светлая, лучше использовать обычный скин.
class="likely likely-small" 
Маленькие кнопки.
class="likely likely-big" 
Большие кнопки.
Параметры у основного элемента:

data-url="..." 
Какая ссылка должна попасть в соцсети. По умолчанию — адрес страницы, на которой стоят кнопки, поэтому обычно можно не указывать.
data-title="Лайкли: социокнопки, которые не стыдно поставить" 
Название страницы, которое должно попасть в соцсети. По умолчанию — тайтл страницы.
У элемента Твиттера:

data-via="ilyabirman" 
Какой акаунт упомянуть в твите. Поменяйте мой на свой :-)
У элемента Телеграма:

data-text="Зацени-ка" 
Какой текст отправить вместе со ссылкой в Телеграм.
У элемента Пинтереса:

data-media="i/pinnable.jpg" 
Картинка, которая должна попасть в Пинтерес.
Для того, чтобы в Фейсбук попадала конкретная, а не случайная картинка, используйте такой тег внутри элемента <head> :

<meta property="og:image" content="path/to/image" /> 
