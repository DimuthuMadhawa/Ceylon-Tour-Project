<div align="center">

# 🌴 Ceylon Tour.com - Sri Lanka Travel Experience Platform

[![PHP Version](https://img.shields.io/badge/PHP-7.4%2B-blue.svg)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-orange.svg)](https://www.mysql.com/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

**A comprehensive tourism management web application for Sri Lankan tour packages, bookings, and customer engagement.**

[Features](#-features) • [Tech Stack](#-tech-stack) • [Installation](#-installation) • [Usage](#-usage) • [Screenshots](#-screenshots) • [API Documentation](#-api-documentation)

</div>

---

## 📋 Table of Contents

- [About The Project](#-about-the-project)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Usage](#-usage)
- [Screenshots](#-screenshots)
- [API Endpoints](#-api-endpoints)
- [Database Schema](#-database-schema)
- [Security](#-security)
- [Performance Optimization](#-performance-optimization)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)
- [Acknowledgments](#-acknowledgments)

---

## 🎯 About The Project

**Ceylon Tour.com** is a full-stack web application designed to showcase Sri Lankan tourism packages, handle bookings, manage customer inquiries, and collect feedback. The platform features a modern, responsive UI plus server-side PHP logic to process bookings and messages.

- **Live Demo**: https://ceylontour.infinityfreeapp.com/  (please verify this URL)

### 🎨 Design Philosophy

- **User-Centric Design**: Intuitive navigation and mobile-responsive interface
- **Performance First**: Optimized loading times with caching and compression
- **Security by Default**: Input validation, SQL injection protection, and secure configurations
- **SEO Optimized**: Structured data, meta tags, and semantic HTML
- **Accessibility**: ARIA labels, keyboard navigation, and WCAG compliance

---

## ✨ Key Features

### 🏖️ Tour Management
- Multiple tour package showcases (Beach holidays, Cultural tours, Wildlife safaris)
- Detailed package information with image galleries
- Interactive booking system with date selection
- Real-time availability checking
- Customizable tour itineraries

### 📞 Customer Engagement
- Contact form with email notifications
- Customer feedback and rating system
- WhatsApp integration for instant messaging
- Live chat support (Tidio integration) — optional
- Newsletter subscription

### 🎨 User Experience
- Dark mode toggle
- Responsive mobile-first design
- Image sliders and galleries (Swiper.js)
- Smooth animations and transitions
- Package filtering and search functionality
- FAQ accordion sections

### 🔐 Security Features
- SQL injection prevention (prepared statements)
- XSS protection with input sanitization
- CSRF protection (recommend adding tokens)
- Secure environment variable management
- Apache security configurations (.htaccess)
- Rate limiting ready (implementation recommended)

### 📧 Email System
- Automated booking confirmations
- Contact form notifications
- Feedback acknowledgments
- HTML email templates
- SMTP integration (Gmail/Custom)

### 📊 Analytics & Tracking
- WhatsApp button click tracking
- Form submission logging
- User behavior analytics ready (add tracking)
- IP address and user agent logging (check privacy compliance)

---

## 🛠️ Tech Stack

### Backend
| Technology | Version | Purpose |
|------------|---------|---------|
| PHP        | 7.4+ (8.0+ recommended) | Server-side logic |
| MySQL      | 5.7+   | Database management |
| Apache     | 2.4+   | Web server |
| Composer   | 2.x    | Dependency manager |

PHP libraries:
- PHPMailer v6.x - SMTP email sending
- MySQLi - Database connectivity

### Frontend
- HTML5, CSS3, JavaScript (ES6+)
- Swiper.js v12 - Image sliders
- Font Awesome v6 - Icons
- Google Fonts (Poppins)

### Database
MySQL schema (example tables)
- contact_messages      — Customer inquiries
- bookings              — Tour reservations
- customer_feedback     — Reviews and ratings

### Development Tools
- Git
- Composer
- VS Code
- Apache/XAMPP (for local development)

---

## 🏗️ Architecture

Project structure (simplified)
```
Ceylon-Tour-Project/
├── backend/
│   ├── api/
│   ├── includes/
│   └── models/
├── config/
├── frontend/
│   ├── assets/
│   └── views/
├── public/                  # Web root
├── vendor/
├── screenshot/
├── storage/
├── .env.example
├── .htaccess
├── composer.json
└── README.md
```

Design pattern:
- MVC-inspired separation of concerns
- Front controller: public/index.php
- Service layer: backend/api/

---

## 🚀 Getting Started

### Prerequisites
- PHP >= 7.4 (recommended 8.0+)
- MySQL >= 5.7 or MariaDB >= 10.3
- Apache 2.4+ with mod_rewrite enabled
- Composer
- Git

Check versions:
```bash
php -v
mysql --version
```

### Installation

1) Clone the repository (corrected to your repo owner)
```bash
git clone https://github.com/DimuthuMadhawa/Ceylon-Tour-Project.git
cd Ceylon-Tour-Project
```

2) Install PHP dependencies
```bash
composer install
```

3) Copy and edit environment file
```bash
cp .env.example .env
# Edit .env with your credentials
```

Example .env entries:
```env
DB_HOST=localhost
DB_NAME=tour_database
DB_USER=your_db_user
DB_PASS=your_secure_password

SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_SECURE=tls
SMTP_USERNAME=your_email@gmail.com
SMTP_PASSWORD=your_gmail_app_password
FROM_EMAIL=your_email@gmail.com
FROM_NAME="Ceylon Tour.com"

APP_ENV=development
DEBUG_MODE=true
```

Note: For Gmail SMTP use an App Password (enable 2FA → App Passwords).

4) Create database
```sql
CREATE DATABASE tour_database CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'tour_user'@'localhost' IDENTIFIED BY 'your_secure_password';
GRANT ALL PRIVILEGES ON tour_database.* TO 'tour_user'@'localhost';
FLUSH PRIVILEGES;
```

5) Import schema
```bash
mysql -u your_db_user -p tour_database < backend/includes/contact_table.sql
mysql -u your_db_user -p tour_database < backend/includes/customer_feedback_table.sql
```
(Or use setup_database.php if available.)

6) Set file permissions (Linux/Mac)
```bash
chmod -R 755 storage/
chmod 600 .env
```

7) Optional: Apache VirtualHost for local development (adjust paths)
```apache
<VirtualHost *:80>
    ServerName ceylontour.local
    DocumentRoot "/path/to/Ceylon-Tour-Project/public"

    <Directory "/path/to/Ceylon-Tour-Project/public">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
Add to hosts file:
```
127.0.0.1  ceylontour.local
```

### Test email
Open the included email test script (if provided):
http://localhost/backend/includes/test_email.php
(Verify this file exists before using.)

---

## 💻 Usage

Start with XAMPP/WAMP or PHP built-in server:

Using built-in server:
```bash
cd public
php -S localhost:8000
```
Visit: http://localhost:8000

Common operations:
- Test contact form — submit and verify database/email
- Make a booking — check confirmation email
- Submit feedback — verify review stored in DB

---

## 📸 Screenshots

Place app screenshots in /screenshot and reference them here. Example:
![Homepage](screenshot/home.png)
![Adventure Packages](screenshot/adventure.png)

(Replace these with actual PNG/JPG files in the screenshot directory.)

---

## 🔐 Security

Recommended implemented practices:
- Input validation and sanitization (htmlspecialchars, filter_var)
- Prepared statements (parameterized queries)
- Use HTTPS (TLS)
- Add CSRF tokens for forms
- Limit rate for public endpoints
- Keep dependencies and PHP up to date

Example XSS prevention in PHP:
```php
$clean_input = htmlspecialchars($input, ENT_QUOTES, 'UTF-8');
```

Example prepared statement:
```php
$stmt = $conn->prepare("INSERT INTO bookings (name,email,phone) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $name, $email, $phone);
$stmt->execute();
```

Protect .env from public access (Apache 2.4+):
```apache
<FilesMatch "^\.env$">
    Require all denied
</FilesMatch>
```

---

## 🧭 Coding Standards & Contribution

- PHP: PSR-12
- JS: ES6+ (use ESLint)
- CSS: BEM preferred
- Commits: Conventional Commits recommended

If you want a CONTRIBUTING.md and ISSUE templates, add them to the repo.

---

## 📄 License

Add a LICENSE file to the repository (for example MIT). If you want, I can add a standard MIT license file for you.

---

## 🔗 Project Links

- Repository: https://github.com/DimuthuMadhawa/Ceylon-Tour-Project
- Live Demo: https://ceylontour.infinityfreeapp.com/  (please verify)
- Issues: https://github.com/DimuthuMadhawa/Ceylon-Tour-Project/issues

---

## 🙏 Acknowledgments

- PHPMailer — Email functionality
- Swiper.js — Image sliders
- Font Awesome — Icons
- Google Fonts — Typography
- Resources: PHP: The Right Way, MDN, OWASP

---
