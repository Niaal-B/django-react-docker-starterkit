Django + React Starter Kit
<div align="center">
Show Image
Show Image
Show Image
Show Image
Show Image
Show Image
</div>
A minimal starter project to build a full-stack web app using Django (Dockerized backend) and React with TypeScript (frontend outside Docker). This setup lets you quickly develop your backend API and React frontend separately with easy local development and Docker deployment.
📋 Table of Contents

Features
Project Structure
Getting Started

Prerequisites
Backend Setup
Frontend Setup


Example API Usage
How to Add New Features
Troubleshooting
License

✨ Features

Django backend running inside Docker with Gunicorn and PostgreSQL
Static files served via Nginx
React frontend (TypeScript) running locally and communicating with backend API
Example API endpoint and React fetch call demonstrating integration
Ready for expansion with authentication, REST APIs, and frontend routes

📁 Project Structure
├── backend/        # Django backend app & Docker setup
├── frontend/       # React (TypeScript) app (run locally)
├── nginx/          # Nginx config for serving static files & proxy
├── docker-compose.yml  # Compose file for backend, db, nginx
└── README.md       # Project documentation
🚀 Getting Started
Prerequisites

Docker & Docker Compose installed
Node.js and npm/yarn installed (for React frontend)

Backend Setup (Dockerized Django)

Clone the repository:
bashgit clone https://github.com/yourusername/django-react-starter.git
cd django-react-starter

Create .env file in the backend directory:
bashcd backend
Create a .env file with your database variables:
DB_NAME=yourdbname
DB_USER=yourdbuser
DB_PASSWORD=yourdbpassword

Build and start backend services:
bashdocker-compose up --build

Run Django migrations (inside the container):
bashdocker exec -it django_app python manage.py migrate

Collect static files:
bashdocker exec -it django_app python manage.py collectstatic --noinput


Your Django backend will be running at: http://localhost:8000
Frontend Setup (React TSX)

Navigate to frontend folder:
bashcd ../frontend

Install dependencies:
bashnpm install
# or
yarn install

Start React development server:
bashnpm start
# or
yarn start


Your React app will run at: http://localhost:3000 and communicate with Django backend API.
🌐 Example API Usage
The starter kit includes a sample integration:

Django provides a sample API endpoint: http://localhost:8000/api/hello/
React fetches this endpoint and displays the message

Example API call in React:
typescript// Sample API call in React component
useEffect(() => {
  const fetchData = async () => {
    try {
      const response = await fetch('http://localhost:8000/api/hello/');
      const data = await response.json();
      setMessage(data.message);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  };
  
  fetchData();
}, []);
🔧 How to Add New Features

Add Django apps inside backend/ with your API logic
Extend React components inside frontend/src
Connect new APIs by updating React fetch URLs to point to backend
Consider adding authentication and routing next
For production deployment, you may want to build the React app and serve it through Nginx

❓ Troubleshooting

Make sure Docker containers are running (docker ps)
Ensure React calls use correct backend URL (http://localhost:8000)
Collect static files when adding/changing static assets in Django
Clear browser cache if styles or API responses don't update
Check Docker logs for errors: docker-compose logs
If you encounter CORS issues, ensure your Django settings include proper CORS configuration

📄 License
MIT License © 2025 Nihal