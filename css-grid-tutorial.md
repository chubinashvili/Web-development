# CSS Grid სახელმძღვანელო 📐

## შესავალი <!-- რა არის CSS Grid? -->
CSS Grid არის ორგანზომილებიანი layout სისტემა, რომელიც საშუალებას გვაძლევს შევქმნათ რთული და რესპონსიული დიზაინები. განსხვავებით Flexbox-ისგან, Grid მუშაობს ორივე მიმართულებით - როგორც ჰორიზონტალურად, ასევე ვერტიკალურად.

## ძირითადი კონცეფციები <!-- მნიშვნელოვანი ტერმინები -->

### Grid Container და Grid Items
```css
/* Grid კონტეინერი - მშობელი ელემენტი */
.container {
  display: grid; /* ან display: inline-grid */
}

/* Grid Items - შვილობილი ელემენტები */
/* ყველა პირდაპირი შვილი ავტომატურად ხდება grid item */
```

## Grid-ის შექმნა <!-- როგორ დავიწყოთ -->

### სვეტების და სტრიქონების განსაზღვრა
```css
.grid-container {
  display: grid;
  
  /* სვეტების განსაზღვრა */
  grid-template-columns: 200px 200px 200px; /* 3 ფიქსირებული სვეტი */
  
  /* სტრიქონების განსაზღვრა */
  grid-template-rows: 100px 100px; /* 2 ფიქსირებული სტრიქონი */
  
  /* დაშორება ელემენტებს შორის */
  gap: 20px; /* ან grid-gap ძველ ბრაუზერებში */
}
```

## fr ერთეული <!-- ფრაქციული ერთეული -->
```css
.grid-container {
  display: grid;
  /* fr (fraction) - თავისუფალი სივრცის პროპორციული განაწილება */
  grid-template-columns: 1fr 2fr 1fr; /* შუა სვეტი ორჯერ უფრო დიდია */
  grid-template-rows: 1fr 1fr; /* თანაბარი სიმაღლის სტრიქონები */
}
```

## repeat() ფუნქცია <!-- გამეორება -->
```css
.grid-container {
  display: grid;
  /* იგივე ზომის სვეტების გამეორება */
  grid-template-columns: repeat(3, 200px); /* 3 სვეტი 200px-ით */
  grid-template-columns: repeat(4, 1fr); /* 4 თანაბარი სვეტი */
  
  /* კომბინირებული მაგალითი */
  grid-template-columns: 200px repeat(3, 1fr) 200px;
}
```

## Grid Lines და Positioning <!-- ხაზები და პოზიციონირება -->

### Grid Lines
```css
/* Grid lines იწყება 1-დან (არა 0-დან!) */
/* 3 სვეტიანი grid-ს აქვს 4 ვერტიკალური ხაზი (1, 2, 3, 4) */
/* 2 სტრიქონიანი grid-ს აქვს 3 ჰორიზონტალური ხაზი (1, 2, 3) */

.item {
  /* ელემენტის განთავსება კონკრეტულ პოზიციაზე */
  grid-column-start: 1; /* დაწყება პირველი ვერტიკალური ხაზიდან */
  grid-column-end: 3;   /* დასრულება მესამე ხაზზე */
  
  /* შემოკლებული ჩანაწერი */
  grid-column: 1 / 3; /* იგივე რაც ზემოთ */
  grid-row: 1 / 2;    /* პირველი სტრიქონი */
}
```

### Span კლავიატურა <!-- რამდენი უჯრის დაკავება -->
```css
.item {
  /* span გვეუბნება რამდენი უჯრა დაიკავოს */
  grid-column: span 2; /* დაიკავე 2 სვეტი */
  grid-row: span 3;    /* დაიკავე 3 სტრიქონი */
  
  /* ან კონკრეტული პოზიციიდან */
  grid-column: 2 / span 2; /* მე-2 ხაზიდან დაიწყე და 2 სვეტი დაიკავე */
}
```

## Grid Template Areas <!-- სახელდებული არეები -->
```css
/* ვიზუალური და ინტუიციური განლაგება */
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto 1fr auto;
  gap: 10px;
  
  /* არეების განსაზღვრა */
  grid-template-areas:
    "header header header"  /* თავსართი მთელ სიგანეზე */
    "sidebar main main"     /* გვერდითა პანელი და მთავარი კონტენტი */
    "footer footer footer";  /* ქვედა კოლონტიტული მთელ სიგანეზე */
}

/* ელემენტების მინიჭება არეებზე */
.header {
  grid-area: header; /* მიანიჭე header არეას */
}

.sidebar {
  grid-area: sidebar; /* მიანიჭე sidebar არეას */
}

.main {
  grid-area: main; /* მიანიჭე main არეას */
}

.footer {
  grid-area: footer; /* მიანიჭე footer არეას */
}
```

## Auto-Fill და Auto-Fit <!-- ავტომატური შევსება -->
```css
.container {
  display: grid;
  
  /* auto-fill - ცარიელი სვეტებიც რჩება */
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  
  /* auto-fit - ცარიელი სვეტები იშლება და კონტენტი ფართოვდება */
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

## Alignment <!-- გასწორება -->

### justify-items და align-items <!-- ელემენტების გასწორება უჯრაში -->
```css
.container {
  display: grid;
  
  /* ჰორიზონტალური გასწორება უჯრაში */
  justify-items: start;   /* მარცხნივ */
  justify-items: end;     /* მარჯვნივ */
  justify-items: center;  /* ცენტრში */
  justify-items: stretch; /* გაჭიმვა (default) */
  
  /* ვერტიკალური გასწორება უჯრაში */
  align-items: start;     /* ზემოთ */
  align-items: end;       /* ქვემოთ */
  align-items: center;    /* ცენტრში */
  align-items: stretch;   /* გაჭიმვა (default) */
  
  /* ორივე ერთად */
  place-items: center center; /* ან უბრალოდ: center */
}
```

### justify-content და align-content <!-- მთელი grid-ის გასწორება -->
```css
.container {
  display: grid;
  height: 500px; /* საჭიროა თავისუფალი სივრცე */
  
  /* მთელი grid-ის ჰორიზონტალური გასწორება */
  justify-content: start;        /* მარცხნივ */
  justify-content: end;          /* მარჯვნივ */
  justify-content: center;       /* ცენტრში */
  justify-content: space-between; /* თანაბარი დაშორება */
  justify-content: space-around;  /* თანაბარი მინდვრები */
  justify-content: space-evenly;  /* სრულიად თანაბარი */
  
  /* მთელი grid-ის ვერტიკალური გასწორება */
  align-content: start;   /* ზემოთ */
  align-content: end;     /* ქვემოთ */
  align-content: center;  /* ცენტრში */
  
  /* ორივე ერთად */
  place-content: center center;
}
```

### ინდივიდუალური ელემენტის გასწორება <!-- self properties -->
```css
.item {
  /* კონკრეტული ელემენტის გასწორება */
  justify-self: start;  /* ჰორიზონტალურად */
  align-self: end;      /* ვერტიკალურად */
  
  /* ან ორივე ერთად */
  place-self: center center;
}
```

## პრაქტიკული მაგალითები <!-- რეალური გამოყენება -->

### რესპონსიული ბარათების განლაგება
```css
/* ბარათების კონტეინერი */
.card-grid {
  display: grid;
  /* რესპონსიული სვეტები - მინიმუმ 250px, მაქსიმუმ 1fr */
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px;
}

/* თითოეული ბარათი */
.card {
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

### Holy Grail Layout <!-- კლასიკური განლაგება -->
```css
.page-layout {
  display: grid;
  min-height: 100vh;
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header header"
    "nav    main   aside"
    "footer footer footer";
  gap: 10px;
}

/* რესპონსიული ვერსია */
@media (max-width: 768px) {
  .page-layout {
    grid-template-columns: 1fr;
    grid-template-areas:
      "header"
      "nav"
      "main"
      "aside"
      "footer";
  }
}
```

### ფოტო გალერეა <!-- მასონრის სტილი -->
```css
.photo-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 200px; /* ავტომატური სტრიქონების სიმაღლე */
  grid-auto-flow: dense; /* ცარიელი ადგილების შევსება */
  gap: 10px;
}

/* დიდი ფოტოები */
.photo-large {
  grid-column: span 2;
  grid-row: span 2;
}

/* ვერტიკალური ფოტოები */
.photo-tall {
  grid-row: span 2;
}

/* ჰორიზონტალური ფოტოები */
.photo-wide {
  grid-column: span 2;
}
```

### Dashboard Layout <!-- საკონტროლო პანელი -->
```css
.dashboard {
  display: grid;
  grid-template-columns: 250px 1fr;
  grid-template-rows: 60px 1fr;
  grid-template-areas:
    "sidebar header"
    "sidebar content";
  height: 100vh;
}

.sidebar {
  grid-area: sidebar;
  background: #2c3e50;
  color: white;
}

.header {
  grid-area: header;
  background: white;
  border-bottom: 1px solid #e0e0e0;
  padding: 0 20px;
}

.content {
  grid-area: content;
  padding: 20px;
  overflow-y: auto;
  
  /* კონტენტის შიგნით კიდევ ერთი grid */
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

## Grid vs Flexbox <!-- როდის რომელი გამოვიყენოთ -->

### გამოიყენე Grid როცა:
- გჭირდება ორგანზომილებიანი განლაგება (სვეტები და სტრიქონები)
- გინდა ზუსტი კონტროლი ელემენტების პოზიციაზე
- აკეთებ რთულ განლაგებებს (dashboards, magazines)
- გჭირდება overlap ელემენტების

### გამოიყენე Flexbox როცა:
- მუშაობ ერთ მიმართულებაში (ან ჰორიზონტალურად ან ვერტიკალურად)
- გჭირდება ელემენტების დინამიური გასწორება
- აკეთებ navigation bars, buttons groups
- გინდა ელემენტებმა კონტენტის მიხედვით დაიკავონ ადგილი

## Browser Support <!-- ბრაუზერების მხარდაჭერა -->
- ყველა თანამედროვე ბრაუზერი მხარს უჭერს CSS Grid-ს
- IE 11 ნაწილობრივ მხარს უჭერს `-ms-` პრეფიქსით
- მობილურ ბრაუზერებში შესანიშნავად მუშაობს

## რჩევები და ტრიუკები <!-- საუკეთესო პრაქტიკები -->

### 1. Firefox DevTools
Firefox-ს აქვს საუკეთესო Grid Inspector - გამოიყენე დებაგინგისთვის!

### 2. Grid და Flexbox კომბინაცია
```css
/* Grid განლაგებისთვის, Flexbox ელემენტების შიგნით */
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.grid-item {
  display: flex; /* ელემენტის შიგნით flexbox */
  align-items: center;
  justify-content: center;
}
```

### 3. Named Lines <!-- დასახელებული ხაზები -->
```css
.container {
  display: grid;
  grid-template-columns: 
    [sidebar-start] 250px 
    [sidebar-end main-start] 1fr 
    [main-end];
}

.sidebar {
  grid-column: sidebar-start / sidebar-end;
}
```

### 4. Minmax() ფუნქცია <!-- მინიმალური და მაქსიმალური ზომები -->
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, minmax(200px, 1fr));
  /* მინიმუმ 200px, მაქსიმუმ 1fr */
}
```

### 5. Grid-auto-flow <!-- ავტომატური განთავსების კონტროლი -->
```css
.container {
  display: grid;
  grid-auto-flow: row;    /* default - სტრიქონებით შევსება */
  grid-auto-flow: column; /* სვეტებით შევსება */
  grid-auto-flow: dense;  /* ცარიელი ადგილების შევსება */
}
```

## დავალებები სტუდენტებისთვის <!-- სავარჯიშოები -->

### დავალება 1: პირადი პორტფოლიო
შექმენით პორტფოლიოს განლაგება Grid-ით:
- Header სრული სიგანით
- 3 სვეტიანი პროექტების სექცია
- Footer სრული სიგანით
- რესპონსიული მობილურისთვის

### დავალება 2: Instagram-ის ტიპის გალერეა
შექმენით ფოტო გალერეა:
- 3x3 grid desktop-ზე
- 2x2 grid tablet-ზე
- 1 სვეტი მობილურზე
- Hover ეფექტები

### დავალება 3: Dashboard
შექმენით admin panel-ის განლაგება:
- Fixed sidebar
- Scrollable content area
- Statistics cards grid-ში
- Responsive design

## დამატებითი რესურსები <!-- სასარგებლო ბმულები -->
- [CSS Grid Garden](https://cssgridgarden.com/) - ინტერაქტიული თამაში
- [Grid by Example](https://gridbyexample.com/) - პრაქტიკული მაგალითები
- [MDN CSS Grid Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) - სრული დოკუმენტაცია
- [CSS-Tricks Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/) - ვიზუალური გზამკვლევი

---

**შენიშვნა:** ეს მასალა მუდმივად განახლდება. თუ გაქვთ შეკითხვები, დამიკავშირდით! 🚀

**ავტორი:** თქვენი სახელი  
**განახლებული:** 2025