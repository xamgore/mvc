###### V in MVC

Ни для кого не секрет, что я принимал участие в разработке сервиса БРС.

И так как я получил там определённый опыт, мне бы хотелось поделиться им с вами
немножечко о вебчике и конкретно о паттерне _MVC_.


Начнём мы с того, что поймём, а что должно нас сподвигнуть на изучение
нового паттерна и последующее его использование?

Как и всегда, пощупаем какой-нибудь код... Например, которому уже 10 лет.

---

Навскидку здесь есть несколько проблем, которые я вам сейчас покажу.

Во-первых используется четыре разных языка:

* HTML (гипертекстовый язык разметки, структура сайта)
* CSS (каскадные таблицы стилей, для оформления и красоты)
* SQL (забрать из базы какие-то данные)
* PHP (инструкции исполняемые на сервере)

---

Так вот теперь вопрос, а вообще вам ясно что здесь происходит?

Поднимите руки, кому ясно.

Если нет, это нормально.

---

Этот код действительно трудно читать, как раз из-за смешения четырёх языков.
Нужно уметь читать эти языки, хотя бы знать их структуру.
А о параллельной работе двух или более специалистов речи не идёт.

Этот код трудно поддерживать. Наверняка где-то в другом месте тоже есть вывод
количества комментариев, рейтинг, и всё-такое. То есть у нас дублирование кода.

В общем, этот код ужасен, нам хочется плакать. И возникает следующий вопрос?

---

ЧТО НАМ ДЕЛАТЬ?

*Спросить кого-нибудь из аудитории*

Очевидно, мой паттерн — это ответ на вопрос.

##### Model

Начнём с того, что обычно в наших приложениях есть некоторые _данные_
и определённая над ними _бизнес-логика_.

Вот в университете такими данными может служить информация о студенте,
например, его фамилия имя отчество и оценочки, а бизнес-логикой является
механизм выставления таких оценочек и последующее отчисление.

---

На этом наша работа с _предметной областью_ окончена.

Мы получили модель студента.

Если преподаватель захочет изменить ваши оценки, то он будет использовать
средства этой самой модели, то есть метод `AddMark`.

---

##### Controller

Писать свой код он будет в другом элементе, в _Контроллере_.

Контроллер принимает входные данные от пользователя (_rate_, _id_),
проверяет их корректность, и отсылает команды в Модель, чтобы она
измененила своё состояние. Контроллер _управляет_ ходом выполнения операции.

##### Router

Очевидно, контроллеров может быть несколько, и наше приложение должно
обращаться к каждому контроллеру в зависимости от запроса пользователя.

Тот элемент, который распределяет запросы пользователя по контроллерам и
называется Router.

...

---

##### View

Напишем контроллер по выводу оценок.

Сам вывод делегируем классу `RatesView`.

---

Вообще, преподавтелям да и деканату тоже интересны ваши оценки,
и информация должна подаваться в разных форматах, так что мы
говорим о нескольких _Представлениях_ модели.

---

##### 

---

##### На примере Google

В адресной строке браузера вы вводите какое-нибудь слово, например, "еноты".

Что происходит:

* Браузер посылает HTTP-запрос
* Сервер гугла передаёт управление главному контроллеру
* Контроллер обращается к поиску текста, изображений, рекламе
* Полученные данные передаёт в представление
* Web, mobile, XML версия


Контроллер обращается к моделям текстовых запросов, изображений, видео, рекламы,
которые загружают всю информацию, связанную с енотами.

Данные моделей передаются в Представление, чтобы сформировался HTML-код страницы.
Также существует мобильная версия, так что под неё идёт другое представление.

---

##### MVC в примерах

* ...Выражения и декораторы — модель
* ...Обработчики событий — контроллер
* ...Графический интерфейс — представление
