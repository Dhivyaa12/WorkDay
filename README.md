> ⚠️ **COPYRIGHT NOTICE**: This project is protected under a proprietary license.  Copying, forking, or using this code without permission is strictly prohibited.  See [LICENSE](./LICENSE) for details.

---

# 🏢 WorkWise - Employee Management System

<div align="center">

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

**A comprehensive, full-stack workforce management solution inspired by enterprise HR platforms like Workday**

[Features](#-features) • [Tech Stack](#-tech-stack) • [Architecture](#-architecture) • [Installation](#-installation) • [API Documentation](#-api-documentation)

</div>

---

## 📋 Overview

**WorkWise** is a modern, enterprise-grade Employee Management System designed to streamline HR operations, workforce planning, and employee data management. Built with a focus on scalability, security, and user experience. 

### 🎯 Problem Statement

Organizations struggle with:
- Fragmented employee data across multiple systems
- Manual and error-prone HR processes
- Lack of real-time workforce analytics
- Poor employee self-service capabilities

### 💡 Solution

WorkWise provides a unified platform that centralizes employee management, automates HR workflows, and delivers actionable insights through intuitive dashboards and reporting tools.

---

## 🏗 Architecture

### System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                                   CLIENT LAYER                                   │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐ │
│    │   Browser    │    │   Desktop    │    │   Mobile     │    │   Tablet     │ │
│    └──────┬───────┘    └──────┬───────┘    └──────┬───────┘    └──────┬───────┘ │
│           └───────────────────┴───────────────────┴───────────────────┘         │
│                                       │                                          │
└───────────────────────────────────────┼──────────────────────────────────────────┘
                                        │ HTTPS
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              FRONTEND (React + Vite)                             │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                           src/                                           │    │
│  ├─────────────────────────────────────────────────────────────────────────┤    │
│  │                                                                          │    │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐ │    │
│  │  │    Pages     │  │  Components  │  │   Contexts   │  │   Services   │ │    │
│  │  │              │  │              │  │              │  │              │ │    │
│  │  │ • Dashboard  │  │ • UI Elements│  │ • AuthContext│  │ • API Client │ │    │
│  │  │ • Employees  │  │ • Forms      │  │ • ThemeCtx   │  │ • Axios      │ │    │
│  │  │ • Login      │  │ • Charts     │  │ • UserContext│  │ • HTTP Utils │ │    │
│  │  │ • Profile    │  │ • Tables     │  │              │  │              │ │    │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘ │    │
│  │                                                                          │    │
│  │  ┌──────────────┐  ┌──────────────┐                                     │    │
│  │  │    Styles    │  │  Guidelines  │   Tech: React 18, TypeScript,       │    │
│  │  │ • Tailwind   │  │ • UI/UX Docs │   React Router, Radix UI, Recharts  │    │
│  │  │ • CSS        │  │              │                                     │    │
│  │  └──────────────┘  └──────────────┘                                     │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└───────────────────────────────────────┬──────────────────────────────────────────┘
                                        │ REST API (JSON)
                                        │ JWT Token Auth
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                          BACKEND (Node.js + Express)                             │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                        workflowBackend/src/                              │    │
│  ├─────────────────────────────────────────────────────────────────────────┤    │
│  │                                                                          │    │
│  │  ┌────────────────────────────────────────────────────────────────────┐ │    │
│  │  │                         MIDDLEWARE LAYER                            │ │    │
│  │  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌────────────┐ │ │    │
│  │  │  │    CORS     │  │   Session   │  │  Passport   │  │    JWT     │ │ │    │
│  │  │  │  Handling   │  │  Management │  │    Auth     │  │ Validation │ │ │    │
│  │  │  └─────────────┘  └─────────────┘  └─────────────┘  └────────────┘ │ │    │
│  │  └────────────────────────────────────────────────────────────────────┘ │    │
│  │                                    │                                     │    │
│  │                                    ▼                                     │    │
│  │  ┌────────────────────────────────────────────────────────────────────┐ │    │
│  │  │                          ROUTE HANDLERS                             │ │    │
│  │  │  ┌─────────────────────────┐    ┌─────────────────────────┐       │ │    │
│  │  │  │     Auth Routes         │    │    Employee Routes      │       │ │    │
│  │  │  │  • POST /auth/register  │    │  • GET    /employees    │       │ │    │
│  │  │  │  • POST /auth/login     │    │  • GET    /employees/:id│       │ │    │
│  │  │  │  • POST /auth/logout    │    │  • POST   /employees    │       │ │    │
│  │  │  │  • GET  /auth/me        │    │  • PUT    /employees/:id│       │ │    │
│  │  │  └─────────────────────────┘    │  • DELETE /employees/:id│       │ │    │
│  │  │                                  └─────────────────────────┘       │ │    │
│  │  └────────────────────────────────────────────────────────────────────┘ │    │
│  │                                    │                                     │    │
│  │                                    ▼                                     │    │
│  │  ┌────────────────────────────────────────────────────────────────────┐ │    │
│  │  │                        BUSINESS LOGIC                               │ │    │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │ │    │
│  │  │  │  Controllers │  │   Services   │  │   Helpers    │             │ │    │
│  │  │  │              │  │              │  │              │             │ │    │
│  │  │  │ • UserCtrl   │  │ • AuthService│  │ • Validators │             │ │    │
│  │  │  │ • EmployeeCtrl│ │ • EmployeeSvc│  │ • Formatters │             │ │    │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │ │    │
│  │  └────────────────────────────────────────────────────────────────────┘ │    │
│  │                                                                          │    │
│  │  Tech: Express 5, TypeScript, Passport.js, Bcrypt, JWT                   │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└───────────────────────────────────────┬──────────────────────────────────────────┘
                                        │ Mongoose ODM
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              DATABASE LAYER (MongoDB)                            │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                            Collections                                   │    │
│  │  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐      │    │
│  │  │      Users       │  │    Employees     │  │    Sessions      │      │    │
│  │  │                  │  │                  │  │                  │      │    │
│  │  │ • _id            │  │ • _id            │  │ • _id            │      │    │
│  │  │ • email          │  │ • firstName      │  │ • userId         │      │    │
│  │  │ • password (hash)│  │ • lastName       │  │ • token          │      │    │
│  │  │ • role           │  │ • email          │  │ • expiresAt      │      │    │
│  │  │ • createdAt      │  │ • department     │  │ • createdAt      │      │    │
│  │  │ • updatedAt      │  │ • position       │  │                  │      │    │
│  │  │                  │  │ • salary         │  │                  │      │    │
│  │  │                  │  │ • hireDate       │  │                  │      │    │
│  │  │                  │  │ • status         │  │                  │      │    │
│  │  └──────────────────┘  └──────────────────┘  └──────────────────┘      │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Data Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              USER INTERACTION FLOW                               │
└─────────────────────────────────────────────────────────────────────────────────┘

    ┌─────────┐         ┌─────────────┐         ┌─────────────┐         ┌─────────┐
    │  User   │         │   React     │         │   Express   │         │ MongoDB │
    │         │         │  Frontend   │         │   Backend   │         │         │
    └────┬────┘         └──────┬──────┘         └──────┬──────┘         └────┬────┘
         │                     │                       │                      │
         │  1. Login Request   │                       │                      │
         │────────────────────>│                       │                      │
         │                     │                       │                      │
         │                     │  2. POST /auth/login  │                      │
         │                     │──────────────────────>│                      │
         │                     │                       │                      │
         │                     │                       │  3. Query User       │
         │                     │                       │─────────────────────>│
         │                     │                       │                      │
         │                     │                       │  4. User Data        │
         │                     │                       │<─────────────────────│
         │                     │                       │                      │
         │                     │                       │  5. Validate Password│
         │                     │                       │  (Bcrypt Compare)    │
         │                     │                       │                      │
         │                     │  6. JWT Token + User  │                      │
         │                     │<──────────────────────│                      │
         │                     │                       │                      │
         │                     │  7. Store Token       │                      │
         │                     │  (LocalStorage/Context)                      │
         │                     │                       │                      │
         │  8. Dashboard View  │                       │                      │
         │<────────────────────│                       │                      │
         │                     │                       │                      │
         │  9. View Employees  │                       │                      │
         │────────────────────>│                       │                      │
         │                     │                       │                      │
         │                     │  10. GET /employees   │                      │
         │                     │  (+ JWT in Header)    │                      │
         │                     │──────────────────────>│                      │
         │                     │                       │                      │
         │                     │                       │  11. Verify JWT      │
         │                     │                       │  (Middleware)        │
         │                     │                       │                      │
         │                     │                       │  12. Fetch Employees │
         │                     │                       │─────────────────────>│
         │                     │                       │                      │
         │                     │                       │  13. Employee Data   │
         │                     │                       │<─────────────────────│
         │                     │                       │                      │
         │                     │  14. JSON Response    │                      │
         │                     │<──────────────────────│                      │
         │                     │                       │                      │
         │                     │  15. Render UI        │                      │
         │                     │  (Recharts/Tables)    │                      │
         │                     │                       │                      │
         │  16. Employee List  │                       │                      │
         │<────────────────────│                       │                      │
         │                     │                       │                      │
    ┌────┴────┐         ┌──────┴──────┐         ┌──────┴──────┐         ┌────┴────┐
    │  User   │         │   React     │         │   Express   │         │ MongoDB │
    └─────────┘         └─────────────┘         └─────────────┘         └─────────┘
```

## ✨ Features

### 👤 Employee Management
- **Employee Directory** - Comprehensive employee profiles with personal and professional details
- **CRUD Operations** - Create, read, update, and delete employee records
- **Search & Filter** - Advanced search functionality with multiple filter options
- **Department Management** - Organize employees by departments and teams

### 🚀 Employee Onboarding
- **Streamlined Workflow** - Step-by-step onboarding process for new hires
- **Document Collection** - Automated collection of required documents
- **Task Checklists** - Customizable onboarding task lists
- **Welcome Kits** - Digital welcome packages and orientation materials
- **Mentor Assignment** - Assign mentors to guide new employees

### ⏰ Attendance & Time Tracking
- **Clock In/Clock Out** - Easy one-click time tracking for employees
- **Real-time Tracking** - Monitor attendance status in real-time
- **Attendance Reports** - Generate daily, weekly, and monthly attendance reports
- **Late/Early Tracking** - Automatic detection of late arrivals and early departures
- **Overtime Calculation** - Automated overtime hours tracking
- **Work Hours Summary** - Visual breakdown of worked hours per employee

### 🏖️ Leave Management
- **Leave Requests** - Submit and manage leave applications
- **Leave Types** - Support for vacation, sick leave, personal days, and custom leave types
- **Approval Workflow** - Multi-level leave approval process
- **Leave Balance** - Track remaining leave balances per employee
- **Holiday Calendar** - Company-wide holiday management
- **Leave History** - Complete history of all leave records

### 💰 Basic Payroll Management
- **Salary Management** - Configure and manage employee salaries
- **Payroll Processing** - Generate monthly payroll calculations
- **Deductions & Allowances** - Manage tax deductions, benefits, and allowances
- **Payslip Generation** - Automated payslip creation and distribution
- **Payment History** - Track all payment records and history
- **Tax Calculations** - Basic tax computation based on salary brackets

### 📈 Progress & Performance Tracking
- **Goal Setting** - Set and track individual and team goals
- **Performance Metrics** - Monitor key performance indicators
- **Progress Reports** - Visual progress tracking with charts and graphs
- **Skill Tracking** - Track employee skills and competencies
- **Training Records** - Manage employee training and certifications
- **Performance Reviews** - Schedule and conduct performance evaluations

### 📊 Dashboard & Analytics
- **Interactive Dashboards** - Real-time visualization of workforce metrics
- **Data Charts** - Visual representations using Recharts library
- **Export Functionality** - Export data to Excel using XLSX integration
- **Key Performance Indicators** - Track essential HR metrics
- **Attendance Analytics** - Visual attendance trends and patterns
- **Workforce Insights** - Data-driven HR decision making

### 🔐 Authentication & Security
- **JWT Authentication** - Secure token-based authentication
- **Password Encryption** - Bcrypt hashing for secure password storage
- **Session Management** - Express session with MongoDB store
- **Passport.js Integration** - Local strategy for authentication

### 🎨 User Interface
- **Responsive Design** - Mobile-first approach with Tailwind CSS
- **Modern UI Components** - Radix UI primitives for accessibility
- **Dark/Light Theme** - Theme switching with next-themes
- **Toast Notifications** - User feedback with Sonner

### 📁 Additional Features
- **Role-Based Access Control** - Different access levels for admins and employees
- **Data Validation** - Form validation with React Hook Form
- **Date Management** - Date handling with date-fns library
- **File Handling** - Document management capabilities

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| **React 18** | UI Library for building component-based interfaces |
| **TypeScript** | Type-safe JavaScript for better code quality |
| **Vite** | Next-generation frontend build tool |
| **Tailwind CSS** | Utility-first CSS framework |
| **Radix UI** | Unstyled, accessible UI components |
| **React Router DOM** | Client-side routing |
| **Recharts** | Composable charting library |
| **React Hook Form** | Performant form handling |
| **Axios** | HTTP client for API requests |
| **Lucide React** | Beautiful icon library |

### Backend
| Technology | Purpose |
|------------|---------|
| **Node.js** | JavaScript runtime environment |
| **Express 5** | Web application framework |
| **TypeScript** | Type-safe backend development |
| **MongoDB** | NoSQL database for flexible data storage |
| **Mongoose** | MongoDB object modeling |
| **JWT** | JSON Web Tokens for authentication |
| **Bcrypt** | Password hashing |
| **Passport.js** | Authentication middleware |
| **Express Session** | Session management |
| **CORS** | Cross-origin resource sharing |

### Development Tools
| Tool | Purpose |
|------|---------|
| **Nodemon** | Auto-restart server during development |
| **ts-node** | TypeScript execution for Node.js |
| **ESLint** | Code linting and quality |

---

## 📚 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | User login |
| POST | `/api/auth/logout` | User logout |
| GET | `/api/auth/me` | Get current user |

### Employee Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/employees` | Get all employees |
| GET | `/api/employees/:id` | Get employee by ID |
| POST | `/api/employees` | Create new employee |
| PUT | `/api/employees/:id` | Update employee |
| DELETE | `/api/employees/:id` | Delete employee |

### Attendance Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/attendance/clock-in` | Clock in for the day |
| POST | `/api/attendance/clock-out` | Clock out for the day |
| GET | `/api/attendance/:employeeId` | Get attendance records |
| GET | `/api/attendance/report` | Generate attendance report |

### Leave Management Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/leaves` | Get all leave requests |
| POST | `/api/leaves` | Submit leave request |
| PUT | `/api/leaves/:id` | Update leave request |
| PUT | `/api/leaves/:id/approve` | Approve leave request |
| PUT | `/api/leaves/:id/reject` | Reject leave request |
| GET | `/api/leaves/balance/:employeeId` | Get leave balance |

### Payroll Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/payroll` | Get payroll records |
| POST | `/api/payroll/generate` | Generate monthly payroll |
| GET | `/api/payroll/payslip/:id` | Get employee payslip |
| GET | `/api/payroll/history/:employeeId` | Get payment history |

### Progress Tracking Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/progress/:employeeId` | Get employee progress |
| POST | `/api/goals` | Create new goal |
| PUT | `/api/goals/:id` | Update goal progress |
| GET | `/api/performance/:employeeId` | Get performance metrics |

---

## 🔧 Available Scripts



## 🎓 Key Learning Outcomes

This project demonstrates proficiency in:

1. **Full-Stack Development** - Building end-to-end applications with React and Node.js
2. **TypeScript** - Type-safe development across frontend and backend
3. **Database Design** - MongoDB schema design with Mongoose
4. **Authentication** - Implementing secure JWT-based authentication
5. **RESTful API Design** - Creating scalable and maintainable APIs
6. **Modern UI/UX** - Building accessible, responsive interfaces
7. **State Management** - Using React Context for global state
8. **Component Architecture** - Creating reusable, modular components
9. **Security Best Practices** - Password hashing, session management, CORS

---

## 🔮 Future Enhancements

- [ ] Advanced reporting and analytics
- [ ] Mobile application (React Native)
- [ ] Real-time notifications (WebSockets)
- [ ] Unit and integration testing
- [ ] Biometric attendance integration
- [ ] AI-powered performance insights

---

## 👩‍💻 Author

**Lakshana**

- GitHub: [@Lakshana07-1108](https://github.com/Lakshana07-1108)

---

## ⚖️ License

This project is protected under a **Proprietary Software License**.  

**Prohibited:** Copying, modifying, distributing, forking, or using this code without explicit permission. 

**Permitted:** Viewing for interview evaluation purposes only.

See the [LICENSE](./LICENSE) file for complete terms. 

---

<div align="center">

**📧 For access requests or inquiries, please contact me via GitHub.**

</div>
