<!DOCTYPE html><html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Yumi 💖</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400;600&family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }body {
        height: 100vh;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        font-family: 'Poppins', sans-serif;
    }

    .card, .letter {
        background: white;
        padding: 40px;
        border-radius: 25px;
        text-align: center;
        box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        max-width: 650px;
        animation: fadeIn 1.5s ease-in-out;
        position: relative;
        z-index: 10;
    }

    h1 {
        font-family: 'Great Vibes', cursive;
        font-size: 42px;
        color: #ff4b6e;
        margin-bottom: 15px;
    }

    h2 {
        font-family: 'Playfair Display', serif;
        color: #ff4b6e;
        margin-bottom: 20px;
    }

    p {
        color: #555;
        margin-bottom: 18px;
        line-height: 1.7;
        font-size: 15px;
    }

    .buttons {
        display: flex;
        justify-content: center;
        gap: 20px;
        margin-top: 20px;
    }

    button {
        padding: 12px 25px;
        border: none;
        border-radius: 25px;
        background-color: #ff4b6e;
        color: white;
        font-size: 16px;
        cursor: pointer;
        transition: 0.3s;
    }

    button:hover {
        background-color: #ff1f4d;
        transform: scale(1.05);
    }

    #noBtn { background-color: #aaa; position: relative; }

    .heart {
        position: absolute;
        color: #ff4b6e;
        font-size: 20px;
        animation: float 5s linear infinite;
    }

    @keyframes float {
        0% { transform: translateY(100vh); opacity: 1; }
        100% { transform: translateY(-10vh); opacity: 0; }
    }

    @keyframes fadeIn {
        from {opacity: 0; transform: translateY(20px);} 
        to {opacity: 1; transform: translateY(0);} 
    }

    .hidden { display: none; }

    .sad {
        margin-top: 15px;
        color: #ff4b6e;
        font-weight: 600;
    }

    canvas {
        position: fixed;
        top: 0;
        left: 0;
        pointer-events: none;
    }
</style>

</head>
<body><!-- Background Music (Perfect - Ed Sheeran Instrumental) --><iframe width="0" height="0" src="https://www.youtube.com/embed/2Vv-BfVoq4g?autoplay=1&loop=1&playlist=2Vv-BfVoq4g" frameborder="0" allow="autoplay"></iframe><div class="card" id="questionCard">
    <h1>Yumi 💕</h1>
    <h2>Will you be my Valentine?</h2>
    <div class="buttons">
        <button onclick="sayYes()">Yes 💖</button>
        <button id="noBtn" onmouseover="moveNo()" onclick="sayNo()">No 💔</button>
    </div>
    <div id="sadText" class="sad hidden"></div>
</div><div class="letter hidden" id="letterCard">
    <h1>for my dearest one</h1>
    <p>If I could hand you this letter quietly, I would. No expectations attached — just honesty.</p>
    <p>We ended things in a way most people don’t get to. No drama, no harsh words. Just two people who cared about each other, but were pulled in different directions by life. And strangely, that makes it harder to forget.</p>
    <p>I’ve thought about us — not with regret, but with clarity. What we had wasn’t loud or reckless. It was steady. Comfortable. Real. And it mattered.</p>
    <p>We didn’t fall apart because we stopped choosing each other. We simply got overwhelmed by responsibilities, deadlines, and the pace of everything around us. Timing can be unforgiving like that.</p>
    <p>I won’t pretend I don’t still carry a quiet space for you. Not in a way that holds me back, but in a way that reminds me something genuine once existed. And that matters to me more than I say.</p>
    <p>Valentine’s Day feels like an easy excuse to speak gently about things we usually keep inside. So here it is — I’m grateful for you. For what we had. For how we ended it with respect.</p>
    <p>If life ever becomes lighter, and our paths align again, I’d meet you with the same sincerity — maybe even stronger than before.</p>
    <p>Until then, I hope you’re happy. Truly. And I hope you know that you were loved in a calm, certain, and intentional way.</p>
</div><canvas id="confetti"></canvas>

<script>
    let noClickCount = 0;

    function moveNo() {
        const noBtn = document.getElementById("noBtn");
        noBtn.style.position = "absolute";
        noBtn.style.top = Math.random() * 200 - 100 + "px";
        noBtn.style.left = Math.random() * 200 - 100 + "px";
    }

    function sayNo() {
        noClickCount++;
        const sadText = document.getElementById("sadText");
        sadText.classList.remove("hidden");
        sadText.innerHTML = "Are you sure? 🥺💔";
    }

    function sayYes() {
        document.getElementById("questionCard").classList.add("hidden");
        document.getElementById("letterCard").classList.remove("hidden");
        startConfetti();
    }

    function createHeart() {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "❤";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = Math.random() * 20 + 10 + "px";
        heart.style.animationDuration = Math.random() * 3 + 2 + "s";
        document.body.appendChild(heart);
        setTimeout(() => { heart.remove(); }, 5000);
    }

    setInterval(createHeart, 300);

    // Simple Confetti Effect
    const canvas = document.getElementById("confetti");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let pieces = [];

    function startConfetti() {
        for (let i = 0; i < 150; i++) {
            pieces.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                r: Math.random() * 6 + 4,
                d: Math.random() * 50
            });
        }
        updateConfetti();
    }

    function updateConfetti() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#ff4b6e";
        pieces.forEach(p => {
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
            ctx.fill();
            p.y += 2;
            if (p.y > canvas.height) p.y = 0;
        });
        requestAnimationFrame(updateConfetti);
    }
</script></body>
</html>
