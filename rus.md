Представление «резинового» будущего веб-дизайна с **Flexbox**
==================================

Расположение в CSS сегодня определяют свойства *float* и *clear*. Базируясь на принципах, оставшихся от веков полиграфического дизайна, они работали достаточно хорошо – даже учитывая, что, строго говоря, *float* не был предназначен для этой цели. Впрочем, как и таблицы, но это не остановило нас в 90-ые.

Тем не менее, **будущее веб-разметки светлое**, и за это спасибо Flexbox’у. Механизм планировки в CSS позволяет нам организовать элементы по-настоящему веб-ориентированно. Некоторые элементы могут быть закреплены, в то время как другие прокручиваются вместе со страницей. Порядок, в котором они появляются может быть независимым от порядка источника. И всё это может подходить под целый ряд экранов разного размера, от широких ТВ-экранов до смартфонов — и даже устройств, пока еще не придуманных. Поддержка браузеров просто фантастична (кроме Вы-Знаете-Кого). Отличное время для того, чтобы «прыгнуть» в Flexbox, если вы еще не сделали этого.

Но изменить наши привычки не так просто, как может показаться. У flexbox’а просто ошеломляющее количество функций, и лишь несколько из них нам знакомы. Здесь довольно много чего нужно познать. К счастью, в целях разметки вам нужно знать только некоторые основы. Давайте посмотрим на то, как мы сможем создать основанный на flexbox интерфейс, подобный Gmail. Если вы еще не изучали, или не поняли flexbox полностью, эта статья поможет пересмотреть и объяснить вещи, которые поначалу могут озадачить.

Образ мыслей **Flexbox** 
--------
Flexbox требует нового способа мышления. Вместо организации элементов в виде строк и колонок слева направо, сверху вниз, мы организуем блоки в линию – на самом деле, в две линии – в главную и поперечную ось, первую из которых мы будем использовать сегодня. Думайте о главной оси, как о верёвке, на которую нанизаны блоки (div’ы или другие элементы HTML). Метафорическая верёвка проходит от одного конца её контейнера до другого – туго натянутая, невидимая ось. Это приводит к четырём интересным идеям.

###ВЫРАВНИВАНИЕ

Для начала, мы можем заставлять блоки скользить от одного конца верёвки до другого, центрировать их, или даже распределять равномерно. Это означает, что объекты могут прицепиться к одной или другой стороне макета – то есть, к левому или правому краю экрана, не важно какой он ширины. Также распределение подразумевает, что они хорошо адаптируются под экран любого размера, что идеально для нашего много-экранного мира.

Flexbox позволяет дизайнерам расположить элементы в оба конца “верёвки.”

###НАПРАВЛЕНИЕ 

Мы можем также не изменяя HTML-код обратить цепочку вспять, так, что блоки пойдут в противоположном направлении. Это схоже с техникой порядка сортировки, которая позволяет нам повернуть колонки обратно — кроме третьей особенности (восстановление стандартного порядка для больших экранов), что на шаг дальше.

Как порядок, так и позиция элементов могут быть изменены на противоположный

###ОРИЕНТАЦИЯ

В-третьих, мы можем повернуть верёвку на 90 градусов, «подвесив» её с верхушки контейнера, вместо расположения элементов от одной стороны к другой. Медиа-запросы и возможности flexbox делают возможным изменение ориентации компонентов – то есть, «шапки», основной части и «подвала» сайта – сверху-вниз на экране смартфона, но слева-направо на экране компьютера. То, что мы привыкли называть строками (rows) может теперь идти сверху-вниз или снизу-вверх, благодаря щепотке CSS.
 
Вся организация может повернуться на 90 градусов, “повиснув” сверху контейнера

###ПОРЯДОК

Наконец, мы можем контролировать, какой из блоков идёт первым, вторым, третьим и так далее на верёвке, без правки HTML. Это грандиозно. Это означает, что мы можем структурировать HTML документ для поисковой оптимизации (SEO), доступности или улучшения семантики — независимо от макета. Хотите отцентрировать элементы по вертикали? Нет проблем. Хотите навигацию в конце вашего HTML, но в начале вашего макета? Конечно. Есть желание поэкспериментировать с разными типами макетов? Всё это в CSS. Именно так, мы уже сейчас думаем в понятиях содержания и устройств, а не жёстких сеток.

Тот же порядок элементов может измениться с CSS – без всяких изменений HTML.

Это далеко не всё, но мы разобрали основы. Резюмируем:

1. Блоки натянуты на невидимую линию.
2.	Мы можем «толкать» их туда-сюда по этой линии.
3.	Мы можем повернуть линию вспять, таким образом перевернув порядок следования блоков.
4.	Линия может повернуться на 90 градусов.
5.	Мы можем смешивать элементы на этой линии так, как нам захочется, независимо от HTML. 

##ПОРЯДОК

Порядок — это важный концепт в flexbox. Давайте возьмем стандартный HTML документ: типичные блоки постов будут включать части информации.

 - Header («Шапка»)

название сайта, описание, форма поиска (это ограничивает содержание и говорит людям, где они находятся.)

 - Мета-данные

автор/издатель, дата, тема(-ы) (это помогает людям решить, что именно они хотят увидеть.)

 - Основной контент

о чем эта страница (причина, по которой страница существует)

 - Дополнительный контент

связанная информация (короткие рекламные объявления, ссылки, “смотрите также…”)

 - Навигация

ссылки в другие разделы сайта (темы более высокого уровня)

 - Footer («Подвал»)

копирайт, RSS-рассылка, социальные сети, форма подписки

Эти элементы перечислены в порядке, в котором их могут просматривать поисковые машины, или софт для сканирования экрана. Теперь, давайте протянем «верёвку» с верха мобильного устройства и изменим их порядок так, чтобы поместить контент на первое место.

1. Основной контент
2.	Мета-данные
3.	Дополнительный контент
4.	Шапка
5.	Навигация
6.	Подвал

Тем временем, на настольных компьютерах всё будет выглядеть иначе.

1. Шапка
2.	Мета-данные
3.	Основной контент
4.	Дополнительный контент
5.	Навигация
6.	Подвал

Подождите, не совсем так. Мы хотим навигацию сверху и flexbox справится с этим.
Из этого следует, что вы также можете протянуть «верёвки» внутри блоков и все правила снова будут работать. Но для начала, давайте поговорим о порядке. Вот где всё становится сложнее.

###Вложенные оси и блоки

Каждый макет flexbox’а – каждый блок – может содержать еще один комплект блоков натянутых на их собственную верёвку. Эта верёвка может идти справа налево или наоборот, снизу вверх или наоборот, «толкать» блоки в оба конца, центрировать, или распределять их. И так как эта гибкость открывает большие возможности, это также значит, что мы должны планировать нашу разметку осторожно.

Элементы на верёвке flexbox могут, в свою очередь, содержать другие flexbox-верёвки.

Чтобы понять, почему это может вызвать осложнения, давайте попробуем организовать некоторый контент; нам нет необходимости в упорядочивании макета (то есть, в приведении его к тому виду, в котором его увидят люди). Представьте, что вы презентуете что-либо публике. Сначала вы объясняете им, о чем вы собираетесь говорить, далее вы переходите к самой теме презентации и после вы суммируете сказанное некоторыми выводами. Наша гипотетическая страница следует схожей структуре:

 - Шапка 
 - Само сообщение 
 - Список всех сообщений 
 - Ссылки к входящим, архиву и т. д. 
 - Подвал

##Набросок Дизайна

Для простоты мы будем работать со знакомым макетом.
 
Типичная организация для почтового приложения.

Здесь всего два flexbox слоя. В первом содержится три блока, расположенных сверху-вниз. Второй слой находится в среднем блоке, слева-направо.
Шапка и подвал растягиваются по ширине экрана. Навигация занимает маленькую колонку слева и область отображения позволяет юзеру прокручивать страницу, если в ней содержится больше контента, чем может быть показано. Мы можем достигнуть этого парой float и фиксированным позиционированием, но flexbox дает нам большее количество опций, при меньшей разметке. Давайте взглянем на это.

###Настройка Документа

Внешний контейнер с классом .flex-container разделён на три части:

    <body>
        <div class="flex-container">
        <header>…</header>
        <main class="flex-container">…</main>
        <footer>…</footer>
      </div>
    </body>

Мы назвали его flex-container чтобы описать его цель в несколько семантическом виде. Как минимум, наш CSS имеет смысл.

Внутри элемента main нам нужно расположить три блока:

    <main class="flex-container content">
      <article class="message">…</article>
      <div class="message-list">…</div>
      <nav class="mailbox-list">…</nav>
    </main>

Этот пример использует article (статья – англ.) в независимой трактовке, не в «журнальном» смысле.

###Присваивание Элементам Свойства Flexbox

Нам нужно сказать браузерам, что эти три элемента будут… гибкими.

    .flex-container,
    .flex-container header,
    .flex-container footer {
      display: -webkit-box;
      display: -moz-box;
      display: -ms-flexbox;
      display: -webkit-flex;
      display: flex;
    }

Заметьте, что это применение свойства flexbox основным контейнерам, а не контенту.

###Добавим Измерения

Основываясь на наброске дизайна, мы знаем, что конкретные элементы будут иметь ширину и высоту. Например, блоки, отраженные тегами header и footer, будут длинными тонкими полосами, в сравнении с высокой main, а навигация, расположенная слева — относительно узкой. Пространство article заполнит оставшуюся часть места. Все эти блоки не будут иметь фиксированной ширины, чтобы оставаться гибкими, независимо от размера экрана (а также для доходчивости этого руководства).

    .message {
      flex-basis: 70%;
    }
    .message-list {
      flex-basis: 15%;
    }
    .mailbox-list {
      flex-basis: 15%;
    }
    .flex-container header,
    .flex-container footer {
      width: 100%;
      height: 5rem;
    }

Flex-basis здесь это что-то вроде ширины – во всяком случае до тех пор, как основная ось – горизонтальная. Если мы «подвесим» ось сверху, flex-basis автоматически станет высотой. Удобно!

###Делаем Основной Раздел Прокручиваемым

Это довольно просто. Нужно добавить overflow: scroll к элементу main, чтобы не давать ему пересекать header и footer. Полезный совет: Попробуйте overflow: auto, чтобы скрыть полосы прокрутки в большинстве браузеров (если эти полосы не нужны).

    .message {
      flex-basis: 70%;
      overflow: scroll;
    }

###Тестируем Содержимое

На данный момент, форма header должна иметь небольшой отступ, даже если изменить браузеру размер. Содержимое должно выглядеть читабельно в окнах любого размера. И если браузер не поддерживает Flexbox, страница должна быть автоматически заменена на макет «сначала контент», который мы рассматривали выше.

Это важно, потому что Вы-Знаете-Кто пока что не поддерживает flexbox. Впрочем, все современные версии поддерживают, так что важно на самом деле лишь то, когда пользователи обновят свои программы. Так, где же flexbox поддерживается?

* Chrome 31 и позднее
* Firefox 31 и позднее
* Internet Explorer 10 и позднее
* Safari для Mac version 7 и позднее
* Safari для iOS 7.1 и позднее
* Android Браузер 4.4 и позднее
* Chrome для Android 42 и позднее
* Opera 27 и позднее

В **Clicky** есть график, отображающий доли рынка мобильных браузеров.
Что на счет более старых браузеров? Решения могут сильно варьироваться, в зависимости от макета, который вы хотите получить, хотя мы можем всё-таки кое-что посоветовать.
Самый безопасный способ поддержки браузеров, не способных использовать flexbox это писать CSS в порядке, в котором вы хотите, чтобы он появлялся. Начните с семантического мышления. Старые версии Internet Explorer игнорируют свойства flexbox — к счастью, старые добрые условные комментарии позволяют нам применять float’ы и clear для семантического макета. Старые версии других браузеров, как правило, дают вам дружелюбные к мобильным устройствам макеты, которые содержат контент в логическом порядке. Так что flexbox может сосуществовать со свойствами float, display: table-cell и позиционированием, при этом современные браузеры применят свойства flexbox, а более старые - проигнорируют. Наконец, если вы хотели бы поэкспериментировать, попробуйте Flexie, который вносит изменения в старые браузеры с помощью основанных на JavaScript авто-заполнениях.

Попробуйте Flexbox. Хотя он и предлагает множество опций, большинство – как выравнивание – вступают в игру сразу после того, как вы настроили организацию элементов. Главные методы, которые мы изучили, это выравнивание, направление, ориентация, порядок и вложенность. Мы обнаружили акцент на этом в новом CSS-фреймворке от Foundation: Если вы можете понять такие вещи, как выравнивание, направление, ориентация и порядок, тогда вы на пути к «гибкому» будущему. Попробуйте вот это демо, чтобы увидеть flexbox в действии (но не забывайте,  что оно пока не адаптивно).

##Читайте так же…

Чтобы узнать больше о flexbox, проверьте следующее:

 - Flexbox in 5 Minutes, небольшая утилита для быстрого создания flexbox
 -  Flexbugs, редактируемый сообществом список проблем с flexbox, а так же кросс-бразуерные обходные пути для решениях этих проблем.
 - Flexy Boxes: Flexbox Playground and Code Generator, Пете Боере
 - “Using Flexbox to Lay Out Web Applications,” Сеть Разработчиков Mozilla
 - “Flexbox,” – статья Сары Суидан, Codrops 
 - “A Visual Guide to CSS Flexbox Properties,” Димитар Стоянов 
 - “CSS Flexible Box Layout Module Level 1,” W3C – официальная спецификация

