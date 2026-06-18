<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SPORTY FIXED GAMES</title>
    <script src="https://js.paystack.co/v1/inline.js"></script>
    <style>
        :root {
            /* Liquid Glass Palette */
            --bg-liquid: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #020617 100%);
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.1);
            --accent-gold: #ffcc00;
            --accent-green: #00ff88;
            --text-bright: #ffffff;
            --text-dim: #949ba4;
            /* Premium gold/yellow gradient globally */
            --btn-gradient: linear-gradient(180deg, #f39c12, #d35400);
        }

        body {
            background: var(--bg-liquid);
            background-attachment: fixed; /* Keeps the "liquid" still while scrolling */
            color: var(--text-bright);
            font-family: 'Inter', -apple-system, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        .container { 
            width: 92%; 
            max-width: 480px; 
            padding-bottom: 120px;
        }

        .header {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            padding: 50px 0 10px 0;
        }

        .logo-main {
            font-size: 2.5rem;
            font-weight: 900;
            margin: 0;
            color: #fff;
            letter-spacing: -1px;
            text-transform: uppercase;
            text-shadow: 0 10px 20px rgba(0,0,0,0.5);
        }

        .logo-highlight { color: var(--accent-gold); }

        .logo-sub {
            font-size: 1rem;
            font-weight: 700;
            color: var(--accent-green);
            letter-spacing: 6px;
            text-transform: uppercase;
            margin-top: 2px;
            display: block;
        }

        .animation-container {
            width: 100%;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 10px 0;
        }

        .track-line {
            width: 80%;
            height: 2px;
            background: rgba(255, 255, 255, 0.1);
            position: relative;
            border-radius: 2px;
        }

        .animated-ball {
            width: 12px;
            height: 12px;
            background: linear-gradient(45deg, var(--accent-gold), var(--accent-green));
            border-radius: 50%;
            position: absolute;
            top: -5px;
            left: 0;
            box-shadow: 0 0 15px var(--accent-green), 0 0 5px white;
            animation: moveBall 2.5s infinite ease-in-out;
        }

        @keyframes moveBall {
            0% { left: 0%; transform: scale(1); }
            50% { left: 100%; transform: translateX(-12px) scale(1.2); }
            100% { left: 0%; transform: scale(1); }
        }

        .section-title {
            font-size: 0.9rem;
            font-weight: 800;
            margin: 15px 0 15px 5px;
            color: var(--accent-gold);
            text-transform: uppercase;
            letter-spacing: 1px;
            text-align: center;
        }

        /* Glassmorphism Cards with Premium Gold Theme applied globally */
        .match-card {
            background: linear-gradient(145deg, rgba(255, 255, 255, 0.02) 0%, rgba(255, 204, 0, 0.02) 100%);
            backdrop-filter: blur(12px); /* The "Glass" effect */
            -webkit-backdrop-filter: blur(12px);
            border-radius: 24px;
            padding: 24px;
            margin-bottom: 20px;
            border: 1px solid var(--accent-gold); /* Unified gold border for all boxes */
            box-shadow: 0 8px 32px 0 rgba(255, 204, 0, 0.15);
        }

        .badge-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .vip-badge {
            background: #27ae60;
            color: #fff;
            font-size: 0.65rem;
            padding: 4px 10px;
            border-radius: 4px;
            font-weight: 900;
            text-transform: uppercase;
        }

        .league-label {
            font-size: 0.7rem;
            color: var(--accent-green);
            font-weight: 700;
            text-transform: uppercase;
            display: block;
            margin-bottom: 5px;
            text-align: center;
        }

        .teams {
            font-size: 1.2rem;
            font-weight: 800;
            margin-bottom: 25px;
            text-align: center;
            color: #fff;
        }

        .result-row {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 10px;
            background: rgba(0,0,0,0.2);
            padding: 15px 10px;
            border-radius: 16px;
            margin-top: 5px;
        }

        .result-item { text-align: center; }

        .result-item b { 
            font-size: 1rem; 
            color: var(--accent-green); 
            display: block;
            margin-top: 5px;
        }

        .result-label { 
            font-size: 0.6rem; 
            color: var(--text-dim); 
            display: block; 
            text-transform: uppercase;
            font-weight: 700;
        }

        .status-won { color: var(--accent-gold) !important; }

        .unlock-btn {
            background: var(--btn-gradient);
            color: white;
            border: none;
            border-radius: 16px;
            padding: 18px;
            width: 100%;
            font-size: 1rem;
            font-weight: 800;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(243, 156, 18, 0.3);
        }

        .bottom-nav {
            position: fixed;
            bottom: 25px;
            width: 90%;
            max-width: 420px;
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            display: flex;
            justify-content: space-around;
            padding: 15px 0;
            border-radius: 28px;
            border: 1px solid var(--glass-border);
        }

        .nav-item { color: var(--text-dim); text-align: center; font-size: 0.75rem; cursor: pointer; }
        .nav-item.active { color: var(--accent-green); font-weight: bold; }
        .hidden { display: none; }
    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1 class="logo-main">Score <span class="logo-highlight"> X </span></h1>
        <span class="logo-sub"> Fixed </span>
    </div>

    <div class="animation-container">
        <div class="track-line">
            <div class="animated-ball"></div>
        </div>
    </div>

    <div id="home-page">
        <div class="section-title">Today's Certified Games</div>
        <div id="today-container"></div>
    </div>

    <div id="results-page" class="hidden">
        <div class="section-title">VERIFIED WINNINGS (YESTERDAY)</div>
        <div id="yesterday-container"></div>
    </div>
</div>

<nav class="bottom-nav">
    <div class="nav-item active" onclick="showPage('home')">🏠<br>Games</div>
    <div class="nav-item" id="results-btn" onclick="showPage('results')">🏆<br>History</div>
    <div class="nav-item" onclick="showPage('home')">💳<br>Payment</div>
</nav>

<script>
    // Paste your brand new public key inside the single quotes below:
    const PAYSTACK_PUBLIC_KEY = pk_live_96a553401ff040dedd4cd39a82aa594eb5cf68bc'; 

    const todayVips = [
        { league: "LEBANON PREMIER LEAGUE-ROUND 17", time: "18:30", home: "Nejmeh SC", away: "AL Ahed", badge: "Direct Source ✅", dataValue: "1 - 3", price: 100, isPremium: false },
        { league: "IRELAND: PREMIER-DIVISION 20", time: "18:45", home: "Waterford", away: "Sligo Rovers", badge: "Insider Fixed ✅", dataValue: "0 - 2", price: 100, isPremium: false },
        // Updated dataValue placeholder with booking code DTHFS0
        { league: "FIFA WORLD CUP", time: "20:00", home: "World Cup Bonanza 🏆🔥", away: "BIG ODDS ⭐", badge: "SPECIAL", dataValue: "BOOKING CODE - DTHFS0", price: 200, isPremium: true }
    ];

    const pastWinnings = [
        { league: "USA: USL LEAGUE ONE", home: "Boise", away: "Richmond Kickers", picked: "2 - 1", outcome: "2 - 1", status: "WON✅" },
        { league: "KAZAKHSTAN: FIRST LEAGUE-ROUND 9", home: "Aktobe 2", away: "Akademiya Ontustik", picked: "1 - 4", outcome: "1 - 4", status: "WON✅" }
    ];

    function showPage(page) {
        document.getElementById('home-page').classList.toggle('hidden', page !== 'home');
        document.getElementById('results-page').classList.toggle('hidden', page !== 'results');
        document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
        if(page === 'home') document.querySelectorAll('.nav-item')[0].classList.add('active');
        else document.getElementById('results-btn').classList.add('active');
    }

    function renderContent() {
        const todayDiv = document.getElementById('today-container');
        todayDiv.innerHTML = todayVips.map(m => {
            const displayTitle = m.isPremium ? `${m.home}` : `${m.home} vs ${m.away}`;
            return `
                <div class="match-card">
                    <div class="badge-container">
                        <span class="vip-badge" style="background:#ffcc00; color:#000;">${m.badge}</span>
                        <span style="font-size: 0.75rem; color: var(--text-dim)">${m.time} GMT</span>
                    </div>
                    <div class="league-label">${m.league}</div>
                    <div class="teams">${displayTitle}</div>
                    <button class="unlock-btn" onclick="payWithPaystack('${displayTitle}', '${m.dataValue}', ${m.price}, ${m.isPremium})">
                        Access ${m.isPremium ? 'Booking Code' : 'Correct Score'} — ${m.price} GHS
                    </button>
                </div>
            `;
        }).join('');

        const yesterdayDiv = document.getElementById('yesterday-container');
        yesterdayDiv.innerHTML = pastWinnings.map(m => `
            <div class="match-card">
                <div class="badge-container">
                    <span class="vip-badge">✅ VERIFIED</span>
                    <span style="font-size: 0.65rem; color: var(--text-dim)">Final Result</span>
                </div>
                <div class="league-label">${m.league}</div>
                <div class="teams">${m.home} vs ${m.away}</div>
                <div class="result-row">
                    <div class="result-item">
                        <span class="result-label">Picked Score</span>
                        <b>${m.picked}</b>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Outcome</span>
                        <b>${m.outcome}</b>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Status</span>
                        <b class="status-won">${m.status}</b>
                    </div>
                </div>
            </div>
        `).join('');
    }

    function payWithPaystack(matchName, secureData, priceAmount, isPremiumGame) {
        let totalAmount = priceAmount * 100;

        let handler = PaystackPop.setup({
            key: PAYSTACK_PUBLIC_KEY,
            email: 'vip@sportyfixed.com', 
            amount: totalAmount, 
            currency: 'GHS',
            callback: function(response) {
                if (isPremiumGame) {
                    // Automatically copies the booking code directly to user clipboard
                    navigator.clipboard.writeText(secureData).then(() => {
                        alert('Payment Confirmed! \n\nBooking Code for ' + matchName + ': \n' + secureData + '\n\nThe code has been copied to your clipboard!');
                    }).catch(err => {
                        // Fallback message if browser clipboards access gets denied
                        alert('Payment Confirmed! \n\nBooking Code for ' + matchName + ': \n' + secureData + '\n\nHighlight text above to copy.');
                    });
                } else {
                    alert('Payment Confirmed! \n\nCorrect Score for ' + matchName + ': ' + secureData);
                }
            }
        });
        handler.openIframe();
    }

    window.onload = renderContent;
</script>

</body>
</html>
