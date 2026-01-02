# AI Agent Chatbot SaaS – Laravel 12 + Gemini API + RAG

[![Laravel 12](https://img.shields.io/badge/Laravel-12.x-red.svg)](https://laravel.com)
[![Gemini API](https://img.shields.io/badge/Powered%20by-Gemini%20API-blue)](https://ai.google.dev)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4.svg)](https://www.php.net)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Arclon** is a modern multi-tenant **AI Chatbot SaaS** platform that allows users to create intelligent, 
context-aware chatbots for their websites and businesses — powered by **Google Gemini API** 
and **Retrieval-Augmented Generation (RAG)** technology.

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
- Beautiful **embeddable frontend chatbot widget** (pure HTML + JavaScript) with customizable appearance 
and easy embed code
- **Company website builder** — users can create simple websites and integrate their AI chatbots directly
- **Admin AI Blog Generator** — generate SEO-optimized, high-quality blog posts using Gemini API
- Fully responsive design using **Bootstrap 5** + custom modern frontend & backend themes
- **Docker-ready** multi-container environment setup for easy local setup and consistent development

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
| Development        | Docker                                                              |
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
docker compose -p arclon up -d --build

# 5. Follow the logs to see progress
docker compose logs -f

# 6. Open in browser
http://localhost:8080

# 7. (Optional) Stop the application
docker compose down
```

### Restart the application (when already installed) 
```bash
[ "$(docker ps -q)" ] && docker stop $(docker ps -q); docker compose -f docker-compose.yml start

```

## Default credentials (if database was seeded):

- Admin: admin@arclon.app / password123!
- Test User: user@arclon.app / password123!

## 🛠 Useful Commands
  
```bash
# Enter the container
docker compose exec php bash

# Run artisan commands
docker compose exec php php artisan queue:work --tries=3
docker compose exec php php artisan cache:clear
docker compose exec php php artisan optimize:clear

# Check MySQL
docker compose exec db mysql -u arclon_user -parclon_passweord arclon

# Restart everything
docker compose down && docker compose -p arclon up -d
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
