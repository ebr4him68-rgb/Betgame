برای بازی حساب خودرا حداقل ۱۰دلار شارژ کنید برداشتها حداکثر48ساعت ارسال میشوند


برای بازی ادرس USDTبربستر شبکه bep20وارد کنید و شروع کنید


<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Jungle Crash</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    min-height:100vh;
    font-family:Tahoma,Arial,sans-serif;

    /* زمینه زرد */
    background:
        radial-gradient(circle at top,#fff59d,#ffd52e 45%,#e5a900);

    color:#fff;
}

.container{
    width:94%;
    max-width:900px;
    margin:18px auto 40px;
}


/* =========================
   HEADER
========================= */

.header{
    background:#075c2b;
    border:3px solid #35ff8a;
    border-radius:22px;
    padding:18px;
    text-align:center;
    box-shadow:
        0 8px 25px rgba(0,0,0,.25),
        0 0 25px rgba(0,255,100,.25);
}

.logo{
    font-size:30px;
    font-weight:bold;
    color:#52ff9b;
}

.subtitle{
    margin-top:7px;
    color:#d8ffe8;
}


/* =========================
   BALANCE
========================= */

.balance-box{
    margin-top:15px;

    background:
        linear-gradient(
            145deg,
            #087536,
            #043d20
        );

    border:3px solid #43ff91;
    border-radius:22px;

    text-align:center;
    padding:20px;

    box-shadow:
        0 7px 22px rgba(0,0,0,.25),
        0 0 25px rgba(0,255,100,.2);
}

.balance-title{
    color:#caffdf;
    font-size:15px;
}

.balance{
    margin-top:5px;

    font-size:48px;
    font-weight:bold;

    color:#fff;

    direction:ltr;

    text-shadow:
        0 0 12px #00ff70;
}

.currency{
    color:#b9ffd4;
}


/* =========================
   GENERAL PANEL
========================= */

.panel{
    margin-top:17px;

    background:
        linear-gradient(
            145deg,
            #075a2b,
            #03401f
        );

    border:2px solid #20d86e;

    border-radius:20px;

    padding:18px;

    box-shadow:
        0 8px 25px rgba(0,0,0,.25);
}

.panel h2{
    margin-top:0;
    color:#45ff94;
}


/* =========================
   ACTIVATION
========================= */

.activation{
    border:2px solid #30ff87;
}

.activation-info{
    text-align:center;
    color:#c9ffe0;
    font-size:13px;
    line-height:1.8;
}

input{
    width:100%;

    padding:14px;

    margin-top:8px;

    border-radius:11px;

    border:2px solid #15944b;

    background:#022612;

    color:white;

    outline:none;

    font-size:16px;

    direction:ltr;

    text-align:center;
}

input:focus{
    border-color:#48ff99;
}


/* =========================
   BUTTONS
========================= */

button{
    width:100%;

    padding:15px;

    margin-top:10px;

    border:0;

    border-radius:12px;

    font-size:17px;

    font-weight:bold;

    cursor:pointer;

    transition:.2s;
}

button:hover{
    transform:translateY(-1px);
}

.green-btn{
    background:#22df76;
    color:#00210f;
}

.green-btn:hover{
    background:#49ff98;
}

.yellow-btn{
    background:#ffd129;
    color:#251c00;
}

.red-btn{
    background:#ff4b4b;
    color:white;
}

button:disabled{
    opacity:.45;
    cursor:not-allowed;
    transform:none;
}


/* =========================
   GAME PANEL
========================= */

.game-panel{
    padding:12px;

    background:#075e2d;

    border:3px solid #29ed79;
}


/* =========================
   FOREST GAME
========================= */

.game{

    position:relative;

    height:370px;

    overflow:hidden;

    border-radius:17px;

    border:2px solid #31ff86;

    /*
       جنگل
    */

    background:

        radial-gradient(
            ellipse at 50% 100%,
            rgba(72,155,62,.9) 0%,
            rgba(19,84,37,.85) 35%,
            rgba(3,35,17,.95) 75%
        ),

        linear-gradient(
            to bottom,
            #071e13,
            #0b4724
        );
}


/* مه جنگل */

.game:before{

    content:"";

    position:absolute;

    left:-20%;

    bottom:0;

    width:140%;

    height:45%;

    background:

        radial-gradient(
            ellipse,
            rgba(90,255,125,.14),
            transparent 65%
        );

    pointer-events:none;
}


/* درخت‌های تزئینی */

.tree{
    position:absolute;

    bottom:0;

    width:70px;

    height:180px;

    opacity:.5;
}

.tree:before{

    content:"";

    position:absolute;

    bottom:0;

    left:32px;

    width:12px;

    height:115px;

    background:#1a2a15;

    border-radius:10px;
}

.tree:after{

    content:"🌲";

    position:absolute;

    bottom:75px;

    left:0;

    font-size:85px;
}

.tree1{left:3%;}
.tree2{left:17%;transform:scale(.75);}
.tree3{right:5%;}
.tree4{right:19%;transform:scale(.7);}


/* =========================
   MULTIPLIER
========================= */

.multiplier{

    position:absolute;

    z-index:10;

    left:50%;

    top:37%;

    transform:
        translate(-50%,-50%);

    font-size:64px;

    font-weight:bold;

    color:#42ff96;

    direction:ltr;

    text-shadow:
        0 0 10px #00ff70,
        0 0 25px #00ff70,
        0 0 45px rgba(0,255,100,.5);
}

.waiting{

    position:absolute;

    z-index:10;

    left:50%;

    top:58%;

    transform:translateX(-50%);

    color:#c6ffda;

    font-size:14px;

    text-align:center;

    width:90%;
}


/* =========================
   SVG GRAPH
========================= */

svg{

    position:absolute;

    width:100%;

    height:100%;

    left:0;
    top:0;
}

#crashLine{

    fill:none;

    stroke:#39ff89;

    stroke-width:6;

    stroke-linecap:round;

    stroke-linejoin:round;

    filter:
        drop-shadow(0 0 8px #00ff6a);
}

#area{

    fill:
        rgba(30,255,110,.08);

    stroke:none;
}


/* =========================
   FIRE
========================= */

.fire{

    position:absolute;

    z-index:20;

    width:22px;

    height:34px;

    display:none;

    transform:
        translate(-50%,-80%);

    animation:
        fireMove .16s infinite alternate;
}

.fire:before{

    content:"🔥";

    position:absolute;

    font-size:30px;

    left:-5px;

    top:-5px;

    filter:
        drop-shadow(0 0 8px #ff8c00);
}

@keyframes fireMove{

    from{
        transform:
            translate(-50%,-80%)
            rotate(-4deg);
    }

    to{
        transform:
            translate(-50%,-84%)
            rotate(4deg);
    }
}


/* =========================
   BET
========================= */

.bet-title{
    color:#c7ffdc;
    margin-bottom:5px;
}

.bet-input{
    direction:ltr;
}


/* =========================
   STATUS
========================= */

.status{

    text-align:center;

    min-height:28px;

    margin-top:10px;

    color:#baffd1;

    line-height:1.7;
}


/* =========================
   HISTORY
========================= */

.history-list{

    display:flex;

    flex-wrap:wrap;

    gap:8px;
}

.round{

    background:#062c17;

    border:1px solid #20b961;

    border-radius:8px;

    padding:8px 12px;

    color:#52ff99;

    direction:ltr;
}

.round.crashed{

    color:#ff7777;

    border-color:#9e3535;
}


/* =========================
   SMALL
========================= */

.small{

    text-align:center;

    color:#a5d9b8;

    font-size:11px;

    line-height:1.8;

    margin-top:12px;
}


/* =========================
   MOBILE
========================= */

@media(max-width:600px){

    .balance{
        font-size:38px;
    }

    .multiplier{
        font-size:48px;
    }

    .game{
        height:320px;
    }
}
</style>
</head>


<body>

<div class="container">


    <!-- HEADER -->

    <div class="header">

        <div class="logo">
            🌲🔥 JUNGLE CRASH
        </div>

        <div class="subtitle">
            بازی انفجار مجازی
        </div>

    </div>


    <!-- BALANCE -->

    <div class="balance-box">

        <div class="balance-title">
            موجودی دلار مجازی
        </div>

        <div class="balance">
            $<span id="balance">0.00</span>
        </div>

        <div class="currency">
            USD Virtual
        </div>

    </div>


    <!-- ACTIVATION -->

    <div
        class="panel activation"
        id="activationBox">

        <h2>
            🔐 فعال‌سازی بازی
        </h2>

        <div class="activation-info">

            ابتدا آدرس USDT خود را وارد کنید.
            <br>

            پس از ثبت آدرس،
            <b>0.05 دلار مجازی</b>
            برای بازی فعال می‌شود.

        </div>

        <input
            id="userUsdtAddress"
            type="text"
            placeholder="آدرس USDT - BEP20"
            dir="ltr"
        >

        <button
            id="activateBtn"
            class="green-btn"
            onclick="activateGame()">

            ✅ ثبت آدرس و فعال‌سازی

        </button>

        <div
            id="activationMessage"
            class="status">
        </div>

        <div class="small">

            فقط آدرس عمومی کیف پول را وارد کنید.
            <br>
            Seed Phrase یا Private Key لازم نیست.

        </div>

    </div>


    <!-- GAME -->

    <div
        class="panel game-panel"
        id="gameSection"
        style="display:none">

        <div class="game">

            <div class="tree tree1"></div>
            <div class="tree tree2"></div>
            <div class="tree tree3"></div>
            <div class="tree tree4"></div>


            <div
                id="multiplier"
                class="multiplier">

                1.00x

            </div>


            <div
                id="waiting"
                class="waiting">

                مبلغ شرط را وارد کنید.

            </div>


            <svg
                viewBox="0 0 900 370"
                preserveAspectRatio="none">

                <polygon
                    id="area"
                    points="0,350 0,350">
                </polygon>

                <polyline
                    id="crashLine"
                    points="0,350 0,350">
                </polyline>

            </svg>


            <div
                id="fire"
                class="fire">
            </div>

        </div>


        <!-- GAME CONTROL -->

        <div class="panel">

            <div class="bet-title">
                مبلغ شرط
            </div>

            <input
                id="bet"
                class="bet-input"
                type="number"
                min="0.05"
                step="0.01"
                value="0.05"
            >


            <button
                id="startBtn"
                class="green-btn"
                onclick="startGame()">

                🚀 شروع بازی

            </button>


            <button
                id="cashoutBtn"
                class="yellow-btn"
                onclick="cashOut()"
                style="display:none">

                💰 برداشت دستی

            </button>


            <div
                id="status"
                class="status">
            </div>

        </div>


        <!-- HISTORY -->

        <div class="panel">

            <h2>
                📊 تاریخچه بازی
            </h2>

            <div
                id="history"
                class="history-list">
            </div>

        </div>

    </div>


    <div class="small">

        
        <br>
        ثبت آدرس USDT

    </div>

</div>


<script>

/* =========================
   VARIABLES
========================= */

let balance = 0;

let gameActivated = false;

let userUsdtAddress = "";

let playing = false;

let cashedOut = false;

let betAmount = 0;

let multiplier = 1;

let startTime = 0;

let animationFrame;

let crashPoint = 2.5;


/* =========================
   ELEMENTS
========================= */

const balanceEl =
    document.getElementById("balance");

const activationBox =
    document.getElementById("activationBox");

const gameSection =
    document.getElementById("gameSection");

const activationMessage =
    document.getElementById("activationMessage");

const multiplierEl =
    document.getElementById("multiplier");

const waitingEl =
    document.getElementById("waiting");

const statusEl =
    document.getElementById("status");

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


/* =========================
   BALANCE
========================= */

function updateBalance(){

    balanceEl.innerText =
        balance.toFixed(2);

}


/* =========================
   ACTIVATE
========================= */

function activateGame(){

    const input =
        document.getElementById(
            "userUsdtAddress"
        );

    const address =
        input.value.trim();


    /* BEP20 FORMAT */

    if(
        !/^0x[a-fA-F0-9]{40}$/.test(address)
    ){

        activationMessage.innerHTML =
            "❌ آدرس BEP-20 معتبر وارد کنید.";

        return;
    }


    userUsdtAddress =
        address;

    gameActivated =
        true;


    /*
       موجودی مجازی اولیه
    */

    balance =
        0.05;

    updateBalance();


    activationMessage.innerHTML =
        "✅ آدرس ثبت شد. موجودی مجازی $0.05 فعال شد.";


    input.readOnly =
        true;


    document.getElementById(
        "activateBtn"
    ).disabled =
        true;


    /*
       نمایش بازی
    */

    setTimeout(()=>{

        activationBox.style.display =
            "none";

        gameSection.style.display =
            "block";

    },700);

}


/* =========================
   CRASH POINT
========================= */

function generateCrashPoint(){

    let r =
        Math.random();


    if(r < .22){

        return (
            1.10 +
            Math.random() * .45
        );

    }


    if(r < .55){

        return (
            1.55 +
            Math.random() * 1.35
        );

    }


    if(r < .82){

        return (
            2.9 +
            Math.random() * 2.5
        );

    }


    return (
        5.4 +
        Math.random() * 5
    );

}


/* =========================
   START
========================= */

function startGame(){

    if(!gameActivated){

        alert(
            "ابتدا آدرس USDT را ثبت کنید."
        );

        return;
    }


    if(playing)
        return;


    betAmount =
        Number(
            document.getElementById(
                "bet"
            ).value
        );


    if(
        !betAmount ||
        betAmount < .05
    ){

        alert(
            "حداقل شرط 0.05 دلار است."
        );

        return;
    }


    if(
        betAmount > balance
    ){

        alert(
            "موجودی مجازی کافی نیست."
        );

        return;
    }


    /*
       کسر شرط
    */

    balance -=
        betAmount;

    updateBalance();


    playing =
        true;

    cashedOut =
        false;

    multiplier =
        1;

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


/* =========================
   ANIMATE
========================= */

function animate(){

    if(!playing)
        return;


    const elapsed =
        performance.now() -
        startTime;


    /*
       رشد آرام
    */

    multiplier =
        1 +
        Math.pow(
            elapsed / 10000,
            1.35
        );


    if(
        multiplier >=
        crashPoint
    ){

        multiplier =
            crashPoint;

        updateGraph();

        crash();

        return;
    }


    multiplierEl.innerText =
        multiplier.toFixed(2) +
        "x";


    updateGraph();


    animationFrame =
        requestAnimationFrame(
            animate
        );

}


/* =========================
   GRAPH
========================= */

function updateGraph(){

    let progress =
        Math.min(
            (multiplier - 1) / 6,
            .87
        );


    let x =
        25 +
        progress * 760;


    let y =
        340 -
        progress * 275;


    let points =
        "0,350 " +
        "25,340 " +
        x.toFixed(1) +
        "," +
        y.toFixed(1);


    line.setAttribute(
        "points",
        points
    );


    area.setAttribute(
        "points",
        points +
        " " +
        x.toFixed(1) +
        ",350"
    );


    /*
       آتش روی سر خط
    */

    fire.style.left =
        (x / 900 * 100) +
        "%";

    fire.style.top =
        (y / 370 * 100) +
        "%";


    multiplierEl.innerText =
        multiplier.toFixed(2) +
        "x";

}


/* =========================
   CASH OUT
========================= */

function cashOut(){

    if(
        !playing ||
        cashedOut
    )
        return;


    cashedOut =
        true;

    playing =
        false;


    cancelAnimationFrame(
        animationFrame
    );


    /*
       مبلغ برد
    */

    let win =
        betAmount *
        multiplier;


    balance +=
        win;


    updateBalance();


    statusEl.innerHTML =
        "✅ برداشت دستی انجام شد<br>" +
        "مبلغ: <b>$" +
        win.toFixed(4) +
        "</b><br>" +
        "ضریب: " +
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


/* =========================
   CRASH
========================= */

function crash(){

    playing =
        false;


    cancelAnimationFrame(
        animationFrame
    );


    statusEl.innerHTML =
        "💥 انفجار در " +
        crashPoint.toFixed(2) +
        "x";


    waitingEl.innerText =
        "انفجار!";


    cashoutBtn.style.display =
        "none";

    startBtn.style.display =
        "block";


    addHistory(
        crashPoint,
        true
    );

}


/* =========================
   HISTORY
========================= */

function addHistory(
    value,
    crashed
){

    const item =
        document.createElement(
            "div"
        );


    item.className =
        "round" +
        (
            crashed
            ? " crashed"
            : ""
        );


    item.innerText =
        value.toFixed(2) +
        "x";


    historyEl.prepend(
        item
    );


    while(
        historyEl.children.length >
        12
    ){

        historyEl.removeChild(
            historyEl.lastChild
        );

    }

}


/* =========================
   INIT
========================= */

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
