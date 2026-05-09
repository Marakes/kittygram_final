# Kittygram
 
A pet photo sharing service. Upload your pets, browse others.  
Deployed via GitHub Actions + Docker Compose.
 
## Features
 
- Pet profiles with photos
- REST API (Django REST Framework)
- JWT authentication (Djoser)
- PostgreSQL in production, SQLite for local dev
- Pytest test suite
- Full CI/CD pipeline: test → build → push → deploy

## Tech Stack

- **Python 3.11+**
- **Django 3.2.3**
- **Django REST Framework 3.12.4**
- **Psycopg2-binary 2.9.3**
- **Djoser 2.1.0**
- **Pytest 6.2.4**
- **Docker, Docker Compose, GitHub Actions**

Full list of dependencies: `requirements.txt`

---

## How to Run Locally
 
```bash
# Clone the repository
git clone https://github.com/vaultik/kittygram_final
cd kittygram_final
```
 
Create `.env` in the project root:
 
```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=your_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
 
DEBUG=False
DJANGO_SECRET=your_secret_key
ALLOWED_HOSTS=localhost,127.0.0.1
SQLITE_ON=False
```
 
```bash
# Build and start containers
docker compose -f docker-compose.production.yml up -d --build
 
# Apply migrations and collect static
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
 
Once running:
 
| Service | URL |
|---|---|
| Frontend | http://127.0.0.1:9000 |
| API | http://127.0.0.1:9000/api/ |
| Admin | http://127.0.0.1:9000/admin/ |
 
## CI/CD
 
GitHub Actions pipeline triggered on push to `main`:
 
1. Run tests
2. Build Docker images — `backend`, `frontend`, `gateway`
3. Push images to DockerHub
4. Deploy to server via SSH using Docker Compose

## Author

[github.com/vaultik](https://github.com/vaultik)

