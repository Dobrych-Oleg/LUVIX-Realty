# LUVIX-Realty
<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LUVIX Realty — Житло та бізнес</title>
<style>
:root {
  --primary-color: #0D1B2A;
  --accent-color: #FFD700;
  --text-color: #FFFFFF;
  --bg-color: #F5F5F5;
}
body { margin:0; font-family: 'Montserrat', sans-serif; background-color: var(--bg-color); color: var(--primary-color);}
header{background-color: var(--primary-color); color: var(--text-color); display:flex; justify-content:space-between; align-items:center; padding:15px 50px; position:sticky; top:0; z-index:1000;}
header img{height:200px;}
nav ul{list-style:none; display:flex; gap:30px; margin:0; padding:0;}
nav ul li{position:relative;}
nav ul li a{color: var(--text-color); text-decoration:none; font-weight:600; padding:5px 0; cursor:pointer;}
nav ul li ul{display:none; position:absolute; background-color: var(--primary-color); list-style:none; padding:10px 0; margin:0; top:35px; min-width:180px;}
nav ul li:hover > ul{display:block;}
nav ul li ul li{padding:5px 20px; position:relative;}
nav ul li ul li ul{top:0; left:180px;}
.hero{background-color: var(--primary-color); color: var(--text-color); text-align:center; padding:100px 20px;}
.hero h1{font-size:48px;margin-bottom:20px;}
.hero p{font-size:24px;}
section{padding:60px 50px;}
section h2{color: var(--primary-color); margin-bottom:30px; border-bottom:2px solid var(--accent-color); display:inline-block; padding-bottom:5px;}
.card-container{display:flex; flex-wrap:wrap; gap:30px;}
.card{background-color:#fff; border:1px solid #ddd; border-radius:10px; width:calc(33.333% - 20px); box-shadow:0 4px 10px rgba(0,0,0,0.1); overflow:hidden; transition:transform 0.3s;}
.card img{width:100%; height:200px; object-fit:cover;}
.card h3{margin:15px;color: var(--primary-color);}
.card p{margin:0 15px 15px 15px;}
.card:hover{transform:translateY(-5px);}
footer{background-color: var(--primary-color); color: var(--text-color); text-align:center; padding:20px;}
@media(max-width:1024px){.card{width:calc(50% - 20px);}}
@media(max-width:600px){header{flex-direction:column; gap:10px;} nav ul{flex-direction:column; gap:10px;} .card{width:100%;}}

/* Стиль адмін-панелі */
#admin-panel{background:#fff; border:1px solid #ddd; padding:20px; margin-bottom:50px; border-radius:10px; box-shadow:0 4px 10px rgba(0,0,0,0.1);}
#admin-panel h2{color: var(--primary-color);}
#admin-panel label{display:block; margin:10px 0 5px;}
#admin-panel input, #admin-panel select, #admin-panel textarea{width:100%; padding:8px; border:1px solid #ccc; border-radius:5px;}
#admin-panel button{background-color: var(--accent-color); color:#0D1B2A; padding:10px 20px; border:none; border-radius:5px; cursor:pointer; margin-top:10px;}
#admin-panel button:hover{opacity:0.9;}
</style>
</head>
<body>

<header>
<img src="LUVIX-logo.png" alt="LUVIX Realty">
<nav>
<ul>
<li><a>Оренда</a>
  <ul>
    <li><a>Житло</a>
      <ul>
        <li><a data-section="rent-apartments">Квартири</a></li>
        <li><a data-section="rent-houses">Будинки</a></li>
      </ul>
    </li>
    <li><a>Комерційна нерухомість</a>
      <ul>
        <li><a data-section="rent-office">Офіс</a></li>
        <li><a data-section="rent-shop">Магазин</a></li>
        <li><a data-section="rent-warehouse">Склад</a></li>
      </ul>
    </li>
  </ul>
</li>
<li><a>Продаж</a>
  <ul>
    <li><a>Житло</a>
      <ul>
        <li><a data-section="sale-apartments">Квартири</a></li>
        <li><a data-section="sale-houses">Будинки</a></li>
      </ul>
    </li>
    <li><a>Комерційна нерухомість</a>
      <ul>
        <li><a data-section="sale-office">Офіс</a></li>
        <li><a data-section="sale-shop">Магазин</a></li>
        <li><a data-section="sale-warehouse">Склад</a></li>
      </ul>
    </li>
  </ul>
</li>
<li><a href="#about">Про компанію</a></li>
<li><a href="#contacts">Контакти</a></li>
</ul>
</nav>
</header>

<div class="hero">
<h1>LUVIX Realty</h1>
<p>Житло та бізнес преміум-класу в Києві</p>
</div>

<section id="admin-panel">
<h2>Адмін-панель: Додати об’єкт нерухомості</h2>
<label>Підрозділ:</label>
<select id="property-section">
  <option value="rent-apartments">Оренда - Квартири</option>
  <option value="rent-houses">Оренда - Будинки</option>
  <option value="rent-office">Оренда - Офіс</option>
  <option value="rent-shop">Оренда - Магазин</option>
  <option value="rent-warehouse">Оренда - Склад</option>
  <option value="sale-apartments">Продаж - Квартири</option>
  <option value="sale-houses">Продаж - Будинки</option>
  <option value="sale-office">Продаж - Офіс</option>
  <option value="sale-shop">Продаж - Магазин</option>
  <option value="sale-warehouse">Продаж - Склад</option>
</select>
<label>Назва об’єкта:</label>
<input type="text" id="property-title" placeholder="Введіть назву">
<label>Фото (URL):</label>
<input type="text" id="property-img" placeholder="Введіть URL фото">
<label>Опис:</label>
<textarea id="property-desc" placeholder="Введіть опис"></textarea>
<button onclick="addProperty()">Додати об’єкт</button>
</section>

<section id="properties">
<h2>Об’єкти нерухомості</h2>
<div id="property-cards" class="card-container"></div>
</section>

<section id="about">
<h2>Про компанію</h2>
<p>LUVIX Realty — агентство преміум-класу в Києві, що спеціалізується на житловій та комерційній нерухомості для оренди та продажу. Ми забезпечуємо професійний сервіс та індивідуальний підхід до кожного клієнта.</p>
</section>

<section id="contacts">
<h2>Контакти</h2>
<p>Адреса: Київ, Україна</p>
<p>Телефон: +380 XX XXX XX XX</p>
<p>Email: info@luvixrealty.ua</p>
</section>

<footer>
&copy; 2026 LUVIX Realty — Житло та бізнес
</footer>

<script>
let properties = [
  {section: 'rent-apartments', title: 'Квартира в центрі', img: 'apartment.jpg', desc: 'Сучасна квартира з ремонтом.'},
  {section: 'rent-houses', title: 'Будинок під Києвом', img: 'house.jpg', desc: 'Приватний будинок з садом.'}
];

const container = document.getElementById('property-cards');

function displayProperties(filter = null) {
  container.innerHTML = '';
  const filtered = filter ? properties.filter(p => p.section === filter) : properties;
  filtered.forEach(p => {
    const card = document.createElement('div');
    card.className = 'card';
    card.innerHTML = `<img src="${p.img}" alt="${p.title}">
                      <h3>${p.title}</h3>
                      <p>${p.desc}</p>`;
    container.appendChild(card);
  });
}

displayProperties();

document.querySelectorAll('a[data-section]').forEach(a => {
  a.addEventListener('click', () => {
    displayProperties(a.getAttribute('data-section'));
    window.scrollTo({top: container.offsetTop - 100, behavior: 'smooth'});
  });
});

// Додавання об’єкта через адмін-панель
function addProperty() {
  const section = document.getElementById('property-section').value;
  const title = document.getElementById('property-title').value.trim();
  const img = document.getElementById('property-img').value.trim();
  const desc = document.getElementById('property-desc').value.trim();

  if(title && img && desc) {
    properties.push({section, title, img, desc});
    displayProperties(section);

    // Очистка форми
    document.getElementById('property-title').value = '';
    document.getElementById('property-img').value = '';
    document.getElementById('property-desc').value = '';
    alert('Об’єкт додано!');
  } else {
    alert('Будь ласка, заповніть усі поля.');
  }
}
</script>

</body>
</html>
