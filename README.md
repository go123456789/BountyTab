# DoraTv
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Doraemon TV - Disney Channel</title>
<script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Baloo+2&display=swap');

  body {
    margin: 0;
    font-family: 'Baloo 2', cursive, Arial, sans-serif;
    background: url('https://i.pinimg.com/1200x/da/fc/08/dafc08ea504481bb5af616fd31a5f664.jpg') no-repeat center center fixed;
    background-size: cover;
    color: #fff;
    text-align: center;
    overflow-x: hidden;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  header {
    padding: 20px 10px 10px;
    background: rgba(0, 0, 60, 0.7);
    box-shadow: 0 0 20px #00bfff88;
    position: relative;
  }

  header h1 {
    font-size: 2.8rem;
    margin: 0;
    color: #00bfff;
    text-shadow: 2px 2px 4px #000a;
  }

  .subtitle {
    font-size: 1.4rem;
    margin: 5px 0 10px;
    color: #00d2ff;
    text-shadow: 1px 1px 4px #002f44;
    font-weight: 700;
    letter-spacing: 1.2px;
    font-style: italic;
  }

  header p {
    font-size: 1.2rem;
    margin: 5px 0 0;
    color: #aad8ff;
    text-shadow: 1px 1px 3px #000a;
  }

  .doraemon-ears {
    position: absolute;
    top: -40px;
    left: 10px;
    width: 120px;
    pointer-events: none;
    user-select: none;
    animation: bounce 3s infinite ease-in-out;
  }

  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  .channel-list {
    margin: 15px auto 0;
    max-width: 160px;
  }
  video {
    margin: 30px auto 0;
    width: 90%;
    max-width: 900px;
    
    border-radius: 20px;
    background: black;
    box-shadow: 0 0 25px #00bfffcc;
  }


  .channel-logo {
    cursor: pointer;
    transition: transform 0.3s ease;
    border: 4px solid #00bfff;
    border-radius: 5px;
    box-shadow: 0 0 15px #00bfff88;
    background: rgba(0, 0, 50, 0.6);
  }

  .channel-logo:hover {
    transform: scale(1.15) rotate(-3deg);
    box-shadow: 0 0 25px #00e0ffcc;
  }


  footer {
    margin-top: auto;
    padding: 15px 10px;
    background: rgba(0, 0, 40, 0.75);
    color: #aad8ff;
    font-size: 1rem;
    box-shadow: inset 0 1px 3px #00bfff55;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }

  .telegram-btn {
    background: #0088cc;
    color: white;
    border: none;
    padding: 12px 22px;
    border-radius: 25px;
    font-weight: bold;
    font-size: 1rem;
    cursor: pointer;
    box-shadow: 0 4px 10px #00bfff99;
    transition: background-color 0.3s ease;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .telegram-btn:hover {
    background: #00aaff;
  }

  .telegram-icon {
    width: 20px;
    height: 20px;
    fill: white;
  }
</style>
</head>
<body>
<video id="video" controls playsinline></video>
<div class="channel-list">
  <img
    src="data:image/png;base64,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"
    alt="Disney Channel"
    class="channel-logo"
    width="220"
    onclick="playChannel()"
    title="Watch Disney Channel"
  />
</div>


<footer>
  <span>Powered by BountyTab</span>
  <button
    class="telegram-btn"
    onclick="window.open('https://web.telegram.org/k/#@BountyTab')"
    aria-label="Join BountyTab Telegram Channel"
  >
    <svg class="telegram-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <path
        d="M22.5 2.5L1.5 11.5l6.5 2.5 2.5 7.5 3.5-9.5 5.5-7.5zM8.5 15.5L5 13l11-5-9 8.5z"
      />
    </svg>
    Join BountyTab Telegram
  </button>
</footer>

<script>
function playChannel() {
  const video = document.getElementById('video');
  const videoSrc = 'https://live.dinesh29.com.np/stream/jiotvplus/disneychannel/master.m3u8';

  if (Hls.isSupported()) {
    const hls = new Hls();
    hls.loadSource(videoSrc);
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function () {
      video.play();
    });
  } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
    video.src = videoSrc;
    video.addEventListener('loadedmetadata', function () {
      video.play();
    });
  } else {
    alert('Your browser does not support HLS streaming.');
  }
}
</script>

</body>
</html>
