 #wa.html
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover,user-scalable=no">
<meta name="theme-color" content="#8c6b52">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="Winter Arc">
<link rel="manifest" href="manifest.json">
<title>Winter Arc 2.0</title>

<style>
:root{
--bg:#f7f6f2;
--card:#fff;
--text:#111;
--muted:#888;
--accent:#8c6b52;
--light:#f0ece6;
--border:#e5e0d8;
}

*{
box-sizing:border-box;
margin:0;
padding:0;
-webkit-tap-highlight-color:transparent;
}

body{
font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Arial,sans-serif;
background:var(--bg);
color:var(--text);
min-height:100vh;
}

button{
font:inherit;
-webkit-appearance:none;
}

.app{
width:100%;
max-width:480px;
margin:auto;
padding:16px 16px 40px;
}

.header{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:14px;
color:#555;
}

.header-title{
font-size:16px;
font-weight:700;
color:#111;
}

.subtitle{
font-size:14px;
font-weight:700;
margin-bottom:18px;
}

.info{
display:flex;
justify-content:space-between;
align-items:flex-start;
margin-bottom:18px;
}

.days-label{
font-size:12px;
font-weight:800;
color:var(--accent);
letter-spacing:1px;
}

h1{
font-size:28px;
font-weight:800;
letter-spacing:-.5px;
}

.streak{
text-align:right;
font-size:30px;
font-weight:800;
}

.streak-label{
display:block;
font-size:11px;
font-weight:400;
color:var(--muted);
}

.install{
width:100%;
border:0;
border-radius:16px;
padding:14px;
background:var(--accent);
color:white;
font-size:14px;
font-weight:700;
margin-bottom:20px;
}

.card{
background:var(--card);
border-radius:20px;
padding:20px;
margin-bottom:22px;
box-shadow:0 2px 10px rgba(0,0,0,.03);
}

.progress-head{
display:flex;
justify-content:space-between;
font-size:16px;
font-weight:700;
margin-bottom:12px;
}

.progress-bg{
height:8px;
background:var(--border);
border-radius:5px;
overflow:hidden;
margin-bottom:18px;
}

.progress-fill{
height:100%;
background:var(--accent);
border-radius:5px;
transition:.25s;
}

.stats{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:9px;
}

.stat{
background:var(--light);
border-radius:15px;
padding:14px 10px;
}

.stat-value{
font-size:20px;
font-weight:800;
margin-bottom:3px;
}

.stat-label{
font-size:10px;
line-height:1.3;
color:var(--muted);
}

.section-head{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:14px;
}

.section-head h2{
font-size:20px;
}

.today{
border:0;
background:var(--light);
border-radius:12px;
padding:8px 14px;
font-size:12px;
font-weight:700;
}

.calendar{
display:grid;
grid-template-columns:repeat(7,1fr);
gap:6px;
margin-bottom:24px;
}

.dow{
text-align:center;
font-size:10px;
font-weight:700;
color:var(--muted);
padding-bottom:3px;
}

.cal-day{
border:2px solid transparent;
background:white;
border-radius:11px;
min-height:48px;
padding:6px 2px;
text-align:center;
cursor:pointer;
}

.cal-day.selected{
background:var(--light);
}

.cal-day.today{
border-color:var(--accent);
}

.cal-number{
font-size:13px;
font-weight:800;
}

.cal-percent{
font-size:9px;
color:var(--muted);
margin-top:2px;
}

.day-head{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:14px;
font-weight:700;
}

.day-percent{
color:var(--accent);
}

.tasks{
display:grid;
grid-template-columns:1fr 1fr;
gap:10px;
margin-bottom:26px;
}

.task{
background:white;
border:1px solid var(--border);
border-radius:16px;
padding:13px;
display:flex;
gap:9px;
align-items:flex-start;
text-align:left;
cursor:pointer;
min-height:85px;
}

.checkbox{
width:23px;
height:23px;
border:2px solid #ccc;
border-radius:6px;
flex-shrink:0;
display:flex;
align-items:center;
justify-content:center;
}

.task.done .checkbox{
background:var(--accent);
border-color:var(--accent);
}

.task.done .checkbox::after{
content:"✓";
color:white;
font-weight:800;
}

.task-title{
font-size:13px;
font-weight:700;
}

.task.done .task-title{
text-decoration:line-through;
opacity:.6;
}

.task-description{
font-size:10px;
line-height:1.35;
color:var(--muted);
margin-top:4px;
}

.task.done .task-description{
opacity:.6;
}

.weeks{
margin-bottom:25px;
}

.week{
display:flex;
align-items:center;
gap:9px;
margin-bottom:12px;
}

.week-name{
width:66px;
font-size:11px;
flex-shrink:0;
}

.week-bar{
flex:1;
height:6px;
background:var(--border);
border-radius:5px;
overflow:hidden;
}

.week-fill{
height:100%;
background:var(--accent);
}

.week-percent{
width:36px;
text-align:right;
font-size:11px;
font-weight:700;
}

.footer{
text-align:center;
font-size:10px;
line-height:1.5;
color:var(--muted);
}

@media(max-width:380px){
.tasks{
grid-template-columns:1fr;
}
}
</style>
</head>

<body>

<main class="app">

<div class="header">
<div>☰</div>
<div class="header-title">Winter Arc 2.0</div>
<div>✎</div>
</div>

<div class="subtitle">⚙️ Winter Arc 2.0</div>

<div class="info">
<div>
<div class="days-label">90 DAYS</div>
<h1>WINTER ARC</h1>
</div>

<div class="streak">
<span id="streak">0</span> 🔥
<span class="streak-label">серия дней</span>
</div>
</div>

<button class="install" id="installButton">
📱 Установить на экран Домой
</button>

<div class="card">

<div class="progress-head">
<span id="overallPercent">0%</span>
<span id="dayCounter">1 / 90 дней</span>
</div>

<div class="progress-bg">
<div class="progress-fill" id="overallBar"></div>
</div>

<div class="stats">

<div class="stat">
<div class="stat-value" id="weekPercent">0%</div>
<div class="stat-label">эта неделя</div>
</div>

<div class="stat">
<div class="stat-value" id="perfectDays">0</div>
<div class="stat-label">идеальных дней</div>
</div>

<div class="stat">
<div class="stat-value" id="completedToday">0</div>
<div class="stat-label">выполнено сегодня</div>
</div>

</div>
</div>

<div class="section-head">
<h2>Календарь</h2>
<button class="today" id="todayButton">Сегодня</button>
</div>

<div class="calendar" id="calendar"></div>

<div class="day-head">
<span id="selectedDayTitle">День 1 · 1 окт</span>
<span class="day-percent" id="selectedDayPercent">0%</span>
</div>

<div class="tasks" id="tasks"></div>

<div class="section-head">
<h2>Недели</h2>
</div>

<div class="weeks" id="weeks"></div>

<div class="footer">
Данные сохраняются на этом устройстве автоматически.<br>
Маленькие галочки → большая трансформация.
</div>

</main>

<script>

const TOTAL_DAYS = 90;

/*
Начало Winter Arc:
1 октября 2026
*/
const START_DATE = new Date(2026,9,1);

const TASKS = [

{
emoji:"🏃",
title:"Бег",
description:"Тренировка по плану или 20–30 минут лёгкого бега"
},

{
emoji:"👣",
title:"Шаги",
description:"Минимум 8 000 шагов за день"
},

{
emoji:"😴",
title:"Сон",
description:"Лечь до 23:00 и поспать 7–9 часов"
},

{
emoji:"📚",
title:"Учёба",
description:"Психология: лекция, чтение, конспект или практика"
},

{
emoji:"☀️",
title:"Уход утром",
description:"Умыться → уход за лицом → крем → уход за телом"
},

{
emoji:"🌙",
title:"Уход вечером",
description:"Вечерний уход за лицом и телом"
},

{
emoji:"💄",
title:"Макияж",
description:"Привести лицо в порядок и сделать макияж"
},

{
emoji:"💇‍♀️",
title:"Укладка",
description:"Расчесать волосы и сделать аккуратную укладку"
},

{
emoji:"💧",
title:"Вода",
description:"Ориентир 1,5–2 литра воды за день"
},

{
emoji:"🍽️",
title:"Питание",
description:"Придерживаться своего плана питания"
},

{
emoji:"🧘",
title:"Движение",
description:"ОФП, ролики, бассейн, прогулка или другая активность"
},

{
emoji:"✍️",
title:"Для себя",
description:"Отдых, чтение, дневник или приятное дело для себя"
},

{
emoji:"📱",
title:"Instagram",
description:"Сторис, пост, Reels или 30 минут работы над блогом"
}

];


/* =========================
   ХРАНЕНИЕ ДАННЫХ
========================= */

let state = JSON.parse(
localStorage.getItem("winterArc90")
|| '{"days":{}}'
);

let selectedDay = 0;

function saveState(){

localStorage.setItem(
"winterArc90",
JSON.stringify(state)
);

}


/* =========================
   РАБОТА С ДНЯМИ
========================= */

function isChecked(day,task){

return !!(
state.days[day]
&&
state.days[day][task]
);

}

function toggleTask(day,task){

if(!state.days[day]){
state.days[day] = {};
}

if(state.days[day][task]){

delete state.days[day][task];

}else{

state.days[day][task] = true;

}

saveState();

render();

}


/* =========================
   ПРОЦЕНТ ДНЯ
========================= */

function getDayPercent(day){

let completed = 0;

for(let i=0;i<TASKS.length;i++){

if(isChecked(day,i)){
completed++;
}

}

return Math.round(
completed / TASKS.length * 100
);

}


/* =========================
   ОБЩИЙ ПРОГРЕСС
========================= */

function getOverallPercent(){

let total = 0;

for(let day=0;day<TOTAL_DAYS;day++){

total += getDayPercent(day);

}

return Math.round(
total / TOTAL_DAYS
);

}


/* =========================
   ИДЕАЛЬНЫЕ ДНИ
========================= */

function getPerfectDays(){

let result = 0;

for(let day=0;day<TOTAL_DAYS;day++){

if(getDayPercent(day) === 100){

result++;

}

}

return result;

}


/* =========================
   СЕРИЯ
========================= */

function getStreak(){

let streak = 0;

for(let day=0;day<TOTAL_DAYS;day++){

if(getDayPercent(day) > 0){

streak++;

}else{

break;

}

}

return streak;

}


/* =========================
   НЕДЕЛЯ
========================= */

function getWeekPercent(week){

let start = week * 7;

let end = Math.min(
start + 7,
TOTAL_DAYS
);

let total = 0;
let count = 0;

for(
let day=start;
day<end;
day++
){

total += getDayPercent(day);
count++;

}

return Math.round(total/count);

}


/* =========================
   КАЛЕНДАРЬ
========================= */

function renderCalendar(){

const calendar =
document.getElementById("calendar");

calendar.innerHTML="";

const weekdays=[
"Пн",
"Вт",
"Ср",
"Чт",
"Пт",
"Сб",
"Вс"
];

weekdays.forEach(day=>{

const element =
document.createElement("div");

element.className="dow";
element.textContent=day;

calendar.appendChild(element);

});


/*
Определяем, на какой день недели
приходится 1 октября 2026
*/

const offset =
(START_DATE.getDay()+6)%7;

for(
let i=0;
i<offset;
i++
){

calendar.appendChild(
document.createElement("div")
);

}


for(
let day=0;
day<TOTAL_DAYS;
day++
){

const element =
document.createElement("button");

element.className="cal-day";

if(day === selectedDay){

element.classList.add("selected");

}


/*
Сегодня по календарю Winter Arc:
6 октября = день 6
*/

const today = new Date();

const todayIndex =
Math.floor(
(
new Date(
today.getFullYear(),
today.getMonth(),
today.getDate()
)
-
new Date(
START_DATE.getFullYear(),
START_DATE.getMonth(),
START_DATE.getDate()
)
)
/86400000
);

if(day === todayIndex){

element.classList.add("today");

}

element.innerHTML=`

<div class="cal-number">
${day+1}
</div>

<div class="cal-percent">
${getDayPercent(day)}%
</div>

`;

element.onclick=()=>{

selectedDay=day;

render();

setTimeout(()=>{

element.scrollIntoView({
behavior:"smooth",
block:"center"
});

},50);

};

calendar.appendChild(element);

}

}


/* =========================
   ЗАДАЧИ
========================= */

function renderTasks(){

const container =
document.getElementById("tasks");

container.innerHTML="";

TASKS.forEach(
(task,index)=>{

const button =
document.createElement("button");

button.className =
"task";

if(
isChecked(
selectedDay,
index
)
){

button.classList.add("done");

}

button.innerHTML=`

<div class="checkbox"></div>

<div>

<div class="task-title">
${task.emoji}
${task.title}
</div>

<div class="task-description">
${task.description}
</div>

</div>

`;

button.onclick=()=>{

toggleTask(
selectedDay,
index
);

};

container.appendChild(button);

}

);

}


/* =========================
   НЕДЕЛИ
========================= */

function renderWeeks(){

const container =
document.getElementById("weeks");

container.innerHTML="";

for(
let week=0;
week<13;
week++
){

const percent =
getWeekPercent(week);

const row =
document.createElement("div");

row.className="week";

row.innerHTML=`

<div class="week-name">
Неделя ${week+1}
</div>

<div class="week-bar">

<div
class="week-fill"
style="width:${percent}%"
></div>

</div>

<div class="week-percent">
${percent}%
</div>

`;

container.appendChild(row);

}

}


/* =========================
   ОСНОВНОЙ РЕНДЕР
========================= */

function render(){

const overall =
getOverallPercent();

const dayPercent =
getDayPercent(
selectedDay
);

const week =
Math.floor(
selectedDay/7
);

const weekPercent =
getWeekPercent(week);


/* Общий прогресс */

document.getElementById(
"overallPercent"
).textContent =
overall+"%";

document.getElementById(
"overallBar"
).style.width =
overall+"%";


/* Номер дня */

document.getElementById(
"dayCounter"
).textContent =
(selectedDay+1)+" / "+TOTAL_DAYS+" дней";


/* Неделя */

document.getElementById(
"weekPercent"
).textContent =
weekPercent+"%";


/* Идеальные дни */

document.getElementById(
"perfectDays"
).textContent =
getPerfectDays();


/* Выполнено сегодня */

let completed = 0;

for(
let i=0;
i<TASKS.length;
i++
){

if(
isChecked(
selectedDay,
i
)
){

completed++;

}

}

document.getElementById(
"completedToday"
).textContent =
completed;


/* Серия */

document.getElementById(
"streak"
).textContent =
getStreak();


/* Заголовок */

const date =
new Date(
START_DATE.getFullYear(),
START_DATE.getMonth(),
START_DATE.getDate()+selectedDay
);

const dateText =
date.toLocaleDateString(
"ru-RU",
{
day:"numeric",
month:"short"
}
);

document.getElementById(
"selectedDayTitle"
).textContent =
`День ${selectedDay+1} · ${dateText}`;


/* Процент дня */

document.getElementById(
"selectedDayPercent"
).textContent =
dayPercent+"%";


renderCalendar();
renderTasks();
renderWeeks();

}


/* =========================
   КНОПКА «СЕГОДНЯ»
========================= */

document.getElementById(
"todayButton"
).onclick=()=>{

const now =
new Date();

const today =
new Date(
now.getFullYear(),
now.getMonth(),
now.getDate()
);

let index =
Math.floor(
(
today -
new Date(
START_DATE.getFullYear(),
START_DATE.getMonth(),
START_DATE.getDate()
)
)
/86400000
);


/*
Если Winter Arc ещё не начался —
показываем День 1.

Если закончился —
показываем День 90.
*/

index =
Math.max(
0,
Math.min(
TOTAL_DAYS-1,
index
)
);

selectedDay=index;

render();

setTimeout(()=>{

document
.querySelector(".cal-day.selected")
?.scrollIntoView({
behavior:"smooth",
block:"center"
});

},100);

};


/* =========================
   УСТАНОВКА
========================= */

let deferredPrompt = null;

window.addEventListener(
"beforeinstallprompt",
event=>{

event.preventDefault();

deferredPrompt=event;

}
);

document.getElementById(
"installButton"
).onclick=async()=>{

if(deferredPrompt){

deferredPrompt.prompt();

await deferredPrompt.userChoice;

deferredPrompt=null;

}else{

alert(
"На iPhone: нажми «Поделиться» в Safari → «На экран Домой» → «Добавить»."
);

}

};


/* =========================
   SERVICE WORKER
========================= */

if(
"serviceWorker" in navigator
){

window.addEventListener(
"load",
()=>{

navigator.serviceWorker
.register("sw.js")
.catch(()=>{});

}
);

}


/* =========================
   ЗАПУСК
========================= */

render();

</script>

</body>
</html>