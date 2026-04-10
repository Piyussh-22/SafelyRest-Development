# SafelyRest

A full-stack property booking platform where guests can browse and book houses, hosts can add and manage listings, and admins can oversee the entire platform. Built with a modern production-grade stack including CI/CD, Docker, and automated testing.

**Live App:** [https://safely-rest-frontend.vercel.app](https://safely-rest-frontend.vercel.app)

---

## Repositories

This is the root repository. It contains both services as Git submodules and a shared Docker Compose file for running the full stack locally.

| Service  | Repository                                                               |
| -------- | ------------------------------------------------------------------------ |
| Backend  | [SafelyRest-Backend](https://github.com/Piyussh-22/SafelyRest-Backend)   |
| Frontend | [SafelyRest-Frontend](https://github.com/Piyussh-22/SafelyRest-Frontend) |

---

## Tech Stack

### Backend

- **Language:** TypeScript
- **Runtime:** Node.js with Express v5
- **Database:** MongoDB via Mongoose
- **Auth:** JWT + Google OAuth
- **Storage:** Cloudinary (image uploads)
- **Testing:** Jest + Supertest + MongoDB Memory Server (31 tests)
- **Deploy:** Docker → Render
- **CI/CD:** Github Actions

### Frontend

- **Language:** TypeScript
- **Framework:** React 19 + Vite
- **State:** Redux Toolkit
- **Styling:** Tailwind CSS v4
- **Testing:** Jest + React Testing Library (24 tests)
- **Deploy:** Vercel

---

## Architecture

```
SafelyRest/
├── B-Safely-Rest/        # Backend submodule (Node.js + Express + MongoDB)
├── F-Savely-Rest/        # Frontend submodule (React + Redux + Tailwind)
├── docker-compose.yml    # Runs both services together locally
└── .gitmodules           # Git submodule configuration
```

The backend follows a three-layer architecture — Routes → Controllers → Services. The frontend uses Redux Toolkit slices for state management with a centralized Axios instance handling all API communication.

---

## CI/CD Pipeline

Both services have independent GitHub Actions workflows. Every push to `main` on either repository triggers:

**Backend:**

```
Install → Run 31 tests → Docker build validation → Deploy to Render
```

**Frontend:**

```
Install → Run 24 tests → Vercel build → Deploy to Vercel
```

Deployments are fully automated and blocked if any test fails. Platform auto-deploy is disabled on both Render and Vercel — all deployments are triggered exclusively via GitHub Actions.

---

## Running Locally with Docker

This is the recommended way to run the full stack locally.

**Prerequisites:** Docker Desktop installed and running.

```bash
# Clone the root repo with submodules
git clone --recurse-submodules https://github.com/Piyussh-22/SafelyRest-Development.git
cd SafelyRest-Development

# Add backend environment variables
cp B-Safely-Rest/.env.example B-Safely-Rest/.env
# Fill in your values in B-Safely-Rest/.env

# Start both services
docker-compose up --build
```

| Service  | URL                   |
| -------- | --------------------- |
| Frontend | http://localhost      |
| Backend  | http://localhost:4000 |

To stop:

```bash
docker-compose down
```

---

## Running Services Individually

If you prefer to run without Docker, refer to the individual README files in each submodule:

- [Backend README](https://github.com/Piyussh-22/SafelyRest-Backend#readme)
- [Frontend README](https://github.com/Piyussh-22/SafelyRest-Frontend#readme)

---

## Test Credentials

| Role  | Email                           | Password        |
| ----- | ------------------------------- | --------------- |
| Admin | admin@gmail.com                 | admin@gmail.com |
| Guest | Create via signup               | —               |
| Host  | Create via signup (select Host) | —               |

---

## Features

**Guest**

- Browse and filter house listings by location, price, and amenities
- View house details with photo gallery and availability checker
- Create booking requests and track booking status
- Save and manage favourite properties

**Host**

- Manage property listings with photo uploads
- View and respond to incoming booking requests
- Confirm or reject bookings — overlapping requests are auto-rejected on confirmation

**Admin**

- Platform overview dashboard with stats
- View and filter all bookings across the platform
- Delete any property platform-wide

---

## Author

**Piyush Raj** — Full Stack Developer
[GitHub](https://github.com/Piyussh-22) · [LinkedIn](https://linkedin.com/in/piyush-raj-tech)

---

## License

MIT
