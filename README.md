<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Timer Widget</title>
    <style>
        #countdownWidget {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: #222;
            color: #fff;
            text-align: center;
            padding: 10px;
            font-family: Arial, sans-serif;
            box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.3);
            z-index: 1000;
        }
        .highlight {
            color: #ffd700;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div id="countdownWidget">
        구독 마감까지 <span id="timeRemaining" class="highlight"></span><br>
        잔여: <span id="remainingSeats" class="highlight">5석</span><br>
        <small>*마감시한 또는 정해진 구독인원 모집이 완료되면 본 구독서비스 이용이 어렵습니다.</small>
    </div>

    <script>
        // Set the target date for the countdown (e.g., 14 days from now)
        const targetDate = new Date();
        targetDate.setDate(targetDate.getDate() + 14);

        function updateCountdown() {
            const now = new Date();
            const timeDifference = targetDate - now;

            if (timeDifference <= 0) {
                document.getElementById("timeRemaining").innerText = "구독 마감되었습니다.";
                return;
            }

            const days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);

            document.getElementById("timeRemaining").innerText = `${days}일 ${hours}시 ${minutes}분 ${seconds}초`;
        }

        // Update countdown every second
        setInterval(updateCountdown, 1000);
    </script>
</body>
</html>
