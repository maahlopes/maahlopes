
<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=B5EAD7&height=120&section=header&text=BEM-VINDO&fontSize=40&fontColor=333&animation=twinkling&fontAlignY=35&desc=🐢%20♡&descAlignY=55"/>

[index.html.html](https://github.com/user-attachments/files/29047747/index.html.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Tartaruga do Git</title>
    <style>
        body { background-color: #1a1a1a; color: white; font-family: monospace; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; overflow: hidden; }
        canvas { border: 2px solid #333; background: #111; }
    </style>
</head>
<body>
    <canvas id="turtleCanvas" width="800" height="300"></canvas>
    <script>
        const canvas = document.getElementById('turtleCanvas');
        const ctx = canvas.getContext('2d');
        
        let x = 50;
        let targetX = 50;
        let step = 0;
        const commits = [
            { msg: "init: casco", target: 200 },
            { msg: "feat: patas", target: 400 },
            { msg: "fix: velocidade", target: 600 }
        ];

        function drawTurtle(cx, cy) {
            ctx.fillStyle = '#39ff14';
            ctx.beginPath(); ctx.arc(cx, cy, 15, 0, Math.PI * 2); ctx.fill();
            ctx.fillStyle = '#1d970c';
            ctx.beginPath(); ctx.arc(cx + 12, cy - 12, 6, 0, Math.PI * 2); ctx.fill();
            ctx.beginPath(); ctx.arc(cx + 12, cy + 12, 6, 0, Math.PI * 2); ctx.fill();
            ctx.beginPath(); ctx.arc(cx - 12, cy - 12, 6, 0, Math.PI * 2); ctx.fill();
            ctx.beginPath(); ctx.arc(cx - 12, cy + 12, 6, 0, Math.PI * 2); ctx.fill();
            ctx.fillStyle = '#4ae225';
            ctx.beginPath(); ctx.arc(cx + 18, cy, 7, 0, Math.PI * 2); ctx.fill();
        }

        function animar() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            ctx.strokeStyle = '#39ff14';
            ctx.lineWidth = 4;
            ctx.beginPath();
            ctx.moveTo(50, 150);
            ctx.lineTo(x, 150);
            ctx.stroke();

            for (let i = 0; i < step; i++) {
                ctx.fillStyle = '#ff007f';
                ctx.beginPath(); ctx.arc(commits[i].target, 150, 8, 0, Math.PI * 2); ctx.fill();
                ctx.fillStyle = '#fff';
                ctx.font = '14px monospace';
                ctx.fillText(commits[i].msg, commits[i].target - 40, 120);
            }

            if (x < targetX) {
                x += 3;
            } else if (step < commits.length) {
                step++;
                if (step < commits.length) {
                    targetX = commits[step].target;
                }
            }

            drawTurtle(x, 150);
            requestAnimationFrame(animar);
        }

        targetX = commits[0].target;
        animar();
    </script>
</body>
</html>


https://github.com/user-attachments/assets/1da8a18c-9e46-40bb-8e6a-115495d6b252

