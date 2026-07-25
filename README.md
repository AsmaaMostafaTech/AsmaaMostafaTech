<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Full-Stack Developer Portfolio | GitHub README</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://code.iconify.design/iconify-icon/1.0.7/iconify-icon.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Cairo:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            bg: '#050510',
                            panel: '#0a0a1a',
                            text: '#e0e0e0',
                            cyan: '#00f0ff',
                            pink: '#ff2d95',
                            green: '#39ff14',
                            yellow: '#ffe600',
                            dim: '#1a1a2e',
                            border: '#1e1e3a',
                        }
                    },
                    fontFamily: {
                        mono: ['JetBrains Mono', 'monospace'],
                        arabic: ['Cairo', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background: #050510;
            color: #e0e0e0;
            font-family: 'Cairo', sans-serif;
            overflow-x: hidden;
        }

        /* Scanlines */
        .scanlines::after {
            content: '';
            position: fixed;
            inset: 0;
            background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.08) 2px, rgba(0,0,0,0.08) 4px);
            pointer-events: none;
            z-index: 9999;
        }

        /* Grid background */
        .grid-bg {
            background-image:
                linear-gradient(rgba(0,240,255,0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0,240,255,0.03) 1px, transparent 1px);
            background-size: 40px 40px;
        }

        /* Glow text */
        .glow-cyan { text-shadow: 0 0 10px rgba(0,240,255,0.6), 0 0 30px rgba(0,240,255,0.3); }
        .glow-pink { text-shadow: 0 0 10px rgba(255,45,149,0.6), 0 0 30px rgba(255,45,149,0.3); }
        .glow-green { text-shadow: 0 0 10px rgba(57,255,20,0.6), 0 0 30px rgba(57,255,20,0.3); }

        /* Typing cursor */
        .typing-cursor::after {
            content: '█';
            color: #00f0ff;
            animation: blink 0.8s infinite;
        }
        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        /* Fade in up */
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .fade-in-up {
            animation: fadeInUp 0.8s cubic-bezier(0.16,1,0.3,1) forwards;
            opacity: 0;
        }

        /* Skill bar fill */
        @keyframes fillBar {
            from { width: 0%; }
        }
        .skill-fill {
            animation: fillBar 1.5s cubic-bezier(0.16,1,0.3,1) forwards;
        }

        /* Card hover */
        .project-card {
            transition: all 0.3s ease;
            border: 1px solid #1e1e3a;
        }
        .project-card:hover {
            border-color: #00f0ff;
            box-shadow: 0 0 20px rgba(0,240,255,0.15);
            transform: translateY(-4px);
        }

        /* Stats card */
        .stat-card {
            background: linear-gradient(135deg, #0a0a1a 0%, #1a1a2e 100%);
            border: 1px solid #1e1e3a;
            transition: all 0.3s;
        }
        .stat-card:hover {
            border-color: #ff2d95;
            box-shadow: 0 0 15px rgba(255,45,149,0.15);
        }

        /* Pulse ring */
        @keyframes pulseRing {
            0% { transform: scale(0.8); opacity: 0.8; }
            100% { transform: scale(2.5); opacity: 0; }
        }
        .pulse-ring::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 50%;
            border: 2px solid #00f0ff;
            animation: pulseRing 2s ease-out infinite;
        }

        /* Terminal window */
        .terminal-window {
            background: #0a0a1a;
            border: 1px solid #1e1e3a;
            border-radius: 8px;
            overflow: hidden;
        }
        .terminal-header {
            background: #1a1a2e;
            padding: 8px 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .terminal-dot {
            width: 12px; height: 12px; border-radius: 50%;
        }

        /* Scroll indicator */
        @keyframes scrollBounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(8px); }
        }
        .scroll-indicator {
            animation: scrollBounce 2s ease-in-out infinite;
        }

        /* Badge hover */
        .tech-badge {
            transition: all 0.2s;
            border: 1px solid rgba(0,240,255,0.2);
        }
        .tech-badge:hover {
            background: rgba(0,240,255,0.1);
            border-color: #00f0ff;
            transform: scale(1.05);
        }

        /* Gradient borders */
        .gradient-border {
            position: relative;
        }
        .gradient-border::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: inherit;
            padding: 1px;
            background: linear-gradient(135deg, #00f0ff, #ff2d95, #00f0ff);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask-composite: exclude;
            -webkit-mask-composite: xor;
            pointer-events: none;
        }

        /* Markdown code block style */
        .md-code {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 6px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 13px;
            overflow-x: auto;
        }

        /* Section divider */
        .section-divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, #00f0ff33, #ff2d9533, transparent);
        }

        /* Glow border on focus */
        *:focus-visible {
            outline: 2px solid #00f0ff;
            outline-offset: 2px;
        }

        /* Smooth scroll */
        html { scroll-behavior: smooth; }

        /* Toast notification */
        .toast {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: #0a0a1a;
            border: 1px solid #00f0ff;
            padding: 12px 24px;
            border-radius: 8px;
            z-index: 10000;
            transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
            font-family: 'JetBrains Mono', monospace;
        }
        .toast.show {
            transform: translateX(-50%) translateY(0);
        }

        /* Tab active */
        .tab-btn {
            transition: all 0.3s;
        }
        .tab-btn.active {
            color: #00f0ff;
            border-bottom: 2px solid #00f0ff;
        }

        /* Connection line animation */
        @keyframes dash {
            to { stroke-dashoffset: 0; }
        }

        /* Counter animation */
        @keyframes countUp {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body class="scanlines grid-bg">

    <!-- Toast -->
    <div id="toast" class="toast">
        <span class="text-cyber-cyan">✓</span> <span id="toast-msg">Copied!</span>
    </div>

    <!-- Navigation -->
    <nav class="fixed top-0 left-0 right-0 z-50 backdrop-blur-md bg-cyber-bg/80 border-b border-cyber-border">
        <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
            <div class="flex items-center gap-2">
                <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-cyber-cyan to-cyber-pink flex items-center justify-center">
                    <iconify-icon icon="mdi:code-braces" class="text-white text-lg"></iconify-icon>
                </div>
                <span class="font-mono text-cyber-cyan text-sm glow-cyan">&lt;dev/&gt;</span>
            </div>
            <div class="hidden md:flex items-center gap-8 font-mono text-xs text-cyber-text/60">
                <a href="#about" class="hover:text-cyber-cyan transition-colors">about()</a>
                <a href="#skills" class="hover:text-cyber-cyan transition-colors">skills()</a>
                <a href="#projects" class="hover:text-cyber-cyan transition-colors">projects()</a>
                <a href="#stats" class="hover:text-cyber-cyan transition-colors">stats()</a>
                <a href="#contact" class="hover:text-cyber-cyan transition-colors">contact()</a>
            </div>
            <button id="copy-md-btn" class="font-mono text-xs px-4 py-2 rounded border border-cyber-cyan/30 text-cyber-cyan hover:bg-cyber-cyan/10 transition-all flex items-center gap-2">
                <iconify-icon icon="mdi:content-copy" class="text-sm"></iconify-icon>
                Copy README.md
            </button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="hero" class="min-h-screen flex items-center justify-center pt-20 pb-16 px-6 relative">
        <!-- Animated background circles -->
        <div class="absolute top-1/4 left-1/4 w-64 h-64 rounded-full bg-cyber-cyan/5 blur-[100px] animate-pulse"></div>
        <div class="absolute bottom-1/4 right-1/4 w-64 h-64 rounded-full bg-cyber-pink/5 blur-[100px] animate-pulse" style="animation-delay:1s"></div>

        <div class="max-w-4xl w-full text-center">
            <!-- Terminal window -->
            <div class="terminal-window mb-8 fade-in-up" style="animation-delay:0.1s">
                <div class="terminal-header">
                    <div class="terminal-dot bg-cyber-pink"></div>
                    <div class="terminal-dot bg-cyber-yellow"></div>
                    <div class="terminal-dot bg-cyber-green"></div>
                    <span class="font-mono text-xs text-cyber-text/40 ml-2">bash — profile.sh</span>
                </div>
                <div class="p-6 font-mono text-sm leading-relaxed" dir="ltr">
                    <div class="text-cyber-text/40 mb-2">$ whoami</div>
                    <div id="typing-line" class="text-cyber-cyan glow-cyan typing-cursor"></div>
                </div>
            </div>

            <!-- Avatar & Name -->
            <div class="fade-in-up flex flex-col items-center gap-6" style="animation-delay:0.4s">
                <div class="relative w-32 h-32 rounded-full overflow-hidden gradient-border pulse-ring">
                    <img src="https://picsum.photos/seed/devavatar2024/256/256.jpg" alt="Profile" class="w-full h-full object-cover rounded-full" />
                    <div class="absolute inset-0 rounded-full bg-gradient-to-b from-cyber-cyan/10 to-transparent"></div>
                </div>

                <div>
                    <h1 class="text-4xl md:text-6xl font-bold font-mono glow-cyan text-cyber-cyan" dir="ltr">
                        Ahmed<span class="text-cyber-pink glow-pink">.</span>dev
                    </h1>
                    <p class="text-lg md:text-xl text-cyber-text/70 mt-3 font-arabic">
                        مطور ويب Full-Stack 🚀 | أبني تطبيقات من الصفر للإنتاج
                    </p>
                </div>

                <!-- Status badge -->
                <div class="flex items-center gap-3 px-4 py-2 rounded-full bg-cyber-green/10 border border-cyber-green/30">
                    <div class="w-2 h-2 rounded-full bg-cyber-green animate-pulse"></div>
                    <span class="font-mono text-xs text-cyber-green glow-green">Available for hire</span>
                </div>

                <!-- Quick stats -->
                <div class="flex items-center gap-6 mt-4 font-mono text-xs text-cyber-text/50">
                    <div class="flex items-center gap-2">
                        <iconify-icon icon="mdi:map-marker" class="text-cyber-pink"></iconify-icon>
                        <span>Egypt 🇪🇬</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <iconify-icon icon="mdi:calendar" class="text-cyber-cyan"></iconify-icon>
                        <span>3+ years exp</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <iconify-icon icon="mdi:coffee" class="text-cyber-yellow"></iconify-icon>
                        <span>∞ cups consumed</span>
                    </div>
                </div>
            </div>

            <!-- Scroll indicator -->
            <div class="mt-12 scroll-indicator">
                <iconify-icon icon="mdi:chevron-double-down" class="text-cyber-cyan/50 text-2xl"></iconify-icon>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- About Section -->
    <section id="about" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-8 fade-in-up">
                <iconify-icon icon="mdi:account-circle" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">about_me<span class="text-cyber-pink">()</span></h2>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <!-- Terminal style about -->
                <div class="terminal-window fade-in-up" style="animation-delay:0.2s" dir="ltr">
                    <div class="terminal-header">
                        <div class="terminal-dot bg-cyber-pink"></div>
                        <div class="terminal-dot bg-cyber-yellow"></div>
                        <div class="terminal-dot bg-cyber-green"></div>
                        <span class="font-mono text-xs text-cyber-text/40 ml-2">about.json</span>
                    </div>
                    <div class="p-5 font-mono text-xs leading-loose">
                        <div class="text-cyber-text/40">{</div>
                        <div class="pl-4"><span class="text-cyber-pink">"name"</span>: <span class="text-cyber-green">"Ahmed Hassan"</span>,</div>
                        <div class="pl-4"><span class="text-cyber-pink">"role"</span>: <span class="text-cyber-green">"Full-Stack Web Developer"</span>,</div>
                        <div class="pl-4"><span class="text-cyber-pink">"location"</span>: <span class="text-cyber-green">"Cairo, Egypt"</span>,</div>
                        <div class="pl-4"><span class="text-cyber-pink">"education"</span>: <span class="text-cyber-green">"CS - Cairo University"</span>,</div>
                        <div class="pl-4"><span class="text-cyber-pink">"languages"</span>: [<span class="text-cyber-yellow">"Arabic"</span>, <span class="text-cyber-yellow">"English"</span>],</div>
                        <div class="pl-4"><span class="text-cyber-pink">"interests"</span>: [<span class="text-cyber-yellow">"Open Source"</span>, <span class="text-cyber-yellow">"UI/UX"</span>, <span class="text-cyber-yellow">"AI"</span>],</div>
                        <div class="pl-4"><span class="text-cyber-pink">"currentFocus"</span>: <span class="text-cyber-green">"Scalable Web Apps"</span>,</div>
                        <div class="pl-4"><span class="text-cyber-pink">"funFact"</span>: <span class="text-cyber-green">"I debug with console.log 😅"</span></div>
                        <div class="text-cyber-text/40">}</div>
                    </div>
                </div>

                <!-- Description -->
                <div class="fade-in-up space-y-4" style="animation-delay:0.4s">
                    <p class="text-cyber-text/80 leading-relaxed text-lg font-arabic">
                        مرحبا! 👋 أنا أحمد، مطور Full-Stack بشغف لبناء تطبيقات ويب حديثة وتجارب مستخدم مميزة.
                    </p>
                    <p class="text-cyber-text/70 leading-relaxed font-arabic">
                        أعمل مع React و Node.js و PostgreSQL لبناء تطبيقات قابلة للتوسع. أحب المساهمة في Open Source والتعلم المستمر. مؤمن أن الكود النظيف والتصميم الجيد لا يتناقضان 💡
                    </p>
                    <p class="text-cyber-text/70 leading-relaxed font-arabic">
                        في وقت فراغي، أقرأ عن AI، أجرب تقنيات جديدة، وأشارك ما تعلمته على مدونتي وبالتويتر.
                    </p>

                    <!-- Philosophy quote -->
                    <div class="p-4 rounded-lg bg-cyber-dim border border-cyber-border mt-6" dir="ltr">
                        <iconify-icon icon="mdi:format-quote-open" class="text-cyber-cyan text-xl"></iconify-icon>
                        <p class="font-mono text-sm text-cyber-text/70 italic mt-1">
                            "First, solve the problem. Then, write the code."
                        </p>
                        <p class="font-mono text-xs text-cyber-text/40 mt-2">— John Johnson</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- Skills Section -->
    <section id="skills" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-8 fade-in-up">
                <iconify-icon icon="mdi:code-tags" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">tech_stack<span class="text-cyber-pink">()</span></h2>
            </div>

            <!-- Tabs -->
            <div class="flex gap-4 mb-8 border-b border-cyber-border pb-2 font-mono text-sm overflow-x-auto" id="skill-tabs">
                <button class="tab-btn active text-cyber-cyan px-3 pb-2 whitespace-nowrap" data-tab="frontend">Frontend</button>
                <button class="tab-btn text-cyber-text/50 px-3 pb-2 whitespace-nowrap" data-tab="backend">Backend</button>
                <button class="tab-btn text-cyber-text/50 px-3 pb-2 whitespace-nowrap" data-tab="database">Database</button>
                <button class="tab-btn text-cyber-text/50 px-3 pb-2 whitespace-nowrap" data-tab="tools">DevOps & Tools</button>
                <button class="tab-btn text-cyber-text/50 px-3 pb-2 whitespace-nowrap" data-tab="other">Other</button>
            </div>

            <!-- Frontend -->
            <div id="tab-frontend" class="tab-content">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:react" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">React</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:90%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:nextjs-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Next.js</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:85%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:typescript-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">TypeScript</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:80%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:tailwindcss-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">TailwindCSS</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:92%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:vue" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Vue.js</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:70%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:javascript" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">JavaScript</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:95%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:html-5" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">HTML5</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:98%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:css-3" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">CSS3</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-cyan rounded skill-fill" style="width:95%"></div></div>
                    </div>
                </div>
            </div>

            <!-- Backend -->
            <div id="tab-backend" class="tab-content hidden">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:nodejs-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Node.js</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:88%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:express" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Express</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:85%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:python" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Python</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:75%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:nestjs" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">NestJS</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:70%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:graphql" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">GraphQL</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:72%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:django-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Django</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:65%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:jwt" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">JWT Auth</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:90%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="mdi:api" class="text-3xl text-cyber-pink"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">REST API</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-pink rounded skill-fill" style="width:92%"></div></div>
                    </div>
                </div>
            </div>

            <!-- Database -->
            <div id="tab-database" class="tab-content hidden">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:postgresql" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">PostgreSQL</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:85%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:mongodb-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">MongoDB</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:80%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:redis" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Redis</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:68%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:prisma" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Prisma</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:78%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:mysql-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">MySQL</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:75%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:supabase-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Supabase</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:72%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:firebase" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Firebase</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:70%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="mdi:database-search" class="text-3xl text-cyber-green"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">SQLite</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-green rounded skill-fill" style="width:80%"></div></div>
                    </div>
                </div>
            </div>

            <!-- DevOps & Tools -->
            <div id="tab-tools" class="tab-content hidden">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:docker-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Docker</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:78%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:git-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Git</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:92%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:github-icon" class="text-3xl invert"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">GitHub</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:90%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:vercel-icon" class="text-3xl invert"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Vercel</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:85%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:aws" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">AWS</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:60%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:linux-tux" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Linux</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:75%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:nginx" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Nginx</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:65%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:github-actions-icon" class="text-3xl invert"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">CI/CD</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-yellow rounded skill-fill" style="width:70%"></div></div>
                    </div>
                </div>
            </div>

            <!-- Other -->
            <div id="tab-other" class="tab-content hidden">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:figma" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Figma</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:70%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:jest" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Jest</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:75%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:storybook-icon" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Storybook</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:65%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:stripe" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Stripe</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:60%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:socket-io" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Socket.io</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:72%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="mdi:robot-outline" class="text-3xl text-cyber-text/70"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">OpenAI API</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:68%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:webpack" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Webpack</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:65%"></div></div>
                    </div>
                    <div class="tech-badge rounded-lg p-4 bg-cyber-panel flex flex-col items-center gap-2 cursor-default">
                        <iconify-icon icon="logos:yarn" class="text-3xl"></iconify-icon>
                        <span class="font-mono text-xs text-cyber-text">Yarn/npm</span>
                        <div class="w-full h-1 rounded bg-cyber-dim overflow-hidden"><div class="h-full bg-cyber-text/60 rounded skill-fill" style="width:90%"></div></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- Projects Section -->
    <section id="projects" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-8 fade-in-up">
                <iconify-icon icon="mdi:folder-open" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">featured_projects<span class="text-cyber-pink">()</span></h2>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Project 1 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.1s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:folder-star" class="text-cyber-cyan text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-cyan transition-colors mb-2" dir="ltr">E-Commerce Platform</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        منصة تجارة إلكترونية كاملة مع نظام دفع Stripe، لوحة تحكم إدارية، وتحليلات مبيعات.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">Next.js</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">Stripe</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">Prisma</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">PostgreSQL</span>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.2s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:chat-processing" class="text-cyber-pink text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-pink transition-colors mb-2" dir="ltr">Real-Time Chat App</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        تطبيق محادثة فورية مع غرف، مكالمات صوتية، مشاركة ملفات، وتشفير end-to-end.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">React</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">Socket.io</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">Node.js</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">MongoDB</span>
                    </div>
                </div>

                <!-- Project 3 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.3s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:brain" class="text-cyber-green text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-green transition-colors mb-2" dir="ltr">AI Content Generator</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        أداة لتوليد المحتوى بالAI مع templates مخصصة، SEO optimization، وتكامل CMS.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">TypeScript</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">OpenAI</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">Express</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">Redis</span>
                    </div>
                </div>

                <!-- Project 4 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.4s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:clipboard-task" class="text-cyber-yellow text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-yellow transition-colors mb-2" dir="ltr">Task Management API</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        REST API متكامل لإدارة المهام مع authentication، roles، وreal-time notifications.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">NestJS</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">JWT</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">PostgreSQL</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">Docker</span>
                    </div>
                </div>

                <!-- Project 5 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.5s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:chart-areaspline" class="text-cyber-cyan text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-cyan transition-colors mb-2" dir="ltr">Analytics Dashboard</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        لوحة تحليلات بيانات تفاعلية مع charts حية، filtering متقدم، وexport PDF.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">React</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">Chart.js</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">GraphQL</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">Supabase</span>
                    </div>
                </div>

                <!-- Project 6 -->
                <div class="project-card rounded-lg p-6 bg-cyber-panel group fade-in-up" style="animation-delay:0.6s">
                    <div class="flex items-center justify-between mb-4">
                        <iconify-icon icon="mdi:book-open-variant" class="text-cyber-pink text-xl"></iconify-icon>
                        <div class="flex items-center gap-2">
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                                <iconify-icon icon="mdi:github" class="text-lg"></iconify-icon>
                            </a>
                            <a href="#" class="text-cyber-text/40 hover:text-cyber-pink transition-colors">
                                <iconify-icon icon="mdi:open-in-new" class="text-lg"></iconify-icon>
                            </a>
                        </div>
                    </div>
                    <h3 class="font-mono text-lg text-cyber-text group-hover:text-cyber-pink transition-colors mb-2" dir="ltr">Dev Blog Platform</h3>
                    <p class="text-sm text-cyber-text/60 font-arabic mb-4">
                        مدونة للمطورين مع MDX support، code highlighting، newsletter، وSEO Optimization.
                    </p>
                    <div class="flex flex-wrap gap-2 font-mono text-xs">
                        <span class="px-2 py-1 rounded bg-cyber-cyan/10 text-cyber-cyan border border-cyber-cyan/20">Next.js</span>
                        <span class="px-2 py-1 rounded bg-cyber-pink/10 text-cyber-pink border border-cyber-pink/20">MDX</span>
                        <span class="px-2 py-1 rounded bg-cyber-green/10 text-cyber-green border border-cyber-green/20">Vercel</span>
                        <span class="px-2 py-1 rounded bg-cyber-yellow/10 text-cyber-yellow border border-cyber-yellow/20">Tailwind</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- GitHub Stats Section -->
    <section id="stats" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-8 fade-in-up">
                <iconify-icon icon="mdi:chart-bar" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">github_stats<span class="text-cyber-pink">()</span></h2>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                <div class="stat-card rounded-lg p-6 text-center fade-in-up" style="animation-delay:0.1s">
                    <iconify-icon icon="mdi:source-commit" class="text-cyber-cyan text-3xl glow-cyan"></iconify-icon>
                    <div class="font-mono text-3xl font-bold text-cyber-text mt-3 counter" data-target="1247">0</div>
                    <div class="font-mono text-xs text-cyber-text/50 mt-1">Total Commits</div>
                </div>
                <div class="stat-card rounded-lg p-6 text-center fade-in-up" style="animation-delay:0.2s">
                    <iconify-icon icon="mdi:star-outline" class="text-cyber-yellow text-3xl glow-green" style="text-shadow:0 0 10px rgba(57,255,20,0.6)"></iconify-icon>
                    <div class="font-mono text-3xl font-bold text-cyber-text mt-3 counter" data-target="89">0</div>
                    <div class="font-mono text-xs text-cyber-text/50 mt-1">Stars Earned</div>
                </div>
                <div class="stat-card rounded-lg p-6 text-center fade-in-up" style="animation-delay:0.3s">
                    <iconify-icon icon="mdi:source-fork" class="text-cyber-pink text-3xl glow-pink"></iconify-icon>
                    <div class="font-mono text-3xl font-bold text-cyber-text mt-3 counter" data-target="34">0</div>
                    <div class="font-mono text-xs text-cyber-text/50 mt-1">Pull Requests</div>
                </div>
                <div class="stat-card rounded-lg p-6 text-center fade-in-up" style="animation-delay:0.4s">
                    <iconify-icon icon="mdi:repository" class="text-cyber-green text-3xl glow-green"></iconify-icon>
                    <div class="font-mono text-3xl font-bold text-cyber-text mt-3 counter" data-target="28">0</div>
                    <div class="font-mono text-xs text-cyber-text/50 mt-1">Repositories</div>
                </div>
            </div>

            <!-- GitHub Stats Cards (simulated) -->
            <div class="grid md:grid-cols-2 gap-6 fade-in-up" style="animation-delay:0.5s" dir="ltr">
                <div class="terminal-window">
                    <div class="terminal-header">
                        <div class="terminal-dot bg-cyber-pink"></div>
                        <div class="terminal-dot bg-cyber-yellow"></div>
                        <div class="terminal-dot bg-cyber-green"></div>
                        <span class="font-mono text-xs text-cyber-text/40 ml-2">github-readme-stats</span>
                    </div>
                    <div class="p-4 flex items-center justify-center">
                        <div class="w-full bg-cyber-dim rounded-lg p-4 border border-cyber-border">
                            <div class="flex items-center justify-between mb-4">
                                <span class="font-mono text-sm text-cyber-cyan">Ahmed's GitHub Stats</span>
                                <span class="font-mono text-xs text-cyber-text/40">A+</span>
                            </div>
                            <div class="space-y-3">
                                <div class="flex items-center justify-between font-mono text-xs">
                                    <span class="text-cyber-text/60">Total Lines</span>
                                    <span class="text-cyber-cyan">145,280</span>
                                </div>
                                <div class="flex items-center justify-between font-mono text-xs">
                                    <span class="text-cyber-text/60">Languages</span>
                                    <span class="text-cyber-pink">12</span>
                                </div>
                                <div class="flex items-center justify-between font-mono text-xs">
                                    <span class="text-cyber-text/60">Contributions</span>
                                    <span class="text-cyber-green">1,247</span>
                                </div>
                                <div class="flex items-center justify-between font-mono text-xs">
                                    <span class="text-cyber-text/60">Streak</span>
                                    <span class="text-cyber-yellow">🔥 42 days</span>
                                </div>
                            </div>
                            <!-- Language bars -->
                            <div class="mt-4 space-y-2">
                                <div class="flex items-center gap-2">
                                    <span class="font-mono text-xs text-cyber-text/50 w-20">JavaScript</span>
                                    <div class="flex-1 h-2 rounded bg-cyber-dim overflow-hidden">
                                        <div class="h-full bg-cyber-yellow rounded" style="width:45%"></div>
                                    </div>
                                    <span class="font-mono text-xs text-cyber-text/40">45%</span>
                                </div>
                                <div class="flex items-center gap-2">
                                    <span class="font-mono text-xs text-cyber-text/50 w-20">TypeScript</span>
                                    <div class="flex-1 h-2 rounded bg-cyber-dim overflow-hidden">
                                        <div class="h-full bg-cyber-cyan rounded" style="width:30%"></div>
                                    </div>
                                    <span class="font-mono text-xs text-cyber-text/40">30%</span>
                                </div>
                                <div class="flex items-center gap-2">
                                    <span class="font-mono text-xs text-cyber-text/50 w-20">Python</span>
                                    <div class="flex-1 h-2 rounded bg-cyber-dim overflow-hidden">
                                        <div class="h-full bg-cyber-green rounded" style="width:15%"></div>
                                    </div>
                                    <span class="font-mono text-xs text-cyber-text/40">15%</span>
                                </div>
                                <div class="flex items-center gap-2">
                                    <span class="font-mono text-xs text-cyber-text/50 w-20">Other</span>
                                    <div class="flex-1 h-2 rounded bg-cyber-dim overflow-hidden">
                                        <div class="h-full bg-cyber-pink rounded" style="width:10%"></div>
                                    </div>
                                    <span class="font-mono text-xs text-cyber-text/40">10%</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Streak card -->
                <div class="terminal-window">
                    <div class="terminal-header">
                        <div class="terminal-dot bg-cyber-pink"></div>
                        <div class="terminal-dot bg-cyber-yellow"></div>
                        <div class="terminal-dot bg-cyber-green"></div>
                        <span class="font-mono text-xs text-cyber-text/40 ml-2">github-readme-streak</span>
                    </div>
                    <div class="p-4 flex items-center justify-center">
                        <div class="w-full bg-cyber-dim rounded-lg p-4 border border-cyber-border text-center">
                            <iconify-icon icon="mdi:fire" class="text-cyber-yellow text-4xl"></iconify-icon>
                            <div class="font-mono text-xl text-cyber-yellow mt-2">42 Day Streak 🔥</div>
                            <div class="font-mono text-xs text-cyber-text/40 mt-1">Current streak ongoing!</div>
                            <div class="mt-4 grid grid-cols-7 gap-1">
                                <!-- Mini contribution grid -->
                                <div class="w-full aspect-square rounded bg-cyber-green/20"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/20"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/60"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/20"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-green/80"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan animate-pulse"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan animate-pulse"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan animate-pulse"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan animate-pulse"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan/40"></div>
                                <div class="w-full aspect-square rounded bg-cyber-cyan/20"></div>
                            </div>
                            <div class="flex items-center justify-between mt-3 font-mono text-xs text-cyber-text/40">
                                <span>Less</span>
                                <div class="flex gap-1">
                                    <div class="w-2 h-2 rounded bg-cyber-green/20"></div>
                                    <div class="w-2 h-2 rounded bg-cyber-green/40"></div>
                                    <div class="w-2 h-2 rounded bg-cyber-green/60"></div>
                                    <div class="w-2 h-2 rounded bg-cyber-green/80"></div>
                                    <div class="w-2 h-2 rounded bg-cyber-green"></div>
                                </div>
                                <span>More</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- Experience Timeline -->
    <section id="experience" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-12 fade-in-up">
                <iconify-icon icon="mdi:briefcase-clock" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">experience<span class="text-cyber-pink">()</span></h2>
            </div>

            <div class="relative" dir="ltr">
                <!-- Timeline line -->
                <div class="absolute left-4 md:left-1/2 top-0 bottom-0 w-px bg-gradient-to-b from-cyber-cyan via-cyber-pink to-cyber-green"></div>

                <!-- Item 1 -->
                <div class="relative flex md:items-center mb-12 fade-in-up" style="animation-delay:0.2s">
                    <div class="absolute left-4 md:left-1/2 w-3 h-3 rounded-full bg-cyber-cyan glow-cyan -translate-x-1/2 border-2 border-cyber-bg"></div>
                    <div class="ml-12 md:ml-0 md:w-1/2 md:pr-12">
                        <div class="p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-cyan/50 transition-colors">
                            <div class="font-mono text-xs text-cyber-cyan mb-1">2023 — Present</div>
                            <div class="font-mono text-sm text-cyber-text">Senior Full-Stack Developer</div>
                            <div class="font-mono text-xs text-cyber-text/50">@ TechCorp Inc.</div>
                        </div>
                    </div>
                </div>

                <!-- Item 2 -->
                <div class="relative flex md:items-center mb-12 fade-in-up" style="animation-delay:0.3s">
                    <div class="absolute left-4 md:left-1/2 w-3 h-3 rounded-full bg-cyber-pink glow-pink -translate-x-1/2 border-2 border-cyber-bg"></div>
                    <div class="ml-12 md:ml-auto md:w-1/2 md:pl-12">
                        <div class="p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-pink/50 transition-colors">
                            <div class="font-mono text-xs text-cyber-pink mb-1">2021 — 2023</div>
                            <div class="font-mono text-sm text-cyber-text">Full-Stack Developer</div>
                            <div class="font-mono text-xs text-cyber-text/50">@ StartupHub</div>
                        </div>
                    </div>
                </div>

                <!-- Item 3 -->
                <div class="relative flex md:items-center mb-12 fade-in-up" style="animation-delay:0.4s">
                    <div class="absolute left-4 md:left-1/2 w-3 h-3 rounded-full bg-cyber-green glow-green -translate-x-1/2 border-2 border-cyber-bg"></div>
                    <div class="ml-12 md:ml-0 md:w-1/2 md:pr-12">
                        <div class="p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-green/50 transition-colors">
                            <div class="font-mono text-xs text-cyber-green mb-1">2020 — 2021</div>
                            <div class="font-mono text-sm text-cyber-text">Frontend Developer</div>
                            <div class="font-mono text-xs text-cyber-text/50">@ WebAgency</div>
                        </div>
                    </div>
                </div>

                <!-- Item 4 -->
                <div class="relative flex md:items-center fade-in-up" style="animation-delay:0.5s">
                    <div class="absolute left-4 md:left-1/2 w-3 h-3 rounded-full bg-cyber-yellow -translate-x-1/2 border-2 border-cyber-bg" style="text-shadow:0 0 10px rgba(255,230,0,0.6)"></div>
                    <div class="ml-12 md:ml-auto md:w-1/2 md:pl-12">
                        <div class="p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-yellow/50 transition-colors">
                            <div class="font-mono text-xs text-cyber-yellow mb-1">2019 — 2020</div>
                            <div class="font-mono text-sm text-cyber-text">Freelance Developer</div>
                            <div class="font-mono text-xs text-cyber-text/50">@ Self-employed</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-6xl mx-auto"></div>

    <!-- Contact Section -->
    <section id="contact" class="py-24 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="flex items-center gap-3 mb-8 fade-in-up">
                <iconify-icon icon="mdi:email-fast-outline" class="text-cyber-cyan text-2xl glow-cyan"></iconify-icon>
                <h2 class="text-2xl md:text-3xl font-bold font-mono text-cyber-cyan glow-cyan" dir="ltr">connect_with_me<span class="text-cyber-pink">()</span></h2>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <!-- Social links -->
                <div class="fade-in-up space-y-4" style="animation-delay:0.2s">
                    <p class="text-cyber-text/70 font-arabic mb-6">
                        دايماً سعيد بالتواصل! سويد عندك مشروع، فرصة عمل، أو بس عايز تتبادل الأفكار 🤝
                    </p>

                    <div class="space-y-3">
                        <a href="#" class="flex items-center gap-4 p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-cyan/50 transition-all group">
                            <iconify-icon icon="mdi:github" class="text-2xl text-cyber-text/60 group-hover:text-cyber-cyan transition-colors"></iconify-icon>
                            <div>
                                <div class="font-mono text-sm text-cyber-text group-hover:text-cyber-cyan transition-colors">GitHub</div>
                                <div class="font-mono text-xs text-cyber-text/40">@ahmed-dev</div>
                            </div>
                            <iconify-icon icon="mdi:arrow-right" class="text-cyber-text/30 group-hover:text-cyber-cyan transition-colors ml-auto"></iconify-icon>
                        </a>

                        <a href="#" class="flex items-center gap-4 p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-pink/50 transition-all group">
                            <iconify-icon icon="mdi:linkedin" class="text-2xl text-cyber-text/60 group-hover:text-cyber-pink transition-colors"></iconify-icon>
                            <div>
                                <div class="font-mono text-sm text-cyber-text group-hover:text-cyber-pink transition-colors">LinkedIn</div>
                                <div class="font-mono text-xs text-cyber-text/40">@ahmed-hassan-dev</div>
                            </div>
                            <iconify-icon icon="mdi:arrow-right" class="text-cyber-text/30 group-hover:text-cyber-pink transition-colors ml-auto"></iconify-icon>
                        </a>

                        <a href="#" class="flex items-center gap-4 p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-green/50 transition-all group">
                            <iconify-icon icon="mdi:twitter" class="text-2xl text-cyber-text/60 group-hover:text-cyber-green transition-colors"></iconify-icon>
                            <div>
                                <div class="font-mono text-sm text-cyber-text group-hover:text-cyber-green transition-colors">Twitter/X</div>
                                <div class="font-mono text-xs text-cyber-text/40">@ahmed_codes</div>
                            </div>
                            <iconify-icon icon="mdi:arrow-right" class="text-cyber-text/30 group-hover:text-cyber-green transition-colors ml-auto"></iconify-icon>
                        </a>

                        <a href="#" class="flex items-center gap-4 p-4 rounded-lg bg-cyber-panel border border-cyber-border hover:border-cyber-yellow/50 transition-all group">
                            <iconify-icon icon="mdi:email-outline" class="text-2xl text-cyber-text/60 group-hover:text-cyber-yellow transition-colors"></iconify-icon>
                            <div>
                                <div class="font-mono text-sm text-cyber-text group-hover:text-cyber-yellow transition-colors">Email</div>
                                <div class="font-mono text-xs text-cyber-text/40">ahmed@devmail.com</div>
                            </div>
                            <iconify-icon icon="mdi:arrow-right" class="text-cyber-text/30 group-hover:text-cyber-yellow transition-colors ml-auto"></iconify-icon>
                        </a>
                    </div>
                </div>

                <!-- Contact form -->
                <div class="terminal-window fade-in-up" style="animation-delay:0.4s" dir="ltr">
                    <div class="terminal-header">
                        <div class="terminal-dot bg-cyber-pink"></div>
                        <div class="terminal-dot bg-cyber-yellow"></div>
                        <div class="terminal-dot bg-cyber-green"></div>
                        <span class="font-mono text-xs text-cyber-text/40 ml-2">send_message.sh</span>
                    </div>
                    <div class="p-5">
                        <form id="contact-form" class="space-y-4 font-mono">
                            <div>
                                <label class="text-xs text-cyber-text/40 mb-1 block">name:</label>
                                <input type="text" placeholder="Your Name" class="w-full bg-cyber-dim border border-cyber-border rounded px-3 py-2 text-sm text-cyber-text focus:border-cyber-cyan transition-colors outline-none" required />
                            </div>
                            <div>
                                <label class="text-xs text-cyber-text/40 mb-1 block">email:</label>
                                <input type="email" placeholder="your@email.com" class="w-full bg-cyber-dim border border-cyber-border rounded px-3 py-2 text-sm text-cyber-text focus:border-cyber-cyan transition-colors outline-none" required />
                            </div>
                            <div>
                                <label class="text-xs text-cyber-text/40 mb-1 block">message:</label>
                                <textarea rows="4" placeholder="Tell me about your project..." class="w-full bg-cyber-dim border border-cyber-border rounded px-3 py-2 text-sm text-cyber-text focus:border-cyber-cyan transition-colors outline-none resize-none" required></textarea>
                            </div>
                            <button type="submit" class="w-full py-2 rounded bg-gradient-to-r from-cyber-cyan to-cyber-pink text-white font-mono text-sm hover:opacity-90 transition-opacity flex items-center justify-center gap-2">
                                <iconify-icon icon="mdi:send" class="text-sm"></iconify-icon>
                                echo $message → /dev/inbox
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-cyber-border py-8 px-6">
        <div class="max-w-6xl mx-auto flex flex-col md:flex-row items-center justify-between gap-4" dir="ltr">
            <div class="font-mono text-xs text-cyber-text/40">
                <span class="text-cyber-cyan">echo</span> "Built with ❤️ and ☕" | <span class="text-cyber-pink">cat</span> >> README.md
            </div>
            <div class="font-mono text-xs text-cyber-text/30">
                © 2024 Ahmed.dev — All rights reserved
            </div>
            <div class="flex items-center gap-3">
                <iconify-icon icon="mdi:github" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors cursor-pointer text-lg"></iconify-icon>
                <iconify-icon icon="mdi:linkedin" class="text-cyber-text/40 hover:text-cyber-pink transition-colors cursor-pointer text-lg"></iconify-icon>
                <iconify-icon icon="mdi:twitter" class="text-cyber-text/40 hover:text-cyber-green transition-colors cursor-pointer text-lg"></iconify-icon>
            </div>
        </div>
    </footer>

    <!-- Markdown Modal -->
    <div id="md-modal" class="fixed inset-0 z-[100] hidden items-center justify-center bg-black/80 backdrop-blur-sm p-4">
        <div class="max-w-4xl w-full max-h-[80vh] overflow-y-auto rounded-lg border border-cyber-border bg-cyber-panel">
            <div class="flex items-center justify-between p-4 border-b border-cyber-border">
                <span class="font-mono text-sm text-cyber-cyan glow-cyan">README.md</span>
                <button id="close-md-modal" class="text-cyber-text/40 hover:text-cyber-cyan transition-colors">
                    <iconify-icon icon="mdi:close" class="text-xl"></iconify-icon>
                </button>
            </div>
            <div class="p-4">
                <div class="md-code p-4 text-cyber-text/80 leading-relaxed" id="md-content" dir="ltr"></div>
                <button id="copy-md-content" class="mt-4 px-6 py-2 rounded bg-cyber-cyan/20 border border-cyber-cyan/50 text-cyber-cyan font-mono text-xs hover:bg-cyber-cyan/30 transition-colors flex items-center gap-2">
                    <iconify-icon icon="mdi:content-copy"></iconify-icon>
                    Copy to Clipboard
                </button>
            </div>
        </div>
    </div>

    <script>
        // ===== Typing Animation =====
        const typingText = "Ahmed Hassan — Full-Stack Web Developer | Building the future, one commit at a time 💻";
        const typingEl = document.getElementById('typing-line');
        let charIndex = 0;

        function typeChar() {
            if (charIndex < typingText.length) {
                typingEl.textContent = typingText.substring(0, charIndex + 1);
                charIndex++;
                setTimeout(typeChar, 40);
            }
        }
        setTimeout(typeChar, 800);

        // ===== Fade-in Observer =====
        const fadeEls = document.querySelectorAll('.fade-in-up');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animationPlayState = 'running';
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.1 });
        fadeEls.forEach(el => {
            el.style.animationPlayState = 'paused';
            observer.observe(el);
        });

        // ===== Counter Animation =====
        const counters = document.querySelectorAll('.counter');
        const counterObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const el = entry.target;
                    const target = parseInt(el.dataset.target);
                    let current = 0;
                    const increment = target / 60;
                    const timer = setInterval(() => {
                        current += increment;
                        if (current >= target) {
                            el.textContent = target;
                            clearInterval(timer);
                        } else {
                            el.textContent = Math.floor(current);
                        }
                    }, 25);
                    counterObserver.unobserve(el);
                }
            });
        }, { threshold: 0.5 });
        counters.forEach(c => counterObserver.observe(c));

        // ===== Skill Tabs =====
        const tabBtns = document.querySelectorAll('.tab-btn');
        const tabContents = document.querySelectorAll('.tab-content');

        tabBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                tabBtns.forEach(b => {
                    b.classList.remove('active', 'text-cyber-cyan');
                    b.classList.add('text-cyber-text/50');
                });
                btn.classList.add('active', 'text-cyber-cyan');
                btn.classList.remove('text-cyber-text/50');

                const tabId = btn.dataset.tab;
                tabContents.forEach(tc => tc.classList.add('hidden'));
                document.getElementById('tab-' + tabId).classList.remove('hidden');
            });
        });

        // ===== Toast =====
        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-msg').textContent = msg;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 2500);
        }

        // ===== Contact Form =====
        document.getElementById('contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            showToast('Message sent successfully! ✨');
            e.target.reset();
        });

        // ===== Markdown Content =====
        const markdownContent = `
<div align="center">

# 👋 Hi, I'm Ahmed Hassan

### Full-Stack Web Developer | Egypt 🇪🇬

<p>
  <img src="https://komarev.com/ghpvc/?username=ahmed-dev&color=00f0ff&style=flat-square&label=Profile+Visitors" alt="visitors" />
</p>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=22&duration=3000&pause=1000&color=00F0FF&center=true&vCenter=true&width=600&lines=Building+the+future%2C+one+commit+at+a+time+%F0%9F%92%BB;Full-Stack+Developer+%7C+React+%2B+Node.js;Always+learning%2C+always+coding+%F0%9F%94%A5" alt="Typing SVG" />

</div>

---

## 🧑‍💻 About Me

\`\`\`json
{
  "name": "Ahmed Hassan",
  "role": "Full-Stack Web Developer",
  "location": "Cairo, Egypt",
  "languages": ["Arabic", "English"],
  "interests": ["Open Source", "UI/UX", "AI", "Clean Code"],
  "currentFocus": "Scalable Web Applications",
  "funFact": "I debug with console.log 😅"
}
\`\`\`

- 🔭 Currently working on **E-Commerce Platform**
- 🌱 Learning **System Design** & **Advanced TypeScript**
- 👯 Looking to collaborate on **Open Source Projects**
- 💬 Ask me about **React, Node.js, PostgreSQL**
- ⚡ Fun fact: _I've consumed ∞ cups of coffee while coding_

---

## 🛠️ Tech Stack

### Frontend
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D)

### Backend
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white)

### Database & DevOps
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=ahmed-dev&show_icons=true&theme=midnight-purple&hide_border=true&bg_color=050510&title_color=00f0ff&icon_color=ff2d95&text_color=e0e0e0" alt="GitHub Stats" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com?user=ahmed-dev&theme=midnight-purple&hide_border=true&background=050510&stroke=1e1e3a&ring=00f0ff&fire=ff2d95&currStreakLabel=00f0ff" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ahmed-dev&theme=midnight-purple&hide_border=true&bg_color=050510&title_color=00f0ff&text_color=e0e0e0&layout=compact" alt="Top Languages" />
</p>

---

## 🏆 Featured Projects

| Project | Description | Tech |
|---------|-------------|------|
| **[E-Commerce Platform](https://github.com/ahmed-dev/ecommerce)** | Full e-commerce with Stripe payments & admin dashboard | Next.js, Stripe, Prisma, PostgreSQL |
| **[Real-Time Chat](https://github.com/ahmed-dev/chat-app)** | Instant messaging with rooms, voice calls, E2E encryption | React, Socket.io, Node.js, MongoDB |
| **[AI Content Gen](https://github.com/ahmed-dev/ai-content)** | AI-powered content generator with SEO optimization | TypeScript, OpenAI, Express, Redis |
| **[Task API](https://github.com/ahmed-dev/task-api)** | REST API for task management with auth & notifications | NestJS, JWT, PostgreSQL, Docker |
| **[Analytics Dashboard](https://github.com/ahmed-dev/analytics)** | Interactive data dashboard with live charts & PDF export | React, Chart.js, GraphQL, Supabase |

---

## 🤝 Connect With Me

<p align="center">
  <a href="https://github.com/ahmed-dev"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /></a>
  <a href="https://linkedin.com/in/ahmed-hassan-dev"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="https://twitter.com/ahmed_codes"><img src="https://img.shields.io/badge/X-000000?style=for-the-badge&logo=x&logoColor=white" /></a>
  <a href="mailto:ahmed@devmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>

---

<div align="center">

<img src="https://capsule-render.vercel.app?type=waving&color=gradient&customColorList=0,2,2,5,30&height=80&section=footer" width="100%" />

⭐️ From [ahmed-dev](https://github.com/ahmed-dev) — Built with ❤️ and ☕

</div>
`;

        document.getElementById('md-content').textContent = markdownContent;

        // ===== Modal Controls =====
        const mdModal = document.getElementById('md-modal');

        document.getElementById('copy-md-btn').addEventListener('click', () => {
            mdModal.classList.remove('hidden');
            mdModal.classList.add('flex');
        });

        document.getElementById('close-md-modal').addEventListener('click', () => {
            mdModal.classList.add('hidden');
            mdModal.classList.remove('flex');
        });

        mdModal.addEventListener('click', (e) => {
            if (e.target === mdModal) {
                mdModal.classList.add('hidden');
                mdModal.classList.remove('flex');
            }
        });

        document.getElementById('copy-md-content').addEventListener('click', () => {
            navigator.clipboard.writeText(markdownContent).then(() => {
                showToast('README.md copied to clipboard! 📋');
                mdModal.classList.add('hidden');
                mdModal.classList.remove('flex');
            });
        });

        // ===== Smooth Nav Scroll =====
        document.querySelectorAll('nav a[href^="#"]').forEach(a => {
            a.addEventListener('click', (e) => {
                e.preventDefault();
                document.querySelector(a.getAttribute('href')).scrollIntoView({ behavior: 'smooth' });
            });
        });

        // ===== Keyboard shortcut to open MD =====
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && mdModal.classList.contains('flex')) {
                mdModal.classList.add('hidden');
                mdModal.classList.remove('flex');
            }
        });
    </script>
</body>
</html>
