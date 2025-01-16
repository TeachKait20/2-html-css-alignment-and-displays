# 2-html-css-alignment-and-displays 
## html-css выравнивание и отображение 

Создадим страницу с изображениями животных и будем по разному их отображать. 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>animals</title>
</head>
<body>
    <div id="animal-box">
        <img src="./photo/cat.png" alt="тут кошка" class="animal">
        <img src="./photo/dog.png" alt="тут пёс" class="animal">
        <img src="./photo/hamster.png" alt="тут хомяк" class="animal">
        <img src="./photo/popug.png" alt="тут попугай" class="animal">
    </div>
</body>
</html>
```
```css
.animal {
    width: 300px;
}

#animal-box {
    width: 50%;
    border: 1px black solid;
    margin: 0 auto 0 auto;
}
```
* `div animal-box` - это контейнер для изображений. Пусть его ширина будет 50% от всей страницы и создадим ему рамку для удобства. Внешними отступами `margin` поместим его по-центру.
* Самим же изображениям зададим один общий класс для установки ширины.

После заготовки перейдём к главному.

## `display` в css

Свойство `display` в CSS определяет, как будет отображаться элемент на странице. Оно позволяет контролировать, как элемент взаимодействует с другими элементами и какова будет его структура (например, блоковая, строчная или гибридная). В зависимости от значения `display`, элемент может вести себя по-разному и изменять разметку на странице.

**Основные значения display:**
1. `display: block;`
Элемент отображается как блок. Он занимает всю ширину контейнера, в котором находится, и каждый такой элемент начинает с новой строки.<br><br>Примеры: `<div>`, `<header>`, `<footer>` и т.д.<br><br>У некоторых HTML-элементов значение display: block; задано по умолчанию. Это означает, что они автоматически занимают всю ширину родительского контейнера и располагаются каждый с новой строки.<br><br>К блочным элементам относятся, например: `<div>`, `<header>`, `<footer>`, `<section>`, `<article>`, `<h1>...<h6>`, `<p>`, `<ul>`, `<ol>`, `<li>`, `<form>`.

![image](https://github.com/user-attachments/assets/ee967388-2bee-497a-b3cb-1fe53198cf72)

2. `display: inline;`
Элемент отображается как строчный (инлайн). Он занимает ровно столько места, сколько нужно для его содержания, и не переносится на новую строку.<br><br>Примеры: `<span>`, `<a>`, `<strong>` и т.д.

![image](https://github.com/user-attachments/assets/728c6f2c-aadc-4ba8-80b0-070e8bccaf68)

3. `display: inline-block;`
Комбинирует свойства блочного и строчного элементов. Элемент занимает ровно столько места, сколько ему нужно, но при этом можно задавать ширину и высоту (чего нельзя сделать для `inline`).

![image](https://github.com/user-attachments/assets/fdde66e7-da62-4b6a-a5c3-1b8ccef93c17)

4. `display: none;`
Полностью скрывает элемент с веб-страницы. Он не занимает места, как будто его нет в HTML-разметке.

![image](https://github.com/user-attachments/assets/1de0b5ac-21c1-40f2-adcb-c8dac43b2ec7)

5. `display: flex;`
Переводит элемент в гибкий контейнер. Его дочерние элементы становятся флекс-элементами, которые можно легко выстраивать по горизонтали или вертикали. Используется для создания адаптивных макетов.

![image](https://github.com/user-attachments/assets/d8845de8-6b79-4b34-88b1-7ab9931f5d36)

7. `display: grid;`
Превращает элемент в сеточный контейнер. Его дочерние элементы выстраиваются в сетку, и можно точно управлять их расположением по строкам и столбцам. Подходит для сложных макетов.

![image](https://github.com/user-attachments/assets/8059c157-686f-4703-8ea4-cba76974affd)

8. `display: table;`, `display: table-row;`, `display: table-cell;` и т.д.
Имитируют поведение таблицы. Можно использовать для создания табличной структуры без `<table>`, если это необходимо.

![image](https://github.com/user-attachments/assets/281f9b7f-49b3-4479-bf71-9a049c67ef88)

## Пример с `grid`
У каждого описанного выше свойства `display` есть отдельные свойства для его работы. разберём пример с `grid`.<br><br>
`grid` - создаст идеальную сетку. Её можно использовать при будущей адаптации страницы. 

```css
.animal {
    width: 300px;
    border: 5px black dashed;
}

#animal-box {
    width: 50%;
    border: 5px blue solid;
    margin: 0 auto 0 auto;

    display: grid; /* Превращаем элемент в контейнер сетки (grid), чтобы управлять расположением его дочерних элементов по строкам и столбцам */

    grid-template-columns: repeat(2, 1fr); /* Задаем две равные по ширине колонки внутри сетки. 
                                              'repeat(2, 1fr)' означает "создать 2 колонки, каждая из которых занимает 1 часть доступного пространства (1fr)".
                                              'fr' (fraction) — это единица измерения, означающая долю от свободного пространства. */
    
    gap: 15px; /* Устанавливаем расстояние (отступ) в 15 пикселей между элементами сетки (и по вертикали, и по горизонтали) */
    
}
```

![image](https://github.com/user-attachments/assets/d3791c7e-f7e8-4070-a016-998312e1f248)

## Пример с `flex`

Можно расположить элементы горизонтально и создать scrollbar. 

Шаг 1.
```css
.animal {
    width: 300px;
    border: 5px black dashed;
    margin-left: 10px;
}

#animal-box {
    width: 300px;
    height: 300px;
    padding-right: 20px;
    border: 5px blue solid;
    margin: 0 auto 0 auto;

    display: flex;
}
```

![image](https://github.com/user-attachments/assets/02f655f8-6ca2-4032-aba9-b828808eaf46)

Шаг 2.
```css
.animal {
    width: 300px;
    border: 5px black dashed;
    margin-left: 10px;
}

#animal-box {
    width: 300px;
    height: 300px;
    padding-right: 20px;
    border: 5px black solid;
    margin: 0 auto 0 auto;

    display: flex;

    overflow: auto; /* Добавление scrollbar */
    scrollbar-color: black white; /* цвет (полоса/фон) scrollbar */
}
```

<img src="https://github.com/TeachKait20/NoneCode/blob/main/display+html/scroll-animals.gif?raw=true">
