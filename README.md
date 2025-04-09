<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Carta do Coração</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            background: linear-gradient(135deg, #ffb6c1 0%, #fff0f5 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 0;
            font-family: 'Dancing Script', cursive;
            overflow: hidden;
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            text-align: center;
            position: relative;
        }

        .hearthover {
            animation: pulse 2s infinite;
            font-size: 3rem;
            margin: 1rem;
            cursor: pointer;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .text-animation {
            animation: typing 3s steps(40), blink-caret 0.75s step-end infinite;
            white-space: nowrap;
            overflow: hidden;
            border-right: 2px solid #ff69b4;
            font-size: 1.5rem;
            margin: 1rem 0;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        /* Corações flutuantes */
        .heart {
            position: absolute;
            opacity: 0;
            animation: float 6s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(45deg); opacity: 0; }
            20% { opacity: 1; }
            100% { transform: translateY(-100vh) rotate(45deg); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="text-animation" id="message"></div>
        <div class="hearthover">❤️</div>
    </div>

    <script>
        // Banco de frases (adicione novas aqui!)
        const frases = [
            "Você é meu hoje e todos os amanhãs.",
            "A cada dia, meu coração encontra novos motivos para te amar.",
            "Nossa história é meu conto favorito."
        ];

        // Seleção aleatória ao carregar a página
        window.onload = function() {
            const randomIndex = Math.floor(Math.random() * frases.length);
            document.getElementById('message').textContent = frases[randomIndex];
            
            // Cria corações flutuantes
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = '❤️';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = Math.random() * 3 + 4 + 's';
                document.body.appendChild(heart);
                
                setTimeout(() => heart.remove(), 6000);
            }, 1000);
        };
    </script>
</body>
</html>
