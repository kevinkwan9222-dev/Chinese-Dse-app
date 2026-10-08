<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HKDSE 中文範文溫習測驗網</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --accent-color: #c0392b;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --text-color: #333;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Microsoft JhengHei", sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            width: 100%;
            max-width: 850px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .hidden { display: none !important; }

        h1, h2, h3 { color: var(--primary-color); text-align: center; }

        /* Countdown Box Styling */
        .timer-box {
            background: #eef2f7;
            border: 2px solid var(--primary-color);
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            margin-bottom: 20px;
        }

        .timer-title {
            font-size: 16px;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 5px;
        }

        .timer-display {
            font-size: 24px;
            font-weight: bold;
            color: var(--accent-color);
            font-family: monospace;
        }

        .quote-box {
            background-color: #f1f2f6;
            border-left: 5px solid var(--accent-color);
            padding: 15px 20px;
            margin: 20px 0;
            font-style: italic;
            border-radius: 4px;
        }

        .quote-author {
            text-align: right;
            font-weight: bold;
            margin-top: 8px;
            font-style: normal;
        }

        .form-group { margin-bottom: 15px; }

        label { display: block; margin-bottom: 5px; font-weight: bold; }

        input[type="text"], input[type="password"], textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
        }

        textarea { resize: vertical; height: 80px; }

        button {
            width: 100%;
            padding: 12px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            cursor: pointer;
            transition: background 0.2s;
            margin-top: 10px;
        }

        button:hover { background-color: #1a252f; }

        .chapter-list {
            list-style-type: none;
            padding: 0;
        }

        .chapter-list li {
            padding: 10px 14px;
            background: #edf2f7;
            margin-bottom: 8px;
            border-radius: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chapter-badge {
            background: var(--primary-color);
            color: white;
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 12px;
        }

        .quiz-question {
            margin-bottom: 25px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }

        .type-badge {
            display: inline-block;
            background-color: #e0e0e0;
            color: #333;
            font-size: 12px;
            padding: 2px 6px;
            border-radius: 4px;
            margin-right: 6px;
        }

        .option-label {
            display: block;
            padding: 8px;
            margin: 5px 0;
            background: #f8f9fa;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
        }

        .option-label:hover { background: #e9ecef; }

        .score-display {
            font-size: 24px;
            text-align: center;
            font-weight: bold;
            color: var(--accent-color);
            margin: 20px 0;
        }

        .result-item {
            background: #f8f9fa;
            border-left: 4px solid var(--primary-color);
            padding: 10px 15px;
            margin-bottom: 15px;
            border-radius: 0 4px 4px 0;
        }

        .nav-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- Auth View -->
    <div id="auth-view">
        <h1 id="auth-title">用戶登入</h1>
        <div class="form-group">
            <label for="username">用戶名稱</label>
            <input type="text" id="username" placeholder="請輸入名字">
        </div>
        <div class="form-group">
            <label for="password">密碼</label>
            <input type="password" id="password" placeholder="請輸入密碼">
        </div>
        <button id="auth-btn" onclick="handleAuth()">登入</button>
        <p style="text-align:center; margin-top:15px;">
            <a href="#" id="auth-toggle" onclick="toggleAuthMode(event)">沒有帳戶？按此註冊</a>
        </p>
    </div>

    <!-- Main View -->
    <div id="main-view" class="hidden">
        <div class="nav-bar">
            <span>歡迎，<strong id="user-display"></strong>！</span>
            <button onclick="logout()" style="width:auto; margin:0; padding: 6px 12px; background:#7f8c8d;">登出</button>
        </div>

        <h1>HKDSE 中文 12 篇指定範文測驗</h1>

        <!-- Countdown Timer -->
        <div class="timer-box">
            <div class="timer-title">⏳ 距離 2027 年 4 月 8 日 HKDSE 中文科開考倒數：</div>
            <div class="timer-display" id="countdown">載入中...</div>
        </div>

        <div class="quote-box">
            「以前既我將鄉寫做鄉下，而家既我識將鄉寫做以往啦！全靠呢個網站！」
            <div class="quote-author">— 楊愷輝</div>
        </div>

        <h3>範文章節列表 (每章題庫共 40 題)：</h3>
        <ul class="chapter-list">
            <li>《論仁、論孝、論君子》（《論語》） <span class="chapter-badge">40 題</span></li>
            <li>《魚我所欲也》（孟子） <span class="chapter-badge">40 題</span></li>
            <li>《逍遙遊（節錄）》（莊子） <span class="chapter-badge">40 題</span></li>
            <li>《勸學（節錄）》（荀子） <span class="chapter-badge">40 題</span></li>
            <li>《廉頗藺相如列傳（節錄）》（司馬遷） <span class="chapter-badge">40 題</span></li>
            <li>《出師表》（諸葛亮） <span class="chapter-badge">40 題</span></li>
            <li>《師說》（韓愈） <span class="chapter-badge">40 題</span></li>
            <li>《始得西山宴遊記》（柳宗元） <span class="chapter-badge">40 題</span></li>
            <li>《岳陽樓記》（范仲淹） <span class="chapter-badge">40 題</span></li>
            <li>《六國論》（蘇洵） <span class="chapter-badge">40 題</span></li>
            <li>唐詩三首：王維《山居秋暝》、李白《月下獨酌》、杜甫《登樓》 <span class="chapter-badge">40 題</span></li>
            <li>詞三首：蘇軾《念奴嬌》、李清照《聲聲慢》、辛棄疾《青玉案》 <span class="chapter-badge">40 題</span></li>
        </ul>

        <button onclick="startQuiz()" style="background-color: var(--accent-color); font-size: 18px;">開始測驗（隨機 10 題：MC / 是非 / 長題目）</button>
    </div>

    <!-- Quiz View -->
    <div id="quiz-view" class="hidden">
        <h2>範文測試中</h2>
        <form id="quiz-form"></form>
        <button onclick="submitQuiz()">提交答案</button>
    </div>

    <!-- Result View -->
    <div id="result-view" class="hidden">
        <h2>測驗結果與參考答案</h2>
        <div class="score-display" id="score-text"></div>
        <div id="result-details"></div>
        <button onclick="showMainView()">返回主頁</button>
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

    // Utility: Generator for 40 questions per chapter dynamically
    function generate40Questions(chapterName) {
        const qList = [];
        for (let i = 1; i <= 40; i++) {
            const remainder = i % 3;
            if (remainder === 1) {
                // Multiple Choice Question (MC)
                qList.push({
                    type: "MC",
                    q: `[${chapterName}] 選擇題 ${i}: 關於文章的核心思想或詞語解釋，下列哪項正確？`,
                    options: [`正確答案 A (${i})`, `錯誤選項 B`, `錯誤選項 C`, `錯誤選項 D`],
                    a: 0,
                    explanation: "正確答案是第一個選項。"
                });
            } else if (remainder === 2) {
                // True/False Question (TF)
                const isTrue = i % 2 === 0;
                qList.push({
                    type: "TF",
                    q: `[${chapterName}] 是非題 ${i}: 文章中提及的觀點「敘述 ${i}」是否符合原意？`,
                    options: ["正確 (True)", "錯誤 (False)"],
                    a: isTrue ? 0 : 1,
                    explanation: `本題陳述為 ${isTrue ? "正確" : "錯誤"}。`
                });
            } else {
                // Long Question (LQ)
                qList.push({
                    type: "LQ",
                    q: `[${chapterName}] 問答題 ${i}: 請結合文章內容，簡述作者於此段落所運用之寫作手法及表達的情感。（自由作答）`,
                    modelAnswer: `參考答案 (${i})：作者運用了對比與層遞手法，藉由具體事物的描繪，表達出深沉的家國情懷或哲理反思。`,
                    type_label: "問答題"
                });
            }
        }
        return qList;
    }

    // 12 Chapters Titles
    const chapters = [
        "《論仁、論孝、論君子》", "《魚我所欲也》", "《逍遙遊》", "《勸學》",
        "《廉頗藺相如列傳》", "《出師表》", "《師說》", "《始得西山宴遊記》",
        "《岳陽樓記》", "《六國論》", "唐詩三首", "詞三首"
    ];

    // Build overall question bank (12 chapters * 40 questions = 480 questions total)
    let fullQuestionBank = [];
    chapters.forEach(ch => {
        fullQuestionBank = fullQuestionBank.concat(generate40Questions(ch));
    });

    let isSignup = false;
    let currentUser = null;
    let currentQuizQuestions = [];

    // Auth logic with LocalStorage
    window.onload = function() {
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
        document.getElementById('auth-view').classList.remove('hidden');
        document.getElementById('main-view').classList.add('hidden');
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.add('hidden');
    }

    function showMainView() {
        document.getElementById('user-display').innerText = currentUser;
        document.getElementById('auth-view').classList.add('hidden');
        document.getElementById('main-view').classList.remove('hidden');
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.add('hidden');
    }

    // Start Quiz with 10 random questions from full pool
    function startQuiz() {
        const shuffled = [...fullQuestionBank].sort(() => 0.5 - Math.random());
        currentQuizQuestions = shuffled.slice(0, 10);

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
                // Long Question Textarea
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

    // Submit and Evaluate Quiz
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
                alert("請完成所有題目後再提交！");
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
                // Long question display
                itemDiv.innerHTML = `
                    <p><strong>${i + 1}. ${item.q}</strong></p>
                    <p>你的作答：${answer}</p>
                    <p style="color:#27ae60;"><strong>${item.modelAnswer}</strong></p>
                `;
            }
            resultDetails.appendChild(itemDiv);
        }

        document.getElementById('score-text').innerText = `客觀題（MC/是非題）得分：${mcTfScore} / ${mcTfTotal} (長題目請參考下方參考答案對對)`;
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.remove('hidden');
    }
</script>

</body>
</html>
