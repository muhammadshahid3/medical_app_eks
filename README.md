# MediBook - Doctor Appointment App

React (Frontend) + .NET 8 Web API (Backend) + MySQL, sab Docker Compose se.

## Run (Docker)

```bash
docker compose up --build
```

| Service  | URL                           |
|----------|-------------------------------|
| Website  | http://localhost:3000         |
| API docs | http://localhost:8080/swagger |
| MySQL    | localhost:3307 (root / rootpassword) |

## Kaise use karein

1. Home page ke navbar mein **Login** aur **Sign up** buttons hain, dono form (popup) kholte hain.
2. Sign up form mein **Patient / Doctor** chun sakte hain. Hero section ke "I'm a Patient" / "I'm a Doctor" buttons bhi seedha signup form kholte hain.
3. **Doctor**: education + specialization likhein -> dashboard par slots add karein, aur dekhein kis patient ne book kiya.
4. **Patient**: doctor search karein -> "View slots" -> "Book". "My appointments" mein cancel bhi ho sakta hai.

## Folders

```
Backend/    .NET 8 API (JWT login, EF Core + MySQL)
Frontend/   React + Vite (nginx se serve hota hai)
docker-compose.yml
```

## API endpoints

| Method | URL | Kaun |
|--------|-----|------|
| POST | /api/auth/signup, /api/auth/login | sab |
| GET | /api/doctors | login user |
| GET | /api/doctors/{id}/slots | login user |
| PUT | /api/doctors/me | Doctor |
| GET/POST | /api/slots/mine, /api/slots | Doctor |
| DELETE | /api/slots/{id} | Doctor |
| POST | /api/appointments | Patient |
| GET | /api/appointments/mine | Patient |
| DELETE | /api/appointments/{slotId} | Patient |

## Bina Docker ke (development)

```bash
# 1) sirf database
docker compose up db -d

# 2) backend (Backend/ folder mein) - http://localhost:5xxx par chalega
dotnet run
# agar port 8080 nahi hai to frontend ko batayein:
#   VITE_PROXY_TARGET=http://localhost:5xxx npm run dev

# 3) frontend (Frontend/ folder mein) - http://localhost:5173
npm install
npm run dev
```

## Production se pehle

`docker-compose.yml` mein `Jwt__Key` aur MySQL password zaroor badal dein.
# medical_app_eks
