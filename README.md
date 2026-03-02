<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Dancing+Script:wght@500&display=swap" rel="stylesheet">

<style>

body {
    margin: 0;
    padding: 0;
    background: black;
    color: #cfcfcf;
    font-family: 'Playfair Display', serif;
    text-align: center;
    overflow-x: hidden;
}

/* النجوم */
canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 0;
}

.container {
    position: relative;
    z-index: 2;
    padding: 60px 15px;
}

h1 {
    font-size: 42px;
    color: #f0f0f0;
    margin-bottom: 30px;
    letter-spacing: 3px;
}

.text {
    max-width: 750px;
    margin: auto;
    line-height: 1.9;
    font-size: 15px;
    color: #b8b8b8;
}

.signature {
    margin-top: 40px;
    font-style: italic;
    font-size: 14px;
    color: #999;
}

/* الشريط */
.gallery {
    margin-top: 70px;
    overflow: hidden;
    width: 100%;
    position: relative;
    mask-image: linear-gradient(to right, transparent, black 10%, black 90%, transparent);
}

.slider {
    display: flex;
    animation: slide 45s linear infinite;
}

.slider:hover {
    animation-play-state: paused;
}

@keyframes slide {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
}

.slider img {
    width: 170px;
    height: 220px;
    object-fit: cover;
    margin: 10px;
    border-radius: 16px;
    border: 1px solid #555;
    filter: grayscale(60%) brightness(85%);
    transition: 0.6s ease;
}

.slider img:hover {
    filter: grayscale(0%) brightness(100%);
    transform: scale(1.08);
}

/* النص الختامي */
.closing {
    margin-top: 80px;
    font-family: 'Dancing Script', cursive;
    font-size: 22px;
    color: #e0e0e0;
}

/* النجمة */
.bigstar {
    font-size: 95px;
    color: #888;
    margin-top: 40px;
    animation: glow 3s infinite alternate;
}

@keyframes glow {
    from { text-shadow: 0 0 10px #666; }
    to { text-shadow: 0 0 40px #ffffff; }
}

/* Responsive */
@media (min-width: 768px) {
    h1 { font-size: 60px; }
    .text { font-size: 18px; }
    .slider img { width: 220px; height: 280px; }
}

</style>
</head>

<body>

<canvas id="stars"></canvas>

<div class="container">

<h1>Happy Birthday</h1>

<div class="text">

<p>
<!-- ضعي هنا نصك الكامل -->
</p>

<div class="signature">
From your girl who never knew how to express,<br>
but always tried for you — with prayers and a hopeless hope.
</div>

</div>

<div class="gallery">
<div class="slider">
<img src="img1.jpg">
<img src="img2.jpg">
<img src="img3.jpg">
<img src="img4.jpg">
<img src="img5.jpg">
<img src="img6.jpg">
<img src="img7.jpg">

<img src="img1.jpg">
<img src="img2.jpg">
<img src="img3.jpg">
<img src="img4.jpg">
<img src="img5.jpg">
<img src="img6.jpg">
<img src="img7.jpg">
</div>
</div>

<div class="closing">
Remember to always be happy and shining in all your moments.<br>
You are the light that never fades — with me or without me.
</div>

<div class="bigstar">★</div>

</div>

<script>
const canvas = document.getElementById("stars");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let stars = [];

for (let i = 0; i < 180; i++) {
    stars.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        radius: Math.random() * 1.5,
        speed: Math.random() * 0.4
    });
}

function drawStars() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "white";

    stars.forEach(star => {
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
        ctx.fill();

        star.y += star.speed;

        if (star.y > canvas.height) {
            star.y = 0;
            star.x = Math.random() * canvas.width;
        }
    });

    requestAnimationFrame(drawStars);
}

drawStars();
</script>

</body>
</html>
