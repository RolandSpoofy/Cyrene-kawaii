<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevBio | Code Your Story</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --dark: #1e293b;
            --light: #f8fafc;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--light);
            color: var(--dark);
            overflow-x: hidden;
            scroll-behavior: smooth;
        }
        
        .gradient-text {
            background: linear-gradient(90deg, #6366f1, #8b5cf6, #ec4899);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .card {
            transition: all 0.3s ease;
            transform: translateY(0);
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        .nav-link {
            position: relative;
        }
        
        .nav-link::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -2px;
            left: 0;
            background-color: var(--primary);
            transition: width 0.3s ease;
        }
        
        .nav-link:hover::after {
            width: 100%;
        }
        
        .hero-section {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
        }
        
        .tech-icon {
            transition: all 0.3s ease;
        }
        
        .tech-icon:hover {
            transform: scale(1.2);
        }
        
        .project-card {
            perspective: 1000px;
        }
        
        .project-inner {
            transition: transform 0.6s;
            transform-style: preserve-3d;
        }
        
        .project-card:hover .project-inner {
            transform: rotateY(180deg);
        }
        
        .project-front, .project-back {
            backface-visibility: hidden;
            position: absolute;
            width: 100%;
            height: 100%;
        }
        
        .project-back {
            transform: rotateY(180deg);
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        .typewriter {
            overflow: hidden;
            border-right: 3px solid var(--primary);
            white-space: nowrap;
            margin: 0 auto;
            letter-spacing: 2px;
            animation: 
                typing 3.5s steps(40, end),
                blink-caret .75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--primary); }
        }
        
        .scroll-down {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            color: var(--primary);
            animation: bounce 2s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-20px);}
            60% {transform: translateY(-10px);}
        }
    </style>
</head>
<body class="antialiased">
    <!-- Navigation -->
    <nav class="fixed w-full bg-white/80 backdrop-blur-md z-50 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center">
                    <div class="flex-shrink-0 flex items-center">
                        <span class="text-2xl font-bold gradient-text">DevBio</span>
                    </div>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-center space-x-8">
                        <a href="#home" class="nav-link text-gray-700 hover:text-indigo-600 px-3 py-2 text-sm font-medium">Home</a>
                        <a href="#about" class="nav-link text-gray-700 hover:text-indigo-600 px-3 py-2 text-sm font-medium">About</a>
                        <a href="#skills" class="nav-link text-gray-700 hover:text-indigo-600 px-3 py-2 text-sm font-medium">Skills</a>
                        <a href="#projects" class="nav-link text-gray-700 hover:text-indigo-600 px-3 py-2 text-sm font-medium">Projects</a>
                        <a href="#contact" class="nav-link text-gray-700 hover:text-indigo-600 px-3 py-2 text-sm font-medium">Contact</a>
                    </div>
                </div>
                <div class="md:hidden">
                    <button id="mobile-menu-button" class="text-gray-700 hover:text-indigo-600 focus:outline-none">
                        <i class="fas fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Mobile menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white shadow-lg rounded-lg mx-4 mb-4">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3 flex flex-col">
                <a href="#home" class="nav-link text-gray-700 hover:text-indigo-600 block px-3 py-2 text-base font-medium">Home</a>
                <a href="#about" class="nav-link text-gray-700 hover:text-indigo-600 block px-3 py-2 text-base font-medium">About</a>
                <a href="#skills" class="nav-link text-gray-700 hover:text-indigo-600 block px-3 py-2 text-base font-medium">Skills</a>
                <a href="#projects" class="nav-link text-gray-700 hover:text-indigo-600 block px-3 py-2 text-base font-medium">Projects</a>
                <a href="#contact" class="nav-link text-gray-700 hover:text-indigo-600 block px-3 py-2 text-base font-medium">Contact</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero-section min-h-screen flex items-center justify-center relative overflow-hidden pt-16">
        <div class="absolute inset-0 overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-r from-indigo-100/20 to-purple-100/20"></div>
            <div class="absolute top-0 left-0 w-full h-full opacity-10">
                <div class="absolute top-1/4 left-1/4 w-32 h-32 rounded-full bg-indigo-400 blur-3xl"></div>
                <div class="absolute top-1/2 right-1/4 w-40 h-40 rounded-full bg-purple-400 blur-3xl"></div>
                <div class="absolute bottom-1/4 left-1/2 w-28 h-28 rounded-full bg-pink-400 blur-3xl"></div>
            </div>
        </div>
        
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 md:py-24 z-10">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
                <div class="space-y-6">
                    <h1 class="text-4xl md:text-6xl font-bold leading-tight">
                        Hi, I'm <span class="gradient-text">Miu</span>
                    </h1>
                    <div class="typewriter text-xl md:text-2xl text-gray-600">
                        Full Stack Developer & UI/UX Enthusiast
                    </div>
                    <p class="text-lg text-gray-600">
                        I build digital experiences that are fast, accessible, and visually appealing. 
                        Passionate about clean code and pixel-perfect designs.
                    </p>
                    <div class="flex space-x-4">
                        <a href="#contact" class="px-6 py-3 bg-indigo-600 text-white rounded-lg font-medium hover:bg-indigo-700 transition duration-300 shadow-lg hover:shadow-indigo-300/50">
                            Get In Touch
                        </a>
                        <a href="#projects" class="px-6 py-3 border border-indigo-600 text-indigo-600 rounded-lg font-medium hover:bg-indigo-50 transition duration-300">
                            View Work
                        </a>
                    </div>
                </div>
                <div class="relative flex justify-center">
                    <div class="relative w-64 h-64 md:w-80 md:h-80 rounded-full overflow-hidden border-4 border-white shadow-2xl">
                        <img src="https://plus.unsplash.com/premium_photo-1720287601920-ee8c503af775?q=80&w=870&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
                             alt="Developer" class="w-full h-full object-cover">
                    </div>
                    <div class="absolute -bottom-6 -left-6 w-32 h-32 bg-indigo-100 rounded-full -z-10 floating"></div>
                    <div class="absolute -top-6 -right-6 w-24 h-24 bg-purple-100 rounded-full -z-10 floating" style="animation-delay: 0.5s;"></div>
                </div>
            </div>
        </div>
        
        <a href="#about" class="scroll-down">
            <i class="fas fa-chevron-down text-2xl"></i>
        </a>
    </section>

    <!-- About Section -->
    <section id="about" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    <span class="gradient-text">About</span> Me
                </h2>
                <div class="w-20 h-1 bg-gradient-to-r from-indigo-500 to-purple-500 mx-auto"></div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
                <div class="space-y-6">
                    <h3 class="text-2xl font-semibold text-gray-800">Who am I?</h3>
                    <p class="text-gray-600 leading-relaxed">
                        I'm a passionate full-stack developer with over 5 years of experience building web applications. 
                        My journey in tech started when I built my first website at 15, and I've been hooked ever since.
                    </p>
                    <p class="text-gray-600 leading-relaxed">
                        I specialize in JavaScript ecosystems, with expertise in React, Node.js, and modern CSS frameworks. 
                        I believe in writing clean, maintainable code and creating intuitive user experiences.
                    </p>
                    <p class="text-gray-600 leading-relaxed">
                        When I'm not coding, you can find me contributing to open-source projects, 
                        reading about new technologies, or hiking in the mountains.
                    </p>
                    
                    <div class="flex flex-wrap gap-4 pt-4">
                        <div class="flex items-center space-x-2 bg-gray-100 px-4 py-2 rounded-full">
                            <i class="fas fa-map-marker-alt text-indigo-600"></i>
                            <span>NUS University, SG</span>
                        </div>
                        <div class="flex items-center space-x-2 bg-gray-100 px-4 py-2 rounded-full">
                            <i class="fas fa-graduation-cap text-indigo-600"></i>
                            <span>Computer Science</span>
                        </div>
                        <div class="flex items-center space-x-2 bg-gray-100 px-4 py-2 rounded-full">
                            <i class="fas fa-briefcase text-indigo-600"></i>
                            <span>200+ Years Exp</span>
                        </div>
                    </div>
                </div>
                
                <div class="grid grid-cols-2 gap-4">
                    <div class="card bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="text-indigo-600 text-3xl mb-3">
                            <i class="fas fa-code"></i>
                        </div>
                        <h4 class="font-semibold text-lg mb-2">Clean Code</h4>
                        <p class="text-gray-600 text-sm">
                            I follow best practices to write maintainable and scalable code.
                        </p>
                    </div>
                    <div class="card bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="text-indigo-600 text-3xl mb-3">
                            <i class="fas fa-paint-brush"></i>
                        </div>
                        <h4 class="font-semibold text-lg mb-2">UI/UX Design</h4>
                        <p class="text-gray-600 text-sm">
                            Creating intuitive interfaces with exceptional user experience.
                        </p>
                    </div>
                    <div class="card bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="text-indigo-600 text-3xl mb-3">
                            <i class="fas fa-rocket"></i>
                        </div>
                        <h4 class="font-semibold text-lg mb-2">Fast Performance</h4>
                        <p class="text-gray-600 text-sm">
                            Optimized applications for blazing fast load times.
                        </p>
                    </div>
                    <div class="card bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="text-indigo-600 text-3xl mb-3">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <h4 class="font-semibold text-lg mb-2">Responsive</h4>
                        <p class="text-gray-600 text-sm">
                            Fully responsive designs that work on any device.
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    My <span class="gradient-text">Skills</span>
                </h2>
                <div class="w-20 h-1 bg-gradient-to-r from-indigo-500 to-purple-500 mx-auto"></div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                <div>
                    <h3 class="text-2xl font-semibold text-gray-800 mb-6">Technologies I Work With</h3>
                    <div class="grid grid-cols-3 sm:grid-cols-4 gap-6">
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-html5 text-4xl text-orange-500 mb-2"></i>
                            <span class="text-sm">HTML5</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-css3-alt text-4xl text-blue-500 mb-2"></i>
                            <span class="text-sm">CSS3</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-js text-4xl text-yellow-500 mb-2"></i>
                            <span class="text-sm">JavaScript</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-react text-4xl text-blue-400 mb-2"></i>
                            <span class="text-sm">React</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-node-js text-4xl text-green-500 mb-2"></i>
                            <span class="text-sm">Node.js</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-python text-4xl text-blue-600 mb-2"></i>
                            <span class="text-sm">Python</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fas fa-database text-4xl text-blue-700 mb-2"></i>
                            <span class="text-sm">MongoDB</span>
                        </div>
                        <div class="tech-icon flex flex-col items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md">
                            <i class="fab fa-git-alt text-4xl text-orange-600 mb-2"></i>
                            <span class="text-sm">Git</span>
                        </div>
                    </div>
                </div>
                
                <div>
                    <h3 class="text-2xl font-semibold text-gray-800 mb-6">My Expertise</h3>
                    <div class="space-y-6">
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-sm font-medium text-gray-700">Frontend Development</span>
                                <span class="text-sm font-medium text-gray-500">95%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 95%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-sm font-medium text-gray-700">Backend Development</span>
                                <span class="text-sm font-medium text-gray-500">85%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 85%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-sm font-medium text-gray-700">UI/UX Design</span>
                                <span class="text-sm font-medium text-gray-500">90%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 90%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-sm font-medium text-gray-700">DevOps</span>
                                <span class="text-sm font-medium text-gray-500">75%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 75%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-sm font-medium text-gray-700">Problem Solving</span>
                                <span class="text-sm font-medium text-gray-500">92%</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-500 h-2.5 rounded-full" style="width: 92%"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    My <span class="gradient-text">Projects</span>
                </h2>
                <div class="w-20 h-1 bg-gradient-to-r from-indigo-500 to-purple-500 mx-auto"></div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Project 1 -->
                <div class="project-card h-80 rounded-xl overflow-hidden relative">
                    <div class="project-inner w-full h-full">
                        <div class="project-front bg-gradient-to-br from-indigo-100 to-purple-100 p-6 flex flex-col justify-between">
                            <div>
                                <div class="w-12 h-12 bg-white rounded-lg flex items-center justify-center shadow-sm mb-4">
                                    <i class="fas fa-code text-indigo-600 text-xl"></i>
                                </div>
                                <h3 class="text-xl font-bold text-gray-800 mb-2">CodeCollab</h3>
                                <p class="text-gray-600">Real-time collaborative code editor with video chat</p>
                            </div>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-2 py-1 bg-indigo-100 text-indigo-800 text-xs rounded-full">React</span>
                                <span class="px-2 py-1 bg-indigo-100 text-indigo-800 text-xs rounded-full">Node.js</span>
                                <span class="px-2 py-1 bg-indigo-100 text-indigo-800 text-xs rounded-full">WebRTC</span>
                            </div>
                        </div>
                        <div class="project-back bg-gradient-to-br from-indigo-600 to-purple-600 p-6 text-white flex flex-col justify-center items-center">
                            <h3 class="text-xl font-bold mb-4">CodeCollab</h3>
                            <p class="text-center mb-6">A platform for developers to collaborate on code in real-time with integrated video chat functionality.</p>
                            <a href="#" class="px-4 py-2 bg-white text-indigo-600 rounded-lg font-medium hover:bg-gray-100 transition duration-300 text-sm">
                                View Project
                            </a>
                        </div>
                    </div>
                </div>
                
                <!-- Project 2 -->
                <div class="project-card h-80 rounded-xl overflow-hidden relative">
                    <div class="project-inner w-full h-full">
                        <div class="project-front bg-gradient-to-br from-blue-100 to-cyan-100 p-6 flex flex-col justify-between">
                            <div>
                                <div class="w-12 h-12 bg-white rounded-lg flex items-center justify-center shadow-sm mb-4">
                                    <i class="fas fa-shopping-cart text-blue-600 text-xl"></i>
                                </div>
                                <h3 class="text-xl font-bold text-gray-800 mb-2">EcoMarket</h3>
                                <p class="text-gray-600">Sustainable e-commerce platform with carbon footprint calculator</p>
                            </div>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full">Next.js</span>
                                <span class="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full">MongoDB</span>
                                <span class="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full">Stripe</span>
                            </div>
                        </div>
                        <div class="project-back bg-gradient-to-br from-blue-600 to-cyan-600 p-6 text-white flex flex-col justify-center items-center">
                            <h3 class="text-xl font-bold mb-4">EcoMarket</h3>
                            <p class="text-center mb-6">An e-commerce platform focused on sustainable products with a built-in carbon footprint calculator for purchases.</p>
                            <a href="#" class="px-4 py-2 bg-white text-blue-600 rounded-lg font-medium hover:bg-gray-100 transition duration-300 text-sm">
                                View Project
                            </a>
                        </div>
                    </div>
                </div>
                
                <!-- Project 3 -->
                <div class="project-card h-80 rounded-xl overflow-hidden relative">
                    <div class="project-inner w-full h-full">
                        <div class="project-front bg-gradient-to-br from-green-100 to-emerald-
</html>
