# Django + React Starter Kit

A minimal starter project to build a full-stack web app using **Django** (Dockerized backend) and **React (TypeScript)** (frontend outside Docker). This setup lets you quickly develop your backend API and React frontend separately with easy local development and Docker deployment.

---

## Features

* Django backend running inside Docker with Gunicorn and PostgreSQL
* Static files served via Nginx
* React frontend (TypeScript) running locally and communicating with backend API
* Example API endpoint and React fetch call demonstrating integration
* Ready for adding authentication, REST APIs, and frontend routes

---

## Project Structure

```
├── backend/           # Django backend app & Docker setup
├── frontend/          # React (TypeScript) app (run locally)
├── nginx/             # Nginx config for serving static files & proxy
├── docker-compose.yml # Compose file for backend, db, nginx
└── README.md          # Project documentation
```

---

## Getting Started

### Prerequisites

* Docker & Docker Compose installed
* Node.js and npm/yarn installed (for React frontend)

---

### Backend Setup (Dockerized Django)

1. Clone the repo:

```bash
git clone https://github.com/yourusername/django-react-starter.git
cd django-react-starter/backend
```

2. Create `.env` file with your database variables:

```env
DB_NAME=yourdbname
DB_USER=yourdbuser
DB_PASSWORD=yourdbpassword
```

3. Build and start backend services:

```bash
docker-compose up --build
```

4. Run Django migrations (inside the container):

```bash
docker exec -it django_app python manage.py migrate
```

5. Collect static files:

```bash
docker exec -it django_app python manage.py collectstatic --noinput
```

6. Your Django backend will be running at: `http://localhost:8000`

---

### Frontend Setup (React TSX)

1. Navigate to frontend folder:

```bash
cd ../frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start React development server:

```bash
npm start
```

4. Your React app will run at: `http://localhost:3000` and communicate with Django backend API.

---

## Example API Usage

* Django provides a sample API endpoint: `http://localhost:8000/api/hello/`
* React fetches this endpoint and displays the message.

---

## How to Add New Features

* Add Django apps inside `backend/` with your API logic.
* Extend React components inside `frontend/src`.
* Connect new APIs by updating React fetch URLs to point to backend.
* Consider adding authentication and routing next.

---

## Troubleshooting

* Make sure Docker containers are running (`docker ps`).
* Ensure React calls use correct backend URL (`http://localhost:8000`).
* Collect static files when adding/changing static assets in Django.
* Clear browser cache if styles or API responses don't update.

---

## License

MIT License © 2025 Nihal
