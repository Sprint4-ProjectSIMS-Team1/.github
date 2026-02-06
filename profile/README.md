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

#### Libraris
- **vue3-toastify:** Add easy toast management. We created a useToast composable with a showToast function that takes the normal toast() functionality and adds some parameters, this is because we want all our error toast to have the same look and behavior. Anyways, we can use the normal toast() function and assign some parameters to it like this toast(message, {parameters}) to create new design for our toasts.
- **@headlessui/vue:** Add easy headless ui components management
- **@heroicons/vue:** Add easy heroicons management
- **spatie/laravel-permission:** Implements a robust Role-Based Access Control (RBAC) system. We utilized this to manage authorization across our API, allowing us to assign roles (Admin, Client, Maintenance) and granular permissions (e.g., `can.activate.reservation`) to users. It integrates directly with Laravel's Policies and Gates, ensuring that logic like "only Admins can force-finish a trip" is decoupled from the main business logic.
- **nesbot/carbon:** An API extension for PHP DateTime. This library is crucial in the `ReservationController` for handling time-sensitive operations. We use it to calculate the exact duration of trips (`diffInMinutes`) to compute the final cost, as well as to manage reservation deadlines (e.g., calculating if a reservation has expired by adding minutes to the `created_at` timestamp).
- **Leaflet (leaflet.js + leaflet.css):** Lightweight JavaScript library for interactive maps. We used Leaflet to render the main map and manage dynamic markers. It allows us to easily display geographic data, update marker positions in real time, and control map interactions such as zoom and pan.
- **OpenStreetMap (Tile Provider):** Open-source map data used as the base tile layer. We configured Leaflet with an OpenStreetMap tile URL to provide the visual map layer without relying on proprietary services like Google Maps.

### Backend
- Laravel
  
#### Libraris
- **Sanctum:** Add's tokens and is in charge of the laravel security and authentication
- **Spatie:** Easy and strong way to manage roles and permissions, this library creates this tables: roles, permissions, role_has_permissions, model_has_roles and model_has_permissions. We are not using this last one because we want all our users to have a role.
  
### Database
- PostgreSQL
---

## Code Conventions

To ensure consistency and readability across the project, the following conventions must be followed:

- **Composables**: `useComposableName.ts`
- **Components**: `PascalCase.vue`
- **Classes**: `PascalCase`
- **Routes**: `kebab-case`
- **Variables, functions, others**: `camelCase`

### General Rules
- All comments, file names, and content **must be written in English**
- Keep code clean, readable, and well-structured please

---

## Commit Messages

Use concise and meaningful commit messages with the following prefixes:

- **Fix**: `Fix: Fixed the users CRUD`
- **Feat**: `Feat: Added users CRUD to the backend`
- **Refactor**: `Refactor: Improved authentication logic`

