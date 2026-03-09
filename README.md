
<html lang="am">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>አፈቅርሻለሁ ርግቤ</title>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://unpkg.com/framer-motion/dist/framer-motion.umd.js"></script>
<style>
  body {
    margin: 0; font-family: 'Nyala', sans-serif;
    background: radial-gradient(circle at center, #3b0a45, #0d0014);
    overflow-x: hidden;
  }
  .nebula {
    position: absolute; top:0; left:0;
    width:100%; height:100%;
    background: url('https://i.ibb.co/8Y5h0wX/nebula.jpg') center/cover no-repeat;
    animation: moveNebula 60s linear infinite; opacity:0.4; z-index:-1;
  }
  @keyframes moveNebula {
    0% { transform: scale(1) translate(0,0);}
    50% { transform: scale(1.05) translate(20px,10px);}
    100% { transform: scale(1) translate(0,0);}
  }
  .glass-button {
    @apply bg-white/10 backdrop-blur-md rounded-xl text-white px-6 py-3 font-semibold
           hover:bg-green-600/30 transition shadow-lg border-2 border-red-600;
  }
  .dove-particle {
    position: absolute; width: 30px;
    animation: floatDove 10s linear infinite;
  }
  @keyframes floatDove {
    0% { transform: translate(0,0) rotate(0deg);}
    50% { transform: translate(50px,-30px) rotate(180deg);}
    100% { transform: translate(0,0) rotate(360deg);}
  }
</style>
</head>
<body>
<div class="nebula"></div>

<!-- Landing Section -->
<section class="flex flex-col items-center justify-center min-h-screen text-center px-4">
  <h1 class="text-5xl md:text-7xl font-extrabold mb-6 text-yellow-400">አፈቅርሻለሁ ርግቤ</h1>
  <p class="text-lg md:text-2xl mb-10 text-white">Experience cinematic Ethiopian love 💖</p>
  <button class="glass-button" id="startBtn">Start Journey</button>
</section>

<!-- Photo Section -->
<section id="photoSection" class="hidden flex flex-col items-center justify-center min-h-screen gap-8 px-4">
  <div class="relative w-full max-w-xl">
    <img src="photo1.jpg" alt="Photo 1" class="rounded-xl shadow-lg mx-auto" />
    <img src="photo2.jpg" alt="Photo 2" class="rounded-xl shadow-lg mx-auto hidden" />
    <img src="photo3.jpg" alt="Photo 3" class="rounded-xl shadow-lg mx-auto hidden" />
  </div>
  <div class="flex gap-4">
    <button class="glass-button" id="prevBtn">Previous</button>
    <button class="glass-button" id="nextBtn">Next</button>
  </div>
</section>

<!-- Closing Section -->
<section id="closingSection" class="hidden flex flex-col items-center justify-center min-h-screen text-center px-4">
  <h2 class="text-4xl md:text-6xl font-bold mb-6 animate-pulse text-red-500">አፈቅርሻለሁ ርግቤ 💕</h2>
  <p class="text-xl md:text-3xl">You are my heart, my dove, my everything.</p>
  <button class="glass-button mt-10" onclick="location.reload()">Replay</button>
</section>

<script>
const startBtn = document.getElementById('startBtn');
const photoSection = document.getElementById('photoSection');
const closingSection = document.getElementById('closingSection');
const photos = document.querySelectorAll('#photoSection img');
let current = 0;

startBtn.addEventListener('click', () => {
  document.querySelector('section').classList.add('hidden');
  photoSection.classList.remove('hidden');
  photos[current].classList.remove('hidden');
});

document.getElementById('nextBtn').addEventListener('click', () => {
  photos[current].classList.add('hidden');
  current++;
  if(current >= photos.length) {
    photoSection.classList.add('hidden');
    closingSection.classList.remove('hidden');
  } else {
    photos[current].classList.remove('hidden');
  }
});

document.getElementById('prevBtn').addEventListener('click', () => {
  if(current === 0) return;
  photos[current].classList.add('hidden');
  current--;
  photos[current].classList.remove('hidden');
});
</script>
</body>
</html>
