<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber Jurist - Cybersecurity Solutions</title>
    
    <!-- YAHAN APKA FAVICON SET HAI -->
    <link rel="icon" type="image/png" sizes="16x16" href="favicon-16x16.png">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #1a73e8;
            --secondary: #0d47a1;
            --accent: #00c853;
            --dark: #121212;
            --light: #f8f9fa;
            --danger: #e53935;
            --warning: #ffb300;
        }

        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Header Styles */
        header {
            background-color: var(--dark);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-icon {
            font-size: 2rem;
            color: var(--accent);
        }

        .logo-text {
            font-size: 1.5rem;
            font-weight: 700;
        }

        .logo-text span {
            color: var(--accent);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        nav a:hover {
            color: var(--accent);
        }

        .nav-icon {
            font-size: 1.1rem;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--dark) 0%, var(--secondary) 100%);
            color: white;
            padding: 5rem 0;
            text-align: center;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .btn {
            display: inline-block;
            background-color: var(--accent);
            color: white;
            padding: 0.8rem 1.8rem;
            border-radius: 4px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            background-color: #00b248;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 200, 83, 0.3);
        }

        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--accent);
            margin-left: 1rem;
        }

        .btn-outline:hover {
            background-color: var(--accent);
        }

        /* Services Section */
        .section {
            padding: 5rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: var(--dark);
            margin-bottom: 1rem;
        }

        .section-title p {
            color: #666;
            max-width: 600px;
            margin: 0 auto;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .service-card {
            background-color: white;
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
            text-align: center;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }

        .service-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 1.5rem;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--dark);
        }

        .service-card p {
            color: #666;
            margin-bottom: 1.5rem;
        }

        /* About Section */
        .about {
            background-color: var(--light);
        }

        .about-content {
            display: flex;
            align-items: center;
            gap: 4rem;
        }

        .about-text {
            flex: 1;
        }

        .about-text h2 {
            font-size: 2.5rem;
            color: var(--dark);
            margin-bottom: 1.5rem;
        }

        .about-text p {
            margin-bottom: 1.5rem;
            color: #555;
        }

        .about-image {
            flex: 1;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .about-image img {
            width: 100%;
            height: auto;
            display: block;
        }

        /* Stats Section */
        .stats {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            text-align: center;
            padding: 4rem 0;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
        }

        .stat-item h3 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
        }

        .stat-item p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Testimonials */
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .testimonial-card {
            background-color: white;
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .testimonial-text {
            font-style: italic;
            margin-bottom: 1.5rem;
            color: #555;
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .author-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .author-info h4 {
            color: var(--dark);
            margin-bottom: 0.2rem;
        }

        .author-info p {
            color: #777;
            font-size: 0.9rem;
        }

        /* Contact Section */
        .contact {
            background-color: var(--light);
        }

        .contact-content {
            display: flex;
            gap: 4rem;
        }

        .contact-info {
            flex: 1;
        }

        .contact-info h3 {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: var(--dark);
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .contact-icon {
            font-size: 1.5rem;
            color: var(--primary);
            width: 40px;
            height: 40px;
            background-color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }

        .contact-form {
            flex: 1;
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--dark);
        }

        .form-control {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
            transition: border 0.3s;
        }

        .form-control:focus {
            border-color: var(--primary);
            outline: none;
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 4rem 0 2rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            color: var(--accent);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .footer-links a:hover {
            color: var(--accent);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid #333;
            color: #999;
            font-size: 0.9rem;
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: #333;
            border-radius: 50%;
            color: white;
            text-decoration: none;
            transition: all 0.3s;
        }

        .social-link:hover {
            background-color: var(--primary);
            transform: translateY(-3px);
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .about-content, .contact-content {
                flex-direction: column;
            }
            
            .about-image {
                order: -1;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            nav ul {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .btn-group {
                display: flex;
                flex-direction: column;
                gap: 1rem;
            }
            
            .btn-outline {
                margin-left: 0;
            }
        }

        @media (max-width: 576px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .section-title h2 {
                font-size: 2rem;
            }
            
            .service-card, .testimonial-card {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-shield-alt logo-icon"></i>
                    <div class="logo-text">Cyber<span>Jurist</span></div>
                </div>
                <nav>
                    <ul>
                        <li><a href="#home"><i class="fas fa-home nav-icon"></i> Home</a></li>
                        <li><a href="#services"><i class="fas fa-cogs nav-icon"></i> Services</a></li>
                        <li><a href="#about"><i class="fas fa-info-circle nav-icon"></i> About</a></li>
                        <li><a href="#testimonials"><i class="fas fa-comments nav-icon"></i> Testimonials</a></li>
                        <li><a href="#contact"><i class="fas fa-envelope nav-icon"></i> Contact</a></li>
                    </ul>
                </nav>
                <button class="mobile-menu-btn">
                    <i class="fas fa-bars"></i>
                </button>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container">
            <div class="hero-content">
                <h1>Advanced Cybersecurity Solutions for Modern Threats</h1>
                <p>Protect your digital assets with our comprehensive security services and expert legal guidance in cybersecurity matters.</p>
                <div class="btn-group">
                    <a href="#contact" class="btn">Get Started</a>
                    <a href="#services" class="btn btn-outline">Our Services</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="section" id="services">
        <div class="container">
            <div class="section-title">
                <h2>Our Cybersecurity Services</h2>
                <p>We offer a comprehensive range of cybersecurity solutions to protect your business from digital threats.</p>
            </div>
            <div class="services-grid">
                <div class="service-card">
                    <i class="fas fa-lock service-icon"></i>
                    <h3>Vulnerability Assessment</h3>
                    <p>Identify security weaknesses in your systems before attackers can exploit them.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
                <div class="service-card">
                    <i class="fas fa-user-shield service-icon"></i>
                    <h3>Penetration Testing</h3>
                    <p>Simulate real-world attacks to test your security defenses and response capabilities.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
                <div class="service-card">
                    <i class="fas fa-gavel service-icon"></i>
                    <h3>Cyber Legal Consulting</h3>
                    <p>Navigate the complex legal landscape of cybersecurity with our expert guidance.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
                <div class="service-card">
                    <i class="fas fa-cloud service-icon"></i>
                    <h3>Cloud Security</h3>
                    <p>Secure your cloud infrastructure and data with our specialized cloud security solutions.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
                <div class="service-card">
                    <i class="fas fa-headset service-icon"></i>
                    <h3>Incident Response</h3>
                    <p>Rapid response and recovery services when security incidents occur.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
                <div class="service-card">
                    <i class="fas fa-chart-line service-icon"></i>
                    <h3>Security Training</h3>
                    <p>Educate your team on cybersecurity best practices and threat awareness.</p>
                    <a href="#" class="btn">Learn More</a>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="section about" id="about">
        <div class="container">
            <div class="about-content">
                <div class="about-text">
                    <h2>About Cyber Jurist</h2>
                    <p>Cyber Jurist is a leading cybersecurity firm that combines technical expertise with legal knowledge to provide comprehensive digital protection solutions.</p>
                    <p>Founded by a team of cybersecurity professionals and legal experts, we understand the complex intersection of technology, security, and law in today's digital landscape.</p>
                    <p>Our mission is to protect businesses from cyber threats while ensuring compliance with relevant regulations and legal requirements.</p>
                    <a href="#" class="btn">Learn More About Us</a>
                </div>
                <div class="about-image">
                    <!-- Placeholder for about image -->
                    <div style="width:100%; height:400px; background:linear-gradient(135deg, #1a73e8 0%, #0d47a1 100%); display:flex; align-items:center; justify-content:center; color:white; font-size:1.5rem;">
                        <i class="fas fa-shield-alt" style="font-size:4rem; margin-right:1rem;"></i>
                        Cybersecurity Excellence
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
        <div class="container">
            <div class="stats-grid">
                <div class="stat-item">
                    <h3>500+</h3>
                    <p>Clients Protected</p>
                </div>
                <div class="stat-item">
                    <h3>99.9%</h3>
                    <p>Threat Detection Rate</p>
                </div>
                <div class="stat-item">
                    <h3>24/7</h3>
                    <p>Security Monitoring</p>
                </div>
                <div class="stat-item">
                    <h3>50+</h3>
                    <p>Security Experts</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section class="section" id="testimonials">
        <div class="container">
            <div class="section-title">
                <h2>What Our Clients Say</h2>
                <p>Hear from businesses we've helped secure their digital assets.</p>
            </div>
            <div class="testimonials-grid">
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "Cyber Jurist helped us identify critical vulnerabilities in our systems that we were completely unaware of. Their team is professional, knowledgeable, and responsive."
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">JS</div>
                        <div class="author-info">
                            <h4>John Smith</h4>
                            <p>CTO, TechSolutions Inc.</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "The legal guidance provided by Cyber Jurist was invaluable during our compliance audit. They helped us navigate complex regulations with ease."
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">AR</div>
                        <div class="author-info">
                            <h4>Amanda Roberts</h4>
                            <p>Compliance Officer, FinancialSecure</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        "Their incident response team was incredibly efficient when we experienced a security breach. They contained the threat and helped us recover quickly."
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">MJ</div>
                        <div class="author-info">
                            <h4>Michael Johnson</h4>
                            <p>IT Director, RetailGlobal</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="section contact" id="contact">
        <div class="container">
            <div class="section-title">
                <h2>Contact Us</h2>
                <p>Get in touch with our cybersecurity experts to discuss your protection needs.</p>
            </div>
            <div class="contact-content">
                <div class="contact-info">
                    <h3>Get In Touch</h3>
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i class="fas fa-map-marker-alt"></i>
                        </div>
                        <div>
                            <h4>Our Office</h4>
                            <p>123 Security Avenue, Cyber City</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i class="fas fa-phone"></i>
                        </div>
                        <div>
                            <h4>Phone</h4>
                            <p>+1 (555) 123-4567</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <div>
                            <h4>Email</h4>
                            <p>info@cyberjurist.com</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i class="fas fa-clock"></i>
                        </div>
                        <div>
                            <h4>Business Hours</h4>
                            <p>Mon - Fri: 9:00 AM - 6:00 PM</p>
                        </div>
                    </div>
                </div>
                <div class="contact-form">
                    <form>
                        <div class="form-group">
                            <label for="name">Full Name</label>
                            <input type="text" id="name" class="form-control" placeholder="Your Name">
                        </div>
                        <div class="form-group">
                            <label for="email">Email Address</label>
                            <input type="email" id="email" class="form-control" placeholder="Your Email">
                        </div>
                        <div class="form-group">
                            <label for="service">Service Interested In</label>
                            <select id="service" class="form-control">
                                <option value="">Select a Service</option>
                                <option value="assessment">Vulnerability Assessment</option>
                                <option value="penetration">Penetration Testing</option>
                                <option value="legal">Cyber Legal Consulting</option>
                                <option value="cloud">Cloud Security</option>
                                <option value="incident">Incident Response</option>
                                <option value="training">Security Training</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="message">Message</label>
                            <textarea id="message" class="form-control" placeholder="Your Message"></textarea>
                        </div>
                        <button type="submit" class="btn">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>Cyber Jurist</h3>
                    <p>Providing comprehensive cybersecurity solutions with legal expertise to protect your digital assets.</p>
                    <div class="social-links">
                        <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#home"><i class="fas fa-chevron-right"></i> Home</a></li>
                        <li><a href="#services"><i class="fas fa-chevron-right"></i> Services</a></li>
                        <li><a href="#about"><i class="fas fa-chevron-right"></i> About Us</a></li>
                        <li><a href="#testimonials"><i class="fas fa-chevron-right"></i> Testimonials</a></li>
                        <li><a href="#contact"><i class="fas fa-chevron-right"></i> Contact</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Our Services</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Vulnerability Assessment</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Penetration Testing</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Cyber Legal Consulting</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Cloud Security</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Incident Response</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Newsletter</h3>
                    <p>Subscribe to our newsletter for the latest cybersecurity insights and updates.</p>
                    <form>
                        <div class="form-group">
                            <input type="email" class="form-control" placeholder="Your Email">
                        </div>
                        <button type="submit" class="btn">Subscribe</button>
                    </form>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 Cyber Jurist. All Rights Reserved. | Designed with <i class="fas fa-heart" style="color:var(--accent);"></i> for Security</p>
            </div>
        </div>
    </footer>

    <script>
        // Simple JavaScript for mobile menu toggle
        document.querySelector('.mobile-menu-btn').addEventListener('click', function() {
            document.querySelector('nav ul').classList.toggle('show');
        });

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if(targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if(targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
    </script>
</body>
</html>
