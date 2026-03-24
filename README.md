# Shoe Store WebApp

[![Codacy Badge](https://app.codacy.com/project/badge/Grade/cf689804086742eb9c888b1bf7611b7a)](https://app.codacy.com/gh/f0rzzzzzz/Shoe_store/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_grade)

Веб-приложение для управления товарами обувного магазина. Проект включает клиентскую часть на React, сервер на FastAPI, работу с товарами и заказами, а также REST API для основных сценариев.

## Содержание

- [Стек технологий](#стек-технологий)
- [Основные возможности](#основные-возможности)
- [Визуальные правила каталога](#визуальные-правила-каталога)
- [Структура проекта](#структура-проекта)
- [Требования](#требования)
- [Быстрый старт](#быстрый-старт)
- [Проверка кода](#проверка-кода)
- [Демо-доступы](#демо-доступы)
- [API](#api)

## Стек технологий

| Слой | Технологии |
|---|---|
| Frontend | React + Vite |
| Backend | FastAPI + Uvicorn |
| Данные | Импорт товаров из `import/Tovar.xlsx` |
| Изображения | Раздаются backend по пути `/images/*` |

## Основные возможности

- Авторизация по ролям: администратор, менеджер, клиент, гость.
- Каталог товаров с ценой, скидкой, остатком и фотографией.
- Поиск по всем текстовым полям и фильтрация по поставщику.
- Сортировка по остатку для менеджера и администратора.
- Добавление, редактирование и удаление товаров для администратора.
- Просмотр блока заказов для менеджера и администратора.
- Добавление, редактирование и удаление заказов для администратора.
- REST API для авторизации, товаров и заказов.
- Проверка качества кода через ESLint для frontend и Flake8 для backend.

## Визуальные правила каталога

| Условие | Отображение |
|---|---|
| Товара нет на складе | Голубой фон |
| Скидка больше 15% | Зеленый фон (`#2E8B57`) |
| На товар действует скидка | Исходная цена отображается зачеркнутой |

## Структура проекта

```text
webapp/
  backend/
	app/
	  main.py
	  schemas.py
	  store.py
	requirements.txt
	.flake8
  frontend/
	src/
	  components/
		LoginPanel.jsx
		ProductTable.jsx
		ProductForm.jsx
		OrdersTable.jsx
		OrderForm.jsx
	  App.jsx
	  api.js
	  styles.css
	eslint.config.js
	package.json
  README.md
```

## Требования

- Python 3.11+
- Node.js 18+
- npm

## Быстрый старт

### 1. Установка зависимостей

Если вы находитесь в корне проекта:

Backend:

```powershell
cd webapp/backend
python -m pip install -r requirements.txt
```

Frontend:

```powershell
cd webapp/frontend
npm install
```

### 2. Запуск приложения

Откройте два отдельных терминала.

Терминал 1, backend:

```powershell
cd webapp/backend
python -m uvicorn app.main:app --reload --port 8000
```

Терминал 2, frontend:

```powershell
cd webapp/frontend
npm run dev -- --host 127.0.0.1 --port 5173
```

### 3. Открыть в браузере

- Frontend: http://127.0.0.1:5173
- Backend API docs: http://127.0.0.1:8000/docs

## Проверка кода

Frontend:

```powershell
cd webapp/frontend
npm run lint
```

Backend:

```powershell
cd webapp/backend
flake8 app/
```

## Демо-доступы

| Роль | Логин | Пароль |
|---|---|---|
| Администратор | admin@shop.local | admin1 |
| Менеджер | manager@shop.local | manager1 |
| Клиент | client@shop.local | client1 |
| Гость | — | — |

## API

| Метод | Endpoint | Назначение |
|---|---|---|
| `POST` | `/auth/login` | Авторизация пользователя |
| `GET` | `/products` | Получение списка товаров |
| `POST` | `/products` | Создание товара |
| `PUT` | `/products/{article}` | Обновление товара |
| `DELETE` | `/products/{article}` | Удаление товара |
| `GET` | `/orders` | Получение списка заказов |
| `POST` | `/orders` | Создание заказа |
| `PUT` | `/orders/{order_id}` | Обновление заказа |
| `DELETE` | `/orders/{order_id}` | Удаление заказа |
