Restaurant Order Trends – Full Stack Project
Overview

This project provides a full-stack analytics dashboard for restaurant orders, built with:

Backend: Laravel (PHP)

Frontend: Next.js (React, App Router)

Database: MySQL or PostgreSQL

The system includes:

Restaurant listing with search, filter, and pagination

Per-restaurant analytics:

Daily orders count

Daily revenue

Average order value

Peak order hour per day

Top restaurants by revenue for a given date range

Filters for date, order amount, and hours

Tech Stack
Layer	Technology
Backend API	Laravel 10+
Frontend UI	Next.js 14+ (App Router)
Database	MySQL or PostgreSQL
Charts	Recharts
Cache	Redis (optional)
Project Structure
restaurant-dashboard/
├─ backend/               # Laravel API
│  ├─ app/
│  ├─ database/
│  │  └─ seeders/data/
│  │     ├─ restaurants.json
│  │     └─ orders.json
│  ├─ artisan
│  └─ .env.example
├─ frontend/              # Next.js frontend
│  ├─ app/
│  ├─ package.json
│  └─ next.config.js
└─ run.sh                  # Optional script to start everything

Installation

Follow these steps to set up and run the project locally.

1. Clone the repository
git clone https://github.com/your-username/restaurant-dashboard.git
cd restaurant-dashboard

2. Backend Setup (Laravel)
Install PHP dependencies
cd backend
composer install

Create .env file
cp .env.example .env

Update .env with database credentials

Example for MySQL:

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=restaurant_db
DB_USERNAME=root
DB_PASSWORD=

Generate application key
php artisan key:generate

Run migrations and seed with sample data

Make sure the provided restaurants.json and orders.json are in:

backend/database/seeders/data/


Run:

php artisan migrate:fresh --seed --class=JsonSeeder

Start the backend server
php artisan serve --port=8000


Backend API will be available at:
http://127.0.0.1:8000

3. Frontend Setup (Next.js)

Open a new terminal and navigate to the frontend folder:

cd frontend

Install Node.js dependencies
npm install

Create .env.local file
echo "NEXT_PUBLIC_API_BASE=http://127.0.0.1:8000/api" > .env.local

Start the frontend
npm run dev


Frontend will be available at:
http://localhost:3000

4. Accessing the Application

Frontend UI: http://localhost:3000

Backend API: http://127.0.0.1:8000/api

Sample API Endpoints
Endpoint	Description
/api/restaurants	List restaurants with pagination & search
/api/restaurants/{id}/analytics?start=2025-06-22&end=2025-06-28	Restaurant analytics by date range
/api/top-restaurants?start=2025-06-22&end=2025-06-28&top=3	Top 3 restaurants by revenue
Seed Data Details

The seeder uses two JSON files:

File	Description
restaurants.json	Contains 4 sample restaurants
orders.json	Contains 200 sample orders over 7 days

Ensure both files are in:

backend/database/seeders/data/


Example directory:

database/
└─ seeders/
   └─ data/
      ├─ restaurants.json
      └─ orders.json

Optional: Start Both Backend & Frontend with One Command

We included a helper script run.sh in the root directory.
Make it executable:

chmod +x run.sh


Run:

./run.sh


This will:

Install dependencies for backend and frontend

Run migrations & seed the database

Start both servers

Stopping the Servers

If started manually:

Backend: Press CTRL+C in the terminal running php artisan serve

Frontend: Press CTRL+C in the terminal running npm run dev

If started via run.sh, find and kill both processes:

kill $(pgrep -f "php artisan serve")
kill $(pgrep -f "npm run dev")

Final Notes

Ensure MySQL/PostgreSQL is running before you migrate.

Adjust .env database credentials as needed.

Default ports:

Laravel backend: 8000

Next.js frontend: 3000

CORS is configured to allow http://localhost:3000 by default. If you deploy, update this setting.

Quick Commands Summary
Step	Command
Install backend dependencies	composer install
Setup backend environment	cp .env.example .env
Generate Laravel key	php artisan key:generate
Migrate & seed data	php artisan migrate:fresh --seed --class=JsonSeeder
Start backend server	php artisan serve --port=8000
Install frontend dependencies	npm install
Start frontend server	npm run dev
Run both with one script	./run.sh
Demo Accounts

Sample restaurant IDs to test with:

101

102

103

104
