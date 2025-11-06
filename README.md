<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Base64 & String Decoder | Noman</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #00f7ff;
            --secondary: #ff00d4;
            --dark: #0a0a16;
            --darker: #050510;
            --light: #f0f8ff;
            --card-bg: rgba(10, 15, 35, 0.8);
        }

        body {
            background: linear-gradient(135deg, var(--darker), var(--dark));
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Header Styles */
        header {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
        }

        .header-content {
            position: relative;
            padding: 30px 0;
        }

        .title-3d {
            font-size: 3.5rem;
            font-weight: 800;
            text-transform: uppercase;
            color: transparent;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            text-shadow: 0 5px 15px rgba(0, 247, 255, 0.3);
            margin-bottom: 15px;
            letter-spacing: 2px;
            transform: perspective(500px) rotateX(15deg);
            transition: all 0.3s ease;
        }

        .title-3d:hover {
            transform: perspective(500px) rotateX(10deg) scale(1.05);
            text-shadow: 0 10px 25px rgba(0, 247, 255, 0.5);
        }

        .subtitle {
            font-size: 1.2rem;
            color: #a0a0e0;
            margin-bottom: 20px;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
        }

        .tagline {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 15px;
        }

        .tag {
            background: rgba(0, 247, 255, 0.1);
            padding: 8px 15px;
            border-radius: 30px;
            font-size: 0.9rem;
            border: 1px solid rgba(0, 247, 255, 0.3);
            box-shadow: 0 0 10px rgba(0, 247, 255, 0.2);
            transition: all 0.3s ease;
        }

        .tag:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 15px rgba(0, 247, 255, 0.4);
        }

        /* Main Content */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 40px;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        /* Card Styles */
        .card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(0, 247, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 247, 255, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.5s ease;
            opacity: 0;
        }

        .card:hover::before {
            opacity: 1;
            animation: shine 3s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .card:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 15px 35px rgba(0, 247, 255, 0.2);
        }

        .card-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card-title i {
            font-size: 1.2rem;
        }

        /* Input and Output Areas */
        .input-group {
            margin-bottom: 20px;
        }

        textarea {
            width: 100%;
            background: rgba(5, 10, 25, 0.7);
            border: 1px solid rgba(0, 247, 255, 0.3);
            border-radius: 10px;
            padding: 15px;
            color: var(--light);
            font-size: 1rem;
            resize: vertical;
            min-height: 150px;
            transition: all 0.3s ease;
        }

        textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 15px rgba(0, 247, 255, 0.3);
        }

        .output-area {
            background: rgba(5, 10, 25, 0.7);
            border: 1px solid rgba(0, 247, 255, 0.3);
            border-radius: 10px;
            padding: 15px;
            min-height: 150px;
            color: var(--light);
            overflow-y: auto;
            word-break: break-all;
        }

        /* Button Styles */
        .btn-3d {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: var(--darker);
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 247, 255, 0.4);
            position: relative;
            overflow: hidden;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .btn-3d::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: all 0.5s ease;
        }

        .btn-3d:hover::before {
            left: 100%;
        }

        .btn-3d:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 247, 255, 0.6);
        }

        .btn-3d:active {
            transform: translateY(1px);
            box-shadow: 0 3px 10px rgba(0, 247, 255, 0.4);
        }

        /* Features Section */
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .feature-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(0, 247, 255, 0.1);
        }

        .feature-card:hover {
            transform: translateY(-5px) rotateY(5deg);
            box-shadow: 0 10px 25px rgba(0, 247, 255, 0.2);
        }

        .feature-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .feature-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--light);
        }

        .feature-desc {
            font-size: 0.9rem;
            color: #a0a0e0;
        }

        /* Social Links */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: white;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .social-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.1);
            transform: scale(0);
            border-radius: 50%;
            transition: all 0.3s ease;
        }

        .social-btn:hover::before {
            transform: scale(1);
        }

        .social-btn:hover {
            transform: translateY(-5px) rotate(10deg);
        }

        .fb { background: #3b5998; }
        .wa { background: #25D366; }
        .tg { background: #0088cc; }

        /* Footer */
        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            border-top: 1px solid rgba(0, 247, 255, 0.2);
            color: #a0a0e0;
            font-size: 0.9rem;
        }

        .tech-stack {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin: 20px 0;
        }

        .tech-item {
            background: rgba(0, 247, 255, 0.1);
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            border: 1px solid rgba(0, 247, 255, 0.2);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .title-3d {
                font-size: 2.5rem;
            }
            
            .tagline {
                flex-direction: column;
                align-items: center;
            }
            
            .social-links {
                flex-wrap: wrap;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="header-content">
                <h1 class="title-3d">Base64 & String Decoder</h1>
                <p class="subtitle">A Beautiful Web-Based Base64 & String Decoder Tool Built by <b>Noman</b></p>
                <div class="tagline">
                    <span class="tag">Fast</span>
                    <span class="tag">Clean UI</span>
                    <span class="tag">Mobile Friendly</span>
                    <span class="tag">100% Free</span>
                </div>
            </div>
        </header>

        <div class="main-content">
            <div class="card">
                <h2 class="card-title"><i class="fas fa-code"></i> Input Base64</h2>
                <div class="input-group">
                    <textarea id="encodedText" placeholder="Paste your Base64 encoded string here..."></textarea>
                </div>
                <button class="btn-3d" onclick="decodeBase64()">
                    <i class="fas fa-play"></i> Decode Now
                </button>
            </div>

            <div class="card">
                <h2 class="card-title"><i class="fas fa-file-code"></i> Decoded Output</h2>
                <div class="output-area" id="outputText">
                    Your decoded text will appear here...
                </div>
                <button class="btn-3d" onclick="copyOutput()" style="margin-top: 15px;">
                    <i class="fas fa-copy"></i> Copy Output
                </button>
            </div>
        </div>

        <div class="features">
            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-bolt"></i>
                </div>
                <h3 class="feature-title">Instant Decoding</h3>
                <p class="feature-desc">Decode Base64 text instantly with a single click</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-shield-alt"></i>
                </div>
                <h3 class="feature-title">Error Handling</h3>
                <p class="feature-desc">Built-in error handling for invalid strings</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-palette"></i>
                </div>
                <h3 class="feature-title">Neon Dark UI</h3>
                <p class="feature-desc">Beautiful hacker-style neon dark theme</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-mobile-alt"></i>
                </div>
                <h3 class="feature-title">Mobile Friendly</h3>
                <p class="feature-desc">Works perfectly on all devices and screen sizes</p>
            </div>
        </div>

        <div class="social-links">
            <a href="#" class="social-btn fb">
                <i class="fab fa-facebook-f"></i>
            </a>
            <a href="#" class="social-btn wa">
                <i class="fab fa-whatsapp"></i>
            </a>
            <a href="#" class="social-btn tg">
                <i class="fab fa-telegram-plane"></i>
            </a>
        </div>

        <div class="tech-stack">
            <span class="tech-item">HTML</span>
            <span class="tech-item">CSS</span>
            <span class="tech-item">JavaScript</span>
            <span class="tech-item">SweetAlert2</span>
        </div>

        <footer>
            <p>Built with ❤️ by Noman | 100% Free & Open Source</p>
            <p>No server needed — runs fully in browser</p>
        </footer>
    </div>

    <script>
        function decodeBase64() {
            var inputBase64 = document.getElementById("encodedText").value.trim();
            
            if (!inputBase64) {
                Swal.fire({
                    title: "Empty Input!",
                    text: "Please enter a Base64 string to decode",
                    icon: "warning",
                    confirmButtonColor: "#00f7ff"
                });
                return;
            }
            
            try {
                // Try to decode the Base64 string
                var decoded = atob(inputBase64);
                
                // Try to convert from UTF-8 if it's text
                try {
                    decoded = decodeURIComponent(escape(decoded));
                } catch (e) {
                    // If it fails, it might be binary data, so we keep the original decoded string
                }
                
                document.getElementById("outputText").textContent = decoded;
                
                // Success animation
                document.getElementById("outputText").style.animation = "none";
                setTimeout(() => {
                    document.getElementById("outputText").style.animation = "pulse 0.5s";
                }, 10);
                
            } catch (e) {
                Swal.fire({
                    title: "❌ Error!",
                    text: "Invalid or non-Base64 string!",
                    icon: "error",
                    confirmButtonColor: "#ff00d4"
                });
            }
        }

        function copyOutput() {
            const outputText = document.getElementById("outputText").textContent;
            
            if (outputText === "Your decoded text will appear here...") {
                Swal.fire({
                    title: "Nothing to Copy!",
                    text: "Please decode some text first",
                    icon: "warning",
                    confirmButtonColor: "#00f7ff"
                });
                return;
            }
            
            navigator.clipboard.writeText(outputText).then(() => {
                Swal.fire({
                    title: "Copied!",
                    text: "Decoded text copied to clipboard",
                    icon: "success",
                    confirmButtonColor: "#00f7ff",
                    timer: 1500
                });
            });
        }

        // Add some example Base64 on page load for demonstration
        window.onload = function() {
            // Example Base64 string: "Hello, World!" encoded
            document.getElementById("encodedText").value = "SGVsbG8sIFdvcmxkIQ==";
        };
    </script>
</body>
</html>
