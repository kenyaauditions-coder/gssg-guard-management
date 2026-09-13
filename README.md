# GSSG Guard Management System

**Protecting People. Securing Property. Building Trust.**

A production-ready web application for managing security guards, attendance, patrols, sites, checkpoints, incidents, and reports. Built with React, Node.js, Express, TypeScript, and PostgreSQL.

## Features

- **Guard Management**: Create, activate, suspend, and manage security guards
- **Real QR Scanning**: Generate, download, and regenerate unique QR codes for checkpoints
- **Attendance System**: Real-time attendance tracking with GPS verification
- **Patrol Management**: Multi-checkpoint patrol routes with real-time monitoring
- **GPS Geofencing**: Server-side location verification within permitted radius
- **Incident Reporting**: Guard incident reports with photos and severity levels
- **Admin Dashboard**: Real-time monitoring of guards, sites, patrols, and incidents
- **Role-Based Access Control**: SUPER_ADMIN, ADMIN, SUPERVISOR, GUARD, CLIENT roles
- **Audit Logs**: Complete action audit trail for compliance
- **Mobile-First Design**: Android and mobile-optimized interface for guards
- **Responsive Admin Interface**: Desktop and tablet-optimized dashboards
- **Reports & Exports**: CSV, Excel, and PDF exports for attendance and patrols

## Technology Stack

### Frontend
- **React 18** with TypeScript
- **Vite** for fast development
- **Tailwind CSS** for styling
- **React Router** for navigation
- **Axios** for API communication
- **Zod** for validation
- **React Query** for data management
- **QR Scanner** for real-time QR code reading
- **Progressive Web App** support

### Backend
- **Node.js** with TypeScript
- **Express.js** for REST API
- **PostgreSQL** for database
- **Prisma** as ORM
- **Argon2** for password hashing
- **JWT & Sessions** for authentication
- **Zod** for request validation
- **Jest** for testing

## Quick Start

### Prerequisites
- Node.js 18+
- PostgreSQL 14+
- npm or yarn

### Installation

1. **Clone and install dependencies:**
```bash
git clone https://github.com/kenyaauditions-coder/gssg-guard-management.git
cd gssg-guard-management
npm install
cd backend && npm install
cd ../frontend && npm install
cd ..
```

2. **Configure environment:**
```bash
# Copy the example env file
cp .env.example .env

# Edit .env with your actual values
# Make sure DATABASE_URL points to your PostgreSQL instance
```

3. **Setup PostgreSQL database:**
```bash
# Create the database
creatdb gssg_dev

# Or use your PostgreSQL client to create a database named 'gssg_dev'
```

4. **Run database migrations and seed:**
```bash
npm run db:migrate
npm run db:seed
```

5. **Start development servers:**
```bash
npm run dev
```

This will start:
- **Backend**: http://localhost:5000
- **Frontend**: http://localhost:5173

## Development

### Project Structure
```
gssg-guard-management/
├── backend/
│   ├── src/
│   │   ├── middleware/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── controllers/
│   │   ├── validators/
│   │   ├── types/
│   │   ├── utils/
│   │   └── server.ts
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── seeds/
│   ├── tests/
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── types/
│   │   ├── utils/
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── public/
│   ├── package.json
│   └── vite.config.ts
└── README.md
```

### Database

**View database in Prisma Studio:**
```bash
npm run db:studio
```

**Create a new migration after schema changes:**
```bash
cd backend
npx prisma migrate dev --name your_migration_name
```

### Useful Commands

```bash
# Run backend only
npm run dev:backend

# Run frontend only
npm run dev:frontend

# Build for production
npm run build

# Start production server
npm start

# Run tests
npm test

# Run linting
npm run lint

# View Prisma database studio
npm run db:studio
```

## Default Credentials (Development Only)

After seeding, use these credentials:

| Role | Email | Password |
|------|-------|----------|
| Super Admin | admin@gssg.local | Admin@123 |
| Admin | john.admin@gssg.local | Admin@123 |
| Supervisor | maria.supervisor@gssg.local | Supervisor@123 |
| Guard | james.guard@gssg.local | Guard@123 |
| Client | acme.client@gssg.local | Client@123 |

⚠️ **IMPORTANT**: Change all default passwords immediately in production.

## Authentication

The system uses secure session-based authentication with:
- Argon2 password hashing
- HTTP-only secure cookies
- CSRF protection
- Rate limiting on login attempts
- Session validation

## Authorization

Role-Based Access Control (RBAC) is enforced:
- **SUPER_ADMIN**: Full system access
- **ADMIN**: Guard, site, checkpoint, attendance, patrol, incident, report management
- **SUPERVISOR**: Site monitoring, guard oversight, patrol tracking
- **GUARD**: Personal attendance, patrols, incidents, profile
- **CLIENT**: View-only access to assigned sites and reports

## API Documentation

### Authentication Endpoints
```
POST   /api/auth/login          - User login
POST   /api/auth/logout         - User logout
GET    /api/auth/me             - Current user info
POST   /api/auth/refresh        - Refresh session
```

### Guard Endpoints
```
GET    /api/guards              - List all guards (admin)
POST   /api/guards              - Create guard (admin)
GET    /api/guards/:id          - Guard details
PATCH  /api/guards/:id          - Update guard
DELETE /api/guards/:id          - Soft delete guard
```

### Site Endpoints
```
GET    /api/sites               - List sites
POST   /api/sites               - Create site (admin)
GET    /api/sites/:id           - Site details
PATCH  /api/sites/:id           - Update site
GET    /api/sites/:id/posts     - Site posts
```

### QR Code Endpoints
```
POST   /api/qr/generate         - Generate QR code
GET    /api/qr/:id              - Get QR details
POST   /api/qr/:id/validate     - Validate QR code
POST   /api/qr/:id/regenerate   - Regenerate QR
PATCH  /api/qr/:id/disable      - Disable QR
```

### Attendance Endpoints
```
POST   /api/attendance/check-in  - Record check-in
POST   /api/attendance/check-out - Record check-out
GET    /api/attendance           - List attendance (filtered)
GET    /api/attendance/:id       - Attendance details
```

### Patrol Endpoints
```
POST   /api/patrol/start         - Start patrol session
POST   /api/patrol/scan          - Scan checkpoint
GET    /api/patrol/sessions      - List patrol sessions
GET    /api/patrol/sessions/:id  - Session details
```

### Incident Endpoints
```
POST   /api/incidents            - Create incident
GET    /api/incidents            - List incidents
GET    /api/incidents/:id        - Incident details
PATCH  /api/incidents/:id        - Update incident
```

### Dashboard Endpoints
```
GET    /api/dashboard            - Dashboard stats
GET    /api/dashboard/activity   - Recent activity feed
GET    /api/dashboard/charts     - Chart data
```

### Reports Endpoints
```
GET    /api/reports/attendance   - Attendance report
GET    /api/reports/patrols      - Patrol report
GET    /api/reports/incidents    - Incident report
GET    /api/reports/export       - Export data (CSV/Excel/PDF)
```

## Deployment on Replit

1. Create a new Replit project from this repository
2. Add environment variables in Replit Secrets:
   - `DATABASE_URL`: Your PostgreSQL connection string
   - `SESSION_SECRET`: Generate a strong random string
   - `JWT_SECRET`: Generate a strong random string
3. Run `npm run db:migrate` in the Shell
4. Run `npm run db:seed` in the Shell
5. Run `npm start` to start the application
6. Or use `npm run dev` for development mode

## Testing

Run automated tests:
```bash
npm test
```

Tests cover:
- Authentication and authorization
- QR code generation and validation
- Attendance check-in/check-out logic
- Patrol scanning and verification
- Geofence calculations
- Role-based permissions
- Duplicate scan prevention
- Incident creation

## License

MIT License - See LICENSE file for details

---

**GSSG Guard Management System** - Building Trust Through Technology

**Protecting People. Securing Property. Building Trust.**
