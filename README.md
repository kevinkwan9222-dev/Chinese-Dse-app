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
            max-width: 800px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .hidden {
            display: none !important;
        }

        h1, h2, h3 {
            color: var(--primary-color);
            text-align: center;
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

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
        }

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

        button:hover {
            background-color: #1a252f;
        }

        .chapter-list {
            list-style-type: none;
            padding: 0;
        }

        .chapter-list li {
            padding: 8px 12px;
            background: #edf2f7;
            margin-bottom: 6px;
            border-radius: 4px;
        }

        .quiz-question {
            margin-bottom: 25px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }

        .options-group {
            margin-top: 10px;
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

        .option-label:hover {
            background: #e9ecef;
        }

        .score-display {
            font-size: 24px;
            text-align: center;
            font-weight: bold;
            color: var(--accent-color);
            margin: 20px 0;
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

        <div class="quote-box">
            「以前既我將鄉寫做鄉下，而家既我識將鄉寫做以往啦！全靠呢個網站！」
            <div class="quote-author">— 楊愷輝</div>
        </div>

        <h3>涵蓋範文章節：</h3>
        <ul class="chapter-list">
            <li>《論仁、論孝、論君子》（《論語》）</li>
            <li>《魚我所欲也》（孟子）</li>
            <li>《逍遙遊（節錄）》（莊子）</li>
            <li>《勸學（節錄）》（荀子）</li>
            <li>《廉頗藺相如列傳（節錄）》（司馬遷）</li>
            <li>《出師表》（諸葛亮）</li>
            <li>《師說》（韓愈）</li>
            <li>《始得西山宴遊記》（柳宗元）</li>
            <li>《岳陽樓記》（范仲淹）</li>
            <li>《六國論》（蘇洵）</li>
            <li>唐詩三首：王維《山居秋暝》、李白《月下獨酌（其一）》、杜甫《登樓》</li>
            <li>詞三首：蘇軾《念奴嬌．赤壁懷古》、李清照《聲聲慢．秋情》、辛棄疾《青玉案．元夕》</li>
        </ul>

        <button onclick="startQuiz()" style="background-color: var(--accent-color); font-size: 18px;">開始測驗（隨機 10 題）</button>
    </div>

    <!-- Quiz View -->
    <div id="quiz-view" class="hidden">
        <h2>範文測試中</h2>
        <form id="quiz-form"></form>
        <button onclick="submitQuiz()">提交答案</button>
    </div>

    <!-- Result View -->
    <div id="result-view" class="hidden">
        <h2>測驗結果</h2>
        <div class="score-display" id="score-text"></div>
        <button onclick="showMainView()">返回主頁</button>
    </div>

</div>

<script>
    // Mock Database containing 40 sample DSE Chinese standard passage questions
    const questionBank = [
        { q: "《論語》中「克己復禮為仁」，「克己」的意思是什麼？", options: ["克制自己的欲望", "克服艱難險阻", "嚴格要求他人", "克服自己的缺點"], a: 0 },
        { q: "《論語》中「君子喻於義，小人喻於利」，「喻」字解作什麼？", options: ["比喻", "明白 / 理解", "宣導", "告知"], a: 1 },
        { q: "孟子在《魚我所欲也》中，以「魚」比喻什麼？", options: ["禮義", "富貴", "生命", "欲望"], a: 2 },
        { q: "《魚我所欲也》中「萬鍾則不辯禮義而受之」，「萬鍾」代表什麼？", options: ["優厚的俸祿", "極高的官位", "大量的糧食", "許多的時間"], a: 0 },
        { q: "《逍遙遊》中，大鵬鳥徙於南冥時，「水擊」多少里？", options: ["三千里", "八千里", "九萬里", "五千里"], a: 0 },
        { q: "《逍遙遊》中，莊子認為「蜩與學鳩」笑大鵬鳥，是因為牠們：", options: ["目光短淺，眼界狹隘", "性格驕傲自滿", "嫉妒大鵬鳥的能力", "不喜歡遠行"], a: 0 },
        { q: "《勸學》中「青，取之於藍，而青於藍」是用來比喻什麼？", options: ["後天學習能超越原本的基礎", "藍色的染料比青色好", "學習需要選擇適當的環境", "顏色會隨時間轉變"], a: 0 },
        { q: "《勸學》中「積土成山，風雨興焉；積水成淵，膠龍生焉」說明了什麼道理？", options: ["環境對人的影響", "累積學習的重要性", "自然的客觀規律", "志向遠大的好處"], a: 1 },
        { q: "《廉頗藺相如列傳》中，藺相如在「完壁歸趙」事件中表現出什麼性格？", options: ["勇而有謀，臨危不屈", "功高蓋主，目中無人", "顧全大局，屈己讓人", "猶豫不決，聽天由命"], a: 0 },
        { q: "《廉頗藺相如列傳》中，藺相如避讓廉頗，最主要的考量是什麼？", options: ["害怕廉頗的武藝", "避免兩虎相爭，以國家安全為先", "等待皇帝調解", "討好其他官員"], a: 1 },
        { q: "諸葛亮在《出師表》中建議後主劉禪「宜自廣開張」，意思是指：", options: ["廣開財源", "廣泛聽取臣子的意見", "擴張國家版圖", "增加軍隊人數"], a: 1 },
        { q: "《出師表》中「親賢臣，遠小人」，諸葛亮指出這是哪個時期興隆的原因？", options: ["先漢（西漢）", "後漢（東漢）", "三國時期", "魏晉時期"], a: 0 },
        { q: "韓愈《師說》中，定義「師」的作用是：", options: ["傳道、受業、解惑", "教授考試技巧", "監督學生品德", "糾正社會風氣"], a: 0 },
        { q: "《師說》中「聖人無常師」，韓愈舉出了哪位古代聖賢作為例子？", options: ["孔子", "孟子", "老子", "荀子"], a: 0 },
        { q: "柳宗元《始得西山宴遊記》中「始得」二字反映出什麼感情變化？", options: ["由憂鬱鬱卒轉為心胸開闊、忘卻自我", "從極度興奮到歸於平靜", "由憤怒轉為平靜", "由平淡轉為悲傷"], a: 0 },
        { q: "《始得西山宴遊記》中「心凝形釋，與萬化冥合」的意思是：", options: ["精神凝聚，形體解脫，與大自然融為一體", "身體疲倦，準備入睡", "心思複雜，無法理解自然", "精神渙散，無精打采"], a: 0 },
        { q: "范仲淹《岳陽樓記》中「先天下之憂而憂，後天下之樂而樂」展現了什麼胸襟？", options: ["以天下為己任的高尚情操", "追求個人名利", "順應自然的消極態度", "退隱山林的決心"], a: 0 },
        { q: "《岳陽樓記》中「不以物喜，不以己悲」是形容哪類人的修養？", options: ["古仁人", "遷客騷人", "一般平民", "功利商人"], a: 0 },
        { q: "蘇洵《六國論》認為六國破滅的根本原因是什麼？", options: ["弊在賂秦", "兵器不精", "人才不足", "策略失當"], a: 0 },
        { q: "《六國論》中「以地事秦，猶抱薪救火」，其中「薪」指什麼？", options: ["木柴 / 土地", "石油", "糧食", "金錢"], a: 0 },
        { q: "王維《山居秋暝》中「明月松間照，清泉石上流」屬於什麼寫景手法？", options: ["動靜結合，以動襯靜", "純粹寫靜景", "虛實相生", "由遠及近"], a: 0 },
        { q: "《山居秋暝》「隨意春芳歇，王孫自可留」中「王孫」指：", options: ["詩人自己（或隱士）", "帝王後代", "貴族子弟", "遠方的朋友"], a: 0 },
        { q: "李白《月下獨酌》中「舉杯邀明月，對影成三人」，「三人」是指：", options: ["李白、明月、自己的影子", "李白、杜甫、高適", "李白和兩個朋友", "月亮、影子、酒杯"], a: 0 },
        { q: "《月下獨酌》表達了李白怎樣的心境？", options: ["孤獨寂寞卻又曠達超脫", "對功名的渴望", "對家鄉的思念", "對現實的不滿與憤怒"], a: 0 },
        { q: "杜甫《登樓》中「花近高樓傷客心」，詩人感到「傷心」的原因是：", options: ["繁花盛開反襯國事蜩螗、身世漂泊", "討厭花朵的香味", "感嘆自己容顏衰老", "因為天氣炎熱"], a: 0 },
        { q: "杜甫《登樓》「錦江春色來天地，玉壘浮雲變古今」展現了怎樣的意境？", options: ["雄渾壯闊，涵蓋古今", "淒涼殘破", "細膩柔美", "平淡無奇"], a: 0 },
        { q: "蘇軾《念奴嬌．赤壁懷古》中「大江東去，浪淘盡，千古風流人物」寫的是哪條江？", options: ["長江", "黃河", "珠江", "淮河"], a: 0 },
        { q: "《念奴嬌．赤壁懷古》中「羽扇綸巾，談笑間，樯櫓灰飛煙滅」描寫的是哪一位歷史人物？", options: ["周瑜", "諸葛亮", "曹操", "劉備"], a: 0 },
        { q: "李清照《聲聲慢》開頭「尋尋覓覓，冷冷清清，悽悽慘慘戚戚」連用了多少個疊字？", options: ["14 個", "10 個", "12 個", "16 個"], a: 0 },
        { q: "《聲聲慢》中「滿地黃花堆積，憔悴損，如今有誰堪摘」中的「黃花」指：", options: ["菊花", "桃花", "荷花", "梅花"], a: 0 },
        { q: "辛棄疾《青玉案．元夕》「東風夜放花千樹」描寫的是什麼節日的盛況？", options: ["元宵節", "中秋節", "端午節", "重陽節"], a: 0 },
        { q: "《青玉案．元夕》「眾里尋他千百度，驀然回首，那人卻在，燈火闌珊處」中「闌珊」意指：", options: ["零落、稀疏暗淡", "燦爛耀眼", "擁擠熱鬧", "多姿多彩"], a: 0 },
        { q: "《論語》「君子病無能焉，不病人之不己知也」中「病」解作：", options: ["擔憂 / 憂慮", "生病", "責備", "嫉妒"], a: 0 },
        { q: "《荀子．勸學》中「假輿馬者，非利足也，而致千里」的「假」字解作：", options: ["借助 / 憑藉", "虛假", "假如", "請假"], a: 0 },
        { q: "《孟子．魚我所欲也》提出「鄉為身死而不受，今為宮室之美為之」，其中「鄉」通哪個字？", options: ["嚮（向）/ 以前", "香", "鄉下", "相"], a: 0 },
        { q: "司馬遷《廉頗藺相如列傳》中「秦王飲酒酣，曰：『寡人竊聞趙王好音...』」，秦王逼趙王彈奏什麼樂器？", options: ["瑟", "箏", "琴", "笛"], a: 0 },
        { q: "諸葛亮《出師表》中「臣本布衣，躬耕於南陽」，「布衣」指：", options: ["平民百姓", "貧窮的商人", "布料商人", "低級官吏"], a: 0 },
        { q: "韓愈《師說》「位卑則足羞，官盛則近諛」描寫了當時哪種不良風氣？", options: ["士大夫階層恥於從師學習", "官員貪污受賄", "朝廷輕視武將", "百姓不重視教育"], a: 0 },
        { q: "范仲淹《岳陽樓記》「微斯人，吾誰與歸」，「斯人」是指：", options: ["古仁人", "滕子京", "屈原", "漁夫"], a: 0 },
        { q: "蘇軾《念奴嬌．赤壁懷古》「人生如夢，一尊還酹江月」，「酹」的意思是：", options: ["將酒灑在地上祭奠/敬月", "喝酒", "唱歌", "洗滌"], a: 0 }
    ];

    let isSignup = false;
    let currentUser = null;
    let currentQuizQuestions = [];

    // Check if user is logged in on load
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

    function startQuiz() {
        // Randomly pick 10 items from 40 questions
        const shuffled = [...questionBank].sort(() => 0.5 - Math.random());
        currentQuizQuestions = shuffled.slice(0, 10);

        const form = document.getElementById('quiz-form');
        form.innerHTML = '';

        currentQuizQuestions.forEach((item, qIndex) => {
            const qDiv = document.createElement('div');
            qDiv.className = 'quiz-question';
            
            let html = `<p><strong>${qIndex + 1}. ${item.q}</strong></p><div class="options-group">`;
            
            // Randomize options for display
            item.options.forEach((opt, oIndex) => {
                html += `
                    <label class="option-label">
                        <input type="radio" name="q${qIndex}" value="${oIndex}" required>
                        ${opt}
                    </label>
                `;
            });
            html += '</div>';
            qDiv.innerHTML = html;
            form.appendChild(qDiv);
        });

        document.getElementById('main-view').classList.add('hidden');
        document.getElementById('quiz-view').classList.remove('hidden');
    }

    function submitQuiz() {
        const form = document.getElementById('quiz-form');
        const formData = new FormData(form);
        let score = 0;

        for (let i = 0; i < currentQuizQuestions.length; i++) {
            const answer = formData.get(`q${i}`);
            if (answer === null) {
                alert("請回答所有問題！");
                return;
            }
            if (parseInt(answer) === currentQuizQuestions[i].a) {
                score++;
            }
        }

        document.getElementById('score-text').innerText = `得分：${score} / 10`;
        document.getElementById('quiz-view').classList.add('hidden');
        document.getElementById('result-view').classList.remove('hidden');
    }
</script>

</body>
</html>
