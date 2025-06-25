# NetNest E-veikala projekts

## Projekta uzstādīšana lokāli

### 1. Projekta lejupielāde

```bash
git clone --recurse-submodules https://github.com/rendijsb/eksamens.git
cd eksamens
```

### 2. Docker konteineru palaišana

```bash
docker-compose up -d
```

### 3. Backend uzstādīšana

Ieiet backend konteinerā:
```bash
docker exec -it eksamens-api-1 bash
```

Instalēt dependences:
```bash
composer install
```

Izveidot vides konfigurācijas failu(.env iekš eksamens_backend mapes un failu nepieciešams sakonfigurēt ar saviem datiem):
```bash
cat > .env << 'EOF'
```
```bash
APP_NAME=NetNest
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost:8000

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=api
DB_USERNAME=root
DB_PASSWORD=root

BROADCAST_DRIVER=log
CACHE_DRIVER=file
FILESYSTEM_DRIVER=local
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_ENCRYPTION=
MAIL_FROM_ADDRESS=""
MAIL_FROM_NAME=""

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=

STRIPE_KEY=
STRIPE_SECRET=
EOF
```

Ģenerēt aplikācijas atslēgu:
```bash
php artisan key:generate
```

Palaist migrācijas:
```bash
php artisan migrate
```

Palaist seeders (izveidot admin lietotāju):
```bash
php artisan db:seed
```

Izveidot storage symlink:
```bash
php artisan storage:link
```

Iziet no konteinera:
```bash
exit
```

### 4. Frontend uzstādīšana

Ieiet frontend konteinerā:
```bash
docker exec -it eksamens-frontend-1 sh
```

Instalēt dependences:
```bash
npm install
```

Iziet no konteinera:
```bash
exit
```

## Piekļuves punkti

Pēc veiksmīgas uzstādīšanas, aplikācija būs pieejama šādos endpointos:

- **Frontend (Angular)**: http://localhost:4200
- **Backend API (Laravel)**: http://localhost:8000
- **phpMyAdmin**: http://localhost:8080
- **Datubāze (MySQL)**: localhost:3306

## Admin pieejas dati

- **E-pasts:** admin@example.com
- **Parole:** password

## Alternatīva (Production)

Ja nevēlaties uzstādīt lokāli, varat izmantot production versiju:

https://net-nest.up.railway.app/

## Problēmu risināšana

### Ja konteineri neieslēdzas:
```bash
docker-compose down
docker-compose up -d
```
