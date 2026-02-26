<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <title>나 사랑해?</title>
  <style>
    body {
      height: 100vh;
      margin: 0;
      background: #ffd6e8;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: "Malgun Gothic", sans-serif;
      overflow: hidden;
    }

    .modal {
      width: 360px;
      padding: 28px;
      background: #ffffff;
      border-radius: 16px;
      text-align: center;
      position: relative;
      box-shadow:
        0 14px 28px rgba(0, 0, 0, 0.18),
        0 6px 12px rgba(0, 0, 0, 0.08);
      z-index: 10;
    }

    h2 {
      margin-bottom: 26px;
      color: #222;
    }

    .buttons {
      display: flex;
      justify-content: center;
      gap: 16px;
      position: relative;
    }

    button {
      padding: 12px 22px;
      border: none;
      border-radius: 10px;
      font-size: 15px;
      cursor: pointer;
    }

    .yes {
      background: #f76aba;
      color: white;
    }

    /* 아니요 자리 유지용 더미 */
    .no-placeholder {
      width: 86px;
      height: 40px;
    }

    .no {
      background: #ffdef1;
      color: black;
      position: relative;
      transition: all 0.15s linear;
      z-index: 999;
    }

    .ending {
      position: fixed;
      inset: 0;
      background: #ffffff;
      display: none;
      align-items: center;
      justify-content: center;
      text-align: center;
      z-index: 2000;
    }
  </style>
</head>
<body>

  <div class="modal">
    <h2>자기야 나랑 계속 사귈거지?</h2>
    <div class="buttons">
      <button class="yes" id="yesBtn">예</button>
      <div class="no-placeholder"></div>
    </div>
  </div>

  <!-- 실제 도망가는 아니요 -->
  <button class="no" id="noBtn">아니요</button>

  <!-- 엔딩 -->
  <div class="ending" id="ending">
    <div>
      <p style="font-size:32px; font-weight:800; margin-bottom:28px;">
        축하합니다 🎉
      </p>

      <p style="font-size:22px; line-height:1.7; margin-bottom:24px;">
        당신은<br>
        <span style="color:#ff4d8d; font-weight:600;">
          멘헤라 집착녀
        </span>와<br>
        계속 사귀게 되었습니다 💗🔒
      </p>

      <p style="font-size:15px; opacity:0.65;">
        넌 이제 내꺼 💗🔪
      </p>
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const ending = document.getElementById("ending");
    const placeholder = document.querySelector(".no-placeholder");

    let speed = 0.2;

    // 🔥 시작 위치를 더 오른쪽으로 이동
    const rect = placeholder.getBoundingClientRect();
    noBtn.style.left = rect.left + 60 + "px"; // ← 여기!
    noBtn.style.top = rect.top + "px";
    noBtn.style.position = "fixed";

    function runAway() {
      const maxX = window.innerWidth - noBtn.offsetWidth;
      const maxY = window.innerHeight - noBtn.offsetHeight;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      speed = Math.max(0.03, speed - 0.015);
      noBtn.style.transition = `all ${speed}s linear`;

      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
    }

    noBtn.addEventListener("mouseover", runAway);
    noBtn.addEventListener("mousedown", runAway);

    yesBtn.addEventListener("click", () => {
      ending.style.display = "flex";
    });
  </script>

</body>
</html>
