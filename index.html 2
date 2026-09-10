<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>이름 궁합 테스트 - 우리 몇 %일까?</title>
    <link href="https://fonts.googleapis.com/css2?family=Gowun+Batang:wght@400;700&family=Jua&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Gowun Batang', serif;
            background: linear-gradient(135deg, #fff5f5 0%, #fed7aa 100%);
            color: #431407;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            border: 2px solid #fbcfe8;
            border-radius: 32px;
            padding: 40px 28px;
            text-align: center;
            max-width: 480px;
            width: 100%;
            box-shadow: 0 20px 40px rgba(244, 63, 94, 0.15);
        }

        h1 {
            font-family: 'Jua', sans-serif;
            font-size: 2.3rem;
            color: #e11d48;
            margin-bottom: 8px;
        }

        p.subtitle {
            font-size: 0.95rem;
            color: #9f1239;
            margin-bottom: 28px;
        }

        .input-group {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 25px;
        }

        .input-box {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .input-box label {
            font-size: 0.85rem;
            font-weight: bold;
            color: #be123c;
        }

        .input-box input {
            width: 100%;
            padding: 14px 10px;
            border: 2px solid #fecdd3;
            border-radius: 16px;
            font-size: 1.1rem;
            font-family: 'Jua', sans-serif;
            text-align: center;
            outline: none;
            transition: all 0.2s ease;
            background: #fff;
        }

        .input-box input:focus {
            border-color: #f43f5e;
            box-shadow: 0 0 0 3px rgba(244, 63, 94, 0.2);
        }

        .heart-divider {
            font-size: 1.8rem;
            color: #f43f5e;
            margin-top: 20px;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        .result-card {
            background: #fff1f2;
            border: 1px dashed #fda4af;
            border-radius: 20px;
            padding: 25px 20px;
            margin-bottom: 25px;
            min-height: 180px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .result-score {
            font-family: 'Jua', sans-serif;
            font-size: 3.5rem;
            color: #e11d48;
            line-height: 1.1;
            margin-bottom: 10px;
        }

        .result-comment {
            font-size: 1.05rem;
            font-weight: bold;
            color: #881337;
            word-break: keep-all;
        }

        .btn-calc {
            font-family: 'Jua', sans-serif;
            font-size: 1.3rem;
            background: linear-gradient(135deg, #f43f5e 0%, #e11d48 100%);
            color: #ffffff;
            border: none;
            padding: 16px 36px;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(244, 63, 94, 0.35);
            transition: all 0.2s ease;
            width: 100%;
            outline: none;
        }

        .btn-calc:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 24px rgba(244, 63, 94, 0.45);
            background: linear-gradient(135deg, #fb7185 0%, #e11d48 100%);
        }

        .btn-calc:active {
            transform: translateY(1px);
        }

        .bounce {
            animation: pop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes pop {
            0% { transform: scale(0.6); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        footer {
            margin-top: 25px;
            font-size: 0.8rem;
            color: #9f1239;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>이름 궁합 테스트 💕</h1>
        <p class="subtitle">두 사람의 이름을 입력하고 궁합을 확인해보세요!</p>

        <div class="input-group">
            <div class="input-box">
                <label for="name1">첫 번째 이름</label>
                <input type="text" id="name1" placeholder="예: 홍길동" maxlength="10">
            </div>
            <div class="heart-divider">❤️</div>
            <div class="input-box">
                <label for="name2">두 번째 이름</label>
                <input type="text" id="name2" placeholder="예: 성춘향" maxlength="10">
            </div>
        </div>

        <div class="result-card">
            <div id="score" class="result-score">? %</div>
            <div id="comment" class="result-comment">이름을 입력하고 아래 버튼을 눌러주세요!</div>
        </div>

        <button class="btn-calc" onclick="calculateCompatibility()">궁합 확인하기 💖</button>
    </div>

    <footer>
        <p>© 2026 재미로 보는 이름 궁합</p>
    </footer>

    <script>
        // 한글 자획수 테이블 (초성/중성/종성)
        const strokeMap = {
            // 초성
            'ㄱ': 2, 'ㄲ': 4, 'ㄴ': 2, 'ㄷ': 3, 'ㄸ': 6, 'ㄹ': 5, 'ㅁ': 4, 'ㅂ': 4, 'ㅃ': 8,
            'ㅅ': 2, 'ㅆ': 4, 'ㅇ': 1, 'ㅈ': 3, 'ㅉ': 6, 'ㅊ': 4, 'ㅋ': 3, 'ㅌ': 4, 'ㅍ': 4, 'ㅎ': 3,
            // 중성
            'ㅏ': 2, 'ㅐ': 3, 'ㅑ': 3, 'ㅒ': 4, 'ㅓ': 2, 'ㅔ': 3, 'ㅕ': 3, 'ㅖ': 4, 'ㅗ': 2, 'ㅘ': 4,
            'ㅙ': 5, 'ㅚ': 3, 'ㅛ': 3, 'ㅜ': 2, 'ㅝ': 4, 'ㅞ': 5, 'ㅟ': 3, 'ㅠ': 3, 'ㅡ': 1, 'ㅢ': 2, 'ㅣ': 1,
            // 종성
            '': 0, 'ㄱ': 2, 'ㄲ': 4, 'ㄳ': 4, 'ㄴ': 2, 'ㄵ': 5, 'ㄶ': 5, 'ㄷ': 3, 'ㄹ': 5, 'ㄺ': 7,
            'ㄻ': 9, 'ㄼ': 9, 'ㄽ': 7, 'ㄾ': 9, 'ㄿ': 9, 'ㅀ': 8, 'ㅁ': 4, 'ㅂ': 4, 'ㅄ': 6, 'ㅅ': 2,
            'ㅆ': 4, 'ㅇ': 1, 'ㅈ': 3, 'ㅊ': 4, 'ㅋ': 3, 'ㅌ': 4, 'ㅍ': 4, 'ㅎ': 3
        };

        const choList = ['ㄱ', 'ㄲ', 'ㄴ', 'ㄷ', 'ㄸ', 'ㄹ', 'ㅁ', 'ㅂ', 'ㅃ', 'ㅅ', 'ㅆ', 'ㅇ', 'ㅈ', 'ㅉ', 'ㅊ', 'ㅋ', 'ㅌ', 'ㅍ', 'ㅎ'];
        const jungList = ['ㅏ', 'ㅐ', 'ㅑ', 'ㅒ', 'ㅓ', 'ㅔ', 'ㅕ', 'ㅖ', 'ㅗ', 'ㅘ', 'ㅙ', 'ㅚ', 'ㅛ', 'ㅜ', 'ㅝ', 'ㅞ', 'ㅟ', 'ㅠ', 'ㅡ', 'ㅢ', 'ㅣ'];
        const jongList = ['', 'ㄱ', 'ㄲ', 'ㄳ', 'ㄴ', 'ㄵ', 'ㄶ', 'ㄷ', 'ㄹ', 'ㄺ', 'ㄻ', 'ㄼ', 'ㄽ', 'ㄾ', 'ㄿ', 'ㅀ', 'ㅁ', 'ㅂ', 'ㅄ', 'ㅅ', 'ㅆ', 'ㅇ', 'ㅈ', 'ㅊ', 'ㅋ', 'ㅌ', 'ㅍ', 'ㅎ'];

        function getCharStrokes(char) {
            const code = char.charCodeAt(0) - 0xAC00;
            if (code < 0 || code > 11172) {
                return (char.charCodeAt(0) % 5) + 1;
            }
            const cho = choList[Math.floor(code / 588)];
            const jung = jungList[Math.floor((code % 588) / 28)];
            const jong = jongList[code % 28];

            return (strokeMap[cho] || 2) + (strokeMap[jung] || 2) + (strokeMap[jong] || 0);
        }

        function calculateCompatibility() {
            const name1 = document.getElementById('name1').value.trim();
            const name2 = document.getElementById('name2').value.trim();
            const scoreEl = document.getElementById('score');
            const commentEl = document.getElementById('comment');

            if (!name1 || !name2) {
                alert('두 사람의 이름을 모두 입력해주세요!');
                return;
            }

            let combined = name1.localeCompare(name2) < 0 ? name1 + name2 : name2 + name1;
            let hash = 0;
            for (let i = 0; i < combined.length; i++) {
                hash += getCharStrokes(combined[i]) * (i + 1);
            }

            let score = (hash * 17 + 31) % 100;
            if (score < 40) score += 40;

            scoreEl.textContent = '계산 중...';
            commentEl.textContent = '두 사람의 운명을 분석하고 있습니다.';

            setTimeout(() => {
                scoreEl.textContent = `${score}%`;

                if (score >= 90) {
                    commentEl.textContent = '💞 환상의 짝꿍! 전생에 부부였을지도 몰라요.';
                } else if (score >= 75) {
                    commentEl.textContent = '💖 서로를 아주 잘 이해하는 찰떡궁합이에요!';
                } else if (score >= 60) {
                    commentEl.textContent = '😊 알콩달콩 좋지만 가끔은 양보가 필요해요.';
                } else {
                    commentEl.textContent = '🌱 서로를 알아가는 노력이 필요한 관계예요!';
                }

                scoreEl.classList.remove('bounce');
                void scoreEl.offsetWidth;
                scoreEl.classList.add('bounce');
            }, 500);
        }
    </script>
</body>
</html>
