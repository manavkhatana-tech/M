<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MGDEVS Studios</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<style>
body{
  margin:0;
  font-family:'Segoe UI',sans-serif;
  color:white;
  background:
    linear-gradient(rgba(0,0,0,0.8), rgba(0,0,0,0.95)),
    url("res/bg.png");
  background-size:cover;
}

/* NAV */
header{
  display:flex;
  justify-content:space-between;
  padding:15px 25px;
  background:rgba(0,0,0,0.6);
  backdrop-filter:blur(10px);
}

nav a{
  color:white;
  margin-left:20px;
  text-decoration:none;
}

nav a:hover{
  color:#00c3ff;
}

/* HERO */
.hero{
  text-align:center;
  padding:140px 20px;
}

.hero h1{
  font-size:60px;
  color:#00c3ff;
  text-shadow:0 0 30px #00c3ff;
}

.dialogue{
  margin-top:10px;
  color:#00c3ff;
}

/* BUTTON */
.btn{
  margin-top:20px;
  padding:12px 25px;
  background:#00c3ff;
  border:none;
  border-radius:10px;
  cursor:pointer;
}

/* 🔥 POPUP (BOTTOM SHEET) */
.popup{
  position:fixed;
  left:0;
  bottom:-100%;
  width:100%;
  display:flex;
  justify-content:center;
  transition:0.4s ease;
  background:rgba(0,0,0,0.8);
}

/* BOX */
.box{
  background:#111;
  padding:20px;
  border-radius:20px 20px 0 0;
  width:100%;
  max-width:400px;
  box-shadow:0 -10px 30px #00c3ff55;
}

input, textarea, select{
  width:100%;
  margin:8px 0;
  padding:10px;
  border:none;
  border-radius:5px;
  background:#000;
  color:white;
}
</style>
</head>

<body>

<header>
  <h2>MGDEVS 😈</h2>
  <nav>
    <a href="#">Home</a>
    <a href="#">Projects</a>
  </nav>
</header>

<section class="hero">
  <h1>MGDEVS Studios</h1>
  <p>From Life to Games</p>

  <div class="dialogue" id="dialogue">
    We don’t just code… We create worlds.
  </div>

  <button class="btn" onclick="openForm()">Create Your Website</button>
</section>

<!-- POPUP FORM -->
<div id="popup" class="popup">
  <div class="box">
    <h3>Create Website</h3>

    <input id="site" placeholder="Site Name">
    
    <select id="style">
      <option>Stylish</option>
      <option>Simple</option>
    </select>

    <textarea id="desc" placeholder="Describe your site"></textarea>

    <input id="name" placeholder="Your Name">
    <input id="number" placeholder="Mobile Number">

    <button class="btn" onclick="submitForm()">Submit</button>
    <button class="btn" onclick="closeForm()">Close</button>
  </div>
</div>

<script>
function openForm(){
  let p=document.getElementById("popup");
  p.style.display="flex";
  setTimeout(()=>{ p.style.bottom="0"; },10);
}

function closeForm(){
  let p=document.getElementById("popup");
  p.style.bottom="-100%";
  setTimeout(()=>{ p.style.display="none"; },300);
}

/* 🔥 MAIN SYSTEM */
function submitForm(){

  let site=document.getElementById("site").value;
  let style=document.getElementById("style").value;
  let desc=document.getElementById("desc").value;
  let name=document.getElementById("name").value;
  let number=document.getElementById("number").value;

  let card=document.createElement("div");
  card.style.background="#000";
  card.style.color="#00c3ff";
  card.style.padding="20px";
  card.style.width="300px";
  card.style.borderRadius="15px";
  card.style.textAlign="center";

  card.innerHTML=`
    <h2>MGDEVS</h2>
    <h3>${site}</h3>
    <p>${style}</p>
    <p>${desc}</p>
    <hr>
    <p>${name}</p>
    <p>${number}</p>
  `;

  document.body.appendChild(card);

  html2canvas(card).then(canvas=>{
    let a=document.createElement("a");
    a.download="data.png";
    a.href=canvas.toDataURL();
    a.click();

    document.body.removeChild(card);

    let subject="MGDEVS Client Request";

    let body=`Site: ${site}
Style: ${style}
Description: ${desc}

Name: ${name}
Number: ${number}

Attach PNG and send`;

    let email="kukabhaikhatana@gmail.com";

    let url=`mailto:${email}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;

    window.location.href=url;
  });
}

/* Dialogue */
let texts=[
"We don’t just code… We create worlds.",
"From Life to Games — MGDEVS",
"Build your dream site with MGDEVS"
];

let i=0;
setInterval(()=>{
  i=(i+1)%texts.length;
  document.getElementById("dialogue").innerText=texts[i];
},3000);
</script>

</body>
</html>
