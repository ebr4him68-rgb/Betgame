
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Crash Game</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    background:
        radial-gradient(circle at top,#063d24,#02150d 65%);
    color:white;
    font-family:Tahoma,Arial,sans-serif;
}

.container{
    width:95%;
    max-width:900px;
    margin:20px auto;
}

/* HEADER */

.header{
    background:#041f14;
    border:1px solid #20ff82;
    border-radius:20px;
    padding:18px;
    text-align:center;
    box-shadow:0 0 30px rgba(0,255,120,.18);
}

.logo{
    color:#39ff91;
    font-size:28px;
    font-weight:bold;
}

/* BALANCE */

.balance-box{
    margin-top:15px;
    background:linear-gradient(135deg,#073e25,#052717);
    border:2px solid #28ff8a;
    border-radius:20px;
    text-align:center;
    padding:20px;
    box-shadow:0 0 25px rgba(0,255,120,.15);
}

.balance-title{
    color:#a7ffd0;
    font-size:15px;
}

.balance{
    margin-top:5px;
    color:#42ff98;
    font-size:42px;
    font-weight:bold;
    direction:ltr;
    text-shadow:0 0 15px rgba(50,255,140,.45);
}

.currency{
    color:#fff;
    font-size:19px;
}

/* GAME */

.game{
    position:relative;
    margin-top:18px;
    height:360px;
    overflow:hidden;
    background:
        linear-gradient(rgba(40,255,140,.07) 1px,transparent 1px),
        linear-gradient(90deg,rgba(40,255,140,.07) 1px,transparent 1px),
        #03180e;
    background-size:45px 45px;
    border:2px solid #176d43;
    border-radius:20px;
}

.multiplier{
    position:absolute;
    z-index:5;
    left:50%;
    top:38%;
    transform:translate(-50%,-50%);
    font-size:65px;
    font-weight:bold;
    color:#45ff99;
    text-shadow:0 0 25px rgba(40,255,130,.65);
    direction:ltr;
}

.waiting{
    position:absolute;
    left:50%;
    top:62%;
    transform:translateX(-50%);
    color:#8ec8a9;
    font-size:14px;
}

/* SVG */

svg{
    position:absolute;
    width:100%;
    height:100%;
    left:0;
    bottom:0;
}

#crashLine{
    fill:none;
    stroke:#29ff83;
    stroke-width:6;
    stroke-linecap:round;
    stroke-linejoin:round;
    filter:drop-shadow(0 0 8px #29ff83);
}

#area{
    fill:rgba(22,255,120,.08);
    stroke:none;
}

/* FIRE */

.fire{
    position:absolute;
    width:20px;
    height:32px;
    display:none;
    z-index:8;
    transform:translate(-50%,-85%);
}

.fire:before{
    content:"";
    position:absolute;
    width:18px;
    height:28px;
    background:#ff8c00;
    border-radius:60% 40% 60% 40%;
    transform:rotate(45deg);
    box-shadow:
        0 0 8px #ff7b00,
        0 0 20px #ff4500;
}

.fire:after{
    content:"";
    position:absolute;
    width:9px;
    height:16px;
    background:#fff36b;
    border-radius:60% 40% 60% 40%;
    transform:rotate(45deg);
    left:5px;
    top:8px;
}

/* CONTROL */

.control{
    margin-top:18px;
    background:#041f14;
    border:1px solid #155d38;
    border-radius:20px;
    padding:18px;
}

label{
    display:block;
    color:#a9eac5;
    margin-bottom:7px;
}

input{
    width:100%;
    background:#020e08;
    color:white;
    border:1px solid #217b4b;
    border-radius:11px;
    padding:14px;
    font-size:18px;
    outline:none;
    direction:ltr;
    text-align:center;
}

input:focus{
    border-color:#36ff91;
}

button{
    width:100%;
    padding:15px;
    border:0;
    border-radius:12px;
    margin-top:10px;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
}

.start{
    background:#18dc73;
    color:#00170b;
}

.start:hover{
    background:#45ff99;
}

.cashout{
    background:#ffb51b;
    color:#211500;
    display:none;
    box-shadow:0 0 18px rgba(255,180,20,.25);
}

.cashout:hover{
    background:#ffc94c;
}

.status{
    text-align:center;
    min-height:25px;
    margin-top:12px;
    color:#9ee8bb;
}

/* HISTORY */

.history{
    margin-top:18px;
    background:#041f14;
    border:1px solid #155d38;
    border-radius:20px;
    padding:18px;
}

.history h3{
    margin-top:0;
    color:#3dff94;
}

.history-list{
    display:flex;
    flex-wrap:wrap;
    gap:8px;
}

.round{
    padding:8px 12px;
    border-radius:8px;
    background:#09291a;
    color:#54ff9a;
    direction:ltr;
}

.round.crashed{
    color:#ff6f78;
}

/* MOBILE */

@media(max-width:600px){

    .balance{
        font-size:34px;
    }

    .multiplier{
        font-size:48px;
    }

    .game{
        height:320px;
    }
}

.note{
    text-align:center;
    color:#6f9e84;
    font-size:11px;
    margin:18px 0;
}
</style>
</head>

<body>

<div class="container">

    <div class="header">
        <div class="logo">🔥 CRASH GAME</div>
        <div style="color:#9bdcb6;margin-top:6px">
            بازی انفجار مجازی
        </div>
    </div>

    <!-- BALANCE -->

    <div class="balance-box">

        <div class="balance-title">
            موجودی شما
        </div>

        <div class="balance">
            $<span id="balance">1000.00</span>
        </div>

        <div class="currency">
            دلار مجازی
        </div>

    </div>


    <!-- GAME -->

    <div class="game">

        <div id="multiplier"
             class="multiplier">
            1.00x
        </div>

        <div id="waiting"
             class="waiting">
            مبلغ شرط را وارد کنید و شروع را بزنید
        </div>

        <svg viewBox="0 0 900 360"
             preserveAspectRatio="none">

            <polygon id="area"
                     points="0,340 0,340">
            </polygon>

            <polyline id="crashLine"
                      points="0,340 0,340">
            </polyline>

        </svg>

        <div id="fire"
             class="fire">
        </div>

    </div>


    <!-- CONTROL -->

    <div class="control">

        <label>
            مبلغ شرط
        </label>

        <input
            id="bet"
            type="number"
            min="0.05"
            step="0.01"
            value="5"
            placeholder="مثلاً 5 دلار"
        >

        <button
            id="startBtn"
            class="start"
            onclick="startGame()">

            🚀 شروع بازی

        </button>

        <button
            id="cashoutBtn"
            class="cashout"
            onclick="cashOut()">

            💰 برداشت دستی

        </button>

        <div id="status"
             class="status">
        </div>

    </div>


    <!-- HISTORY -->

    <div class="history">

        <h3>
            تاریخچه ضرایب
        </h3>

        <div
            id="history"
            class="history-list">
        </div>

    </div>


    <div class="note">
        این نسخه صرفاً یک بازی مجازی/آزمایشی است و انتقال یا پرداخت واقعی دلار انجام نمی‌دهد.
    </div>

</div>


<script>

let balance = 1000.00;

let playing = false;
let cashedOut = false;

let betAmount = 0;
let multiplier = 1;

let startTime = 0;
let animationFrame;

let crashPoint = 2.5;


/* ELEMENTS */

const balanceEl =
    document.getElementById("balance");

const multiplierEl =
    document.getElementById("multiplier");

const statusEl =
    document.getElementById("status");

const waitingEl =
    document.getElementById("waiting");

const startBtn =
    document.getElementById("startBtn");

const cashoutBtn =
    document.getElementById("cashoutBtn");

const line =
    document.getElementById("crashLine");

const area =
    document.getElementById("area");

const fire =
    document.getElementById("fire");

const historyEl =
    document.getElementById("history");


/* BALANCE */

function updateBalance(){

    balanceEl.innerText =
        balance.toFixed(2);

}


/* RANDOM CRASH */

function generateCrashPoint(){

    /*
      فقط برای بازی آزمایشی.
      ضریب پایان هر دور به صورت تصادفی
      تولید می‌شود.
    */

    let r = Math.random();

    if(r < 0.20)
        return 1.10 + Math.random() * 0.40;

    if(r < 0.50)
        return 1.50 + Math.random() * 1.20;

    if(r < 0.80)
        return 2.70 + Math.random() * 2.50;

    return 5 + Math.random() * 6;

}


/* START */

function startGame(){

    if(playing)
        return;

    betAmount =
        Number(
            document.getElementById("bet").value
        );

    if(!betAmount || betAmount < 0.05){

        alert("حداقل مبلغ شرط 0.05 دلار است.");
        return;
    }

    if(betAmount > balance){

        alert("موجودی کافی نیست.");
        return;
    }


    /* کم کردن شرط */

    balance -= betAmount;

    updateBalance();


    /* GAME STATE */

    playing = true;
    cashedOut = false;

    multiplier = 1;

    crashPoint =
        generateCrashPoint();

    startTime =
        performance.now();


    startBtn.style.display =
        "none";

    cashoutBtn.style.display =
        "block";

    waitingEl.innerText =
        "ضریب در حال افزایش است...";

    statusEl.innerText =
        "در هر لحظه می‌توانید برداشت کنید.";

    fire.style.display =
        "block";


    animate();

}


/* ANIMATION */

function animate(){

    if(!playing)
        return;


    const elapsed =
        performance.now() - startTime;


    /*
      رشد آرام ضریب
    */

    multiplier =
        1 + Math.pow(elapsed / 10000, 1.35);


    if(multiplier >= crashPoint){

        multiplier =
            crashPoint;

        updateGraph();

        crash();

        return;
    }


    multiplierEl.innerText =
        multiplier.toFixed(2) + "x";


    updateGraph();

    animationFrame =
        requestAnimationFrame(animate);

}


/* GRAPH */

function updateGraph(){

    const width = 900;
    const height = 360;

    /*
      مسیر خط تا قبل از لبه متوقف می‌شود
    */

    let progress =
        Math.min(
            (multiplier - 1) / 6,
            .88
        );


    let x =
        25 + progress * 760;

    let y =
        330 -
        progress * 260;


    let points =
        "0,340 " +
        "25,330 " +
        x.toFixed(1) + "," +
        y.toFixed(1);


    line.setAttribute(
        "points",
        points
    );


    area.setAttribute(
        "points",
        points + " " +
        x.toFixed(1) + ",340"
    );


    /*
      جای آتش
    */

    fire.style.left =
        (x / 900 * 100) + "%";

    fire.style.top =
        (y / 360 * 100) + "%";


    multiplierEl.innerText =
        multiplier.toFixed(2) + "x";

}


/* CASH OUT */

function cashOut(){

    if(!playing || cashedOut)
        return;


    cashedOut = true;

    playing = false;

    cancelAnimationFrame(
        animationFrame
    );


    /*
      مبلغ دریافتی
    */

    let win =
        betAmount * multiplier;


    balance += win;

    updateBalance();


    statusEl.innerHTML =
        "✅ برداشت شد: <b>$" +
        win.toFixed(2) +
        "</b> در ضریب " +
        multiplier.toFixed(2) +
        "x";


    waitingEl.innerText =
        "برداشت موفق";


    cashoutBtn.style.display =
        "none";

    startBtn.style.display =
        "block";

    fire.style.display =
        "none";


    addHistory(
        multiplier,
        false
    );

}


/* CRASH */

function crash(){

    playing = false;

    cancelAnimationFrame(
        animationFrame
    );


    statusEl.innerHTML =
        "💥 انفجار در " +
        crashPoint.toFixed(2) +
        "x — شرط این دور از بین رفت.";


    waitingEl.innerText =
        "انفجار!";


    fire.style.display =
        "block";


    cashoutBtn.style.display =
        "none";

    startBtn.style.display =
        "block";


    addHistory(
        crashPoint,
        true
    );

}


/* HISTORY */

function addHistory(
    value,
    crashed
){

    const item =
        document.createElement("div");

    item.className =
        "round" +
        (crashed ? " crashed" : "");

    item.innerText =
        value.toFixed(2) + "x";

    historyEl.prepend(item);


    /*
      فقط 12 نتیجه آخر
    */

    while(
        historyEl.children.length > 12
    ){

        historyEl.removeChild(
            historyEl.lastChild
        );

    }

}


/* INITIAL */

updateBalance();

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
