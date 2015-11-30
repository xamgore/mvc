---

layout: bright

style: |
    .slide { background-color: white; }

    .slide pre code { line-height: inherit; }

    .slide mark {
        background: 0 0;
    }

    a, .slide mark {
        color: #0080e0;
    }

    .slide b, .slide strong {
        font-weight: 700;
    }


    .slide h2 {
        margin: 0 0 58px;
        font: 48px/1 'Open Sans Light',sans-serif;
    }

    .slide h2 em {
        display: block;
        position: absolute;
        margin-top: -45px;
        font-size: 35px;
        font-style: normal;
        font-weight: 400;
        padding-bottom: 6px;
        color: #0080e0;
    }

    .slide.is-title.space {
        color: white;
        background-color: #112626;
        background-image: url('pictures/space_background.jpg');
    }
    .slide.is-title.space h2 {
        margin-top: 300px;
    }

    .slide.is-title.sky {
        background-image: url('pictures/sky_background.jpg');
        color: #F5FFE9;
    }

    .slide.is-title.mountains {
        color: white;
        background-color: #112626;
        background-image: url('pictures/title_background.jpg');
        opacity: 0.88;
    }

    .slide.is-title {
        background-size: cover;
    }

    .slide.is-title h2 strong {
        display: block;
        font-weight: 400;
        font-size: 350%;
        line-height: 1.35;
        position: relative;
        left: -7px;
    }

    .slide.is-title h2 {
        font-size: 32px;
    }

    [lang=en] .slide.is-title h2 strong {
        top: -5px;
        font-size: 380%;
        line-height: 1.3;
    }
    .slide.is-title h2 strong {
        display: block;
        font-weight: 400;
        font-size: 350%;
        line-height: 1.35;
        position: relative;
        left: -7px;
    }

    pre.low { line-height: 1.6 }

---

# **MVC Pattern** который вы ждали всегда
{: .is-title.sky }

---

~~~csharp
<mark>class</mark> StudentModel {









}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> StudentModel {
    <mark>string</mark> Фио;








}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> StudentModel {
    <mark>string</mark> Фио;
    <mark> int</mark>[] Оценочки;







}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> StudentModel {
    <mark>string</mark> Фио;
    <mark> int</mark>[] Оценочки;

    <mark>public void</mark> AddMark(<mark>int</mark> mark)
        <mark>=></mark> Оценочки.Add(mark);




}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> StudentModel {
    <mark>string</mark> Фио;
    <mark> int</mark>[] Оценочки;

    <mark>public void</mark> AddMark(<mark>int</mark> mark)
        <mark>=></mark> Оценочки.Add(mark);

    <mark>public void</mark> Отчислить()
        <mark>=></mark> if (Sum(Оценочки) < 60)
               Деканат.ОтчислитьСтудента(ФИО);
}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> TeacherController {
    <mark>static void</mark> Action() {







    }
}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> TeacherController {
    <mark>static void</mark> Action() {
        <mark>int</mark> rate = Console.ReadInteger(),
              id = Console.ReadInteger();





    }
}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> TeacherController {
    <mark>static void</mark> Action() {
        <mark>int</mark> rate = Console.ReadInteger(),
              id = Console.ReadInteger();

        <mark>if</mark> (rate < <mark>0</mark>)
            Console.WriteLine(<mark>"Это не гуманно, чувак!"</mark>);


    }
}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> TeacherController {
    <mark>static void</mark> Action() {
        <mark>int</mark> rate = Console.ReadInteger(),
              id = Console.ReadInteger();

        <mark>if</mark> (rate < <mark>0</mark>)
            Console.WriteLine(<mark>"Это не гуманно, чувак!"</mark>);

        <mark class="important">StudentModel</mark>.With(id).AddMark(rate);
    }
}
~~~
{: .low }

## Router

В зависимости от запроса вызывает нужный контроллер.

~~~csharp
<mark>public static void</mark> Main(<mark>string</mark>[] args) {
    <mark>switch</mark> (Console.ReadLine()) {
        <mark>case</mark> "<mark class="comment">оценить</mark>":
            <mark class="important">TeacherController</mark>.Action(); <mark>break;</mark>
        <mark>case</mark> "<mark class="comment">насладиться</mark>":
            MarksController.Action(); <mark>break;</mark>
    }
}
~~~
{: .low.next }

---

~~~csharp
<mark>class</mark> MarksController {
    <mark>static void</mark> Action() {
        student = Console.ReadInteger();
        <mark class="comment">RatesView.PrintRatesOf(student)</mark>;
    }
}
~~~
{: .low }

---

~~~csharp
<mark>class</mark> MarksController {
    <mark>static void</mark> Action() {
        student = Console.ReadInteger();
        RatesView.PrintRatesOf(student);
    }
}

<mark>class</mark> RatesView {
    <mark>static void</mark> PrintRatesOf(student)
        <mark>=></mark> Console.WriteLine(
            <mark>string</mark>.Join(<mark class="comment">", "</mark>, student.Оценочки));
}
~~~
{: .low }

## Ещё раз и кратко

* ​**Router** — выбирает нужный контроллер <mark class="next">| оценить и насладиться</mark>
* ​**Controller** — обрабатывает запрос <mark class="next">           | распихивает данные</mark>
* ​**Model** — данные и операции над ними <mark class="next">   | умеет в базу данных</mark>
* ​**View** — умеет выводить данные
* ...**<mark>???</mark>**
* ...**<mark>PROFIT</mark>**

## *Невинности нет* MVC был хотя бы раз у каждого!

<span class="next">Что ты делаешь, когда не знаешь, что делать?</span><br/>
<span class="next">Гуглишь!</span><br/>
<img src="pictures/query.png" class="next" alt=""/>

## *Даже у Google!* MVC был хотя бы раз у каждого!

*Рисуй картиночку!* <mark># TODO</mark>
{: .next }

## *Даже у тебя ;)* MVC был хотя бы раз у каждого!

Вспоминаем первое задание, магазин.
{: .next }

* ...Обработчик команд — роутер
* ...Обработка конкретной команды — конкретный контроллер
* ...Библиотека классов магазина — модели
* ...View тривиальный — `<mark>Console</mark>.WriteLine()`

## *Даже у меня ;)* MVC был хотя бы раз у каждого!

Второе задание, калькулятор выражений

*Вставь скриншотик!* <mark>#TODO</mark>
{: .next }

## Где нет MVC

*Вставь скрин кода!* <mark>#TODO</mark>
{: .next }




<!--img src="pictures/MVC-Process.svg" style="height: 400px" class="next"-->
