<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber Jurist - Prosecuting E-Crimes</title>
    
    <!-- PWA Meta Tags -->
    <meta name="theme-color" content="#1a2a6c">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">

    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #7c3aed;
            --accent: #f59e0b;
            --dark: #0f172a;
            --darker: #020617;
            --light: #f8fafc;
            --gray: #64748b;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 100%);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Loading Spinner */
        .spinner {
            display: none;
            width: 40px;
            height: 40px;
            border: 4px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1s ease-in-out infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Success Message */
        .success-message {
            display: none;
            background: rgba(16, 185, 129, 0.2);
            border: 1px solid var(--success);
            border-radius: 10px;
            padding: 1.5rem;
            text-align: center;
            margin-bottom: 2rem;
            color: var(--light);
        }

        .success-message i {
            color: var(--success);
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        /* 3D Logo Styles */
        .logo-3d-container {
            width: 80px;
            height: 80px;
        }

        .scene {
            width: 100%;
            height: 100%;
            perspective: 300px;
        }

        .cube {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            animation: rotate 15s infinite linear;
        }

        .cube-face {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            box-sizing: border-box;
            color: white;
            text-align: center;
            font-weight: bold;
            backface-visibility: visible;
        }

        .front  { transform: translateZ(40px); }
        .back   { transform: rotateY(180deg) translateZ(40px); }
        .right  { transform: rotateY(90deg) translateZ(40px); }
        .left   { transform: rotateY(-90deg) translateZ(40px); }
        .top    { transform: rotateX(90deg) translateZ(40px); }
        .bottom { transform: rotateX(-90deg) translateZ(40px); }

        .main-title {
            font-size: 0.5em;
            line-height: 1.1;
            color: white;
            font-weight: 700;
        }

        @keyframes rotate {
            from { transform: rotateX(15deg) rotateY(0deg); }
            to { transform: rotateX(15deg) rotateY(360deg); }
        }

        /* Header & Navigation */
        .header {
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            padding: 1rem 0;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--light);
            text-decoration: none;
        }

        .nav-menu {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-menu a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-menu a:hover {
            color: var(--accent);
        }

        .nav-menu a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-menu a:hover::after {
            width: 100%;
        }

        .nav-actions {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .btn {
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(37, 99, 235, 0.3);
        }

        .btn-outline {
            border: 2px solid var(--primary);
            color: var(--primary);
            background: transparent;
        }

        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding: 8rem 2rem 4rem;
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 50%, rgba(37, 99, 235, 0.1) 100%);
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1000"><polygon fill="%232563eb" fill-opacity="0.05" points="0,1000 1000,0 1000,1000"/></svg>');
            background-size: cover;
        }

        .hero-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            font-weight: 800;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--light) 0%, var(--primary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-content p {
            font-size: 1.2rem;
            color: var(--gray);
            margin-bottom: 2rem;
        }

        .hero-stats {
            display: flex;
            gap: 2rem;
            margin-top: 2rem;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--accent);
            display: block;
        }

        .stat-label {
            font-size: 0.9rem;
            color: var(--gray);
        }

        .hero-visual {
            position: relative;
        }

        .floating-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 20px;
            padding: 2rem;
            margin-bottom: 1rem;
            animation: float 6s ease-in-out infinite;
        }

        .floating-card:nth-child(2) {
            animation-delay: 2s;
            margin-left: 2rem;
        }

        .floating-card:nth-child(3) {
            animation-delay: 4s;
            margin-left: -2rem;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        /* YouTube Video Section */
        .youtube-section {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .video-container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%;
            height: 0;
            overflow: hidden;
            border-radius: 15px;
            margin-bottom: 1.5rem;
        }

        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        .channel-link {
            text-align: center;
            margin-top: 2rem;
        }

        /* Client Reviews Section */
        .reviews {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .reviews-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .review-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.3s ease;
            position: relative;
        }

        .review-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .review-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .review-avatar {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
        }

        .review-info h4 {
            color: var(--light);
            margin-bottom: 0.25rem;
            font-size: 1.1rem;
        }

        .review-location {
            color: var(--accent);
            font-size: 0.9rem;
        }

        .review-stars {
            color: var(--accent);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        .review-text {
            color: var(--gray);
            line-height: 1.6;
            font-style: italic;
        }

        .review-case {
            background: rgba(255, 255, 255, 0.1);
            padding: 0.5rem 1rem;
            border-radius: 10px;
            margin-top: 1rem;
            font-size: 0.9rem;
            color: var(--light);
        }

        .review-case strong {
            color: var(--accent);
        }

        /* About Us Section */
        .about {
            padding: 6rem 2rem;
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 100%);
        }

        .about-content {
            max-width: 1000px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--light) 0%, var(--primary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .about-text p {
            color: var(--gray);
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
        }

        .about-features {
            list-style: none;
            margin-top: 2rem;
        }

        .about-features li {
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 1rem;
            color: var(--light);
        }

        .about-features i {
            color: var(--accent);
            font-size: 1.2rem;
        }

        .about-visual {
            text-align: center;
        }

        .about-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin-top: 2rem;
        }

        /* FAQ Section */
        .faq {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .faq-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .faq-item {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            margin-bottom: 1rem;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .faq-item:hover {
            border-color: var(--primary);
        }

        .faq-question {
            padding: 1.5rem;
            background: rgba(255, 255, 255, 0.1);
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 600;
            color: var(--light);
        }

        .faq-answer {
            padding: 0 1.5rem;
            max-height: 0;
            overflow: hidden;
            transition: all 0.3s ease;
            color: var(--gray);
        }

        .faq-item.active .faq-answer {
            padding: 1.5rem;
            max-height: 500px;
        }

        .faq-item.active .faq-question i {
            transform: rotate(180deg);
        }

        /* Booking Form */
        .booking-section {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .booking-container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 3rem;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .booking-header {
            text-align: center;
            margin-bottom: 2rem;
        }

        .booking-header h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--light) 0%, var(--primary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .booking-header p {
            color: var(--gray);
            font-size: 1.1rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--light);
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        textarea.form-control {
            min-height: 120px;
            resize: vertical;
        }

        /* Features Grid */
        .features {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-header h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--light) 0%, var(--primary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .section-header p {
            font-size: 1.1rem;
            color: var(--gray);
            max-width: 600px;
            margin: 0 auto;
        }

        .features-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
        }

        .feature-card:hover {
            transform: translateY(-10px);
            background: rgba(255, 255, 255, 0.1);
            border-color: var(--primary);
        }

        .feature-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1.5rem;
            font-size: 1.5rem;
        }

        .feature-card h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--light);
        }

        .feature-card p {
            color: var(--gray);
            margin-bottom: 1rem;
        }

        /* Services Section */
        .services {
            padding: 6rem 2rem;
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 100%);
        }

        .services-grid {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .service-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .service-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .service-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1.5rem;
            font-size: 2rem;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--light);
        }

        .service-card p {
            color: var(--gray);
            margin-bottom: 1.5rem;
        }

        .service-price {
            font-size: 2rem;
            font-weight: 700;
            color: var(--accent);
            margin-bottom: 1.5rem;
        }

        /* Team Section */
        .team {
            padding: 6rem 2rem;
            background: var(--dark);
        }

        .team-grid {
            max-width: 1000px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 3rem;
        }

        .team-member {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .member-avatar {
            width: 120px;
            height: 120px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1.5rem;
            font-size: 3rem;
        }

        .member-info h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            color: var(--light);
        }

        .member-title {
            color: var(--accent);
            font-weight: 600;
            margin-bottom: 1rem;
            display: block;
        }

        .member-contact {
            color: var(--gray);
            margin-bottom: 1rem;
            display: block;
        }

        .member-qualification {
            background: rgba(255, 255, 255, 0.1);
            padding: 0.5rem 1rem;
            border-radius: 50px;
            color: var(--light);
            font-size: 0.9rem;
            display: inline-block;
            margin-bottom: 1rem;
        }

        /* CTA Section */
        .cta {
            padding: 6rem 2rem;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .cta::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1000"><polygon fill="%23ffffff" fill-opacity="0.1" points="0,0 1000,1000 0,1000"/></svg>');
            background-size: cover;
        }

        .cta-content {
            max-width: 600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        .cta h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: white;
        }

        .cta p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            color: rgba(255, 255, 255, 0.9);
        }

        .btn-light {
            background: white;
            color: var(--primary);
        }

        .btn-light:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(255, 255, 255, 0.3);
        }

        /* Footer */
        .footer {
            background: var(--darker);
            padding: 4rem 2rem 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 3rem;
        }

        .footer-column h4 {
            color: var(--light);
            margin-bottom: 1.5rem;
            font-size: 1.2rem;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.5rem;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: var(--accent);
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-links a {
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--light);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: var(--primary);
            transform: translateY(-2px);
        }

        .footer-bottom {
            max-width: 1200px;
            margin: 0 auto;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            text-align: center;
            color: var(--gray);
            font-size: 0.9rem;
        }

        .software-house {
            color: var(--accent);
            font-weight: 600;
        }

        .emergency-numbers {
            background: rgba(239, 68, 68, 0.1);
            padding: 1rem;
            border-radius: 10px;
            margin-top: 1rem;
            border-left: 4px solid var(--danger);
        }

        .emergency-numbers h5 {
            color: var(--danger);
            margin-bottom: 0.5rem;
        }

        /* Mobile Menu */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--light);
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .logo-3d-container {
                width: 60px;
                height: 60px;
            }
            
            .main-title {
                font-size: 0.4em;
            }
            
            .scene {
                perspective: 200px;
            }
            
            .front  { transform: translateZ(30px); }
            .back   { transform: rotateY(180deg) translateZ(30px); }
            .right  { transform: rotateY(90deg) translateZ(30px); }
            .left   { transform: rotateY(-90deg) translateZ(30px); }
            .top    { transform: rotateX(90deg) translateZ(30px); }
            .bottom { transform: rotateX(-90deg) translateZ(30px); }

            .nav-menu {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background: var(--dark);
                flex-direction: column;
                padding: 2rem;
                border-top: 1px solid rgba(255, 255, 255, 0.1);
            }

            .nav-menu.show {
                display: flex;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero-container {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .hero-content h1 {
                font-size: 2.5rem;
            }

            .about-content {
                grid-template-columns: 1fr;
            }

            .footer-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .features-grid,
            .services-grid,
            .team-grid,
            .reviews-grid {
                grid-template-columns: 1fr;
            }

            .form-row {
                grid-template-columns: 1fr;
            }
        }

        /* Install Prompt */
        .install-prompt {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            background: var(--primary);
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 25px rgba(37, 99, 235, 0.3);
            z-index: 1000;
            display: none;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
    </style>
</head>
<body>
    <!-- Install Prompt -->
    <div class="install-prompt" id="installPrompt">
        <i class="fas fa-download"></i> Install App
    </div>

    <!-- Header -->
    <header class="header">
        <div class="nav-container">
            <a href="#" class="logo">
                <div class="logo-3d-container">
                    <div class="scene">
                        <div class="cube">
                            <div class="cube-face front">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                            <div class="cube-face back">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                            <div class="cube-face right">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                            <div class="cube-face left">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                            <div class="cube-face top">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                            <div class="cube-face bottom">
                                <div class="main-title">LAW<br>CYBER<br>JURIST</div>
                            </div>
                        </div>
                    </div>
                </div>
            </a>
            
            <button class="mobile-menu-btn">
                <i class="fas fa-bars"></i>
            </button>

            <ul class="nav-menu">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About Us</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#youtube">Videos</a></li>
                <li><a href="#reviews">Client Reviews</a></li>
                <li><a href="#team">Our Team</a></li>
                <li><a href="#faq">FAQ</a></li>
                <li><a href="#booking">Free Consultation</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>

            <div class="nav-actions">
                <a href="#contact" class="btn btn-outline">Emergency Help</a>
                <a href="#booking" class="btn btn-primary">Free Consultation</a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-container">
            <div class="hero-content">
                <h1>Fight Cyber Crime With Legal & Technical Power</h1>
                <p>Combining IT expertise with legal authority to protect your digital life. Immediate response, global reach, unbeatable results.</p>
                
                <div class="hero-actions">
                    <a href="#booking" class="btn btn-primary">Get Free Consultation</a>
                    <a href="#contact" class="btn btn-outline">Emergency Help</a>
                </div>

                <div class="hero-stats">
                    <div class="stat">
                        <span class="stat-number" data-count="500">0</span>
                        <span class="stat-label">Hackers Arrested</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number" data-count="1200">0</span>
                        <span class="stat-label">Million Recovered</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number" data-count="95">0</span>
                        <span class="stat-label">Success Rate</span>
                    </div>
                </div>
            </div>

            <div class="hero-visual">
                <div class="floating-card">
                    <h3><i class="fas fa-bolt"></i> 24/7 Emergency Response</h3>
                    <p>Immediate action within 1 hour of reporting</p>
                </div>
                <div class="floating-card">
                    <h3><i class="fas fa-globe"></i> Global Legal Network</h3>
                    <p>International cooperation with 50+ countries</p>
                </div>
                <div class="floating-card">
                    <h3><i class="fas fa-shield-alt"></i> Complete Protection</h3>
                    <p>Technical + Legal solutions combined</p>
                </div>
            </div>
        </div>
    </section>

    <!-- YouTube Video Section -->
    <section id="youtube" class="youtube-section">
        <div class="section-header">
            <h2>Watch Our Success Stories</h2>
            <p>See how we help people recover from cyber crimes</p>
        </div>
        
        <div class="video-container">
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/jnL5SkZFISw" 
                        title="Cyber Jurist Success Story" 
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                        allowfullscreen>
                </iframe>
            </div>
            <div class="channel-link">
                <a href="https://www.youtube.com/channel/UCTwuXLOMOsQ100Qn-aCXfQw" 
                   target="_blank" 
                   class="btn btn-primary">
                    <i class="fab fa-youtube"></i> Visit Our YouTube Channel
                </a>
            </div>
        </div>
    </section>

    <!-- About Us Section -->
    <section id="about" class="about">
        <div class="section-header">
            <h2>About Cyber Jurist</h2>
            <p>Your trusted partner in fighting cyber crimes</p>
        </div>
        
        <div class="about-content">
            <div class="about-text">
                <h2>Who We Are</h2>
                <p>Cyber Jurist is Pakistan's premier cyber crime fighting organization that combines cutting-edge IT expertise with legal authority to protect citizens from digital threats.</p>
                
                <p>Founded by Ashfaq Haider Advocate (Cyber Law Attorney) and Yasir Zareen Khan (IT Engineer), we provide comprehensive solutions for all types of electronic crimes.</p>
                
                <ul class="about-features">
                    <li><i class="fas fa-check-circle"></i> Legal action under PECA 2016</li>
                    <li><i class="fas fa-check-circle"></i> Advanced digital forensics</li>
                    <li><i class="fas fa-check-circle"></i> 24/7 emergency response</li>
                    <li><i class="fas fa-check-circle"></i> International cooperation</li>
                    <li><i class="fas fa-check-circle"></i> Success-based fee structure</li>
                </ul>
            </div>
            
            <div class="about-visual">
                <div class="about-stats">
                    <div class="stat">
                        <span class="stat-number">500+</span>
                        <span class="stat-label">Cases Solved</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">1200+</span>
                        <span class="stat-label">Million Recovered</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">95%</span>
                        <span class="stat-label">Success Rate</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">24/7</span>
                        <span class="stat-label">Support</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Client Reviews Section -->
    <section id="reviews" class="reviews">
        <div class="section-header">
            <h2>Client Success Stories</h2>
            <p>Real people, real results - Read what our satisfied clients have to say</p>
        </div>

        <div class="reviews-grid">
            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">AA</div>
                    <div class="review-info">
                        <h4>Ahmed Ali</h4>
                        <span class="review-location">Lahore, Punjab</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐⭐ 5.0
                </div>
                <p class="review-text">
                    "میرا Facebook اکاؤنٹ ہیک ہو گیا تھا اور ہیکر نے میرے دوستوں سے پیسے مانگنا شروع کر دیے تھے۔ Cyber Jurist ٹیم نے صرف 2 گھنٹے میں میرا اکاؤنٹ واپس حاصل کر لیا۔ بہت شکریہ!"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Facebook Account Hacking
                </div>
            </div>

            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">FS</div>
                    <div class="review-info">
                        <h4>Fatima Shah</h4>
                        <span class="review-location">Karachi, Sindh</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐ 4.5
                </div>
                <p class="review-text">
                    "بینک اکاؤنٹ سے 5 لاکھ روپے کا فراڈ ہو گیا تھا۔ Cyber Jurist نے نہ صرف پیسے واپس دلائے بلکہ مجرم کو بھی پکڑوایا۔ پیشہ ورانہ کام کے لیے دل سے شکریہ۔"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Banking Fraud Recovery
                </div>
            </div>

            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">BR</div>
                    <div class="review-info">
                        <h4>Bilal Raza</h4>
                        <span class="review-location">Islamabad</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐⭐ 5.0
                </div>
                <p class="review-text">
                    "کسی نے میری تصاویر کا غلط استعمال کر کے بلیک میل کرنا شروع کر دیا تھا۔ Ashfaq Haider Advocate نے فوری قانونی کارروائی کر کے مسئلہ حل کر دیا۔ بہترین سروس!"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Online Blackmail & Harassment
                </div>
            </div>

            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">SK</div>
                    <div class="review-info">
                        <h4>Sana Khan</h4>
                        <span class="review-location">Rawalpindi</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐ 4.5
                </div>
                <p class="review-text">
                    "میرا Instagram اکاؤنٹ چوری ہو گیا تھا اور ہیکر نے میرے فالوورز کو اسکیم میسج بھیجے۔ Yasir Zareen Khan نے ٹیکنیکل طور پر اکاؤنٹ واپس لے لیا۔ بہت ماہرانہ کام!"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Instagram Account Recovery
                </div>
            </div>

            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">MR</div>
                    <div class="review-info">
                        <h4>Mohammad Rizwan</h4>
                        <span class="review-location">Faisalabad</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐⭐ 5.0
                </div>
                <p class="review-text">
                    "Online shopping میں میرا 75,000 روپے ڈوب گئے تھے۔ Cyber Jurist نے seller کو ٹریک کیا اور میرا پیسہ واپس دلایا۔ یہ ٹیم واقعی قابل اعتماد ہے۔"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Online Shopping Fraud
                </div>
            </div>

            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">NZ</div>
                    <div class="review-info">
                        <h4>Nadia Zafar</h4>
                        <span class="review-location">Multan</span>
                    </div>
                </div>
                <div class="review-stars">
                    ⭐⭐⭐⭐ 4.5
                </div>
                <p class="review-text">
                    "کسی نے میری شناخت چرا کر loan لے لیا تھا۔ Cyber Jurist نے میری شناخت بحال کی اور legal notice بھیج کر میرا نام کلیئر کروایا۔ بہت شکریہ پوری ٹیم کا!"
                </p>
                <div class="review-case">
                    <strong>Case:</strong> Identity Theft Protection
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ Section -->
    <section id="faq" class="faq">
        <div class="section-header">
            <h2>Frequently Asked Questions</h2>
            <p>Find answers to common questions about our services</p>
        </div>

        <div class="faq-container">
            <div class="faq-item">
                <div class="faq-question">
                    What types of cyber crimes do you handle?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    We handle all types of cyber crimes including social media hacking, banking fraud, identity theft, online blackmail, cyber harassment, data breaches, and online shopping fraud.
                </div>
            </div>

            <div class="faq-item">
                <div class="faq-question">
                    How quickly can you respond to emergencies?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    We provide 24/7 emergency response and typically take action within 1 hour of receiving your complaint. For critical cases like banking fraud, we respond immediately.
                </div>
            </div>

            <div class="faq-item">
                <div class="faq-question">
                    What is your success rate?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    We maintain a 95% success rate in resolving cyber crime cases. Our unique combination of IT expertise and legal authority makes us highly effective.
                </div>
            </div>

            <div class="faq-item">
                <div class="faq-question">
                    Do you charge upfront fees?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    No, we offer free initial consultation and work on success-based fees for most cases. You only pay when we successfully resolve your case.
                </div>
            </div>

            <div class="faq-item">
                <div class="faq-question">
                    Can you help with international cyber crimes?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    Yes, we have international cooperation with cyber crime authorities in 50+ countries and can handle cases with international elements.
                </div>
            </div>

            <div class="faq-item">
                <div class="faq-question">
                    What legal powers do you have?
                    <i class="fas fa-chevron-down"></i>
                </div>
                <div class="faq-answer">
                    Our legal team operates under PECA 2016 (Pakistan Electronic Crimes Act) and has the authority to file cases, obtain warrants, and prosecute cyber criminals through proper legal channels.
                </div>
            </div>
        </div>
    </section>

    <!-- Booking Form Section -->
    <section id="booking" class="booking-section">
        <div class="booking-container">
            <div class="booking-header">
                <h2>Free Consultation</h2>
                <p>Get expert advice from our IT + Law team. No commitment required.</p>
            </div>

            <!-- Success Message -->
            <div class="success-message" id="successMessage">
                <i class="fas fa-check-circle"></i>
                <h3>Thank You!</h3>
                <p>Your consultation request has been submitted successfully. Our team will contact you within 1 hour.</p>
            </div>
            
            <form id="consultationForm" action="https://formspree.io/f/xjvnerjg" method="POST">
                <input type="hidden" name="_subject" value="New Consultation Request - Cyber Jurist">
                <input type="hidden" name="_replyto" value="cyberjurist.pk@gmail.com">
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="fullName">Full Name *</label>
                        <input type="text" id="fullName" name="fullName" class="form-control" required placeholder="Enter your full name">
                    </div>
                    <div class="form-group">
                        <label for="phone">Phone Number *</label>
                        <input type="tel" id="phone" name="phone" class="form-control" required placeholder="0300-1234567">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" name="email" class="form-control" placeholder="your@email.com">
                    </div>
                    <div class="form-group">
                        <label for="caseType">Case Type *</label>
                        <select id="caseType" name="caseType" class="form-control" required>
                            <option value="">Select your issue</option>
                            <option value="social-media">Social Media Hacking</option>
                            <option value="banking">Banking Fraud</option>
                            <option value="identity">Identity Theft</option>
                            <option value="blackmail">Online Blackmail</option>
                            <option value="harassment">Cyber Harassment</option>
                            <option value="other">Other Issue</option>
                        </select>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="query">Describe Your Issue *</label>
                    <textarea id="query" name="query" class="form-control" required placeholder="Please describe your problem in detail..."></textarea>
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%; padding: 1.2rem;" id="submitBtn">
                    <i class="fas fa-paper-plane"></i> Submit for Free Consultation
                </button>
                
                <!-- Loading Spinner -->
                <div class="spinner" id="loadingSpinner"></div>
            </form>
        </div>
    </section>

    <!-- Features Section -->
    <section id="features" class="features">
        <div class="section-header">
            <h2>Why We Are Unbeatable</h2>
            <p>The unique combination that makes hackers fear and clients trust</p>
        </div>

        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-laptop-code"></i>
                </div>
                <h3>IT Forensics</h3>
                <p>Advanced digital evidence collection and analysis with cutting-edge technology</p>
                <ul class="footer-links">
                    <li>• Digital Footprint Analysis</li>
                    <li>• Server Log Examination</li>
                    <li>• Network Traffic Monitoring</li>
                </ul>
            </div>

            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-gavel"></i>
                </div>
                <h3>Legal Authority</h3>
                <p>Full legal power to prosecute under Pakistani and international laws</p>
                <ul class="footer-links">
                    <li>• PECA 2016 Enforcement</li>
                    <li>• International Warrants</li>
                    <li>• Court Admissible Evidence</li>
                </ul>
            </div>

            <div class="feature-card">
                <div class="feature-icon">
                    <i class="fas fa-bolt"></i>
                </div>
                <h3>Instant Response</h3>
                <p>24/7 emergency response team ready to take immediate action</p>
                <ul class="footer-links">
                    <li>• 1-Hour Initial Response</li>
                    <li>• Account Recovery</li>
                    <li>• Evidence Preservation</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Team Section -->
    <section id="team" class="team">
        <div class="section-header">
            <h2>Founder & CEO</h2>
            <p>Meet the experts behind Cyber Jurist's success</p>
        </div>

        <div class="team-grid">
            <div class="team-member">
                <div class="member-avatar">
                    <i class="fas fa-gavel"></i>
                </div>
                <div class="member-info">
                    <h3>Ashfaq Haider Advocate</h3>
                    <span class="member-title">Cyber Law Attorney (CLA)</span>
                    <div class="member-qualification">Legal Expert - PECA 2016 Specialist</div>
                    <span class="member-contact">
                        <i class="fas fa-phone"></i> 📞 0300-989-3632
                    </span>
                    <p>Expert in cyber laws with successful track record of prosecuting electronic crimes under PECA 2016 and international cyber laws.</p>
                </div>
            </div>

            <div class="team-member">
                <div class="member-avatar">
                    <i class="fas fa-laptop-code"></i>
                </div>
                <div class="member-info">
                    <h3>Yasir Zareen Khan</h3>
                    <span class="member-title">IT Engineer (ITE)</span>
                    <div class="member-qualification">Digital Forensics & Cybersecurity Expert</div>
                    <span class="member-contact">
                        <i class="fas fa-phone"></i> 📞 0314-507-9122
                    </span>
                    <p>Specialized in digital forensics, network security, and cyber crime investigation with advanced technical expertise.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="services">
        <div class="section-header">
            <h2>Our Protection Services</h2>
            <p>Comprehensive solutions for all digital security threats</p>
        </div>

        <div class="services-grid">
            <div class="service-card">
                <div class="service-icon">
                    <i class="fab fa-facebook"></i>
                </div>
                <h3>Social Media Protection</h3>
                <p>Complete security for Facebook, Instagram, WhatsApp, LinkedIn</p>
                <div class="service-price">Free Consultation</div>
                <a href="#booking" class="btn btn-primary">Get Protected</a>
            </div>

            <div class="service-card">
                <div class="service-icon">
                    <i class="fas fa-credit-card"></i>
                </div>
                <h3>Banking Fraud Recovery</h3>
                <p>Immediate action for hacked bank accounts and financial fraud</p>
                <div class="service-price">Success-Based Fee</div>
                <a href="#booking" class="btn btn-primary">Recover Money</a>
            </div>

            <div class="service-card">
                <div class="service-icon">
                    <i class="fas fa-id-card"></i>
                </div>
                <h3>Identity Theft Protection</h3>
                <p>Complete identity restoration and legal action against thieves</p>
                <div class="service-price">Free Initial Case Review</div>
                <a href="#booking" class="btn btn-primary">Restore Identity</a>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta">
        <div class="cta-content">
            <h2>⏰ 24/7 Free Advisory Available</h2>
            <p>Don't wait until you become a victim. Get professional protection now with our IT+Law combination.</p>
            <a href="#booking" class="btn btn-light">Start Free Consultation</a>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact" class="footer">
        <div class="footer-content">
            <div class="footer-column">
                <h4>Cyber Jurist</h4>
                <p>Combining IT expertise with legal authority to fight cyber crime. Your digital protection partner.</p>
                
                <div class="emergency-numbers">
                    <h5>🚨 Emergency Numbers:</h5>
                    <p>Police: <strong>15</strong></p>
                    <p>FIA Cyber Crime: <strong>051-111-345-786 & 1991</strong></p>
                </div>

                <div class="hero-stats">
                    <div class="stat">
                        <span class="stat-number">24/7</span>
                        <span class="stat-label">Free Advisory</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">Free</span>
                        <span class="stat-label">Consultation</span>
                    </div>
                </div>
            </div>

            <div class="footer-column">
                <h4>Services</h4>
                <ul class="footer-links">
                    <li><a href="#services">Social Media Security</a></li>
                    <li><a href="#services">Banking Fraud Recovery</a></li>
                    <li><a href="#services">Identity Theft Protection</a></li>
                    <li><a href="#services">Cyber Harassment</a></li>
                    <li><a href="#services">Data Breach Response</a></li>
                </ul>
            </div>

            <div class="footer-column">
                <h4>Contact Info</h4>
                <ul class="footer-links">
                    <li><i class="fas fa-envelope"></i> 📧 cyberjurist.pk@gmail.com</li>
                    <li><i class="fas fa-globe"></i> https://pakistancyberjurist.netlify.app/</li>
                    <li><i class="fas fa-globe"></i> https://cyberjurist-pak.github.io/cyberjurist/</li>
                    <li><i class="fas fa-clock"></i> ⏰ 24/7 Free Advisory</li>
                </ul>

                <div class="social-links">
                    <a href="https://www.facebook.com/profile.php?id=61581846842847" title="Facebook">
                        <i class="fab fa-facebook-f"></i>
                    </a>
                    <a href="https://www.facebook.com/cyberjurist.pk/" title="Facebook Page">
                        <i class="fab fa-facebook"></i>
                    </a>
                    <a href="https://www.instagram.com/cyberjurist.pk/" title="Instagram">
                        <i class="fab fa-instagram"></i>
                    </a>
                    <a href="https://wa.me/923009893632" title="WhatsApp">
                        <i class="fab fa-whatsapp"></i>
                    </a>
                    <a href="#" title="Twitter">
                        <i class="fab fa-twitter"></i>
                    </a>
                    <a href="https://www.youtube.com/channel/UCTwuXLOMOsQ100Qn-aCXfQw" title="YouTube">
                        <i class="fab fa-youtube"></i>
                    </a>
                    <a href="https://www.linkedin.com/feed/?trk=onboarding-landing" title="LinkedIn">
                        <i class="fab fa-linkedin"></i>
                    </a>
                </div>
            </div>

            <div class="footer-column">
                <h4>Legal</h4>
                <ul class="footer-links">
                    <li><a href="#">PECA 2016</a></li>
                    <li><a href="#">Cyber Laws</a></li>
                    <li><a href="#">International Cooperation</a></li>
                    <li><a href="#">Case Studies</a></li>
                    <li><a href="#">Legal Rights</a></li>
                </ul>
            </div>
        </div>

        <div class="footer-bottom">
            <p>&copy; 2024 Cyber Jurist. All rights reserved. | <span class="software-house">Powered by Zareen Software House</span> | Fighting E-Crimes with IT+Law Power</p>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        document.querySelector('.mobile-menu-btn').addEventListener('click', function() {
            document.querySelector('.nav-menu').classList.toggle('show');
        });

        // Smooth Scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    document.querySelector('.nav-menu').classList.remove('show');
                }
            });
        });

        // Booking Form Handling with Email Backend
        document.getElementById('consultationForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const submitBtn = document.getElementById('submitBtn');
            const spinner = document.getElementById('loadingSpinner');
            const successMessage = document.getElementById('successMessage');
            
            // Show loading state
            submitBtn.disabled = true;
            submitBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Submitting...';
            spinner.style.display = 'block';
            
            const formData = {
                name: document.getElementById('fullName').value,
                phone: document.getElementById('phone').value,
                email: document.getElementById('email').value,
                caseType: document.getElementById('caseType').value,
                query: document.getElementById('query').value,
                timestamp: new Date().toLocaleString()
            };
            
            try {
                // Send form data to Formspree
                const response = await fetch('https://formspree.io/f/xjvnerjg', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        _subject: `New Consultation Request - ${formData.name}`,
                        _replyto: formData.email || 'cyberjurist.pk@gmail.com',
                        name: formData.name,
                        phone: formData.phone,
                        email: formData.email,
                        caseType: formData.caseType,
                        query: formData.query,
                        timestamp: formData.timestamp
                    })
                });
                
                if (response.ok) {
                    // Show success message
                    successMessage.style.display = 'block';
                    submitBtn.style.display = 'none';
                    
                    // Scroll to success message
                    successMessage.scrollIntoView({ behavior: 'smooth' });
                    
                    // Reset form
                    this.reset();
                    
                    console.log('Form submitted successfully:', formData);
                } else {
                    throw new Error('Form submission failed');
                }
                
            } catch (error) {
                console.error('Error submitting form:', error);
                alert('Sorry, there was an error submitting your form. Please try again or contact us directly.');
            } finally {
                // Reset button state
                submitBtn.disabled = false;
                submitBtn.innerHTML = '<i class="fas fa-paper-plane"></i> Submit for Free Consultation';
                spinner.style.display = 'none';
            }
        });

        // FAQ Accordion
        document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
                const item = question.parentElement;
                item.classList.toggle('active');
            });
        });

        // Animated Counter
        function animateCounter() {
            const counters = document.querySelectorAll('.stat-number');
            counters.forEach(counter => {
                const target = +counter.getAttribute('data-count');
                const count = +counter.innerText;
                if (count < target) {
                    counter.innerText = Math.ceil(count + (target / 100));
                    setTimeout(animateCounter, 20);
                } else {
                    counter.innerText = target;
                }
            });
        }

        // Start counter when section is visible
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateCounter();
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.5 });

        observer.observe(document.querySelector('.hero'));

        // PWA Installation
        let deferredPrompt;
        const installPrompt = document.getElementById('installPrompt');
        
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            installPrompt.style.display = 'block';
        });

        installPrompt.addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') {
                    installPrompt.style.display = 'none';
                }
                deferredPrompt = null;
            }
        });

        // Floating cards animation
        document.addEventListener('mousemove', (e) => {
            const cards = document.querySelectorAll('.floating-card');
            cards.forEach((card, index) => {
                const speed = (index + 1) * 0.5;
                const x = (window.innerWidth - e.pageX * speed) / 100;
                const y = (window.innerHeight - e.pageY * speed) / 100;
                card.style.transform = `translateX(${x}px) translateY(${y}px)`;
            });
        });
    </script>
</body>
</html>
