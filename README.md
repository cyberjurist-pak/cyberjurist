<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber Jurist - Cyber Crime Help Pakistan</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            background: #001F3F;
            color: white;
        }

        /* Header Styles */
        .header {
            background: linear-gradient(135deg, #00264d, #001F3F);
            padding: 60px 20px;
            text-align: center;
            border-bottom: 3px solid #007BFF;
        }

        .logo {
            font-size: 3rem;
            margin-bottom: 15px;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.2rem;
            margin-bottom: 25px;
            opacity: 0.9;
        }

        /* Button Styles */
        .btn {
            display: inline-block;
            background: #007BFF;
            color: white;
            padding: 15px 35px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            margin: 10px;
            cursor: pointer;
            text-decoration: none;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 123, 255, 0.3);
        }

        .btn:hover {
            background: #0056b3;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 123, 255, 0.4);
        }

        /* Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        /* Sections */
        .section {
            background: rgba(255, 255, 255, 0.05);
            padding: 40px;
            margin: 30px 0;
            border-radius: 15px;
            border-left: 5px solid #007BFF;
        }

        .section h2 {
            color: #007BFF;
            margin-bottom: 20px;
            font-size: 1.8rem;
        }

        .section ul {
            list-style: none;
            padding-left: 20px;
        }

        .section li {
            margin: 10px 0;
            padding-left: 25px;
            position: relative;
        }

        .section li:before {
            content: "✓";
            color: #007BFF;
            font-weight: bold;
            position: absolute;
            left: 0;
        }

        /* Contact Section */
        .contact {
            background: linear-gradient(135deg, #00264d, #001F3F);
            padding: 50px 20px;
            text-align: center;
            border-top: 3px solid #007BFF;
        }

        .contact-info {
            font-size: 1.2rem;
            margin: 15px 0;
        }

        .contact-info i {
            color: #007BFF;
            margin-right: 10px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2rem;
            }
            
            .btn {
                padding: 12px 25px;
                font-size: 1rem;
            }
            
            .container {
                padding: 20px 15px;
            }
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header class="header">
        <div class="logo">🛡️</div>
        <h1>CYBER JURIST PAKISTAN</h1>
        <p>Free Cyber Crime Advisory & Legal Help under PECA Act 2016</p>
        <div>
            <a href="#contact" class="btn">📞 Get Free Advisory</a>
            <a href="#courses" class="btn">🎓 View Courses</a>
            <a href="#blog" class="btn">📝 Read Blog</a>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container">
        <!-- Services Section -->
        <section class="section">
            <h2>🛡️ Our Services</h2>
            <ul>
                <li>Free Cyber Crime Consultation & Legal Guidance</li>
                <li>PECA Act 2016 Complete Explanation & Support</li>
                <li>Cybersecurity Training & Professional Courses</li>
                <li>Social Media Harassment & Fake Profile Help</li>
                <li>Financial Fraud & Online Scam Assistance</li>
                <li>Family Cyber Crime Issues Resolution</li>
                <li>Digital Rights Protection & Privacy Security</li>
            </ul>
        </section>

        <!-- CLAP Programs -->
        <section class="section">
            <h2>🌟 CLAP Free Programs</h2>
            <ul>
                <li>Cybersecurity Awareness Workshops</li>
                <li>Digital Literacy Training</li>
                <li>Legal Rights Education</li>
                <li>Community Support Programs</li>
            </ul>
        </section>

        <!-- Courses Section -->
        <section id="courses" class="section">
            <h2>🎓 Cybersecurity Courses</h2>
            <ul>
                <li>Basic Cyber Hygiene - FREE</li>
                <li>Advanced Security Training</li>
                <li>PECA Act Legal Course</li>
                <li>Professional Certifications</li>
            </ul>
            <a href="#" class="btn">Book Your Seat Now</a>
        </section>

        <!-- Blog Section -->
        <section id="blog" class="section">
            <h2>📝 Latest Articles</h2>
            <ul>
                <li>How to Protect Your Social Media Accounts</li>
                <li>Understanding PECA Act 2016 - Complete Guide</li>
                <li>Recent Cyber Crime Cases & Solutions</li>
                <li>Family Privacy Protection Tips</li>
            </ul>
            <a href="#" class="btn">Read Our Blog</a>
        </section>
    </div>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <h2>📞 Contact Us 24/7</h2>
        <div class="contact-info">
            <p>📧 Email: cyberjurist.pk@gmail.com</p>
            <p>📞 Phone: 0317-597-5569 | 0314-507-9122</p>
            <p>🕒 24/7 Free Advisory Available</p>
        </div>
        <p style="margin-top: 20px; opacity: 0.8;">
            &copy; 2024 Cyber Jurist Pakistan. All rights reserved.
        </p>
    </section>

    <script>
        // Simple smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
