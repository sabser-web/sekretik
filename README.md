<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Личный сайт</title>
<style>
  body {
    margin: 0;
    display: flex;
    font-family: Arial, sans-serif;
    background-color: white;
    height: 100vh;
  }
  .sidebar {
    width: 25%;
    background-color: #2ecc71; /* зелёное меню */
    padding: 20px;
    box-sizing: border-box;
  }
  .sidebar button {
    display: block;
    width: 100%;
    margin-bottom: 10px;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    background: white;
    border: none;
    border-radius: 5px;
  }
  .content {
    width: 75%;
    padding: 20px;
    box-sizing: border-box;
    overflow-y: auto;
    height: 100vh;
  }
  .section {
    display: none;
  }
  .section.active {
    display: block;
  }
  .item {
    margin-bottom: 10px;
  }
  .item img {
    max-width: 100%;
    display: block;
    margin-bottom: 5px;
  }
  .add-btn {
    margin-bottom: 10px;
    padding: 5px 10px;
  }
</style>
</head>
<body>

<div class="sidebar">
  <button onclick="showSection('colors')">Цвета</button>
  <button onclick="showSection('other')">.</button>
</div>

<div class="content">
  <!-- Раздел Цвета -->
  <div id="colors" class="section active">
    <button class="add-btn" onclick="addItem('colors')">Создать</button>
    <div class="items"></div>
  </div>
  <!-- Раздел "." -->
  <div id="other" class="section">
    <button class="add-btn" onclick="addItem('other')">Создать</button>
    <div class="items"></div>
  </div>
</div>

<script>
let password = prompt("Введите пароль для редактирования:");
let editAllowed = password === "мойпароль"; // поменяй на свой пароль

function showSection(id) {
  document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function addItem(sectionId) {
  if(!editAllowed){
    alert("Только автор может добавлять контент!");
    return;
  }
  const text = prompt("Введите текст:");
  const img = prompt("Вставьте ссылку на изображение или оставьте пусто:");
  const section = document.getElementById(sectionId).querySelector('.items');

  const div = document.createElement('div');
  div.className = 'item';

  if(img) {
    const image = document.createElement('img');
    image.src = img;
    div.appendChild(image);
  }

  if(text) {
    const p = document.createElement('p');
    p.textContent = text;
    div.appendChild(p);
  }

  section.appendChild(div);
}
</script>

</body>
</html>
