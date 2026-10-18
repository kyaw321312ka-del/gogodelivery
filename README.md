# GogoDelivery

GogoDelivery is a delivery management system built with Laravel and Vite. It supports multiple user roles for managing shops, assigning orders to bikers, updating delivery statuses, and tracking delivery history across the full workflow.

## Overview

This project is designed for:

- Admins to manage shops, users, bikers, orders, and delivery history
- Staff users to support admin workflows
- Shops to create and review delivery orders
- Bikers to view assigned work and update delivery progress

Core features include:

- Multi-role authentication and role-based access
- Shop and biker management
- Order creation and assignment workflow
- Delivery status tracking (`pending`, `onway`, `failed`, `delivered`)
- Detailed status history logs
- History exports and PDF reports
- Order image and signature handling

## Tech Stack

- PHP 8.3+
- Laravel 13
- Vite for frontend assets
- Dompdf for PDF export
- Eloquent ORM with SQLite/MySQL support

## Project Structure

```bash
app/               # Application logic and models
config/            # Laravel configuration
database/          # Migrations, factories, seeders
public/            # Public entry files
resources/         # Blade templates, CSS, JS, and assets
routes/            # Web routes
storage/           # Cached and generated files
tests/             # Automated tests
```

## Local Setup

1. Install PHP dependencies:

```bash
composer install
```

2. Install frontend dependencies:

```bash
npm install
```

3. Create the environment file and generate the application key:

```bash
cp .env.example .env
php artisan key:generate
```

4. Configure your database connection inside `.env`.

5. Run the migrations and seed the default users:

```bash
php artisan migrate --seed
```

6. Build the frontend assets:

```bash
npm run build
```

7. Start the app:

```bash
php artisan serve
```

Open the site at:

```text
http://localhost:8000
```

## Default Login Accounts

The database seeder creates the following test accounts:

| Role | Username | Email | Password |
| --- | --- | --- | --- |
| Admin | `admin` | `admin@gogodelivery.test` | `admin123` |
| Shop | `shop1` | `shop@gogodelivery.test` | `shop123` |
| Biker | `biker1` | `biker@gogodelivery.test` | `biker123` |

You can log in with either the username or the email address.

## Main Routes

- `/login` — login page
- `/admin/shops` — shop management
- `/admin/users` — user management
- `/admin/bikers` — biker management
- `/admin/history` — delivery tracking and history
- `/shop/orders` — shop order dashboard
- `/bikers/ways` — biker assignment dashboard

## Common Commands

```bash
php artisan migrate
php artisan db:seed
php artisan test
npm run dev
```

## Notes

- The app redirects users to their role-specific dashboard after login.
- Delivery history is recorded in dedicated status history tables.
- PDF exports and order assets are handled through Laravel response logic and the public asset directory.

## License

This project is open source and licensed under the MIT license.
