<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Birthday!</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      background: #f0f8ff;
      margin: 0;
      padding: 0;
    }
    #envelope, #balloon-container, #final-message {
      margin-top: 50px;
    }
    #envelope img {
      width: 200px;
      cursor: pointer;
    }
    .balloon {
      width: 100px;
      cursor: pointer;
      margin: 20px;
      transition: transform 0.2s;
    }
    .balloon:hover {
      transform: scale(1.1);
    }
    .hidden {
      display: none;
    }
    #messages {
      margin-top: 30px;
      font-size: 18px;
    }
    #final-message {
      font-size: 22px;
      font-weight: bold;
      color: #d63384;
      margin-top: 40px;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>
<body>

  <div id="envelope">
    <img src="https://i.imgur.com/O8zjS5D.png" alt="Envelope" onclick="openEnvelope()">
    <p>Click the envelope to open your surprise!</p>
  </div>

  <div id="balloon-container" class="hidden">
    <img src="https://i.imgur.com/WFOTCUh.png" class="balloon" onclick="popBalloon(0)" alt="Red Balloon">
    <img src="https://i.imgur.com/L3RzB4D.png" class="balloon" onclick="popBalloon(1)" alt="Blue Balloon">
    <img src="https://i.imgur.com/WFOTCUh.png" class="balloon" onclick="popBalloon(2)" alt="Red Balloon">
    <img src="https://i.imgur.com/L3RzB4D.png" class="balloon" onclick="popBalloon(3)" alt="Blue Balloon">
  </div>

  <div id="messages"></div>
  <div id="final-message" class="hidden"></div>

  <audio id="birthday-audio" preload="auto">
    <source src="https://www.bensound.com/bensound-music/bensound-birthday.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
  </audio>

  <script>
    const messages = [
      "Hari ini adalah hari spesial...",
      "Teman sepertimu itu langka...",
      "Semoga semua harapanmu terkabul...",
      "Kamu layak mendapatkan yang terbaik!"
    ];

    const finalMessage = "Selamat ulang tahun! Aku harap hari ini penuh kebahagiaan, tawa, dan momen spesial. Terima kasih sudah jadi teman yang luar biasa. Semoga tahun ini membawa banyak berkah dan mimpi yang jadi kenyataan!";

    let clicked = [];

    function openEnvelope() {
      document.getElementById('envelope').classList.add('hidden');
      document.getElementById('balloon-container').classList.remove('hidden');
      document.getElementById('birthday-audio').play();
    }

    function popBalloon(index) {
      if (clicked.includes(index)) return;

      clicked.push(index);
      const messageBox = document.getElementById('messages');
      const newMessage = document.createElement('p');
      newMessage.textContent = messages[index];
      messageBox.appendChild(newMessage);

      if (clicked.length === 4) {
        setTimeout(() => {
          document.getElementById('balloon-container').classList.add('hidden');
          document.getElementById('messages').classList.add('hidden');
          document.getElementById('final-message').classList.remove('hidden');
          document.getElementById('final-message').textContent = finalMessage;
        }, 1000);
      }
    }
  </script>

</body>
</html>
