
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Crash Demo</title>

<style>
*{box-sizing:border-box}

body{
 margin:0;
 background:#020805;
 color:#ecfff2;
 font-family:Tahoma,Arial,sans-serif
}

.game{
 max-width:760px;
 margin:20px auto;
 padding:18px;
 background:linear-gradient(145deg,#06110a,#0b2113);
 border:1px solid #195b31;
 border-radius:22px
}

.top{
 display:flex;
 justify-content:space-between;
 align-items:center;
 flex-wrap:wrap;
 gap:10px;
 margin-bottom:14px
}

.badge{
 padding:8px 13px;
 border-radius:20px;
 background:#082817;
 border:1px solid #287542;
 color:#7cffaa;
 font-size:13px
}

.balance{
 color:#b8cdbf;
 font-size:14px
}

.balance strong{
 color:#61ff96;
 font-size:18px
}

/* نمودار */

.chart{
 position:relative;
 height:330px;
 overflow:hidden;
 border-radius:18px;
 background:
 radial-gradient(circle at 45% 70%,
 rgba(40,255,110,.10),
 transparent 52%),
 #020603;
 border:1px solid #17472a
}

.grid{
 position:absolute;
 inset:0;
 background-image:
 linear-gradient(rgba(60,255,120,.055) 1px,transparent 1px),
 linear-gradient(90deg,rgba(60,255,120,.055) 1px,transparent 1px);
 background-size:42px 42px
}

svg{
 position:absolute;
 inset:0;
 width:100%;
 height:100%
}

.main-line{
 fill:none;
 stroke:#39ff79;
 stroke-width:5;
 stroke-linecap:round;
 filter:
 drop-shadow(0 0 5px #39ff79)
 drop-shadow(0 0 14px #39ff79)
}

.main-dot{
 fill:#d5ffe2;
 filter:
 drop-shadow(0 0 6px #39ff79)
 drop-shadow(0 0 18px #39ff79)
}

/* شعله */

.flame{
 position:absolute;
 width:24px;
 height:34px;
 transform:translate(-50%,-50%);
 pointer-events:none;
 z-index:5
}

.flame:before{
 content:"";
 position:absolute;
 left:7px;
 top:4px;
 width:14px;
 height:25px;
 background:#ff3d00;
 border-radius:70% 30% 65% 35%;
 transform:rotate(45deg);
 box-shadow:
  0 0 7px #ff4d00,
  0 0 15px #ff7700,
  0 0 25px rgba(255,80,0,.8);
 animation:fire .18s infinite alternate
}

.flame:after{
 content:"";
 position:absolute;
 left:10px;
 top:11px;
 width:8px;
 height:15px;
 background:#ffe45c;
 border-radius:70% 30% 65% 35%;
 transform:rotate(45deg);
 box-shadow:0 0 8px #fff06a
}

@keyframes fire{
 from{
  transform:rotate(40deg) scale(.9);
  opacity:.8
 }
 to{
  transform:rotate(50deg) scale(1.08);
  opacity:1
 }
}

.multiplier{
 position:absolute;
 inset:0;
 display:flex;
 align-items:center;
 justify-content:center;
 font-size:58px;
 font-weight:bold;
 color:white;
 text-shadow:
  0 0 12px #39ff79,
  0 0 28px rgba(57,255,121,.55);
 pointer-events:none
}

.status{
 position:absolute;
 bottom:12px;
 right:14px;
 color:#9bb8a5;
 font-size:13px
}

/* موجودی */

.money-panel{
 margin-top:14px;
 padding:14px;
 border-radius:15px;
 background:#06130b;
 border:1px solid #16472a
}

.money-title{
 display:flex;
 justify-content:space-between;
 margin-bottom:8px;
 color:#aac5b4;
 font-size:13px
}

.money-value{
 color:#72ffa0;
 font-size:22px;
 font-weight:bold
}

.money-chart{
 height:70px;
 position:relative;
 overflow:hidden;
 border-radius:10px;
 background:#030805
}

.money-chart svg{
 width:100%;
 height:100%
}

.money-line{
 fill:none;
 stroke:#45ff82;
 stroke-width:3;
 stroke-linecap:round;
 filter:
 drop-shadow(0 0 5px #45ff82)
 drop-shadow(0 0 10px #45ff82)
}

.controls{
 display:grid;
 grid-template-columns:1fr auto;
 gap:10px;
 margin-top:14px
}

input{
 width:100%;
 min-height:50px;
 border-radius:12px;
 border:1px solid #28633d;
 background:#041009;
 color:white;
 padding:12px;
 font-size:17px;
 outline:none
}

button{
 min-height:50px;
 padding:0 25px;
 border:0;
 border-radius:12px;
 background:linear-gradient(135deg,#16b957,#45ff82);
 color:#03200d;
 font-size:16px;
 font-weight:bold;
 cursor:pointer
}

button:disabled{
 opacity:.45;
 cursor:not-allowed
}

.quota{
 text-align:center;
 margin-top:10px;
 color:#9fb9a9;
 font-size:13px
}

.quota b{
 color:#6cff9b
}

.history{
 margin-top:16px;
 border-top:1px solid #17472a;
 padding-top:12px
}

.history-title{
 color:#9db9a7;
 font-size:13px;
 margin-bottom:8px
}

.pills{
 display:flex;
 gap:7px;
 flex-wrap:wrap
}

.pill{
 padding:6px 9px;
 border-radius:8px;
 background:#091a10;
 border:1px solid #204b30;
 color:#b8d6c2;
 font-size:12px
}

@media(max-width:520px){
 .game{
  margin:8px;
  padding:12px
 }

 .chart{
  height:270px
 }

 .multiplier{
  font-size:45px
 }

 .controls{
  grid-template-columns:1fr
 }

 button{
  width:100%
 }
}
</style>
</head>

<body>

<div class="game">

<div class="top">
 <div class="badge">● حالت آزمایشی — بدون پول واقعی</div>

 <div class="balance">
 موجودی مجازی:
 <strong id="balance">$0.001</strong>
 </div>
</div>

<div class="chart">

 <div class="grid"></div>

 <svg viewBox="0 0 700 330"
      preserveAspectRatio="none">

  <path id="mainLine"
        class="main-line"
        d="M0 285 C100 283 180 275 260 260"/>

  <circle id="mainDot"
          class="main-dot"
          cx="20"
          cy="285"
          r="7"/>
 </svg>

 <!-- شعله متحرک در نوک خط -->
 <div id="flame" class="flame"></div>

 <div id="multiplier" class="multiplier">
  1.00x
 </div>

 <div id="status" class="status">
  برای شروع راند دکمه را بزنید
 </div>

</div>

<div class="money-panel">

 <div class="money-title">
  <span>حرکت موجودی دلار مجازی</span>
  <span class="money-value" id="moneyValue">$0.001</span>
 </div>

 <div class="money-chart">

  <svg viewBox="0 0 700 70"
       preserveAspectRatio="none">

   <path id="moneyLine"
         class="money-line"
         d="M0 55"/>
  </svg>

 </div>
</div>

<div class="controls">

 <input id="bet"
        type="number"
        min="0.05"
        step="0.01"
        value="0.05"
        placeholder="مبلغ مجازی">

 <button id="start">
  شروع راند
 </button>

</div>

<div class="quota">
 سهمیه آزمایشی کاربر:
 <b>$0.001</b>
</div>

<div class="history">

 <div class="history-title">
  راندهای قبلی
 </div>

 <div id="history" class="pills">
  <span class="pill">
   هنوز راندی ثبت نشده
  </span>
 </div>

</div>

</div>

<script>

const startButton =
 document.getElementById("start");

const betInput =
 document.getElementById("bet");

const multiplier =
 document.getElementById("multiplier");

const statusText =
 document.getElementById("status");

const mainLine =
 document.getElementById("mainLine");

const mainDot =
 document.getElementById("mainDot");

const flame =
 document.getElementById("flame");

const balanceElement =
 document.getElementById("balance");

const moneyValue =
 document.getElementById("moneyValue");

const moneyLine =
 document.getElementById("moneyLine");

const historyElement =
 document.getElementById("history");

let balance = 0.001;
let running = false;
let animationFrame = null;
let history = [];


/* نمایش موجودی */
function showBalance(value){

 const safe =
   Math.max(0,value);

 balanceElement.textContent =
   "$"+safe.toFixed(4);

 moneyValue.textContent =
   "$"+safe.toFixed(4);
}


/*
   تابع اصلی راند

   مدت راند عمداً طولانی‌تر شده
   و حرکت خط با easing نرم انجام می‌شود.
*/
function startRound(){

 if(running)return;

 const bet =
   Number(betInput.value);

 if(!Number.isFinite(bet) || bet < 0.05){

   statusText.textContent =
     "حداقل شرط مجازی ۰٫۰۵ است";

   return;
 }

 running = true;

 startButton.disabled = true;
 betInput.disabled = true;

 /*
    مدت زمان طولانی‌تر:
    خط خیلی آرام‌تر بالا می‌رود.
 */
 const duration =
   10000 + Math.random()*5000;

 /*
    ضریب انفجار برای دمو
 */
 const crash =
   1.35 + Math.random()*7;

 const startTime =
   performance.now();

 statusText.textContent =
   "ضریب در حال افزایش است...";


 function animate(now){

  if(!running)return;

  const raw =
    Math.min(
      (now-startTime)/duration,
      1
    );

  /*
     easing آهسته و نرم
  */
  const progress =
    raw*raw*(3-2*raw);

  /*
     ضریب
  */
  const current =
    1+(crash-1)*progress;

  multiplier.textContent =
    current.toFixed(2)+"x";


  /*
     محدوده کاملاً محدود شده:

     X هرگز از 650 عبور نمی‌کند.
     Y هرگز به بالاترین لبه نمی‌رسد.
  */

  const x =
    25 + 625*progress;

  const y =
    285 -
    225*Math.pow(progress,1.45);


  /*
     مسیر نرم
  */

  const control1X =
    x*0.35;

  const control2X =
    x*0.70;

  const control1Y =
    285 -
    25*progress;

  const control2Y =
    y+65;

  const path =
   `M25 285
    C${control1X} ${control1Y},
     ${control2X} ${control2Y},
     ${x} ${y}`;

  mainLine.setAttribute(
    "d",
    path
  );


  /*
     نقطه انتهای خط
  */

  mainDot.setAttribute(
    "cx",
    x
  );

  mainDot.setAttribute(
    "cy",
    y
  );


  /*
     شعله دقیقاً روی نوک خط
  */

  flame.style.left =
    ((x/700)*100)+"%";

  flame.style.top =
    ((y/330)*100)+"%";


  /*
     موجودی مجازی نمایشی
  */

  const virtualBalance =
    Math.max(
      0,
      balance-bet+
      bet*(current-1)*0.15
    );

  showBalance(
    virtualBalance
  );


  /*
     نمودار موجودی
  */

  const moneyX =
    700*progress;

  const moneyY =
    55-
    38*progress+
    Math.sin(progress*16)*3;

  moneyLine.setAttribute(
    "d",
    `M0 55
     C${moneyX*.35} 54,
      ${moneyX*.70} ${moneyY+15},
      ${moneyX} ${moneyY}`
  );


  /*
     ادامه حرکت
  */

  if(raw < 1){

    animationFrame =
      requestAnimationFrame(
        animate
      );

  }else{

    finishRound(crash);
  }
 }


 animationFrame =
   requestAnimationFrame(
     animate
   );
}


/* پایان راند */
function finishRound(crash){

 running = false;

 cancelAnimationFrame(
   animationFrame
 );

 /*
    خط در محدوده باقی می‌ماند
    و از نمودار خارج نمی‌شود.
 */

 multiplier.textContent =
   crash.toFixed(2)+"x";

 statusText.textContent =
   "💥 انفجار — راند تمام شد";

 /*
    شعله خاموش می‌شود.
 */

 flame.style.opacity =
   "0";

 history.unshift(
   crash.toFixed(2)+"x"
 );

 history =
   history.slice(0,8);

 historyElement.innerHTML =
   history.map(
    value =>
     `<span class="pill">${value}</span>`
   ).join("");

 setTimeout(
   resetRound,
   2000
 );
}


/* راند جدید */
function resetRound(){

 startButton.disabled = false;
 betInput.disabled = false;

 multiplier.textContent =
   "1.00x";

 statusText.textContent =
   "برای شروع راند دکمه را بزنید";

 mainLine.setAttribute(
   "d",
   "M25 285 C90 283 170 278 260 260"
 );

 mainDot.setAttribute(
   "cx",
   "25"
 );

 mainDot.setAttribute(
   "cy",
   "285"
 );

 flame.style.left =
   "3.5%";

 flame.style.top =
   "86%";

 flame.style.opacity =
   "1";

 moneyLine.setAttribute(
   "d",
   "M0 55"
 );

 showBalance(balance);
}


startButton.addEventListener(
 "click",
 startRound
);

resetRound();

</script>
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>USDT Wallet Demo</title>
<style>
body{
  margin:0;background:#07130d;color:#ecfff2;
  font-family:Tahoma,Arial,sans-serif
}
.container{max-width:650px;margin:25px auto;padding:15px}
.card{
  background:#0c2115;border:1px solid #205c35;
  border-radius:18px;padding:18px;margin-bottom:15px
}
h2{margin-top:0;color:#71ff9b}
label{display:block;margin:12px 0 6px;color:#aac7b5}
input{
  width:100%;box-sizing:border-box;padding:13px;
  border-radius:10px;border:1px solid #326d46;
  background:#061009;color:white;font-size:16px
}
button{
  margin-top:12px;width:100%;padding:13px;
  border:0;border-radius:10px;
  background:#32df72;color:#03200e;
  font-weight:bold;font-size:16px
}
.info{
  background:#071a0d;border:1px solid #174c2b;
  border-radius:10px;padding:12px;margin-top:12px;
  color:#9fc2aa
}
.hidden{display:none}
.request{
  background:#07170d;border:1px solid #1c4c2c;
  padding:12px;border-radius:10px;margin-top:8px
}
.small{font-size:12px;color:#8da99a}
.success{color:#6dff9a}
.error{color:#ff8585}
</style>
</head>

<body>
<div class="container">

<div class="card">
<h2>USDT Wallet</h2>

<div class="info">
شبکه: <b>BNB Smart Chain (BEP-20)</b><br>
حداقل واریز: <b>10 USDT</b><br>
حداقل برداشت: <b>100 USDT</b>
</div>
</div>

<div class="card">
<h2>واریز USDT</h2>

<label>مقدار واریز</label>
<input id="depositAmount" type="number" min="10" step="0.01"
       placeholder="حداقل 10 USDT">

<label>شناسه تراکنش / TXID</label>
<input id="depositTx" type="text"
       placeholder="برای نسخه آزمایشی">

<button onclick="submitDeposit()">ثبت واریز</button>

<div id="depositMessage"></div>
</div>

<div class="card">
<h2>برداشت USDT</h2>

<label>مقدار برداشت</label>
<input id="withdrawAmount" type="number" min="100" step="0.01"
       placeholder="حداقل 100 USDT">

<label>آدرس کیف پول BEP-20</label>
<input id="withdrawAddress" type="text"
       placeholder="0x...">

<button onclick="submitWithdraw()">ثبت درخواست برداشت</button>

<div id="withdrawMessage"></div>
</div>

<div class="card">
<h2>پنل مدیریت</h2>

<input id="adminPassword"
       type="password"
       placeholder="رمز مدیریت">

<button onclick="loginAdmin()">ورود به پنل</button>

<div id="adminPanel" class="hidden">

<h3>درخواست‌ها</h3>
<div id="requests"></div>

</div>
</div>

</div>

<script>

/*
 نسخه دمو:
 اطلاعات فقط در حافظه مرورگر نگهداری می‌شوند.
 برای استفاده واقعی باید احراز هویت، دیتابیس،
 کنترل دسترسی سمت سرور و ثبت سوابق تراکنش اضافه شود.
*/

const ADMIN_PASSWORD = "CHANGE_THIS_PASSWORD";

let requests = [];


/* ثبت واریز */
function submitDeposit(){

 const amount =
   Number(document.getElementById("depositAmount").value);

 const tx =
   document.getElementById("depositTx").value.trim();

 const msg =
   document.getElementById("depositMessage");

 if(!Number.isFinite(amount) || amount < 10){

   msg.className="error";
   msg.textContent="حداقل واریز 10 USDT است.";
   return;
 }

 if(!tx){

   msg.className="error";
   msg.textContent="شناسه تراکنش را وارد کنید.";
   return;
 }

 requests.push({
   type:"deposit",
   amount:amount,
   tx:tx,
   status:"در انتظار بررسی"
 });

 msg.className="success";
 msg.textContent="درخواست واریز ثبت شد.";

 renderRequests();
}


/* ثبت برداشت */
function submitWithdraw(){

 const amount =
   Number(document.getElementById("withdrawAmount").value);

 const address =
   document.getElementById("withdrawAddress").value.trim();

 const msg =
   document.getElementById("withdrawMessage");

 if(!Number.isFinite(amount) || amount < 100){

   msg.className="error";
   msg.textContent="حداقل برداشت 100 USDT است.";
   return;
 }

 if(!address){

   msg.className="error";
   msg.textContent="آدرس کیف پول را وارد کنید.";
   return;
 }

 if(!/^0x[a-fA-F0-9]{40}$/.test(address)){

   msg.className="error";
   msg.textContent="فرمت آدرس BEP-20 صحیح نیست.";
   return;
 }

 requests.push({
   type:"withdraw",
   amount:amount,
   address:address,
   status:"در انتظار پرداخت"
 });

 msg.className="success";
 msg.textContent="درخواست برداشت ثبت شد.";

 renderRequests();
}


/* ورود مدیر */
function loginAdmin(){

 const password =
   document.getElementById("adminPassword").value;

 if(password !== ADMIN_PASSWORD){

   alert("رمز اشتباه است.");
   return;
 }

 document
   .getElementById("adminPanel")
   .classList.remove("hidden");

 renderRequests();
}


/* نمایش درخواست‌ها */
function renderRequests(){

 const box =
   document.getElementById("requests");

 if(!box)return;

 if(requests.length === 0){

   box.innerHTML =
     "<p class='small'>درخواستی وجود ندارد.</p>";

   return;
 }

 box.innerHTML = requests.map((r,i)=>{

   if(r.type === "deposit"){

     return `
       <div class="request">
         <b>واریز</b><br>
         مقدار: ${r.amount} USDT<br>
         TXID: ${escapeHtml(r.tx)}<br>
         وضعیت: ${r.status}

         <button onclick="setStatus(${i},'تأیید شد')">
           تأیید
         </button>

         <button onclick="setStatus(${i},'رد شد')">
           رد
         </button>
       </div>
     `;
   }

   return `
     <div class="request">
       <b>برداشت</b><br>
       مقدار: ${r.amount} USDT<br>
       آدرس: ${escapeHtml(r.address)}<br>
       وضعیت: ${r.status}

       <button onclick="setStatus(${i},'پرداخت شد')">
         ثبت به‌عنوان پرداخت‌شده
       </button>

       <button onclick="setStatus(${i},'رد شد')">
         رد درخواست
       </button>
     </div>
   `;

 }).join("");
}


/* تغییر وضعیت */
function setStatus(index,status){

 requests[index].status = status;

 renderRequests();
}


/* جلوگیری از تزریق HTML */
function escapeHtml(value){

 return String(value)
   .replaceAll("&","&amp;")
   .replaceAll("<","&lt;")
   .replaceAll(">","&gt;")
   .replaceAll('"',"&quot;")
   .replaceAll("'","&#039;");
}

</script>

</body>
</html>
```

</body>
</html>
```
