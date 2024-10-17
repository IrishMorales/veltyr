<div align="center">
<h1>Veltyr</h1>
Open source Laravel 11 boilerplate for admin dashboards optimized for scalablility, complex web apps, offline-first PWAs, & SPAs. Built with Jetstream + Inertia + React.
</div>

### System Requirements
- PostgreSQL 15.x

### First-time Setup
Run the following in your terminal:
```bash
// Start PostgreSQL server as user 'postgres'
psql -U postgres`

// Run commands below inside postgresql server
ALTER USER postgres WITH password 'postgres';
CREATE DATABASE veltyr;
GRANT ALL PRIVILEGES ON DATABASE veltyr TO postgres;
\c veltyr postgres
GRANT ALL ON SCHEMA public TO postgres;
\q

// Install dependencies
composer install
npm install

// Create and update .env settings
cp .env.example .env

// In .env, change APP_TIMEZONE to your timezone if needed

// Generate application key and use it as the value for APP_KEY in .env
php artisan key:generate

// Create symbolic link between storage/app/public and public/storage
php artisan storage:link

// Create and seed tables
php artisan migrate --seed

// Cache config, events, routes, views to bootstrap/cache
php artisan optimize
```

### Starting the development server
Run the following in your terminal:
```bash
composer run dev
http://localhost:8000
```


### Deployment
```
// Open .env in a command-line text editor
vim .env

// Update .env settings to the following
APP_ENV=production
APP_DEBUG=false

// Cache config, events, routes, views to bootstrap/cache
php artisan optimize
```
Once deployed, check `/up`. A 200 HTTP response means the application is working as intended.