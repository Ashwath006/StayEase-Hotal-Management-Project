# StayEase – Hotel Booking System

A MERN-based hotel booking application with user authentication, hotel and room management, bookings, reviews, and Razorpay payment integration.

## Project structure

- `frontend/` – React + Vite user interface
- `backend/` – Node.js + Express API
- `backend/models/` – MongoDB/Mongoose models
- `backend/controllers/` – API business logic
- `backend/routes/` – API routes
- `backend/middleware/` – authentication and upload middleware

## Requirements

- Node.js (use a current LTS release)
- npm
- MongoDB database
- Optional service credentials for Razorpay, Cloudinary, and Gmail email delivery

## Packages and technologies used

### Frontend packages

| Package | Purpose |
|---|---|
| `react`, `react-dom` | Build the user interface with React |
| `vite`, `@vitejs/plugin-react` | Frontend development server and production build |
| `react-router-dom` | Client-side page navigation and routing |
| `axios` | Send HTTP requests to the backend API |
| `bootstrap`, `bootstrap-icons` | Responsive layout, styling utilities, and icons |
| `react-icons` | Icon components |
| `react-toastify` | Toast notifications |
| `sweetalert2` | Alert and confirmation dialogs |
| `react-hook-form` | Form state and validation support |
| `react-countup` | Animated number counters |
| `react-intersection-observer` | Detect when elements enter the viewport |
| `react-loader-spinner` | Loading indicators |
| `react-scroll-trigger` | Trigger actions during page scrolling |

### Backend packages

| Package | Purpose |
|---|---|
| `express` | Create the REST API server and routes |
| `mongoose` | Connect to MongoDB and manage database models |
| `dotenv` | Load environment variables from `.env` |
| `cors` | Configure cross-origin requests |
| `bcryptjs` | Hash passwords securely |
| `jsonwebtoken` | Create and verify JWT authentication tokens |
| `express-validator` | Validate and sanitize request data |
| `helmet` | Add common HTTP security headers |
| `morgan` | HTTP request logging |
| `multer` | Handle file uploads |
| `cloudinary` | Store and manage images in Cloudinary |
| `multer-storage-cloudinary` | Connect Multer uploads to Cloudinary storage |
| `nodemailer` | Send emails from the backend |
| `razorpay` | Integrate Razorpay payment orders and verification |

### Development and code-quality packages

| Package | Used in | Purpose |
|---|---|---|
| `nodemon` | Backend | Restart the server automatically during development |
| `eslint` | Frontend | Check code for common issues |
| `@eslint/js`, `globals` | Frontend | ESLint base rules and global definitions |
| `eslint-plugin-react-hooks` | Frontend | Check React Hooks usage |
| `eslint-plugin-react-refresh` | Frontend | Check React Fast Refresh compatibility |
| `@types/react`, `@types/react-dom` | Frontend | React type definitions used by tooling |

Exact package versions are recorded in `frontend/package.json`, `backend/package.json`, and their respective lockfiles. Install dependencies with `npm install` inside each folder.

## Setup

### 1. Backend

Open a terminal:

```bash
cd backend
npm install
```

Copy `backend/.env.example` to `backend/.env` and replace the placeholders with your own private credentials.

Start the API:

```bash
npm run dev
```

The API defaults to `http://localhost:5000`.

### 2. Frontend

Open another terminal:

```bash
cd frontend
npm install
```

Copy `frontend/.env.example` to `frontend/.env`. Set `VITE_API_URL` if your API is hosted somewhere other than `http://localhost:5000/api`.

Start the frontend:

```bash
npm run dev
```

Vite will print the local frontend URL in the terminal.

## Environment variables

Backend variables are documented in `backend/.env.example`:

- `MONGO_URI` – MongoDB connection string
- `JWT_SECRET` – private JWT signing secret
- `RAZORPAY_KEY_ID`, `RAZORPAY_KEY_SECRET` – Razorpay credentials
- `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET` – Cloudinary credentials
- `EMAIL_USER`, `EMAIL_PASS` – email sender credentials
- `ADMIN_NAME`, `ADMIN_EMAIL`, `ADMIN_PASSWORD` – values used only when creating an admin account
- `PORT` – backend port (defaults to 5000)

Never commit `.env` files or real credentials to GitHub.

## Create an admin account

After configuring `backend/.env`, run:

```bash
cd backend
node createAdmin.js
```

The script uses `ADMIN_NAME`, `ADMIN_EMAIL`, and `ADMIN_PASSWORD` from your local `.env`. Do not publish those values.

## Production notes

- Configure a production `VITE_API_URL` and deploy the backend separately.
- Restrict CORS to your deployed frontend origin.
- Protect all admin APIs with backend authentication and role authorization.
- Use HTTPS and production credentials stored in your hosting provider's secret manager.
- Do not use demo credentials in a public repository.

## GitHub safety checklist

- Keep `.env` files private; commit only `.env.example` files with placeholder values.
- Do not commit `node_modules/`, build output, logs, or uploaded private files.
- Keep `package.json` and `package-lock.json` so dependencies can be installed reproducibly.
- If a credential was ever committed or shared publicly, rotate it at the provider.
