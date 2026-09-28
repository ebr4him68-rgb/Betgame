# Betgame
GAME BET90
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Crash Demo</title>

<style>
*{box-sizing:border-box}

body{
    margin:0;
    font-family:Tahoma,Arial,sans-serif;
    background:#020805;
    color:#ecfff2;
}

.game{
    max-width:760px;
    margin:20px auto;
    padding:18px;
    background:linear-gradient(145deg,#06110a,#0b2113);
    border:1px solid #195b31;
    border-radius:22px;
}

.top{
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:10px;
    flex-wrap:wrap;
    margin-bottom:14px;
}

.badge{
    padding:8px 13px;
    border-radius:20px;
    background:#082817;
    border:1px solid #287542;
    color:#7cffaa;
    font-size:13px;
}

.balance{
    color:#b8cdbf;
    font-size:14px;
}

.balance strong{
    color:#61ff96;
    font-size:18px;
}

/* نمودار اصلی */
.chart{
    position:relative;
    height:330px;
    overflow:hidden;
    border-radius:18px;
    background:
      radial-gradient(circle at 50% 70%,
      rgba(40,255,110,.12),transparent 52%),
      #020603;
    border:1px solid #17472a;
}

.grid{
    position:absolute;
    inset:0;
    background-image:
      linear-gradient(rgba(60,255,120,.055) 1px,transparent 1px),
      linear-gradient(90deg,rgba(60,255,120,.055) 1px,transparent 1px);
    background-size:42px 42px;
}

svg{
    position:absolute;
    inset:0;
    width:100%;
    height:100%;
}

.main-line{
    fill:none;
    stroke:#39ff79;
    stroke-width:5;
    stroke-linecap:round;
    filter:
      drop-shadow(0 0 5px #39ff79)
      drop-shadow(0 0 14px #39ff79);
}

.main-dot{
    fill:#d5ffe2;
    filter:
      drop-shadow(0 0 6px #39ff79)
      drop-shadow(0 0 18px #39ff79);
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
}

.status{
    position:absolute;
    bottom:12px;
    right:14px;
    color:#9bb8a5;
    font-size:13px;
}

/* موجودی متحرک */
.money-panel{
    margin-top:14px;
    padding:14px;
    border-radius:15px;
    background:#06130b;
    border:1px solid #16472a;
}

.money-title{
    display:flex;
    justify-content:space-between;
    margin-bottom:8px;
    color:#aac5b4;
    font-size:13px;
}

.money-value{
    color:#72ffa0;
    font-size:22px;
    font-weight:bold;
}

.money-chart{
    height:70px;
    position:relative;
    overflow:hidden;
    border-radius:10px;
    background:#030805;
}

.money-chart svg{
    width:100%;
    height:100%;
}

.money-line{
    fill:none;
    stroke:#45ff82;
    stroke-width:3;
    stroke-linecap:round;
    filter:
      drop-shadow(0 0 5px #45ff82)
      drop-shadow(0 0 10px #45ff82);
}

.controls{
    display:grid;
    grid-template-columns:1fr auto;
    gap:10px;
    margin-top:14px;
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
    outline:none;
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
    cursor:pointer;
    box-shadow:0 0 18px rgba(57,255,121,.25);
}

button:disabled{
    opacity:.45;
    cursor:not-allowed;
}

.quota{
    text-align:center;
    margin-top:10px;
    color:#9fb9a9;
    font-size:13px;
}

.quota b{
    color:#6cff9b;
}

.history{
    margin-top:16px;
    border-top:1px solid #17472a;
    padding-top:12px;
}

.history-title{
    color:#9db9a7;
    font-size:13px;
    margin-bottom:8px;
}

.pills{
    display:flex;
    gap:7px;
    flex-wrap:wrap;
}

.pill{
    padding:6px 9px;
    border-radius:8px;
    background:#091a10;
    border:1px solid #204b30;
    color:#b8d6c2;
    font-size:12px;
}

@media(max-width:520px){
    .game{
        margin:8px;
        padding:12px;
    }

    .chart{
        height:270px;
    }

    .multiplier{
        font-size:45px;
    }

    .controls{
        grid-template-columns:1fr;
    }

    button{
        width:100%;
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

    <!-- نمودار انفجار -->
    <div class="chart">

        <div class="grid"></div>

        <svg viewBox="0 0 700 330"
             preserveAspectRatio="none">

            <path id="mainLine"
                  class="main-line"
                  d="M0 290 C120 285 190 270 270 245 C380 210 450 180 540 125 C610 85 650 60 700 35"/>

            <circle id="mainDot"
                    class="main-dot"
                    cx="700"
                    cy="35"
                    r="7"/>
        </svg>

        <div id="multiplier" class="multiplier">
            1.00x
        </div>

        <div id="status" class="status">
            برای شروع راند دکمه را بزنید
        </div>

    </div>

    <!-- نمودار موجودی -->
    <div class="money-panel">

        <div class="money-title">
            <span>حرکت موجودی دلار مجازی</span>
            <span class="money-value" id="moneyValue">
                $0.001
            </span>
        </div>

        <div class="money-chart">

            <svg viewBox="0 0 700 70"
                 preserveAspectRatio="none">

                <path id="moneyLine"
                      class="money-line"
                      d="M0 48 L80 45 L150 50 L230 38 L310 43 L390 30 L470 34 L550 22 L630 28 L700 15"/>
            </svg>

        </div>

    </div>

    <div class="controls">

        <input
            id="bet"
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

const startButton = document.getElementById("start");
const betInput = document.getElementById("bet");

const multiplier = document.getElementById("multiplier");
const statusText = document.getElementById("status");

const mainLine = document.getElementById("mainLine");
const mainDot = document.getElementById("mainDot");

const balanceElement = document.getElementById("balance");
const moneyValue = document.getElementById("moneyValue");
const moneyLine = document.getElementById("moneyLine");

const historyElement = document.getElementById("history");

let balance = 0.001;
let running = false;
let animationFrame = null;
let history = [];


/* نمایش پول */
function showMoney(){

    const value = Math.max(0,balance);

    balanceElement.textContent =
        "$" + value.toFixed(4);

    moneyValue.textContent =
        "$" + value.toFixed(4);
}


/* انیمیشن تغییر موجودی */
function animateMoney(oldValue,newValue){

    const startTime = performance.now();
    const duration = 600;

    function frame(now){

        const progress =
            Math.min((now-startTime)/duration,1);

        const eased =
            progress * (2-progress);

        const value =
            oldValue + (newValue-oldValue)*eased;

        balanceElement.textContent =
            "$" + value.toFixed(4);

        moneyValue.textContent =
            "$" + value.toFixed(4);

        if(progress < 1){

            requestAnimationFrame(frame);

        }else{

            balance = newValue;
            showMoney();
        }
    }

    requestAnimationFrame(frame);
}


/* تغییر خط موجودی */
function updateMoneyGraph(progress,up){

    const x =
        Math.min(progress*700,700);

    let y;

    if(up){

        y =
            55 -
            (progress*40) +
            Math.sin(progress*18)*4;

    }else{

        y =
            25 +
            progress*30 +
            Math.sin(progress*18)*4;
    }

    const previousX =
        Math.max(0,x-100);

    const previousY =
        up ? y+18 : y-12;

    const path =
        `M0 55
         C${previousX/2} 52,
          ${previousX} ${previousY},
          ${x} ${y}`;

    moneyLine.setAttribute("d",path);
}


/* شروع راند */
function startRound(){

    if(running) return;

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
      نقطه انفجار کاملاً تصادفی
      و فقط برای شبیه‌سازی بازی است.
    */
    const crash =
        1.30 + Math.random()*7;

    const oldBalance =
        balance;

    const duration =
        4000 + Math.random()*2500;

    const startTime =
        performance.now();

    /*
      تغییر اولیه موجودی مجازی
    */
    let virtualBalance =
        Math.max(0,balance-bet);

    animateMoney(
        oldBalance,
        virtualBalance
    );

    function animate(now){

        if(!running) return;

        const progress =
            Math.min(
                (now-startTime)/duration,
                1
            );

        const eased =
            progress*progress*(3-2*progress);

        const current =
            1+(crash-1)*eased;

        multiplier.textContent =
            current.toFixed(2)+"x";

        /*
          حرکت خط سبز
        */
        const x =
            20 + 680*eased;

        const y =
            285 -
            245*Math.pow(eased,1.45);

        const curve =
            `M0 285
             C120 285 180 270 250 255
             C330 235 370 215 ${x-100} ${y+60}
             C${x-60} ${y+35} ${x-20} ${y+10} ${x} ${y}`;

        mainLine.setAttribute(
            "d",
            curve
        );

        mainDot.setAttribute(
            "cx",
            x
        );

        mainDot.setAttribute(
            "cy",
            y
        );

        /*
          خط موجودی همزمان حرکت می‌کند
        */
        updateMoneyGraph(
            progress,
            true
        );

        /*
          مقدار مجازی با افزایش ضریب رشد می‌کند
        */
        const liveBalance =
            virtualBalance +
            bet*(current-1)*0.25;

        balanceElement.textContent =
            "$"+Math.max(0,liveBalance).toFixed(4);

        moneyValue.textContent =
            "$"+Math.max(0,liveBalance).toFixed(4);

        if(progress < 1){

            animationFrame =
                requestAnimationFrame(animate);

        }else{

            finishRound(crash);
        }
    }

    animationFrame =
        requestAnimationFrame(animate);
}


/* پایان راند */
function finishRound(crash){

    running = false;

    cancelAnimationFrame(
        animationFrame
    );

    multiplier.textContent =
        crash.toFixed(2)+"x";

    statusText.textContent =
        "💥 انفجار — راند تمام شد";

    /*
      برای نمایش آزمایشی:
      موجودی دوباره مقدار پایه را نشان می‌دهد.
    */

    const finalBalance =
        Math.max(
            0,
            balance
        );

    animateMoney(
        finalBalance,
        finalBalance
    );

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

    setTimeout(resetRound,1800);
}


/* آماده‌سازی راند بعدی */
function resetRound(){

    startButton.disabled = false;
    betInput.disabled = false;

    multiplier.textContent =
        "1.00x";

    statusText.textContent =
        "برای شروع راند دکمه را بزنید";

    mainLine.setAttribute(
        "d",
        "M0 290 C120 285 190 270 270 245 C380 210 450 180 540 125 C610 85 650 60 700 35"
    );

    mainDot.setAttribute(
        "cx",
        "700"
    );

    mainDot.setAttribute(
        "cy",
        "35"
    );

    moneyLine.setAttribute(
        "d",
        "M0 48 L80 45 L150 50 L230 38 L310 43 L390 30 L470 34 L550 22 L630 28 L700 15"
    );

    showMoney();
}


/* کلیک شروع */
startButton.addEventListener(
    "click",
    startRound
);

showMoney();

</script>

</body>
</html>
