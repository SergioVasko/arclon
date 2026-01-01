# AI Agent Chatbot SaaS – Laravel 12 + Gemini API + RAG

[![Laravel 12](https://img.shields.io/badge/Laravel-12.x-red.svg)](https://laravel.com)
[![Gemini API](https://img.shields.io/badge/Powered%20by-Gemini%20API-blue)](https://ai.google.dev)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4.svg)](https://www.php.net)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Arclon** is a modern multi-tenant **AI Chatbot SaaS** platform that allows users to create intelligent, context-aware chatbots for their websites and businesses — powered by **Google Gemini API** and **Retrieval-Augmented Generation (RAG)** technology.

Built from scratch with **Laravel 12** — clean architecture, real-world SaaS features and modern development practices.

> Project developed while following the Udemy course:  
> **Build AI Agent Chatbot SaaS with Laravel 12 & Gemini API**  
> (40+ hours • Last updated September 2025)

## ✨ Key Features

- **Multi-tenant SaaS** architecture with separate **user** and **admin** roles
- Secure authentication including **Two-Factor Authentication (2FA)**
- Modern **admin dashboard** with full CRUD operations for:
    - Users
    - Subscription plans & pricing
    - Payments
    - Content (blogs, etc.)
- Complete **subscription & pricing plans** system with manual payment status management & approval
- **Knowledge Base** management — upload documents → automatic text chunking & embedding
- Full **Google Gemini API** integration (text generation + embeddings)
- Advanced **RAG pipeline** — Retrieval-Augmented Generation for highly relevant, context-aware chatbot responses
- Background **queue job processing** for document chunking, embedding generation & knowledge processing
- Powerful **Chatbot builder** — create, customize, store & manage multiple chatbots per user
- Beautiful **embeddable frontend chatbot widget** (pure HTML + JavaScript) with customizable appearance and easy embed code
- **Company website builder** — users can create simple websites and integrate their AI chatbots directly
- **Admin AI Blog Generator** — generate SEO-optimized, high-quality blog posts using Gemini API
- Fully responsive design using **Bootstrap 5** + custom modern frontend & backend themes
- **Docker-ready** single-container development environment

### Prerequisites

- PHP ≥ 8.2
- Composer
- Node.js + NPM (for assets)
- Laravel 12 compatible local server (Laravel Sail, Valet, Herd, XAMPP/WAMP)
- **Google Gemini API Key** (get it from https://aistudio.google.com/app/apikey)

## 🛠 Technology Stack

| Category           | Technology/Tools                                                    |
|--------------------|---------------------------------------------------------------------|
| Backend            | Laravel 12 • PHP 8.2+                                               |
| Database           | MySQL (with proper relationships: User ↔ Chatbots ↔ Knowledge)      |
| AI Engine          | Google Gemini API (generative + embeddings)                         |
| Frontend           | Blade • Bootstrap 5 • Vanilla JS widget                             |
| Queue & Processing | Laravel Queues (database driver)  + Jobs (for chunking & embedding) |
| Authentication     | Laravel Breeze + custom 2FA                                         |
| Development        | Docker (nicecollab/php8.2-apache-mysql)                             |
| Asset Compilation  | Vite                                                                |
| Other              | Composer, Laravel Mix, Cron jobs (optional)                         |


## 🚀 Quick Start (Docker – Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/SergioVasko/arclon.git
cd arclon

# 2. Copy environment file
cp .env.example .env

# 3. (Important!) Add your Gemini API key
#    nano .env
#    GEMINI_API_KEY=your-actual-key-from-ai.google.dev

# 4. Start the application (first run: 5–15 minutes)
docker compose up -d --build

# 5. Follow the logs to see progress
docker compose logs -f

# 6. Open in browser
http://localhost:8080
```

## Default credentials (if database was seeded):

- Admin: admin@arclon.app / password123!
- Test User: user@arclon.app / password123!

## 📋 Recommended docker-compose.yml

```yaml
version: '3.9'

services:
  app:
    image: nicecollab/php8.2-apache-mysql:latest
    container_name: arclon
    restart: unless-stopped
    ports:
      - "8080:80"
    volumes:
      - .:/var/www/html
    environment:
      MYSQL_ROOT_PASSWORD: rootsecret
      MYSQL_DATABASE: arclon
      MYSQL_USER: laravel
      MYSQL_PASSWORD: laravel123

      APP_NAME="Arclon"
      APP_ENV=local
      APP_DEBUG=true
      APP_URL=http://localhost:8080

      DB_CONNECTION=mysql
      DB_HOST=127.0.0.1
      DB_PORT=3306
      DB_DATABASE=arclon
      DB_USERNAME=laravel
      DB_PASSWORD=laravel123

      QUEUE_CONNECTION=database
      GEMINI_API_KEY=your-real-gemini-api-key-here

    command: >
      bash -c "
        service mysql start &&
        sleep 5 &&
        composer install --no-interaction --prefer-dist --optimize-autoloader &&
        php artisan key:generate --force &&
        php artisan migrate:fresh --seed --force &&
        php artisan storage:link &&
        apache2-foreground
      "
  ```

## 🛠 Useful Commands
  
```bash
# Enter the container
docker compose exec app bash

# Run artisan commands
docker compose exec app php artisan queue:work --tries=3
docker compose exec app php artisan cache:clear
docker compose exec app php artisan optimize:clear

# Check MySQL
docker compose exec app mysql -u laravel -plaravel123 arclon

# Restart everything
docker compose down && docker compose up -d
```

## 📂 Project Structure Highlights

```text
app/
├── Http/Controllers/
│   ├── Admin/              # Admin panel controllers
│   ├── User/               # User dashboard
│   └── Frontend/           # Public website + widget
├── Jobs/                   # Document chunking & embedding jobs
├── Models/
│   ├── Chatbot.php
│   ├── Knowledge.php
│   ├── Message.php
│   └── Subscription.php
├── Services/
│   ├── GeminiService.php   # Main Gemini API wrapper
│   └── RagService.php      # Core RAG logic
resources/views/
├── admin/
├── user/
├── frontend/
└── components/
public/js/
└── chatbot-widget.js       # The magic embeddable widget
```

## 🎯 Who is this for?
- Laravel developers who want to master AI integration & SaaS architecture
- Entrepreneurs looking to build or launch AI chatbot services
- Students & portfolio builders wanting a serious, modern full-stack project
- Anyone interested in RAG, Gemini API, multi-tenancy, and queue processing

## 📜 License
MIT License
Use it freely for learning, personal projects, or commercial purposes
(please respect original course terms and Google Gemini API usage policies)

## ❤️ Credits & Inspiration
Built with passion while following the outstanding Udemy course:
Build AI Agent Chatbot SaaS with Laravel 12 & Gemini API
Special thanks to the Laravel community, Google AI team, and everyone who shares knowledge!

## ⭐ If you like this project — give it a star!
It really helps spread the word about open-source AI + Laravel projects.

Happy building! 🚀

January 2026
