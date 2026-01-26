# Sprint 4 – SIMS Project

## Overview

In this sprint, we take everything learned during **Sprint 3** and apply it to build a more robust, scalable, and professional application.

The main goal is to modernize both the frontend and backend with this new stack:

- **Frontend**: migrate from plain HTML, CSS, and JavaScript to **Vue**, **TypeScript**, and **Tailwind CSS**
- **Backend**: migrate from vanilla PHP to **Laravel**
- **Database**: we are still going to use **PostgreSQL**

---

## Architecture Decisions

### Multi-Tenant Architecture

This application is designed as a **SaaS platform (B2B / B2G)**.

We use a **multi-tenant architecture** to:

- Centralize tenant management
- Improve scalability
- Simplify maintenance and deployments

Each tenant is logically isolated while sharing the same database infrastructure.

---

### Single-Page Application (SPA)

The frontend is implemented as a **Single-Page Application**.

#### Implications
- Using a SPA makes the page not indexable by google so we will need to develop a **Landing page** on the server side in order to be indexed by google
---

## Tech Stack

### Frontend
- Vue
- TypeScript
- Tailwind CSS

### Backend
- Laravel
  - Spatie: Easy way to manage roles and permissions 
  - Sanctum: Add's tokens

### Database
- PostgreSQL
