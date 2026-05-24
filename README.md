<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Birthday ❤️</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family: "Courier New", monospace;
    }

    body{
      background:black;
      color:#00ff88;
      overflow:hidden;
      height:100vh;
    }

    .matrix{
      position:fixed;
      width:100%;
      height:100%;
      z-index:-1;
      opacity:0.15;
    }

    .container{
      height:100vh;
      display:flex;
      justify-content:center;
      align-items:center;
      text-align:center;
      padding:20px;
    }

    .card{
      background:rgba(0,0,0,0.7);
      border:1px solid #00ff88;
      padding:40px;
      border-radius:20px;
      box-shadow:0 0 25px #00ff88;
      max-width:700px;
      animation:glow 2s infinite alternate;
    }

    @keyframes glow{
      from{
        box-shadow:0 0 10px #00ff88;
      }
      to{
        box-shadow:0 0 30px #00ff88;
      }
    }

    h1{
      font-size:3rem;
      margin-bottom:20px;
      text-shadow:0 0 15px #00ff88;
    }

    .typing{
      font-size:1.2rem;
      white-space:nowrap;
      overflow:hidden;
      border-right:2px solid #00ff88;
      width:0;
      animation:
        typing 4s steps(40,end) forwards,
        blink .8s infinite;
      margin:auto;
    }

    @keyframes typing{
      from{ width:0 }
      to{ width:100% }
    }

    @keyframes blink{
      50%{
        border-color:transparent;
      }
    }

    .btn{
      margin-top:30px;
      padding:12px 25px;
      border:none;
      background:#00ff88;
      color:black;
      font-weight:bold;
      border-radius:10px;
      cursor:pointer;
      transition:0.3s;
    }

    .btn:hover{
      transform:scale(1.08);
      box-shadow:0 0 20px #00ff88;
    }

    .hidden-message{
      display:none;
      margin-top:25px;
      font-size:1.1rem;
      color:white;
      line-height:1.8;
    }
  </style>
</head>

<body>

<canvas class="matrix"></canvas>

<div class="container">
  <div class="card">
    <h1>HAPPY BIRTHDAY ❤️</h1>

    <div class="typing">
      Access Granted To The Best Boyfriend Ever...
    </div>

    <button class="btn" onclick="showMessage()">
      Click To Decrypt Message
    </button>

    <div class="hidden-message" id="message">
      Dear LOVE,<br><br>

      Out of billions of people,<br>
      my favorite notification is still you 🫶🏻<br><br>

      Thank you for existing,<br>
      for making my days softer,<br>
      and my heart happier.<br><br>

      Happy Birthday, Hacker Boy 💚
    </div>
  </div>
</div>

<script>
  function showMessage(){
    document.getElementById("message").style.display="block";
  }

  // Matrix effect
  const canvas = document.querySelector(".matrix");
  const ctx = canvas.getContext("2d");

  canvas.height = window.innerHeight;
  canvas.width = window.innerWidth;

  const letters = "01";
  const fontSize = 14;
  const columns = canvas.width/fontSize;

  const drops = [];

  for(let x = 0; x < columns; x++)
    drops[x] = 1;

  function draw(){
    ctx.fillStyle = "rgba(0,0,0,0.05)";
    ctx.fillRect(0,0,canvas.width,canvas.height);

    ctx.fillStyle = "#00ff88";
    ctx.font = fontSize + "px monospace";

    for(let i = 0; i < drops.length; i++){
      const text = letters[Math.floor(Math.random()*letters.length)];

      ctx.fillText(text, i*fontSize, drops[i]*fontSize);

      if(drops[i]*fontSize > canvas.height && Math.random() > 0.975)
        drops[i] = 0;

      drops[i]++;
    }
  }

  setInterval(draw, 33);
</script>

</body>
</html>
