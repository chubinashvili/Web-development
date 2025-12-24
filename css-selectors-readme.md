# CSS Selectors - სელექტორების სახელმძღვანელო

## შესავალი | Introduction

CSS სელექტორები არის შაბლონები, რომლებიც გამოიყენება HTML ელემენტების არჩევისთვის სტილების მისანიჭებლად.

```css
/* ძირითადი სინტაქსი */
selector {
    property: value;
}
```

## ძირითადი სელექტორები | Basic Selectors

### 1. Universal Selector - უნივერსალური სელექტორი (*)

```css
/* ყველა ელემენტს მიენიჭება სტილი */
* {
    margin: 0;
    padding: 0;
}
```

### 2. Type Selector - ტიპის სელექტორი

```css
/* ყველა <p> ელემენტს მიენიჭება სტილი */
p {
    color: blue;
}

/* ყველა <h1> ელემენტს მიენიჭება სტილი */
h1 {
    font-size: 32px;
}
```

### 3. Class Selector - კლასის სელექტორი (.)

```css
/* ყველა ელემენტს class="highlight" ატრიბუტით */
.highlight {
    background-color: yellow;
}

/* კონკრეტული ელემენტი კლასით */
p.warning {
    color: red;
}
```

```html
<!-- HTML მაგალითი -->
<p class="highlight">ეს ტექსტი გამოირჩევა</p>
<p class="warning">გაფრთხილება!</p>
```

### 4. ID Selector - ID სელექტორი (#)

```css
/* ელემენტს id="header" ატრიბუტით */
#header {
    background-color: navy;
}

/* ID უნიკალური უნდა იყოს გვერდზე */
#main-title {
    font-weight: bold;
}
```

```html
<!-- HTML მაგალითი -->
<div id="header">საიტის ჰედერი</div>
<h1 id="main-title">მთავარი სათაური</h1>
```

## კომბინირებული სელექტორები | Combinator Selectors

### 1. Descendant Selector - შთამომავლის სელექტორი (space)

```css
/* div-ის შიგნით ყველა p ელემენტი */
div p {
    margin: 10px;
}

/* nav-ის შიგნით ყველა a ელემენტი */
nav a {
    text-decoration: none;
}
```

### 2. Child Selector - შვილის სელექტორი (>)

```css
/* მხოლოდ პირდაპირი შვილები */
ul > li {
    list-style: none;
}

/* div-ის პირდაპირი შვილი p ელემენტები */
div > p {
    padding: 5px;
}
```

### 3. Adjacent Sibling Selector - მეზობელი სელექტორი (+)

```css
/* h1-ის შემდეგ მყოფი პირველი p ელემენტი */
h1 + p {
    font-style: italic;
}

/* ერთი და იგივე მშობლის შვილები */
.box + .box {
    margin-top: 20px;
}
```

### 4. General Sibling Selector - ზოგადი მეზობელი (~)

```css
/* h1-ის შემდეგ ყველა p ელემენტი */
h1 ~ p {
    color: gray;
}
```

## ატრიბუტის სელექტორები | Attribute Selectors

```css
/* ელემენტები type ატრიბუტით */
input[type] {
    border: 1px solid #ccc;
}

/* კონკრეტული მნიშვნელობით */
input[type="text"] {
    padding: 5px;
}

/* ატრიბუტი იწყება მნიშვნელობით */
a[href^="https"] {
    color: green;
}

/* ატრიბუტი მთავრდება მნიშვნელობით */
a[href$=".pdf"] {
    color: red;
}

/* ატრიბუტი შეიცავს მნიშვნელობას */
a[href*="example"] {
    font-weight: bold;
}

/* ატრიბუტი შეიცავს სიტყვას */
div[class~="container"] {
    max-width: 1200px;
}

/* ატრიბუტი იწყება სიტყვით და ტირე */
div[lang|="ka"] {
    font-family: "BPG Arial", sans-serif;
}
```

## Pseudo-Classes - ფსევდო-კლასები

### 1. მდგომარეობის ფსევდო-კლასები

```css
/* მაუსის დაყენებისას */
a:hover {
    color: red;
    text-decoration: underline;
}

/* ლინკზე დაჭერისას */
a:active {
    color: orange;
}

/* ფოკუსირებული ელემენტი */
input:focus {
    border-color: blue;
    outline: none;
}

/* ნანახი ლინკი */
a:visited {
    color: purple;
}

/* არანანახი ლინკი */
a:link {
    color: blue;
}
```

### 2. სტრუქტურული ფსევდო-კლასები

```css
/* პირველი შვილი */
p:first-child {
    margin-top: 0;
}

/* ბოლო შვილი */
p:last-child {
    margin-bottom: 0;
}

/* n-ური შვილი */
li:nth-child(2) {
    color: red;
}

/* ყოველი მეორე ელემენტი */
li:nth-child(even) {
    background-color: #f0f0f0;
}

/* ყოველი კენტი ელემენტი */
li:nth-child(odd) {
    background-color: white;
}

/* ფორმულით არჩევა */
li:nth-child(3n+1) {
    font-weight: bold;
}

/* ბოლოდან n-ური */
li:nth-last-child(2) {
    color: green;
}

/* ერთადერთი შვილი */
p:only-child {
    font-size: 20px;
}

/* ტიპის პირველი ელემენტი */
p:first-of-type {
    font-weight: bold;
}

/* ტიპის ბოლო ელემენტი */
p:last-of-type {
    font-style: italic;
}
```

### 3. ფორმის ფსევდო-კლასები

```css
/* ჩართული ელემენტები */
input:enabled {
    background-color: white;
}

/* გამორთული ელემენტები */
input:disabled {
    background-color: #e0e0e0;
    cursor: not-allowed;
}

/* მონიშნული checkbox ან radio */
input:checked {
    border-color: green;
}

/* სავალდებულო ველები */
input:required {
    border-color: red;
}

/* არასავალდებულო ველები */
input:optional {
    border-color: gray;
}

/* ვალიდური მნიშვნელობით */
input:valid {
    border-color: green;
}

/* არავალიდური მნიშვნელობით */
input:invalid {
    border-color: red;
}
```

### 4. ნეგაციის ფსევდო-კლასი

```css
/* ყველა div რომელსაც არ აქვს class="container" */
div:not(.container) {
    padding: 10px;
}

/* ყველა input გარდა submit ღილაკისა */
input:not([type="submit"]) {
    width: 200px;
}
```

## Pseudo-Elements - ფსევდო-ელემენტები

```css
/* ელემენტის პირველი ხაზი */
p::first-line {
    font-weight: bold;
}

/* ელემენტის პირველი ასო */
p::first-letter {
    font-size: 2em;
    float: left;
}

/* ელემენტამდე კონტენტის დამატება */
h1::before {
    content: "📌 ";
}

/* ელემენტის შემდეგ კონტენტის დამატება */
h1::after {
    content: " ✓";
}

/* მონიშნული ტექსტი */
::selection {
    background-color: yellow;
    color: black;
}

/* Firefox-ისთვის */
::-moz-selection {
    background-color: yellow;
    color: black;
}
```

## სპეციფიურობა | Specificity

სელექტორების პრიორიტეტი (სპეციფიურობა) გამოითვლება შემდეგნაირად:

```css
/* სპეციფიურობა: 0,0,0,1 */
p {
    color: blue;
}

/* სპეციფიურობა: 0,0,1,0 */
.text {
    color: green;
}

/* სპეციფიურობა: 0,1,0,0 */
#title {
    color: red;
}

/* სპეციფიურობა: 1,0,0,0 */
/* inline სტილი HTML-ში */
<p style="color: purple;">

/* გადაწერა ნებისმიერი სპეციფიურობით */
p {
    color: orange !important;
}
```

### სპეციფიურობის გამოთვლა:

- Inline სტილი = 1000
- ID = 100
- Class, pseudo-class, attribute = 10
- Element = 1

```css
/* მაგალითები */
p                     /* 0,0,0,1 = 1 */
p.text                /* 0,0,1,1 = 11 */
#header p             /* 0,1,0,1 = 101 */
#header .menu li      /* 0,1,1,1 = 111 */
#header .menu li:hover /* 0,1,2,1 = 121 */
```

## პრაქტიკული მაგალითები | Practical Examples

### 1. ნავიგაციის მენიუ

```css
/* ძირითადი სტილი */
nav ul {
    list-style: none;
    padding: 0;
}

nav li {
    display: inline-block;
}

/* ლინკების სტილი */
nav a {
    display: block;
    padding: 10px 15px;
    text-decoration: none;
    color: #333;
}

/* ჰოვერ ეფექტი */
nav a:hover {
    background-color: #f0f0f0;
}

/* აქტიური გვერდი */
nav a.active {
    background-color: #007bff;
    color: white;
}
```

### 2. ფორმის სტილი

```css
/* ყველა input ველი */
form input[type="text"],
form input[type="email"],
form input[type="password"] {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ddd;
}

/* ფოკუსირებული ველი */
form input:focus {
    border-color: #007bff;
    box-shadow: 0 0 5px rgba(0,123,255,0.3);
}

/* ვალიდაცია */
form input:invalid {
    border-color: #dc3545;
}

form input:valid {
    border-color: #28a745;
}

/* Submit ღილაკი */
form button[type="submit"] {
    background-color: #007bff;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
}

form button[type="submit"]:hover {
    background-color: #0056b3;
}
```

### 3. ცხრილის სტილი

```css
/* ზოლებიანი ცხრილი */
table tr:nth-child(even) {
    background-color: #f2f2f2;
}

/* პირველი სვეტი bold */
table td:first-child {
    font-weight: bold;
}

/* ბოლო სვეტი მარჯვენა alignment */
table td:last-child {
    text-align: right;
}

/* Header-ის სტილი */
table th {
    background-color: #333;
    color: white;
    padding: 10px;
}
```

### 4. Card კომპონენტი

```css
/* ბარათის კონტეინერი */
.card {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
}

/* სათაური */
.card h3:first-child {
    margin-top: 0;
    color: #333;
}

/* სურათი */
.card img {
    width: 100%;
    height: auto;
}

/* ღილაკები */
.card .btn {
    display: inline-block;
    padding: 8px 16px;
    background-color: #007bff;
    color: white;
    text-decoration: none;
    border-radius: 4px;
}

.card .btn:hover {
    background-color: #0056b3;
}

/* ბოლო ბარათს არ ჭირდება margin-bottom */
.card:last-child {
    margin-bottom: 0;
}
```

## რჩევები | Tips

### 1. Performance - შესრულების ოპტიმიზაცია

```css
/* ცუდი - ძალიან ზოგადი */
* {
    margin: 0;
    padding: 0;
}

/* უკეთესი - კონკრეტული */
body, h1, h2, h3, p, ul, li {
    margin: 0;
    padding: 0;
}

/* ცუდი - ღრმა ჩადგმულობა */
body div ul li a span {
    color: blue;
}

/* უკეთესი - კლასის გამოყენება */
.menu-link {
    color: blue;
}
```

### 2. BEM მეთოდოლოგია

```css
/* Block */
.button {
    padding: 10px;
}

/* Element */
.button__icon {
    margin-right: 5px;
}

/* Modifier */
.button--primary {
    background-color: blue;
}

.button--secondary {
    background-color: gray;
}
```

### 3. მობილური პირველი დიზაინი

```css
/* მობილური (default) */
.container {
    width: 100%;
    padding: 10px;
}

/* ტაბლეტი */
@media (min-width: 768px) {
    .container {
        width: 750px;
        margin: 0 auto;
    }
}

/* დესკტოპი */
@media (min-width: 1024px) {
    .container {
        width: 1000px;
    }
}
```

## სავარჯიშოები | Exercises

### სავარჯიშო 1: აირჩიეთ სწორი ელემენტები

```html
<!-- HTML -->
<div class="container">
    <header id="main-header">
        <h1>საიტის სათაური</h1>
        <nav>
            <ul class="menu">
                <li><a href="#home" class="active">მთავარი</a></li>
                <li><a href="#about">ჩვენს შესახებ</a></li>
                <li><a href="#contact">კონტაქტი</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <article class="post">
            <h2>სტატიის სათაური</h2>
            <p class="intro">შესავალი ტექსტი</p>
            <p>ძირითადი ტექსტი</p>
        </article>
    </main>
</div>
```

დაწერეთ სელექტორები:
1. მთავარი სათაურის ასარჩევად
2. აქტიური ლინკის ასარჩევად
3. პირველი პარაგრაფის ასარჩევად article-ში
4. ყველა ლინკის ასარჩევად მენიუში

### პასუხები:

```css
/* 1. მთავარი სათაური */
#main-header h1
/* ან */
header h1

/* 2. აქტიური ლინკი */
.menu a.active
/* ან */
nav .active

/* 3. პირველი პარაგრაფი article-ში */
.post p:first-of-type
/* ან */
article p.intro

/* 4. ყველა ლინკი მენიუში */
.menu a
/* ან */
nav ul li a
```

## დამატებითი რესურსები | Additional Resources

- [MDN CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
- [CSS Tricks Selectors](https://css-tricks.com/almanac/selectors/)
- [W3Schools CSS Selectors](https://www.w3schools.com/css/css_selectors.asp)
- [CSS Selector Game](https://flukeout.github.io/) - ინტერაქტიული სავარჯიშო

## დასკვნა | Conclusion

CSS სელექტორების ცოდნა აუცილებელია ეფექტური და მოქნილი სტილების შესაქმნელად. დაიწყეთ ძირითადი სელექტორებით და თანდათან გადადით უფრო რთულ კომბინაციებზე. პრაქტიკა დაგეხმარებათ სწორი სელექტორების არჩევაში!

---

*შექმნილია მასწავლებლისთვის CSS სელექტორების ასახსნელად*  
*ვერსია: 1.0*  
*თარიღი: 2025*
