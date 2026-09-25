<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website Generate Key</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 50%, #6a11cb 100%);
            padding: 20px;
            position: relative;
            overflow: hidden;
        }

        /* Efek dekorasi background */
        body::before,
        body::after {
            content: '';
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.5;
            z-index: 0;
        }

        body::before {
            width: 400px;
            height: 400px;
            background: #ff6ec4;
            top: -100px;
            left: -100px;
            animation: float 8s ease-in-out infinite;
        }

        body::after {
            width: 500px;
            height: 500px;
            background: #7873f5;
            bottom: -150px;
            right: -150px;
            animation: float 10s ease-in-out infinite reverse;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(30px, 30px); }
        }

        .card {
            position: relative;
            z-index: 1;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 24px;
            padding: 50px 40px;
            max-width: 600px;
            width: 100%;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
            animation: slideUp 0.8s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .icon {
            width: 80px;
            height: 80px;
            margin: 0 auto 25px;
            background: linear-gradient(135deg, #ff6ec4, #7873f5);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 10px 30px rgba(255, 110, 196, 0.4);
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .icon svg {
            width: 40px;
            height: 40px;
            fill: white;
        }

        h1 {
            font-size: 1.8rem;
            color: #ffffff;
            margin-bottom: 15px;
            font-weight: 700;
            letter-spacing: 1px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .subtitle {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.85);
            margin-bottom: 35px;
            line-height: 1.6;
            letter-spacing: 0.5px;
        }

        .btn {
            display: inline-block;
            padding: 18px 45px;
            font-size: 1.1rem;
            font-weight: 700;
            letter-spacing: 1px;
            text-transform: uppercase;
            text-decoration: none;
            color: #ffffff;
            background: linear-gradient(135deg, #ff6ec4 0%, #7873f5 100%);
            border-radius: 50px;
            box-shadow: 0 10px 30px rgba(120, 115, 245, 0.5);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            border: none;
            cursor: pointer;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s ease;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(120, 115, 245, 0.7);
        }

        .btn:active {
            transform: translateY(-1px);
            box-shadow: 0 8px 20px rgba(120, 115, 245, 0.5);
        }

        /* Responsif */
        @media (max-width: 600px) {
            .card {
                padding: 40px 25px;
            }

            h1 {
                font-size: 1.4rem;
            }

            .subtitle {
                font-size: 0.9rem;
            }

            .btn {
                padding: 16px 30px;
                font-size: 0.95rem;
            }

            .icon {
                width: 65px;
                height: 65px;
            }

            .icon svg {
                width: 32px;
                height: 32px;
            }
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="icon">
            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4zm0 10.99h7c-.53 4.12-3.28 7.79-7 8.94V12H5V6.3l7-3.11v8.8z"/>
            </svg>
        </div>

        <h1>WEBSITE GENERATE KEY</h1>
        <p class="subtitle">
            SUDAH TIDAK ADA DISINI UNTUK LANJUT GENERATE KEY,<br>
            MOHON TEKAN TOMBOL BERIKUT
        </p>

        <a href="https://vertifikasi-zetgames.lovable.app" class="btn" target="_blank" rel="noopener noreferrer">
            Generate Key Sekarang
        </a>
    </div>
</body>
</html>
