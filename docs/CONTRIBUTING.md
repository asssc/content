# CONTRIBUTING.md

[![Issues](https://img.shields.io/github/issues/Y-Doka/y-doka.site)](https://github.com/Y-Doka/y-doka.site/issues)

## Чем вы можете помочь

### Реальные задачи

Загляните в [раздел Issues](https://github.com/Y-Doka/y-doka.site/issues) нашего репозитория, чтобы ознакомиться со списком актуальных задач. Мы будем рады, если вы поможете закрыть [good first issues](https://github.com/Y-Doka/y-doka.site/issues?q=is%3Aissue+is%3Aopen+label%3A"good+first+issue") — с ними можно справиться, даже если вы только начинаете обучение.

Также мы будем постепенно выкладывать задачи посложнее, связанные с допиливанием сайта Доки. Дизайн и описание фичи — всё, как во взрослых опенсорсных проектах. Тут мы надеемся на помощь старших студентов, выпускников Практикума и всех, кто чувствует в себе силы, чтобы решить реальную задачу.

### Сообщество

Если вы уже трудитесь в разработке и хотите присоединиться к команде авторов, напишите нам на [feedback@y-doka.site](mailto:feedback@y-doka.site), мы всегда рады обсудить новые идеи, познакомиться и подумать, как сделать самую бодрую Доку в интернете.

Напоминаем, что сейчас мы на стадии закрытого бета-теста и хотим сохранить эту ламповость. Просим не делиться проектом публично. Однако личная рекомендация или метко отправленное сообщение — это рабочий способ привлекать в команду единомышленников.

### Обратная связь

В каждой статье у нас есть форма обратной связи, которая помогает нам делать Доку лучше. Если вы прочитали статью, и она вам понравилась, смело жмите «лайк». Это не Инстаграм и не Юра Дудь, мы не будем спамить в ваши соцсети — вся обратная связь отправится только во внутреннюю форму фидбека для команды.

Если вы считаете тему нераскрытой или вам не понравился текст, жмите «дизлайк» и напишите в форме, чего вам не хватило. Команда авторов будет регулярно просматривать фидбек — это ляжет в основу нашей работы в следующем году. Мы делаем Доку для вас, поэтому давайте улучшать ее вместе!

## Как мы пишем статьи

### Команда

Авторы Доки работают в командах по вёрстке (HTML и CSS), и JavaScript (плюс инфраструктура). У каждой команды есть свой тимлид, который организует работу и составляет план статей.

### Флоу

Автор выбирает статью из списка задач, пишет текст, создает примеры кода, после чего статья отдаётся тимлиду, который её проверяет. Другие авторы тоже могут заглянуть в статью и дополнить раздел «В работе» — поделиться опытом о том, как эта штука используется в реальной жизни.

### Дизайн

Если статья принята, она направляется команде дизайнеров, которые готовят иллюстрации, схемы и оформление для примеров кода. Параллельно с этим она проверяется редактором и публикуется на GitHub.

## Как работает Дока

Это мощный раздел, до конца дойдут не многие, но после — гарантируем вам базовое понимание того, на чем сделана Дока, и возможность действовать.

Дока собрана на базе [Eleventy — генератора статических сайтов](https://www.11ty.dev/) и хранится на GitHub в этом репозитории.

Если вы работаете под Windows, проверьте, что у вас установлено [окружение bash](https://gitforwindows.org/), в Linux и macOS bash установлен по умолчанию.

Для того, чтобы помочь в разработке Доки вам потребуется «форкнуть» репозиторий, проверить, что [у вас установлен Node.js](https://nodejs.org/en/) и [npm](https://www.npmjs.com/) (он есть в составе Node.js), ещё вам потребуется установить Sass.

```bash
# проверим версию Node.js
node -v

# проверим установленную версию npm
npm -v

# устанавливаем Sass глобально на вашей машине
npm install -g sass
```

### Как начать

После того, как вы клонировали репозиторий на ваш компьютер и проверили наличие установленного Node.js и npm, вам необходимо запустить bash-терминал в папке проекта и установить все зависимости.

```bash
# устанавливаем зависимости
npm i
```

В файле package.json вы можете найти полный список зависимостей и команд, которые мы используем при сборке проекта.

```bash
# для запуска локальной версии проекта
npm start
```

- Проект будет собран и запущен на `http://localhost:8080`
- Можно посмотреть сборку с разных устройств в локальной сети на `http://192.168.1.42:8080`
- Статус локального сервера доступен на `http://localhost:3001`

### Где что лежит

Все стили, скрипты, шрифты, иконки и картинки находятся в `/src/assets/`. Папка `/src` является корневой, поэтому, когда вы будете вставлять картинки, или подключать демки, можно использовать относительные адреса, например:

```markdown
![Альтернативное описание для alt-атрибута](/assets/images/posts/active/active.gif)
```

- Шаблоны для страниц хранятся в формате `*.njk` и находятся в директории `/layouts/`.
- Статика хранится в `/pages/`.
- Статьи находятся в директории `/posts/`.

### Из чего состоит страница

Рассмотрим на примере about.njk то, что каждый файл должен начинаться с описания переменных.

```markdown
---
layout: no-aside <!-- укажите название шаблона страницы -->
permalink: /about/ <!-- постоянная ссылка для страницы -->
eleventyNavigation: <!-- внутренняя навигация 11ty -->
  key: About
---

<!-- ниже ваш HTML с возможностью использовать переменные *.njk-файлов -->

<div class="container">
    <h1>About</h1>
</div>
```

Подробнее о переменных, доступных в Eleventy (например, о коллекциях) и как их использовать можно [прочитать в официальной документации (англ.)](https://www.11ty.dev/docs/collections/) или посмотреть пример реализации в навигационных страницах Доки (`/pages/naw-pases/`).

### Из чего состоит статья

Разберем это на примере гайда по flexbox.

```markdown
---
title: Гайд по flexbox <!-- название статьи, <h1> страницы -->
name: flexbox-guide <!-- название файла без расширения для работы URL -->
author: ABatickaya <!-- ник автора основного текста для работы коллекций-->
co-authors:
  - furtivite <!-- ники всех соавторов (дописали "В работе"? Вам сюда)-->
designers: <!-- ники всех дизайнеров -->
contributors: <!-- ники всех прочих разработчиков -->
summary: <!-- ключевые слова для работы поиска -->
  - флексбокс
  - flexbox
cover:
  desktop: 'desktop.png' <!-- адрес широкой картинки для десктопной обложки -->
  mobile: 'mobile.png' <!-- адрес узкой картинки для мобильной обложки -->
  alt: 'Умная собака подозрительно смотрит' <!-- альтернативное описание для обложки -->
---

<!-- далее обычная статья в markdown -->

## Что это?

Долгое время веб существовал в статичном виде. Сайты разрабатывались и просматривались только на экранах мониторов стационарных компьютеров. В масштабах истории совсем недавно у нас появилось огромное разнообразие различных экранов — от мобильных телефонов, до телевизоров — на которых мы можем взаимодействовать с сайтами. Отсюда появилась необходимость в гибких системах раскладки.

Идея флексбоксов появилась ещё в 2009 году и по сей день этот стандарт развивается и прорабатывается. Основная идея флексов — гибкое распределение места между элементами, гибкая расстановка, выравнивание, гибкое управление. Ключевое слово **гибкое**, что и отражено в названии (_flex — англ. гибко_).
```

- [Посмотрите пример статьи для справочника в файле](./EXAMPLE_article.md)
- [Посмотрите пример статьи-лонгрида в файле](./EXAMPLE_long-read.md)

#### Как пользоваться полями

Используйте поля только там, где это необходимо. Если вам нечем заполнить поле — удалите его, не оставляйте его пустым.

#### Обложки

К статье можно добавить обложку (хиро-картинку), которая предваряет контент:

![Пример обложки](./src/assets/images/docs/contributing/contributing.png)

Если вы хотите добавить обложку, позовите [кого-нибудь из мейнтейнеров](https://github.com/Y-Doka/y-doka.site/blob/master/CODEOWNERS), мы закажем картинку у дизайнера.

#### Подписи авторов

Так же в статье используется ссылка на авторов раздела «В работе» и подписи статьи:

```markdown
<!-- подпись автора в раздел «В работе» -->

{% include "authors/furtivite/in-work.njk" %}

<!-- подпись автора в конец статьи -->

{% include "authors/ABatickaya/author.njk" %}
```

Подписи можно найти в папке `/includes/authors/`

#### Интерактивные примеры кода

В статьях мы используем интерактивные примеры, они встраиваются так же, через `{% include %}`, как и подписи авторов. Встроенные в страницу «демки» позволяют плавнее строить повествование и демонстрацию концепций.

Визуально такие демки — интерактивная часть в стандартной верстке, не выделенная явно. Это главное отличие инлайновых демок от интеграций с CodePen.

Такие примеры мы оборачиваем в специальные блоки-обёртки, чтобы задать им стандартные стили-рамки и иметь возможность увеличить специфичность во время работы с CSS-файлом примера:

```markdown
<!-- ваша статья -->

{% include 'demos/mydemo/index.njk'%}
```

Технически демка может состоять из любого набора файлов в папке `/includes/demos`, но чаще всего это три файла:

- `.njk` со стартовой вёрсткой демки и вложением CSS и JS-файлов.
- `.css` — стили
- `.js` — JavaScript-код

```html
<!-- файл демки -->
<style>
  {% include './index.css' %}
</style>

<div class="article__code" id="my-demo"></div>

<script>
  {% include './index.js' %}
</script>
```

Добавление класса article\_\_code является обязательным, он даёт черную рамку и усиливает специфичность.