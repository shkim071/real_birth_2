<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>생일 축하합니다</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;700&display=swap');
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #000;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #fff;
            overflow: hidden;
            position: relative;
        }
        .container {
            text-align: center;
            z-index: 2;
            opacity: 1;
            animation: fadeIn 1s forwards;
        }
        h1 {
            font-size: 3rem;
            margin: 0;
        }
        h2, h3 {
            font-size: 1.5rem;
            margin: 10px 0 0;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 1rem;
            background-color: #fff;
            color: #333;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #ddd;
        }
        .ground {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 50px;
            background: white;
            z-index: 1;
        }
        .tree {
            position: absolute;
            bottom: 50px;
            width: 20px;
            height: 60px;
            background: brown;
            border-radius: 0 0 5px 5px;
            z-index: 1;
        }
        .tree::before {
            content: '';
            position: absolute;
            bottom: 100%;
            left: 50%;
            width: 60px;
            height: 60px;
            background: green;
            border-radius: 50%;
            transform: translateX(-50%);
        }
        .tree1 { left: 10%; }
        .tree2 { left: 50%; }
        .tree3 { left: 90%; }
        @keyframes snow {
            0% { transform: translateY(0); }
            100% { transform: translateY(100vh); }
        }
        .snowflake {
            position: absolute;
            top: -10px;
            z-index: 1;
            color: white;
            font-size: 1em;
            pointer-events: none;
            user-select: none;
            animation: snow 10s linear infinite;
        }
        @keyframes fadeOut {
            to {
                opacity: 0;
            }
        }
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        .fade-out {
            animation: fadeOut 1s forwards;
        }
        .fade-in {
            animation: fadeIn 1s forwards;
        }
    </style>
</head>
<body onload="showInitial()">
    <div class="ground"></div>
    <div class="tree tree1"></div>
    <div class="tree tree2"></div>
    <div class="tree tree3"></div>
    <script>
        let attempt = 0;

        function createSnowflakes() {
            const snowflakeCount = 100;
            for (let i = 0; i < snowflakeCount; i++) {
                const snowflake = document.createElement('div');
                snowflake.className = 'snowflake';
                snowflake.style.left = `${Math.random() * 100}vw`;
                snowflake.style.animationDuration = `${Math.random() * 3 + 7}s`;
                snowflake.style.opacity = Math.random();
                snowflake.style.fontSize = `${Math.random() * 10 + 10}px`;
                snowflake.innerHTML = '❄';
                document.body.appendChild(snowflake);
            }
        }

        function showInitial() {
            document.body.innerHTML = `
                <div class="container fade-in">
                    <h1>생일 축하합니다!</h1>
                    <h2>Happy Birthday!</h2>
                    <h3>お誕生日おめでとう!</h3>
                    <button onclick="showMessage()">여기를 눌러보세요</button>
                </div>
            `;
            createSnowflakes();
        }

        function showMessage() {
            document.querySelector('.container').classList.add('fade-out');
            setTimeout(() => {
                document.body.innerHTML = `
                    <div class="container fade-in">
                        <h1>현영아!! 생일축하해!!!</h1>
                        <button onclick="showPath()">여기를 눌러보세요</button>
                    </div>
                `;
                createSnowflakes();
            }, 1000);
        }

        function showPath() {
            document.querySelector('.container').classList.add('fade-out');
            setTimeout(() => {
                document.body.innerHTML = `
                    <div class="container fade-in">
                        <h1>23년 동안 걸어온 길</h1>
                        <p>산곡여자중학교</p>
                        <p>명신여자고등학교</p>
                        <p>인천대학교</p>
                        <p>이디야커피</p>
                        <p>테라커피</p>
                        <button onclick="showFuture()">다음</button>
                    </div>
                `;
                createSnowflakes();
            }, 1000);
        }

        function showFuture() {
            document.querySelector('.container').classList.add('fade-out');
            setTimeout(() => {
                document.body.innerHTML = `
                    <div class="container fade-in">
                        <h1>2025년에 걸어갈 길</h1>
                        <p>일본 교환학생</p>
                        <p>성공적인 카페 창업</p>
                        <button onclick="startGame()">가위바위보 시작</button>
                    </div>
                `;
                createSnowflakes();
            }, 1000);
        }

        function startGame() {
            document.querySelector('.container').classList.add('fade-out');
            setTimeout(() => {
                document.body.innerHTML = `
                    <div class="container fade-in">
                        <h1>가위바위보 묵찌빠</h1>
                        <p>가위바위보 게임을 플레이하고 승리하면 2025년 행복쿠폰을 받을 수 있습니다!</p>
                        <button onclick="playGame()">게임 시작</button>
                    </div>
                `;
                createSnowflakes();
            }, 1000);
        }

        function playGame() {
            document.body.innerHTML = `
                <div class="container fade-in">
                    <h1>가위바위보 묵찌빠</h1>
                    <p>가위, 바위, 보 중 하나를 선택하세요:</p>
                    <button onclick="playRound('가위')">가위</button>
                    <button onclick="playRound('바위')">바위</button>
                    <button onclick="playRound('보')">보</button>
                </div>
            `;
        }

        function playRound(playerChoice) {
            const choices = ['가위', '바위', '보'];
            const computerChoice = choices[Math.floor(Math.random() * choices.length)];
            const result = getResult(playerChoice, computerChoice);

            document.body.innerHTML = `
                <div class="container fade-in">
                    <h1>결과는...</h1>
                    <p>${playerChoice} vs ${computerChoice}</p>
                    <p>${result}</p>
                    <button onclick="playGame()">다시 플레이</button>
                </div>
            `;
        }

        function getResult(playerChoice, computerChoice) {
            if (playerChoice === computerChoice) {
                return '무승부!';
            } else if (
                (playerChoice === '가위' && computerChoice === '보') ||
                (playerChoice === '바위' && computerChoice === '가위') ||
                (playerChoice === '보' && computerChoice === '바위')
            ) {
                return '승리!';
            } else {
                return '패배!';
            }
        }
    </script>
</body>
