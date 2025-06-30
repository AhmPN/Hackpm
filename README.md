<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>HACKER TERMINAL PRO V4</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: #000;
      color: #00FF00;
      font-family: 'Courier New', monospace;
      overflow: hidden;
    }
    #terminal {
      padding: 20px;
      height: 100vh;
      overflow-y: scroll;
      white-space: pre-wrap;
    }
    #formOverlay {
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      background: black;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 99;
    }
    input {
      padding: 12px;
      width: 300px;
      font-size: 18px;
      background: #000;
      border: 2px solid #00ff00;
      color: #00ff00;
      margin-bottom: 20px;
      font-family: 'Courier New', monospace;
    }
    button {
      padding: 12px 30px;
      font-size: 20px;
      background: #00ff00;
      color: black;
      border: none;
      cursor: pointer;
      font-weight: bold;
    }
    .cursor {
      display: inline-block;
      animation: blink 1s step-start infinite;
    }
    @keyframes blink {
      50% { opacity: 0; }
    }
    .progress-bar {
      display: inline-block;
      width: 0;
      height: 15px;
      background-color: #00ff00;
      animation: load 3s linear forwards;
      margin-bottom: 10px;
    }
    @keyframes load {
      from { width: 0; }
      to { width: 100%; }
    }
  </style>
</head>
<body>

  <div id="formOverlay">
    <h2 style="color: #00ff00; font-family: 'Courier New';">Enter The Target Name</h2>
    <input type="text" id="targetName" placeholder="Username...">
    <button onclick="start()">Start Hacking</button>
  </div>

  <div id="terminal"><span class="cursor">█</span></div>

  <audio id="beep" src="https://www.soundjay.com/button/beep-07.wav" preload="auto"></audio>

  <script>
    const terminal = document.getElementById("terminal");
    const beep = document.getElementById("beep");
    const cursor = document.querySelector(".cursor");
    const formOverlay = document.getElementById("formOverlay");

    let target = "";
    let index = 0;

    function start() {
      target = document.getElementById("targetName").value || "Target Tidak Diketahui";
      formOverlay.style.display = 'none';
      document.documentElement.requestFullscreen?.();
      simulateTyping();
    }

    const generateFakeData = () => ([
      `[✔] Menghubungkan ke satelit global...`,
      `[✔] Satelit terkoneksi, mendapatkan akses root...`,
      `[✔] Mendeteksi target: ${target}`,
      `[✔] Nama lengkap: ${target} Ahmad Putra Nurrohim`,
      `[✔] Username Instagram: @${target.toLowerCase().replace(/\s/g, "_")}ahmad_putra_31`,
      `[✔] Email: ${target.toLowerCase().replace(/\s/g, ".")}put31@gmail.com`,
      `[✔] Nomor HP: +62 812-5673-2435`,
      `[✔] Lokasi terakhir: Desa Pandu Senjaya${Math.floor(Math.random()*100+1)}, Kalimantan Tengah`,
      `[✔] Wajah terdeteksi: https://thispersondoesnotexist.com/`,
      `[✔] Membuka kamera depan target...`,
      `[✔] Audio mic terekam: "Ip : *********"`,
      `[✔] Membuka aplikasi terakhir: TikTok & Mobile Legends`,
      `[✔] Mengunduh semua data rahasia...`,
      "██████████████████████████████████████████████████ 100%",
      `[✔] Menghapus jejak digital dan log jaringan...`,
      `[✔] Semua data berhasil dicuri dan diamankan 💾`,
      `[✔] Proses hack terhadap ${target} berhasil ✅`
    ]);

    const fakeData = generateFakeData();

    function simulateTyping() {
      if (index < fakeData.length) {
        if (fakeData[index].includes("████")) {
          const bar = document.createElement("div");
          bar.className = "progress-bar";
          terminal.insertBefore(bar, cursor);
          terminal.scrollTop = terminal.scrollHeight;
        } else {
          const line = document.createElement("div");
          line.textContent = fakeData[index];
          terminal.insertBefore(line, cursor);
          beep.play();
          terminal.scrollTop = terminal.scrollHeight;
        }
        index++;
        setTimeout(simulateTyping, 1500);
      } else {
        cursor.remove();
      }
    }
  </script>
</body>
</html>
