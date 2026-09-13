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
cp .env.example .env
# Edit .env with your actual values
```

3. **Setup PostgreSQL database:**
```bash
creatdb gssg_dev
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

## Default Credentials (Development Only)

| Role | Email | Password |
|------|-------|----------|
| Super Admin | admin@gssg.local | Admin@123 |
| Admin | john.admin@gssg.local | Admin@123 |
| Supervisor | maria.supervisor@gssg.local | Supervisor@123 |
| Guard | james.guard@gssg.local | Guard@123 |
| Client | acme.client@gssg.local | Client@123 |

⚠️ **IMPORTANT**: Change all default passwords immediately in production.

## Deployment on Replit

1. Create a new Replit project from this repository
2. Add environment variables in Replit Secrets
3. Run `npm run db:migrate` and `npm run db:seed`
4. Run `npm start` to start the application

## License

MIT License

---

**Protecting People. Securing Property. Building Trust.**
