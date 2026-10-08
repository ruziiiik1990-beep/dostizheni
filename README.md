<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Достижения</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
 body {
   margin: 0;
   background: transparent;
   font-family: 'Inter', sans-serif;
 }

 /* === Achievements Section === */
 .ach-section {
   padding: 20px 24px;
   border-top: 1px solid rgba(255,255,255,0.08);
 }
 .ach-header {
   display: flex;
   align-items: center;
   gap: 8px;
   font-size: 16px;
   font-weight: 600;
   color: #e0e6f0;
   margin-bottom: 16px;
 }
 .ach-header .material-symbols-outlined {
   font-size: 22px;
   color: #66c0f4;
 }
 .ach-grid {
   display: flex;
   flex-wrap: wrap;
   gap: 12px;
 }
 .ach-item {
   position: relative;
   cursor: pointer;
   transition: transform 0.2s ease;
 }
 .ach-item:hover {
   transform: scale(1.08);
 }
 .ach-item img {
   width: 70px;
   height: 70px;
   object-fit: cover;
   border-radius: 10px;
   border: 2px solid rgba(255,255,255,0.15);
   display: block;
 }
 .ach-delete-btn {
   position: absolute;
   top: -4px;
   right: -4px;
   width: 18px;
   height: 18px;
   border-radius: 50%;
   background: #dc2626;
   color: #fff;
   border: none;
   font-size: 12px;
   line-height: 18px;
   text-align: center;
   cursor: pointer;
   display: none;
   z-index: 10;
   padding: 0;
 }
 .ach-item:hover .ach-delete-btn {
   display: block;
 }
 .ach-tooltip {
   position: absolute;
   bottom: calc(100% + 12px);
   left: 50%;
   transform: translateX(-50%) translateY(8px) scale(0.8);
   opacity: 0;
   background: #1a1a2e;
   color: #fff;
   padding: 12px 16px;
   border-radius: 12px;
   font-size: 13px;
   line-height: 1.5;
   max-width: 260px;
   min-width: 160px;
   box-shadow: 0 6px 20px rgba(0,0,0,0.6);
   pointer-events: none;
   z-index: 100;
   transition: all 0.35s cubic-bezier(0.175, 0.885, 0.32, 1.275);
   white-space: normal;
   text-align: center;
 }
 .ach-tooltip::after {
   content: '';
   position: absolute;
   top: 100%;
   left: 50%;
   transform: translateX(-50%);
   border: 7px solid transparent;
   border-top-color: #1a1a2e;
 }
 .ach-item.active .ach-tooltip {
   transform: translateX(-50%) translateY(0) scale(1);
   opacity: 1;
 }
 .ach-tooltip .ach-title {
   display: block;
   font-weight: 700;
   color: #66c0f4;
   margin-bottom: 4px;
   font-size: 14px;
 }
 .ach-empty {
   color: #6b7280;
   font-size: 13px;
   font-style: italic;
 }

 /* === Admin Panel === */
 .ach-admin-btn {
   display: inline-flex;
   align-items: center;
   gap: 6px;
   margin-top: 16px;
   padding: 8px 16px;
   background: rgba(102,192,244,0.1);
   border: 1px solid rgba(102,192,244,0.3);
   color: #66c0f4;
   border-radius: 8px;
   cursor: pointer;
   font-size: 13px;
   font-weight: 500;
   font-family: 'Inter', sans-serif;
   transition: all 0.2s;
 }
 .ach-admin-btn:hover {
   background: rgba(102,192,244,0.2);
 }
 .ach-admin-panel {
   display: none;
   margin-top: 16px;
   padding: 16px;
   background: rgba(0,0,0,0.3);
   border-radius: 12px;
   border: 1px dashed rgba(102,192,244,0.25);
 }
 .ach-admin-panel.visible {
   display: block;
 }
 .ach-admin-panel h4 {
   margin: 0 0 12px 0;
   color: #e0e6f0;
   font-size: 14px;
 }
 .ach-img-picker {
   display: flex;
   flex-wrap: wrap;
   gap: 8px;
   margin-bottom: 12px;
 }
 .ach-img-option {
   width: 56px;
   height: 56px;
   border-radius: 8px;
   border: 3px solid transparent;
   cursor: pointer;
   object-fit: cover;
   transition: all 0.2s;
 }
 .ach-img-option:hover {
   border-color: rgba(102,192,244,0.5);
   transform: scale(1.1);
 }
 .ach-img-option.selected {
   border-color: #66c0f4;
   box-shadow: 0 0 12px rgba(102,192,244,0.4);
 }
 .ach-admin-input {
   width: 100%;
   box-sizing: border-box;
   padding: 8px 12px;
   margin-bottom: 10px;
   border-radius: 8px;
   border: 1px solid rgba(255,255,255,0.12);
   background: rgba(0,0,0,0.3);
   color: #e0e6f0;
   font-size: 13px;
   font-family: 'Inter', sans-serif;
   outline: none;
 }
 .ach-admin-input:focus {
   border-color: #66c0f4;
 }
 .ach-admin-input::placeholder {
   color: #5a6378;
 }
 .ach-add-btn {
   padding: 10px 20px;
   border-radius: 8px;
   border: none;
   background: linear-gradient(135deg, #1b2838, #2a475e);
   color: #c7d0e0;
   font-size: 13px;
   font-weight: 600;
   cursor: pointer;
   font-family: 'Inter', sans-serif;
   transition: all 0.2s;
 }
 .ach-add-btn:hover {
   background: linear-gradient(135deg, #2a475e, #66c0f4);
   color: #fff;
 }
</style>
</head>
<body>

<!-- === ACHIEVEMENTS SECTION === -->
<div class="ach-section">
  <div class="ach-header">
    <span class="material-symbols-outlined">military_tech</span>
    Достижения
  </div>
  <div class="ach-grid" id="achGrid">
    <div class="ach-empty" id="achEmpty">Достижений пока нет</div>
  </div>
  <!-- Admin button shown only if admin=1 in URL -->
  <div id="achAdminWrap" style="display:none;">
    <button class="ach-admin-btn" onclick="achToggleAdmin()">
      <span class="material-symbols-outlined" style="font-size:16px;">add_circle</span>
      Добавить достижение
    </button>
    <div class="ach-admin-panel" id="achAdminPanel">
      <h4>Выберите картинку достижения:</h4>
      <div class="ach-img-picker" id="achImgPicker">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_2-fotor-bg-remover-20260926224846.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_2-fotor-bg-remover-20260926224846.png')" alt="Достижение 1">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_8-fotor-bg-remover-20260926224924.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_8-fotor-bg-remover-20260926224924.png')" alt="Достижение 2">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_4-fotor-bg-remover-2026092622505.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_4-fotor-bg-remover-2026092622505.png')" alt="Достижение 3">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/2de846dbc4a11f1ac4d768cfd41a853_1.jpeg" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/2de846dbc4a11f1ac4d768cfd41a853_1.jpeg')" alt="Достижение 4">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_4-fotor-bg-remover-20260926223859.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_4-fotor-bg-remover-20260926223859.png')" alt="Достижение 5">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_9-fotor-bg-remover-2026092615118.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_9-fotor-bg-remover-2026092615118.png')" alt="Достижение 6">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_7-fotor-bg-remover-2026092615157.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_7-fotor-bg-remover-2026092615157.png')" alt="Достижение 7">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_15-fotor-bg-remover-202609304119.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_15-fotor-bg-remover-202609304119.png')" alt="Достижение 8">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/osen-fotor-bg-remover-2026092603655.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/osen-fotor-bg-remover-2026092603655.png')" alt="Достижение 9">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_3-fotor-bg-remover-2026092622425.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_3-fotor-bg-remover-2026092622425.png')" alt="Достижение 10">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_7-fotor-bg-remover-20260926224621.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_7-fotor-bg-remover-20260926224621.png')" alt="Достижение 11">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/1_kusok_chak_chak-fotor-bg-remover-20260929235845.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/1_kusok_chak_chak-fotor-bg-remover-20260929235845.png')" alt="Достижение 12">
        <img class="ach-img-option" src="https://4ak4ak.moy.su/dostizhenia/Screenshot_1.png" onclick="achSelectImg(this, 'https://4ak4ak.moy.su/dostizhenia/Screenshot_1.png')" alt="Достижение 13">
      </div>
      <input type="hidden" id="achSelectedImg" value="">
      <input type="text" class="ach-admin-input" id="achTitle" placeholder="Название достижения (например: Легенда)">
      <input type="text" class="ach-admin-input" id="achDesc" placeholder="За что выдано (например: За 1000 часов в игре)">
      <button class="ach-add-btn" onclick="achAdd()">Добавить достижение</button>
      <button class="ach-admin-btn" style="margin-left:8px;" onclick="achToggleAdmin()">Отмена</button>
    </div>
  </div>
</div>
<!-- === END ACHIEVEMENTS SECTION === -->

<!-- === ACHIEVEMENTS SCRIPT === -->
<script type="module">
import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js';
import { getDatabase, ref, onValue, set, push, remove } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js';

// --- Config ---
const firebaseConfig = {
  databaseURL: 'https://ak4ak-d948e-default-rtdb.firebaseio.com/'
};

const app = initializeApp(firebaseConfig);
const db = getDatabase(app);

// --- Get uid and admin from URL ---
const params = new URLSearchParams(window.location.search);
const profileUserId = params.get('uid') || 'unknown';
const isAdmin = params.get('admin') === '1';
var selectedImgUrl = '';

// Show admin panel if admin=1
if (isAdmin) {
  document.getElementById('achAdminWrap').style.display = 'block';
}

// --- Real-time listener on Firebase ---
const achRef = ref(db, 'achievements/' + profileUserId);

onValue(achRef, function(snapshot) {
  var data = [];
  if (snapshot.exists()) {
    var val = snapshot.val();
    // Data stored as object with push keys: { "-Nxabc": { img, title, desc }, ... }
    Object.keys(val).forEach(function(key) {
      data.push({ ...val[key], _key: key });
    });
  }
  achRender(data);
});

function achRender(data) {
  var grid = document.getElementById('achGrid');
  var empty = document.getElementById('achEmpty');
  if (!data || data.length === 0) {
    if (empty) empty.style.display = 'block';
    grid.querySelectorAll('.ach-item').forEach(function(el) { el.remove(); });
    return;
  }
  if (empty) empty.style.display = 'none';
  grid.querySelectorAll('.ach-item').forEach(function(el) { el.remove(); });
  data.forEach(function(item) {
    var div = document.createElement('div');
    div.className = 'ach-item';
    div.onclick = function() { achToggleTooltip(this); };
    var deleteBtn = '';
    if (isAdmin) {
      deleteBtn = '<button class="ach-delete-btn" onclick="achDelete(\'' + item._key + '\'); event.stopPropagation();" title="Удалить">&times;</button>';
    }
    div.innerHTML = '<img src="' + item.img + '" alt="' + item.title + '">' +
      deleteBtn +
      '<div class="ach-tooltip">' +
      '<span class="ach-title">' + item.title + '</span>' +
      (item.desc || '') +
      '</div>';
    grid.appendChild(div);
  });
}

// --- Global functions ---
window.achToggleTooltip = function(el) {
  document.querySelectorAll('.ach-item').forEach(function(item) {
    if (item !== el) item.classList.remove('active');
  });
  el.classList.toggle('active');
};

window.achToggleAdmin = function() {
  var panel = document.getElementById('achAdminPanel');
  panel.classList.toggle('visible');
};

window.achSelectImg = function(el, url) {
  selectedImgUrl = url;
  document.querySelectorAll('.ach-img-option').forEach(function(opt) {
    opt.classList.remove('selected');
  });
  el.classList.add('selected');
  document.getElementById('achSelectedImg').value = url;
};

window.achAdd = function() {
  var img = document.getElementById('achSelectedImg').value;
  var title = document.getElementById('achTitle').value.trim();
  var desc = document.getElementById('achDesc').value.trim();
  if (!img) { alert('Выберите картинку достижения!'); return; }
  if (!title) { alert('Введите название достижения!'); return; }

  // Push to Firebase
  var newItemRef = push(achRef);
  set(newItemRef, {
    img: img,
    title: title,
    desc: desc,
    createdAt: Date.now()
  });

  // Reset form
  document.getElementById('achTitle').value = '';
  document.getElementById('achDesc').value = '';
  document.getElementById('achSelectedImg').value = '';
  selectedImgUrl = '';
  document.querySelectorAll('.ach-img-option').forEach(function(opt) {
    opt.classList.remove('selected');
  });
  document.getElementById('achAdminPanel').classList.remove('visible');
};

window.achDelete = function(key) {
  if (!confirm('Удалить это достижение?')) return;
  remove(ref(db, 'achievements/' + profileUserId + '/' + key));
};

// Close tooltip on outside click
document.addEventListener('click', function(e) {
  if (!e.target.closest('.ach-item')) {
    document.querySelectorAll('.ach-item').forEach(function(item) {
      item.classList.remove('active');
    });
  }
});
</script>
<!-- === END ACHIEVEMENTS SCRIPT === -->

</body>
</html>
