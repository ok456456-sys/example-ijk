# example-ijk
연습용으로 만들어 본 페이지입니다.
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>실험용 버튼 화면 전환</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo", "Noto Sans KR", sans-serif;
      background-color: #f4f6f9;
      color: #222;
      padding: 24px 16px;
      line-height: 1.6;
    }

    .container {
      max-width: 520px;
      margin: 0 auto;
    }

    h1 {
      font-size: 22px;
      margin-bottom: 8px;
      color: #111;
    }

    .subtitle {
      font-size: 14px;
      color: #666;
      margin-bottom: 24px;
    }

    /* 위에서 아래로 쌓이는 직사각형 버튼 목록 */
    .button-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 24px;
    }

    .menu-btn {
      width: 100%;
      padding: 18px 20px;
      text-align: left;
      font-size: 16px;
      font-weight: 600;
      color: #1f2937;
      background-color: #ffffff;
      border: 2px solid #d1d5db;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.15s ease;
    }

    .menu-btn:hover {
      border-color: #3b82f6;
      background-color: #f8fbff;
    }

    /* 선택된 버튼 강조 스타일 */
    .menu-btn.active {
      background-color: #2563eb;
      color: #ffffff;
      border-color: #2563eb;
    }

    /* 버튼을 눌렀을 때 나타나는 메시지 화면 카드 */
    .screen-box {
      background-color: #ffffff;
      border-radius: 12px;
      padding: 24px;
      border: 1px solid #e5e7eb;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
      min-height: 160px;
    }

    .screen-badge {
      display: inline-block;
      font-size: 12px;
      font-weight: 700;
      color: #2563eb;
      background-color: #eff6ff;
      padding: 4px 10px;
      border-radius: 999px;
      margin-bottom: 12px;
    }

    .screen-title {
      font-size: 19px;
      font-weight: 700;
      margin-bottom: 10px;
      color: #111827;
    }

    .screen-message {
      font-size: 15px;
      color: #374151;
      white-space: pre-line;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>항목을 선택해 보세요</h1>
    <p class="subtitle">아래 세 가지 버튼 중 하나를 누르면 해당 안내 화면이 열립니다.</p>

    <!-- 버튼 3개 목록 -->
    <div class="button-list">
      <button class="menu-btn active" onclick="showScreen(1, this)">
        1. 첫 번째 버튼 — 안내 시작하기
      </button>
      <button class="menu-btn" onclick="showScreen(2, this)">
        2. 두 번째 버튼 — 핵심 규칙 확인하기
      </button>
      <button class="menu-btn" onclick="showScreen(3, this)">
        3. 세 번째 버튼 — 다음 행동 제안 보기
      </button>
    </div>

    <!-- 선택 결과 메시지 화면 -->
    <div class="screen-box">
      <span class="screen-badge" id="screen-badge">화면 1</span>
      <h2 class="screen-title" id="screen-title">첫 번째 화면입니다</h2>
      <p class="screen-message" id="screen-message">안녕하세요! 첫 번째 버튼을 눌렀을 때 전달되는 메시지 공간입니다.
이곳에 원하는 설명이나 안내 문구를 자유롭게 채워 넣을 수 있습니다.</p>
    </div>
  </div>

  <script>
    // 각 버튼별 화면 데이터 (나중에 이 부분의 글자만 바꾸면 내용이 바뀝니다)
    const screens = {
      1: {
        badge: "화면 1",
        title: "첫 번째 화면입니다",
        message: "안녕하세요! 첫 번째 버튼을 눌렀을 때 전달되는 메시지 공간입니다.\n이곳에 원하는 설명이나 안내 문구를 자유롭게 채워 넣을 수 있습니다."
      },
      2: {
        badge: "화면 2",
        title: "두 번째 화면: 핵심 안내",
        message: "두 번째 버튼을 선택하셨습니다.\n상황에 맞는 기준이나 체크리스트, 주의할 점을 여기에 적어 보여줄 수 있습니다."
      },
      3: {
        badge: "화면 3",
        title: "세 번째 화면: 지금 해볼 일",
        message: "세 번째 버튼을 선택하셨습니다.\n마지막으로 당장 실행할 행동 1~2가지를 정리해 전달하는 화면으로 활용할 수 있습니다."
      }
    };

    function showScreen(number, clickedButton) {
      // 모든 버튼에서 active 표시 제거 후 클릭한 버튼만 강조
      const buttons = document.querySelectorAll(".menu-btn");
      buttons.forEach(btn => btn.classList.remove("active"));
      clickedButton.classList.add("active");

      // 선택한 번호에 맞는 내용으로 화면 교체
      const data = screens[number];
      document.getElementById("screen-badge").textContent = data.badge;
      document.getElementById("screen-title").textContent = data.title;
      document.getElementById("screen-message").textContent = data.message;
    }
  </script>
</body>
</html>
