# Little Lemon — Restaurant Booking App

End-to-end Django web app for a restaurant: users register and log in, browse the menu and book a table. It ships both server-rendered pages and a REST API.

> Final capstone of the **Meta Back-End Developer Professional Certificate**.

## Features

- **Web pages** (Django templates): home, about, menu, menu item detail, booking form, reservations by date, register / login / logout.
- **REST API** (Django REST Framework): menu CRUD, bookings, user registration.
- **Token authentication** (DRF token + Djoser).
- **Permissions**: anyone can read the menu; only staff can create, edit or delete items (`IsAdminOrReadOnly`).
- **MySQL** database through the Django ORM.
- **Unit tests** for models and queries.
- Git flow with a `develop` branch merged into `main` through pull requests.

## Tech stack

Python · Django · Django REST Framework · Djoser · MySQL · HTML/CSS templates

## Run locally

Requirements: Python 3.12+ and a local MySQL server with a database named `little_lemon`.

```bash
git clone https://github.com/karencl516/little_lemon.git
cd little_lemon/littlelemon
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
export DB_PASSWORD=your_mysql_password
python manage.py migrate
python manage.py runserver
```

Run the tests:

```bash
python manage.py test
```

## API endpoints

Base URL: `http://127.0.0.1:8000`

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/api/menu-items/` | List menu items | Public |
| GET | `/api/menu-items/{id}/` | Menu item detail | Public |
| POST / PUT / DELETE | `/api/menu-items/` · `/api/menu-items/{id}/` | Create, edit, delete items | Staff |
| GET | `/api/bookings/?date=YYYY-MM-DD` | Bookings for a date | Public |
| POST | `/api/bookings/` | Create a booking | Token |
| POST | `/api/registration/` | Register a user | Public |
| POST | `/api/api-token-auth/` | Get an auth token | Public |

**Create a booking**

```json
POST /api/bookings/
Authorization: Token <your_token>

{
  "name": "Ana",
  "persons": 2,
  "reservation_date": "2030-05-10"
}
```

## Web pages

| Route | Page |
|---|---|
| `/` | Home |
| `/about/` | About |
| `/menu/` | Menu |
| `/book/` | Booking form |
| `/reservations/` | Reservations by date |
| `/register/` · `/login/` | Account |

## Author

**Karen Cañón** — Backend Developer · [LinkedIn](https://www.linkedin.com/in/karencl16) · [GitHub](https://github.com/karencl516)
