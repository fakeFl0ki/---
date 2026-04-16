# Partner Main

Това е проект с:

- frontend: `Vite + React`
- backend: `Express + TypeScript`
- база и аутентикация: `Supabase`

## Какво трябва да изтеглиш

Преди да стартираш сайта, инсталирай:

- `Node.js` LTS, препоръчително версия `20+`
- `npm` (идва с Node.js)
- достъп до `Supabase` проект

Провери версиите:

```bash
node -v
npm -v
```

## Какво трябва да настроиш

Проектът използва два `.env` файла:

- `/.env` за frontend
- `/backend/.env` за backend

### 1. Frontend `.env`

Създай файл `/.env` със следните променливи:

```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_anon_key
VITE_API_BASE_URL=http://localhost:5000/api
```

Забележка:

- `VITE_API_BASE_URL` е препоръчително да е зададен, въпреки че проектът има и fallback към `http://localhost:5000/api`.

### 2. Backend `.env`

Създай файл `/backend/.env` със следните променливи:

```env
PORT=5000
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
```

Важно:

- `SUPABASE_SERVICE_ROLE_KEY` е secret ключ и не трябва да се качва публично.
- frontend използва `publishable/anon key`
- backend използва `service role key`

## Как се инсталира

Инсталирай зависимостите и в двата пакета.

### Frontend

В главната папка:

```bash
npm install
```

### Backend

В папката `backend`:

```bash
cd backend
npm install
cd ..
```

## Как се стартира

Трябват 2 терминала.

### Терминал 1: backend

```bash
cd backend
npm run dev
```

Backend ще тръгне на:

```text
http://localhost:5000
```

### Терминал 2: frontend

От главната папка:

```bash
npm run dev
```

Frontend ще тръгне на:

```text
http://localhost:8080
```

## Проверка дали всичко работи

След стартиране провери:

- frontend: `http://localhost:8080`
- backend health check: `http://localhost:5000/api/health`

Ако backend е свързан правилно към Supabase, `health` endpoint трябва да върне `status: ok`.

## Полезни команди

От главната папка:

```bash
npm run build
npm run test
```

От `backend`:

```bash
npm run build
```

## Чести проблеми

### 1. Липсва връзка със Supabase

Провери дали са попълнени правилно:

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`
- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`

### 2. Frontend работи, но backend не отговаря

Провери дали backend е стартиран с:

```bash
cd backend
npm run dev
```

### 3. Портът е зает

Смени:

- `PORT` в `backend/.env`
- `VITE_API_BASE_URL` в `/.env`, ако backend не е на `5000`

