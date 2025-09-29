# nosso-cantinho 
<!DOCTYPE html>  <html lang="pt-br">  
<head>  
  <meta charset="utf-8" />  
  <meta name="viewport" content="width=device-width,initial-scale=1" />  
  <title>Nosso Cantinho ❤️</title>  
  <style>  
    :root{  
      --rose:#ff4d6d;  
      --rose-light:#ffe6ec;  
      --bg:#fff6f8;  
      --card:#ffffff;  
    }  
    *{box-sizing:border-box}  
    body{  
      margin:0;  
      font-family:Inter, "Segoe UI", Arial;  
      background:linear-gradient(180deg,var(--bg),#fff);  
      color:#333;  
      -webkit-font-smoothing:antialiased;  
    }  
    header{  
      background:var(--rose);  
      color:white;  
      padding:18px 12px;  
      text-align:center;  
      font-size:20px;  
    }  
    nav{  
      display:flex;  
      gap:8px;  
      justify-content:center;  
      padding:12px;  
      background:var(--rose-light);  
      flex-wrap:wrap;  
    }  
    nav a{  
      text-decoration:none;  
      color:var(--rose);  
      font-weight:600;  
      padding:8px 12px;  
      border-radius:10px;  
    }  
    nav a:hover{background:#ffd7e0}  
    .container{max-width:1000px;margin:20px auto;padding:12px;}  
    .login-box{  
      width:320px;margin:40px auto;padding:20px;background:var(--card);border-radius:12px; box-shadow:0 6px 18px rgba(0,0,0,0.08);  
      text-align:center;  
    }  
    .btn{background:var(--rose);color:white;border:none;padding:10px 16px;border-radius:10px;cursor:pointer;margin:6px}  
    .card{background:var(--card);padding:14px;border-radius:12px;box-shadow:0 6px 18px rgba(0,0,0,0.05);margin-bottom:14px}  
    input[type="text"],textarea{width:100%;padding:8px;border-radius:8px;border:1px solid #eee;margin-top:8px}  
    .row{display:flex;gap:12px;flex-wrap:wrap}  
    .small{flex:1 1 200px}  
    figure{display:inline-block;margin:8px;padding:6px;background:#fff;border-radius:8px;box-shadow:0 3px 10px rgba(0,0,0,0.04)}  
    figure img{max-width:180px;border-radius:6px;display:block}  
    .muted{color:#777;font-size:13px}  
    .timeline-item{border-left:3px solid var(--rose);padding-left:12px;margin-bottom:12px}  
    footer{padding:20px;text-align:center;color:#777}  
    @media(max-width:600px){  
      nav{font-size:14px}  
      figure img{max-width:140px}  
      .login-box{width:90%}  
    }  
  </style>  
</head>  
<body>  
  <header>🌹 Nosso Cantinho</header>    <!-- LOGIN -->    <div id="login" class="login-box">  
    <h2>Quem está entrando?</h2>  
    <div style="margin:10px 0">  
      <button class="btn" onclick="login('Isa')">Isa</button>  
      <button class="btn" onclick="login('Kauan')">Kauan</button>  
    </div>  
    <p class="muted">Ao entrar, as ações ficam marcadas com quem postou (Isa ou Kauan).</p>  
  </div>    <!-- SITE -->    <div id="site" style="display:none;">  
    <nav>  
      <a href="#" onclick="showPage('home')">Home</a>  
      <a href="#" onclick="showPage('perfil')">Perfis</a>  
      <a href="#" onclick="showPage('fotos')">Fotos</a>  
      <a href="#" onclick="showPage('musicas')">Músicas</a>  
      <a href="#" onclick="showPage('frases')">Frases</a>  
      <a href="#" onclick="showPage('memorias')">Memórias</a>  
      <a href="#" onclick="logout()" style="color:#444">Sair</a>  
    </nav>  <div class="container">  
  <section id="home" class="card active">  
    <h2>Bem-vindo ao nosso cantinho ❤️</h2>  
    <p id="bemvindo"></p>  
    <p class="muted">Use o menu para navegar. Tudo que vocês adicionarem fica salvo no navegador.</p>  
  </section>  

  <section id="perfil" class="card" style="display:none">  
    <h3>Perfis</h3>  
    <div id="profiles-area"></div>  
  </section>  

  <section id="fotos" class="card" style="display:none">  
    <h3>Galeria de Fotos 📸</h3>  
    <div class="row">  
      <div class="small card">  
        <label>Adicionar foto</label>  
        <input type="file" id="photoInput" accept="image/*">  
        <p class="muted">A foto será salva no seu navegador.</p>  
      </div>  
    </div>  
    <div id="gallery"></div>  
  </section>  

  <section id="musicas" class="card" style="display:none">  
    <h3>Músicas 🎵</h3>  
    <div class="row">  
      <div class="small card">  
        <label>Adicionar música por URL (recomendado)</label>  
        <input id="musicUrl" type="text" placeholder="Cole link direto para mp3/ogg..." />  
        <button class="btn" onclick="addMusicByUrl()">Adicionar</button>  
      </div>  
      <div class="small card">  
        <label>Ou enviar arquivo (pode ser grande)</label>  
        <input type="file" id="musicFile" accept="audio/*">  
      </div>  
    </div>  
    <div id="musicList"></div>  
  </section>  

  <section id="frases" class="card" style="display:none">  
    <h3>Frases & Declarações 💌</h3>  
    <textarea id="phraseText" rows="3" placeholder="Escreva algo especial..."></textarea>  
    <div style="text-align:right;margin-top:8px">  
      <button class="btn" onclick="addPhrase()">Publicar</button>  
    </div>  
    <div id="phrasesList" style="margin-top:12px"></div>  
  </section>  

  <section id="memorias" class="card" style="display:none">  
    <h3>Memórias 📖</h3>  
    <div id="timeline"></div>  
  </section>  
</div>  

<footer class="muted">Feito com carinho para minha Princesa 💖.</footer>

  </div>    <script>  
    /* ---------- UTIL ---------- */  
    function save(key, value){ localStorage.setItem(key, JSON.stringify(value)); }  
    function load(key){ return JSON.parse(localStorage.getItem(key) || 'null'); }  
    function uid(){ return Math.random().toString(36).slice(2,9); }  
  
    /* ---------- INICIALIZAÇÃO ---------- */  
    let usuario = "";  
    document.addEventListener('DOMContentLoaded', ()=>{  
      // inicializa estruturas se não existirem  
      if(!load('profiles')){  
        save('profiles', [  
          {id:uid(), name:'Você', desc:'', photo:''},  
          {id:uid(), name:'Ela', desc:'', photo:''}  
        ]);  
      }  
      if(!load('photos')) save('photos', []);  
      if(!load('musics')) save('musics', []);  
      if(!load('phrases')) save('phrases', []);  
      // bind events  
      document.getElementById('photoInput').addEventListener('change', handlePhotoUpload);  
      document.getElementById('musicFile').addEventListener('change', handleMusicFile);  
      renderAll();  
    });  
  
    /* ---------- LOGIN ---------- */  
    function login(name){  
      usuario = name;  
      localStorage.setItem('currentUser', usuario);  
      document.getElementById('login').style.display = 'none';  
      document.getElementById('site').style.display = 'block';  
      document.getElementById('bemvindo').innerText = `Olá ${usuario}! Você está logado.`;  
      showPage('home');  
    }  
    function logout(){  
      usuario = "";  
      localStorage.removeItem('currentUser');  
      document.getElementById('site').style.display = 'none';  
      document.getElementById('login').style.display = 'block';  
    }  
  
    /* ---------- PAGES ---------- */  
    function showPage(id){  
      document.querySelectorAll('section').forEach(s => s.style.display = 'none');  
      document.getElementById(id).style.display = 'block';  
      if(id==='perfil') renderProfiles();  
      if(id==='fotos') renderGallery();  
      if(id==='musicas') renderMusicList();  
      if(id==='frases') renderPhrases();  
      if(id==='memorias') renderTimeline();  
    }  
  
    /* ---------- PROFILES ---------- */  
    function renderProfiles(){  
      const profiles = load('profiles') || [];  
      const el = document.getElementById('profiles-area');  
      el.innerHTML = '';  
      profiles.forEach((p, idx) => {  
        const div = document.createElement('div');  
        div.className = 'card';  
        div.innerHTML = `  
          <div style="display:flex;gap:12px;align-items:center">  
            <div style="width:80px;height:80px;border-radius:8px;overflow:hidden;background:#f4f4f4;display:flex;align-items:center;justify-content:center">  
              ${p.photo ? `<img src="${p.photo}" style="width:100%;height:100%;object-fit:cover">` : '<span class="muted">sem foto</span>'}  
            </div>  
            <div style="flex:1;text-align:left">  
              <input id="pname${idx}" type="text" value="${p.name}" />  
              <textarea id="pdesc${idx}" rows="2" placeholder="Descrição">${p.desc}</textarea>  <div style="margin-top:6px">  
            <button class="btn" onclick="saveProfile(${idx})">Salvar</button>  
            <input id="pphoto${idx}" type="file" accept="image/*" style="margin-left:8px" onchange="changeProfilePhoto(event, ${idx})">  
          </div>  
        </div>  
      </div>  
    `;  
    el.appendChild(div);  
  });  
}  
function saveProfile(idx){  
  const profiles = load('profiles');  
  profiles[idx].name = document.getElementById(`pname${idx}`).value || profiles[idx].name;  
  profiles[idx].desc = document.getElementById(`pdesc${idx}`).value || '';  
  save('profiles', profiles);  
  alert('Perfil salvo!');  
  renderProfiles();  
  renderAll();  
}  
function changeProfilePhoto(e, idx){  
  const file = e.target.files[0];  
  if(!file) return;  
  const reader = new FileReader();  
  reader.onload = () => {  
    const profiles = load('profiles');  
    profiles[idx].photo = reader.result;  
    save('profiles', profiles);  
    renderProfiles();  
    renderAll();  
  }  
  reader.readAsDataURL(file);  
}  

/* ---------- PHOTOS ---------- */  
function handlePhotoUpload(e){  
  const file = e.target.files[0];  
  if(!file) return;  
  const reader = new FileReader();  
  reader.onload = () => {  
    const photos = load('photos') || [];  
    const item = {id:uid(), data: reader.result, author: usuario || localStorage.getItem('currentUser') || 'Anônimo', date: new Date().toISOString()};  
    photos.unshift(item);  
    save('photos', photos);  
    renderGallery();  
    renderTimeline();  
    e.target.value = ''; // limpa input  
  };  
  reader.readAsDataURL(file);  
}  
function renderGallery(){  
  const photos = load('photos') || [];  
  const el = document.getElementById('gallery');  
  el.innerHTML = '';  
  photos.forEach(p=>{  
    const fig = document.createElement('figure');  
    fig.innerHTML = `<img src="${p.data}" alt="foto"><figcaption style="text-align:left">${p.author} · <span class="muted">${new Date(p.date).toLocaleString()}</span></figcaption>`;  
    el.appendChild(fig);  
  });  
}  

/* ---------- MUSIC ---------- */  
function addMusicByUrl(){  
  const url = document.getElementById('musicUrl').value.trim();  
  if(!url) { alert('Cole uma URL válida'); return; }  
  const musics = load('musics') || [];  
  musics.unshift({id:uid(), url, title: url.split('/').pop(), author: usuario || localStorage.getItem('currentUser') || 'Anônimo', date: new Date().toISOString()});  
  save('musics', musics);  
  document.getElementById('musicUrl').value = '';  
  renderMusicList();  
  renderTimeline();  
}  
function handleMusicFile(e){  
  const file = e.target.files[0];  
  if(!file) return;  
  const reader = new FileReader();  
  reader.onload = () => {  
    const musics = load('musics') || [];  
    musics.unshift({id:uid(), url: reader.result, title: file.name, author: usuario || localStorage.getItem('currentUser') || 'Anônimo', date:new Date().toISOString()});  
    save('musics', musics);  
    renderMusicList();  
    renderTimeline();  
    e.target.value = '';  
  };  
  reader.readAsDataURL(file);  
}  
function renderMusicList(){  
  const musics = load('musics') || [];  
  const el = document.getElementById('musicList');  
  el.innerHTML = '';  
  musics.forEach(m=>{  
    const d = document.createElement('div'); d.className='card';  
    d.innerHTML = `<strong>${m.title}</strong> <div class="muted">${m.author} · ${new Date(m.date).toLocaleString()}</div>  
      <div style="margin-top:8px"><audio controls src="${m.url}"></audio></div>`;  
    el.appendChild(d);  
  });  
}  

/* ---------- PHRASES ---------- */  
function addPhrase(){  
  const txt = document.getElementById('phraseText').value.trim();  
  if(!txt) return alert('Escreva algo antes');  
  const phrases = load('phrases') || [];  
  const item = {id:uid(), text: txt, author: usuario || localStorage.getItem('currentUser') || 'Anônimo', date: new Date().toISOString()};  
  phrases.unshift(item);  
  save('phrases', phrases);  
  document.getElementById('phraseText').value = '';  
  renderPhrases();  
  renderTimeline();  
}  
function renderPhrases(){  
  const phrases = load('phrases') || [];  
  const el = document.getElementById('phrasesList');  
  el.innerHTML = '';  
  phrases.forEach(p=>{  
    const d = document.createElement('div'); d.className='card';  
    d.innerHTML = `<div style="font-size:15px">${p.text}</div><div class="muted">${p.author} · ${new Date(p.date).toLocaleString()}</div>`;  
    el.appendChild(d);  
  });  
}  

/* ---------- TIMELINE (MEMÓRIAS) ---------- */  
function renderTimeline(){  
  const photos = load('photos') || [];  
  const musics = load('musics') || [];  
  const phrases = load('phrases') || [];  
  // unir e ordenar por data  
  const all = [];  
  photos.forEach(p=> all.push({...p, type:'photo'}));  
  musics.forEach(m=> all.push({...m, type:'music'}));  
  phrases.forEach(ph=> all.push({...ph, type:'phrase'}));  
  all.sort((a,b)=> new Date(b.date) - new Date(a.date));  
  const el = document.getElementById('timeline');  
  el.innerHTML = '';  
  all.forEach(item=>{  
    const div = document.createElement('div'); div.className='timeline-item card';  
    if(item.type==='photo'){  
      div.innerHTML = `<div><strong>Foto</strong> · <span class="muted">${item.author} · ${new Date(item.date).toLocaleString()}</span></div>  
        <div style="margin-top:8px"><img src="${item.data}" style="max-width:280px;border-radius:8px"></div>`;  
    } else if(item.type==='music'){  
      div.innerHTML = `<div><strong>Música</strong> · <span class="muted">${item.author} · ${new Date(item.date).toLocaleString()}</span></div>  
        <div style="margin-top:8px"><div>${item.title}</div><audio controls src="${item.url}"></audio></div>`;  
    } else {  
      div.innerHTML = `<div><strong>Frase</strong> · <span class="muted">${item.author} · ${new Date(item.date).toLocaleString()}</span></div>  
        <div style="margin-top:8px">${item.text}</div>`;  
    }  
    el.appendChild(div);  
  });  
}  

/* ---------- RENDER ALL ---------- */  
function renderAll(){  
  renderProfiles();  
  renderGallery();  
  renderMusicList();  
  renderPhrases();  
  renderTimeline();  
}

  </script>  
</body>  
</html>
