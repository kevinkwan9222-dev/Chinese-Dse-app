<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HKDSE 中文範文溫習測驗網</title>
    <style>
        :root {
            --primary-color: #1a252f;
            --accent-color: #c0392b;
            --bg-color: #f0f2f5;
            --card-bg: #ffffff;
            --text-color: #2c3e50;
        }

        /* Full Screen Responsive Layout */
        * {
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Microsoft JhengHei", sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            width: 100vw;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .app-header {
            background-color: var(--primary-color);
            color: white;
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .app-header h1 {
            margin: 0;
            font-size: 20px;
        }

        .app-body {
            flex: 1;
            padding: 30px;
            max-width: 1400px;
            width: 100%;
            margin: 0 auto;
        }

        .hidden { display: none !important; }

        /* Auth Screen Centering */
        .auth-container {
            max-width: 450px;
            margin: 60px auto;
            background: var(--card-bg);
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }

        /* Countdown & Banner */
        .timer-box {
            background: white;
            border-left: 6px solid var(--accent-color);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 25px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .timer-title {
            font-size: 18px;
            font-weight: bold;
            color: var(--primary-color);
        }

        .timer-display {
            font-size: 26px;
            font-weight: bold;
            color: var(--accent-color);
            font-family: monospace;
        }

        .quote-box {
            background-color: #fff8f8;
            border: 1px solid #f5c6cb;
            padding: 15px 20px;
            margin-bottom: 25px;
            font-style: italic;
            border-radius: 8px;
            font-size: 16px;
        }

        .quote-author {
            text-align: right;
            font-weight: bold;
            margin-top: 8px;
            font-style: normal;
            color: var(--accent-color);
        }

        /* Chapter Grid Selector Box */
        .chapters-container {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 2px 12px rgba(0,0,0,0.06);
            margin-bottom: 30px;
        }

        .chapters-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }

        .chapter-card {
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chapter-card:hover {
            border-color: var(--primary-color);
            background: #ffffff;
            transform: translateY(-2px);
        }

        .chapter-card.selected {
            border-color: var(--accent-color);
            background: #fff5f5;
        }

        .chapter-card .title {
            font-weight: bold;
            font-size: 15px;
        }

        .chapter-card .badge {
            background: var(--primary-color);
            color: white;
            font-size: 12px;
            padding: 4px 8px;
            border-radius: 12px;
            white-space: nowrap;
        }

        /* Form elements & buttons */
        .form-group { margin-bottom: 20px; }

        label { display: block; margin-bottom: 8px; font-weight: bold; }

        input[type="text"], input[type="password"], textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 15px;
        }

        textarea { resize: vertical; height: 100px; }

        .btn {
            padding: 14px 24px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s;
        }

        .btn:hover { opacity: 0.9; }
        .btn-accent { background-color: var(--accent-color); }
        .btn-block { width: 100%; }

        /* Quiz UI */
        .quiz-container {
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .quiz-question {
            margin-bottom: 30px;
            border-bottom: 1px solid #eee;
            padding-bottom: 20px;
        }

        .type-badge {
            display: inline-block;
            background-color: #34495e;
            color: white;
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 4px;
            margin-right: 8px;
        }

        .option-label {
            display: block;
            padding: 12px;
            margin: 8px 0;
            background: #f8f9fa;
            border: 1px solid #ddd;
            border-radius: 6px;
            cursor: pointer;
        }

        .option-label:hover { background: #e9ecef; }

        .score-display {
            font-size: 28px;
            text-align: center;
            font-weight: bold;
            color: var(--accent-color);
            margin: 20px 0;
        }

        .result-item {
            background: #f8f9fa;
            border-left: 5px solid var(--primary-color);
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 0 6px 6px 0;
        }
    </style>
</head>
<body>

    <header class="app-header">
        <h1>HKDSE 中文 12 篇指定範文專用測驗平台</h1>
        <div id="user-controls" class="hidden">
            <span>歡迎，<strong id="user-display"></strong>！</span>
            <button class="btn" style="padding:6px 12px; margin-left:15px; background:#7f8c8d;" onclick="logout()">登出</button>
        </div>
    </header>

    <div class="app-body">

        <!-- Auth View -->
        <div id="auth-view" class="auth-container">
            <h2 id="auth-title" style="text-align: center; margin-top:0;">用戶登入</h2>
            <div class="form-group">
                <label for="username">用戶名稱</label>
                <input type="text" id="username" placeholder="請輸入名字">
            </div>
            <div class="form-group">
                <label for="password">密碼</label>
                <input type="password" id="password" placeholder="請輸入密碼">
            </div>
            <button class="btn btn-block" id="auth-btn" onclick="handleAuth()">登入</button>
            <p style="text-align:center; margin-top:15px;">
                <a href="#" id="auth-toggle" onclick="toggleAuthMode(event)">沒有帳戶？按此註冊</a>
            </p>
        </div>

        <!-- Main View -->
        <div id="main-view" class="hidden">

            <!-- Countdown Timer -->
            <div class="timer-box">
                <div class="timer-title">⏳ 距離 2027 年 4 月 8 日 HKDSE 中文科開考倒數：</div>
                <div class="timer-display" id="countdown">載入中...</div>
            </div>

            <!-- Quote Box -->
            <div class="quote-box">
                「以前既我將鄉寫做鄉下，而家既我識將鄉寫做以往啦！全靠呢個網站！」
                <div class="quote-author">— 楊愷輝</div>
            </div>

            <!-- Single Box For All Chapters -->
            <div class="chapters-container">
                <h2 style="margin-top: 0;">選擇練習章節 (每章獨立 40 題庫)</h2>
                <p style="color: #666;">點擊選擇指定章節進行針對性練習，或選擇「全部 12 章混合練習」：</p>
                
                <div class="chapters-grid" id="chapters-grid">
                    <!-- Cards rendered by JS -->
                </div>
            </div>

            <div style="text-align: center;">
                <button class="btn btn-accent" style="font-size: 20px; padding: 16px 40px;" onclick="startQuiz()">開始隨機 10 題測驗</button>
            </div>
        </div>

        <!-- Quiz View -->
        <div id="quiz-view" class="hidden class-container quiz-container">
            <h2 id="quiz-header-title">範文測試中</h2>
            <form id="quiz-form"></form>
            <button class="btn btn-accent btn-block" onclick="submitQuiz()">提交答案</button>
        </div>

        <!-- Result View -->
        <div id="result-view" class="hidden quiz-container">
            <h2>測驗結果與參考答案</h2>
            <div class="score-display" id="score-text"></div>
            <div id="result-details"></div>
            <button class="btn btn-block" onclick="showMainView()">返回主頁</button>
        </div>

    </div>

<script>
    // Countdown Timer logic for 8/4/2027
    const targetDate = new Date("2027-04-08T08:30:00").getTime();

    function updateCountdown() {
        const now = new Date().getTime();
        const distance = targetDate - now;

        if (distance < 0) {
            document.getElementById("countdown").innerHTML = "DSE 中文科開考中！加油！";
            return;
        }

        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distance % (1000 * 60)) / 1000);

        document.getElementById("countdown").innerHTML = `${days} 天 ${hours} 小時 ${minutes} 分 ${seconds} 秒`;
    }
    setInterval(updateCountdown, 1000);
    updateCountdown();

    // 12 Chapter Titles
    const chapterTitles = [
        "《論仁、論孝、論君子》", "《魚我所欲也》", "《逍遙遊》", "《勸學》",
        "《廉頗藺相如列傳》", "《出師表》", "《師說》", "《始得西山宴遊記》",
        "《岳陽樓記》", "《六國論》", "唐詩三首", "詞三首"
    ];

    // Dynamic 40-question generator for each specific chapter
    function generate40QuestionsForChapter(chapterName) {
        const qList = [];
        for (let i = 1; i <= 40; i++) {
            const remainder = i % 3;
            if (remainder === 1) {
                qList.push({
                    chapter: chapterName,
                    type: "MC",
                    q: `[${chapterName}] 選擇題 ${i}: 下列哪項最能精準解釋文中核心關鍵字詞或意旨？`,
                    options: [`正確解析 A (第 ${i} 題)`, `錯誤選項 B`, `錯誤選項 C`, `錯誤選項 D`],
                    a: 0,
                    explanation: "選項 A 精確對應課文原意。"
                });
            } else if (remainder === 2) {
                const isTrue = i % 2 === 0;
                qList.push({
                    chapter: chapterName,
                    type: "TF",
                    q: `[${chapterName}] 是非題 ${i}: 關於文中此處句式結構或推論敘述「重點 ${i}」是否正確？`,
                    options: ["正確 (True)", "錯誤 (False)"],
                    a: isTrue ? 0 : 1,
                    explanation: `本題敘述為 ${isTrue ? "正確" : "錯誤"}。`
                });
            } else {
                qList.push({
                    chapter: chapterName,
                    type: "LQ",
                    q: `[${chapterName}] 問答題 ${i}: 請結合課文全文，分析作者如何運用相關寫作手法以達至其論點或抒情目的？`,
                    modelAnswer: `參考答案 (${i})：作者善用對比、借景抒情及層遞推進手法，深層演繹了文章中心哲理。`
                });
            }
        }
        return qList;
    }

    // Build database separated by chapters
    const chapterData = {};
    chapterTitles.forEach(title => {
        chapterData[title] = generate40QuestionsForChapter(title);
    });

    let selectedChapter = "ALL"; // Default to All
    let isSignup = false;
    let currentUser = null;
    let currentQuizQuestions = [];

    // Render Chapters Grid
    function renderChapterGrid() {
        const grid = document.getElementById('chapters-grid');
        grid.innerHTML = '';

        // "ALL" Option Card
        const allCard = document.createElement('div');
        allCard.className = `chapter-card ${selectedChapter === 'ALL' ? 'selected' : ''}`;
        allCard.onclick = () => selectChapter('ALL');
        allCard.innerHTML = `<span class="title">🌟 全部 12 章 (混合練習)</span> <span class="badge">480 題庫</span>`;
        grid.appendChild(allCard);

        // Individual Chapter Cards
        chapterTitles.forEach(title => {
            const card = document.createElement('div');
            card.className = `chapter-card ${selectedChapter === title ? 'selected' : ''}`;
            card.onclick = () => selectChapter(title);
            card.innerHTML = `<span class="title">${title}</span> <span class="badge">40 題庫</span>`;
            grid.appendChild(card);
        });
    }

    function selectChapter(title) {
        selectedChapter = title;
        renderChapterGrid();
    }

    // Auth Handling
    window.onload = function() {
        renderChapterGrid();
        const savedUser = localStorage.getItem('dse_quiz_current_user');
        if (savedUser) {
            currentUser = savedUser;
            showMainView();
        }
    };

    function toggleAuthMode(e) {
        e.preventDefault();
        isSignup = !isSignup;
        document.getElementById('auth-title').innerText = isSignup ? "用戶註冊" : "用戶登入";
        document.getElementById('auth-btn').innerText = isSignup ? "註冊" : "登入";
        document.getElementById('auth-toggle').innerText = isSignup ? "已有帳戶？按此登入" : "沒有帳戶？按此註冊";
    }

    function handleAuth() {
        const userIn = document.getElementById('username').value.trim();
        const passIn = document.getElementById('password').value.trim();

        if (!userIn || !passIn) {
            alert("請填寫用戶名稱和密碼！");
            return;
        }

        let users = JSON.parse(localStorage.getItem('dse_quiz_users') || '{}');

        if (isSignup) {
            if (users[userIn]) {
                alert("該用戶名稱已被註冊！");
            } else {
                users[userIn] = passIn;
                localStorage.setItem('dse_quiz_users', JSON.stringify(users));
                alert("註冊成功，請登入！");
                toggleAuthMode(new Event('click'));
            }
        } else {
            if (users[userIn] && users[userIn] === passIn) {
                currentUser = userIn;
                localStorage.setItem('dse_quiz_current_user', currentUser);
                showMainView();
            } else {
                alert("用戶名稱或密碼錯誤！");
            }
        }
    }

    function logout() {
        localStorage.removeItem('dse_quiz_current_user');
        currentUser = null;
        document.getElementById('user-controls').classList.add('hidden');
        document.getElementById('auth-view').classList.remove('hidden');
        document.getElementById('main-view').classList.add('hidden');
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.add('hidden');
    }

    function showMainView() {
        document.getElementById('user-display').innerText = currentUser;
        document.getElementById('user-controls').classList.remove('hidden');
        document.getElementById('auth-view').classList.add('hidden');
        document.getElementById('main-view').classList.remove('hidden');
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.add('hidden');
    }

    // Start quiz pulling 10 random questions from the selected pool
    function startQuiz() {
        let pool = [];
        if (selectedChapter === 'ALL') {
            Object.keys(chapterData).forEach(key => {
                pool = pool.concat(chapterData[key]);
            });
        } else {
            pool = [...chapterData[selectedChapter]];
        }

        const shuffled = pool.sort(() => 0.5 - Math.random());
        currentQuizQuestions = shuffled.slice(0, 10);

        document.getElementById('quiz-header-title').innerText = selectedChapter === 'ALL' ? "全篇章混合測試中" : `${selectedChapter} 專修測試中`;

        const form = document.getElementById('quiz-form');
        form.innerHTML = '';

        currentQuizQuestions.forEach((item, qIndex) => {
            const qDiv = document.createElement('div');
            qDiv.className = 'quiz-question';
            
            let badgeText = item.type === "MC" ? "選擇題" : (item.type === "TF" ? "是非題" : "問答題");
            let html = `<p><span class="type-badge">${badgeText}</span><strong>${qIndex + 1}. ${item.q}</strong></p>`;
            
            if (item.type === "MC" || item.type === "TF") {
                html += `<div class="options-group">`;
                item.options.forEach((opt, oIndex) => {
                    html += `
                        <label class="option-label">
                            <input type="radio" name="q${qIndex}" value="${oIndex}" required>
                            ${opt}
                        </label>
                    `;
                });
                html += '</div>';
            } else {
                html += `
                    <div class="form-group">
                        <textarea name="q${qIndex}" placeholder="請在此輸入你的作答..." required></textarea>
                    </div>
                `;
            }

            qDiv.innerHTML = html;
            form.appendChild(qDiv);
        });

        document.getElementById('main-view').classList.add('hidden');
        document.getElementById('quiz-view').classList.remove('hidden');
    }

    function submitQuiz() {
        const form = document.getElementById('quiz-form');
        const formData = new FormData(form);
        let mcTfScore = 0;
        let mcTfTotal = 0;

        const resultDetails = document.getElementById('result-details');
        resultDetails.innerHTML = '';

        for (let i = 0; i < currentQuizQuestions.length; i++) {
            const item = currentQuizQuestions[i];
            const answer = formData.get(`q${i}`);

            if (answer === null || answer.trim() === '') {
                alert("請填寫所有問題後再提交！");
                return;
            }

            const itemDiv = document.createElement('div');
            itemDiv.className = 'result-item';

            if (item.type === "MC" || item.type === "TF") {
                mcTfTotal++;
                const isCorrect = parseInt(answer) === item.a;
                if (isCorrect) mcTfScore++;

                itemDiv.innerHTML = `
                    <p><strong>${i + 1}. ${item.q}</strong></p>
                    <p>你的答案：${item.options[parseInt(answer)]} 
                       <span style="color:${isCorrect ? 'green' : 'red'}; font-weight:bold;">
                          ${isCorrect ? '✓ 正確' : '✗ 錯誤'}
                       </span>
                    </p>
                    <p style="color:#555;">正確答案：${item.options[item.a]} (${item.explanation})</p>
                `;
            } else {
                itemDiv.innerHTML = `
                    <p><strong>${i + 1}. ${item.q}</strong></p>
                    <p>你的作答：${answer}</p>
                    <p style="color:#27ae60;"><strong>${item.modelAnswer}</strong></p>
                `;
            }
            resultDetails.appendChild(itemDiv);
        }

        document.getElementById('score-text').innerText = `客觀題得分：${mcTfScore} / ${mcTfTotal}`;
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.remove('hidden');
    }
</script>

</body>
</html>
