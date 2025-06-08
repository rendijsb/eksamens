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

Kopēt vides konfigurāciju:
```bash
cp .env.example .env
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

### 4. Frontend uzstādīšana

Ieiet frontend konteinerā:
```bash
docker exec -it eksamens-frontend-1 bash
```

Instalēt dependences:
```bash
npm install
```

## Alternatīva

https://net-nest.up.railway.app/

## Admin pieejas dati

- **E-pasts:** admin@example.com
- **Parole:** password

## Datubāzes konfigurācija

Datubāzes savienojuma iestatījumi backend `.env` failā:

```env
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=api
DB_USERNAME=root
DB_PASSWORD=root
```
