
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
 * { margin: 0; padding: 0; box-sizing: border-box; }
 body {
   font-family: 'Inter', sans-serif;
   background: transparent;
   color: #e0e6f0;
 }

 /* === Profile Table (как на странице пользователя) === */
 .profile-table-wrapper {
   max-width: 900px;
   margin: 0 auto;
   background: #374151;
   border-radius: 16px;
   box-shadow: 0 8px 32px rgba(0,0,0,0.4);
   overflow: hidden;
 }
 .profile-table-wrapper .profile { margin: 0; }
 .profile-body { padding: 0 24px; }

 .profile-section {
   background: transparent;
   padding: 20px 0;
   border-top: 1px solid rgba(255,255,255,0.08);
 }
 .profile-section:first-child { border-top: none; }

 .profile-section-name {
   font-size: 16px;
   font-weight: 600;
   color: #e0e6f0;
   margin-bottom: 16px;
   display: flex;
   align-items: center;
   gap: 8px;
 }
 .profile-section-name .material-symbols-outlined {
   font-size: 22px;
   color: #66c0f4;
 }

 .profile-section-content {
   color: #c7d0e0;
   font-size: 14px;
   line-height: 1.6;
 }

 /* === Сетка достижений внутри profile-section-content === */
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
 .ach-item:hover { transform: scale(1.08); }
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
 .ach-item:hover .ach-delete-btn { display: block; }

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

 /* === Кнопки и админ-панель в стиле profile-labels === */
 .profile-labels {
   display: flex;
   flex-wrap: wrap;
   gap: 8px;
   margin-top: 16px;
 }
 .profile-label {
   display: inline-flex;
   align-items: center;
   gap: 6px;
   padding: 8px 16px;
   background: rgba(102,192,244,0.1);
   border: 1px solid rgba(102,192,244,0.3);
   color: #66c0f4;
   border-radius: 8px;
   cursor: pointer;
   font-size: 13px;
   font-weight: 500;
   font-family: 'Inter', sans-serif;
   text-decoration: none;
   transition: all 0.2s;
 }
 .profile-label:hover {
   background: rgba(102,192,244,0.2);
 }
 .profile-label .material-symbols-outlined { font-size: 16px; }

 .ach-admin-panel {
   display: none;
   margin-top: 16px;
   padding: 16px;
   background: rgba(0,0,0,0.3);
   border-radius: 12px;
   border: 1px dashed rgba(102,192,244,0.25);
 }
 .ach-admin-panel.visible { display: block; }
 .ach-admin-panel h4 {
   margin: 0 0 12px 0;
   color: #e0e6f0;
   font-size: 14px;
   font-weight: 600;
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

 /* Инпуты в стиле профиля */
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
   transition: border-color 0.2s;
 }
 .ach-admin-input:focus { border-color: #66c0f4; }
 .ach-admin-input::placeholder { color: #5a6378; }

 .ach-add-btn {
   display: inline-flex;
   align-items: center;
   gap: 6px;
   padding: 8px 16px;
   border-radius: 8px;
   border: 1px solid rgba(102,192,244,0.3);
   background: rgba(102,192,244,0.1);
   color: #66c0f4;
   font-size: 13px;
   font-weight: 500;
   cursor: pointer;
   font-family: 'Inter', sans-serif;
   transition: all 0.2s;
 }
 .ach-add-btn:hover { background: rgba(102,192,244,0.2); }

 /* Статус загрузки */
 .ach-loading {
   color: #6b7280;
   font-size: 13px;
   font-style: italic;
   text-align: center;
   padding: 20px;
 }
</style>
</head>
<body>

<div class="profile-table-wrapper">
  <div class="profile">
    <div class="profile-body" style="padding: 20px 24px;">
      <div class="profile-section" style="border-top: none;">
        <h3 class="profile-section-name">
          <span class="material-symbols-outlined">military_tech</span>
          Достижения
        </h3>
        <div class="profile-section-content">
          <div class="ach-grid" id="achGrid">
            <div class="ach-loading" id="achLoading">Загрузка...</div>
            <div class="ach-empty" id="achEmpty" style="display:none;">Достижений пока нет</div>
          </div>
          <div class="profile-labels" id="achAdminBtns" style="display:none;">
            <a href="javascript:void(0)" class="profile-label" onclick="achToggleAdmin()">
              <span class="material-symbols-outlined">add_circle</span>
              Добавить достижение
            </a>
          </div>
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
            <div class="profile-labels">
              <a href="javascript:void(0)" class="profile-label" onclick="achAdd()">
                <span class="material-symbols-outlined">check</span>
                Добавить достижение
              </a>
              <a href="javascript:void(0)" class="profile-label" onclick="achToggleAdmin()">
                <span class="material-symbols-outlined">close</span>
                Отмена
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<script type="module">
import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js';
import { getDatabase, ref, onValue, push, set, remove } from 'https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js';

const firebaseConfig = {
  databaseURL: 'https://ak4ak-d948e-default-rtdb.firebaseio.com/'
};

const app = initializeApp(firebaseConfig);
const db = getDatabase(app);

const params = new URLSearchParams(window.location.search);
const uid = params.get('uid') || 'unknown';
const isAdmin = params.get('admin') === '1';

var selectedImgUrl = '';

if (isAdmin) {
  document.getElementById('achAdminBtns').style.display = 'flex';
}

const achRef = ref(db, 'achievements/' + uid);

onValue(achRef, function(snapshot) {
  var loading = document.getElementById('achLoading');
  if (loading) loading.style.display = 'none';

  var grid = document.getElementById('achGrid');
  var empty = document.getElementById('achEmpty');
  var data = snapshot.val();

  if (!data) {
    if (empty) empty.style.display = 'block';
    grid.querySelectorAll('.ach-item').forEach(function(el) { el.remove(); });
    return;
  }

  if (empty) empty.style.display = 'none';
  grid.querySelectorAll('.ach-item').forEach(function(el) { el.remove(); });

  Object.keys(data).forEach(function(key) {
    var item = data[key];
    var div = document.createElement('div');
    div.className = 'ach-item';
    div.onclick = function() { achToggleTooltip(this); };

    var deleteBtn = '';
    if (isAdmin) {
      deleteBtn = '<button class="ach-delete-btn" onclick="achDelete(\'' + key + '\'); event.stopPropagation();" title="Удалить">&times;</button>';
    }

    div.innerHTML = '<img src="' + item.img + '" alt="' + (item.title || '') + '">' +
      deleteBtn +
      '<div class="ach-tooltip">' +
      '<span class="ach-title">' + (item.title || '') + '</span>' +
      (item.desc || '') +
      '</div>';
    grid.appendChild(div);
  });
});

window.achToggleTooltip = function(el) {
  document.querySelectorAll('.ach-item').forEach(function(item) {
    if (item !== el) item.classList.remove('active');
  });
  el.classList.toggle('active');
};

window.achToggleAdmin = function() {
  document.getElementById('achAdminPanel').classList.toggle('visible');
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

  var newItemRef = push(achRef);
  set(newItemRef, {
    img: img,
    title: title,
    desc: desc
  }).then(function() {
    document.getElementById('achTitle').value = '';
    document.getElementById('achDesc').value = '';
    document.getElementById('achSelectedImg').value = '';
    selectedImgUrl = '';
    document.querySelectorAll('.ach-img-option').forEach(function(opt) {
      opt.classList.remove('selected');
    });
    document.getElementById('achAdminPanel').classList.remove('visible');
  });
};

window.achDelete = function(key) {
  if (!confirm('Удалить это достижение?')) return;
  remove(ref(db, 'achievements/' + uid + '/' + key));
};

document.addEventListener('click', function(e) {
  if (!e.target.closest('.ach-item')) {
    document.querySelectorAll('.ach-item').forEach(function(item) {
      item.classList.remove('active');
    });
  }
});
</script>


<script>
function sendHeight() {
  var h = Math.max(
    document.body.scrollHeight,
    document.body.offsetHeight,
    document.documentElement.scrollHeight,
    document.documentElement.offsetHeight
  );
  window.parent.postMessage({ type: 'resize', frame: 'achievements', height: h }, '*');
}
window.addEventListener('load', sendHeight);
setTimeout(sendHeight, 500);
setTimeout(sendHeight, 1500);
setTimeout(sendHeight, 3000);
if (window.ResizeObserver) {
  new ResizeObserver(sendHeight).observe(document.body);
}
// Also send height whenever new items are added to the grid
var grid = document.getElementById('achGrid');
if (grid && window.MutationObserver) {
  new MutationObserver(sendHeight).observe(grid, { childList: true, subtree: true });
}
</script>

</body>
</html>
