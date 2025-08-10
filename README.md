<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Global Styles */
        :root {
            --primary: #2563eb;
            --secondary: #1e40af;
            --dark: #1e293b;
            --light: #f8fafc;
            --accent: #f59e0b;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            background-color: var(--light);
            color: var(--dark);
            overflow-x: hidden;
        }
        
        section {
            min-height: 100vh;
            padding: 6rem 2rem;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .section-title {
            font-size: 2.5rem;
            margin-bottom: 3rem;
            text-align: center;
            position: relative;
            color: var(--primary);
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--accent);
            border-radius: 2px;
        }
        
        .btn {
            display: inline-block;
            padding: 0.8rem 2rem;
            background: var(--primary);
            color: white;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }
        
        .btn:hover {
            background: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        /* Navigation */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            transition: all 0.3s ease;
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 2rem;
            background-color: rgba(255, 255, 255, 0.9);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary);
        }
        
        .logo span {
            color: var(--accent);
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 2rem;
        }
        
        .nav-links a {
            color: var(--dark);
            text-decoration: none;
            font-weight: 500;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background-color: var(--primary);
            transition: width 0.3s ease;
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        .hamburger {
            display: none;
            cursor: pointer;
        }
        
        /* Hero Section */
        #hero {
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: linear-gradient(135deg, rgba(37, 99, 235, 0.1) 0%, rgba(245, 158, 11, 0.1) 100%);
            position: relative;
            overflow: hidden;
        }
        
        .hero-content {
            max-width: 800px;
            z-index: 1;
        }
        
        .hero-content h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            line-height: 1.2;
        }
        
        .hero-content h1 span {
            color: var(--primary);
        }
        
        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            color: #64748b;
        }
        
        .hero-btns {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }
        
        .hero-btns .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }
        
        .hero-btns .btn-outline:hover {
            background: var(--primary);
            color: white;
        }
        
        .hero-image {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            margin: 2rem auto;
            overflow: hidden;
            border: 5px solid var(--primary);
            box-shadow: 0 20px 30px rgba(0, 0, 0, 0.1);
            animation: float 3s ease-in-out infinite;
        }
        
        .hero-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-20px);
            }
        }
        
        /* About Section */
        #about {
            background-color: white;
        }
        
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }
        
        .about-image {
            position: relative;
        }
        
        .about-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: 0 20px 30px rgba(0, 0, 0, 0.1);
        }
        
        .about-image::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border: 5px solid var(--accent);
            border-radius: 10px;
            top: 20px;
            left: 20px;
            z-index: -1;
        }
        
        .about-text h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: var(--primary);
        }
        
        .about-text p {
            margin-bottom: 1.5rem;
            line-height: 1.6;
            color: #64748b;
        }
        
        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 2rem;
        }
        
        .skill {
            background: rgba(37, 99, 235, 0.1);
            padding: 0.5rem 1rem;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 500;
            color: var(--primary);
        }
        
        /* Projects Section */
        #projects {
            background: linear-gradient(135deg, rgba(37, 99, 235, 0.05) 0%, rgba(245, 158, 11, 0.05) 100%);
        }
        
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .project-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }
        
        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }
        
        .project-image {
            height: 200px;
            overflow: hidden;
        }
        
        .project-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .project-card:hover .project-image img {
            transform: scale(1.1);
        }
        
        .project-info {
            padding: 1.5rem;
        }
        
        .project-info h3 {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }
        
        .project-info p {
            color: #64748b;
            margin-bottom: 1rem;
            font-size: 0.9rem;
        }
        
        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }
        
        .project-tag {
            background: rgba(37, 99, 235, 0.1);
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            font-size: 0.7rem;
            font-weight: 500;
            color: var(--primary);
        }
        
        .project-links {
            display: flex;
            gap: 1rem;
        }
        
        .project-links a {
            color: var(--dark);
            transition: all 0.3s ease;
        }
        
        .project-links a:hover {
            color: var(--primary);
            transform: translateY(-3px);
        }
        
        /* Contact Section */
        #contact {
            background-color: white;
        }
        
        .contact-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 3rem;
        }
        
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .contact-icon {
            width: 50px;
            height: 50px;
            background: rgba(37, 99, 235, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            font-size: 1.2rem;
        }
        
        .contact-text h3 {
            font-size: 1.2rem;
            margin-bottom: 0.3rem;
        }
        
        .contact-text p, .contact-text a {
            color: #64748b;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .contact-text a:hover {
            color: var(--primary);
        }
        
        .contact-form {
            background: #f8fafc;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #e2e8f0;
            border-radius: 5px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .form-group input:focus,
        .form-group textarea:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }
        
        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }
        
        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }
        
        .social-links a {
            color: white;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }
        
        .social-links a:hover {
            color: var(--accent);
            transform: translateY(-5px);
        }
        
        .copyright {
            color: #94a3b8;
            font-size: 0.9rem;
        }
        
        /* Animations */
        .fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.6s ease;
        }
        
        .fade-in.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        /* Responsive Styles */
        @media (max-width: 992px) {
            .about-content {
                grid-template-columns: 1fr;
            }
            
            .about-image {
                max-width: 500px;
                margin: 0 auto;
            }
        }
        
        @media (max-width: 768px) {
            section {
                padding: 4rem 1.5rem;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .hero-content h1 {
                font-size: 2.5rem;
            }
            
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background: white;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                transition: all 0.5s ease;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }
            
            .nav-links.active {
                right: 0;
            }
            
            .nav-links li {
                margin: 1.5rem 0;
            }
            
            .hamburger {
                display: block;
                z-index: 1000;
            }
            
            .hamburger i {
                font-size: 1.8rem;
                color: var(--primary);
            }
            
            .hero-btns {
                flex-direction: column;
            }
        }
        
        @media (max-width: 576px) {
            .hero-content h1 {
                font-size: 2rem;
            }
            
            .hero-image {
                width: 200px;
                height: 200px;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <header>
        <nav>
            <div class="logo">CELL<span>REPAIR</span></div>
            <ul class="nav-links">
                <li><a href="#hero">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="hamburger">
                <i class="fas fa-bars"></i>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="hero">
        <div class="container">
            <div class="hero-content">
                <h1 class="fade-in">Hi, I'<m></m> <span>Abdul Aziz Omar</span></h1>
                <p class="fade-in">Bachelor of Science in Information Systems</p>
                <div class="hero-btns fade-in">
                    <a href="#projects" class="btn">View My Work</a>
                    <a href="#contact" class="btn btn-outline">Contact Me</a>
                </div>
                <div class="hero-image fade-in">
                    <img src="Abdul A. Omar.jpg" alt="Profile Image">
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <div class="container">
            <h2 class="section-title fade-in">About Me</h2>
            <div class="about-content">
                <div class="about-image fade-in">
                    <img src="https://images.unsplash.com/photo-1580927752452-89d86da3fa0a?ixlib=rb-4.0.3&ixid=see%3D%3D&auto=format&fit=crop&w=1170&q=80" alt="About Image">
                </div>
                <div class="about-text fade-in">
                    <h3>A BSIS student who loves to create</h3>
                    <p>With 5 months of experience in web development, I specialize in creating responsive, user-friendly websites and applications. My approach combines technical expertise with an eye for design to deliver exceptional digital experiences.</p>
                    <p>When I'm not coding, you can find me hiking in the mountains or experimenting with new recipes in the kitchen. I believe in continuous learning and staying updated with the latest web technologies.</p>
                    <div class="skills">
                        <span class="skill">HTML5</span>
                        <span class="skill">CSS</span>
                        <span class="skill">JavaScript</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <div class="container">
            <h2 class="section-title fade-in">My Projects</h2>
            <div class="projects-grid">
                <!-- Project 1 -->
                <div class="project-card fade-in">
                    <div class="project-image">
                        <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80" alt="Project 1">
                    </div>
                    <div class="project-info">
                        <h3>E-commerce Website</h3>
                        <p>A fully responsive e-commerce platform with product filtering, cart functionality, and secure checkout.</p>
                        <div class="project-tags">
                            <span class="project-tag">React</span>
                            <span class="project-tag">Node.js</span>
                            <span class="project-tag">MongoDB</span>
                        </div>
                        <div class="project-links">
                            <a href="#"><i class="fas fa-external-link-alt"></i> Live Demo</a>
                            <a href="#"><i class="fab fa-github"></i> Code</a>
                        </div>
                    </div>
                </div>
                
              <!-- Project 2 -->
                <div class="project-card fade-in">
                    <div class="project-image">
                        <img src="https://images.unsplash.com/photo-1467232004584-a241de8bcf5d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1169&q=80" alt="Project 2">
                    </div>
                    <div class="project-info">
                        <h3>Task Management App</h3>
                        <p>A productivity application for organizing tasks with drag-and-drop functionality and team collaboration.</p>
                        <div class="project-tags">
                            <span class="project-tag">Vue.js</span>
                            <span class="project-tag">Firebase</span>
                            <span class="project-tag">Tailwind CSS</span>
                        </div>
                        <div class="project-links">
                            <a href="#"><i class="fas fa-external-link-alt"></i> Live Demo</a>
                            <a href="#"><i class="fab fa-github"></i> Code</a>
                        </div>
                    </div>
                </div>
                
                <!-- Project 3 -->
                <div class="project-card fade-in">
                    <div class="project-image">
                        <img src="https://images.unsplash.com/photo-1559028012-481c04fa702d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1136&q=80" alt="Project 3">
                    </div>
                    <div class="project-inf
