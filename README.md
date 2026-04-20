# ⬡ ShopZone — Angular E-Commerce Application

A full-featured Angular 18 e-commerce application with JSON Server as a mock REST backend.

---

## 🚀 Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Angular 18 (Standalone Components) |
| Styling | SCSS with CSS Variables |
| Forms | Reactive Forms (auth) + Template-driven (cart) |
| HTTP | Angular HttpClient + functional interceptor |
| State | RxJS BehaviorSubject (cart count) |
| Backend | JSON Server (mock REST API) |
| Routing | Angular Router with lazy-loaded routes |

---

## 📁 Project Structure

```
src/
├── app/
│   ├── core/
│   │   ├── guards/
│   │   │   └── auth.guard.ts            # CanActivate functional guard
│   │   ├── interceptors/
│   │   │   └── auth.interceptor.ts      # Attaches Authorization header
│   │   ├── models/
│   │   │   ├── user.model.ts
│   │   │   ├── product.model.ts
│   │   │   ├── cart-item.model.ts
│   │   │   ├── order.model.ts
│   │   │   └── index.ts
│   │   └── services/
│   │       ├── auth.service.ts          # login, register, logout, isLoggedIn
│   │       ├── product.service.ts
│   │       ├── cart.service.ts          # BehaviorSubject cart count
│   │       ├── order.service.ts
│   │       └── index.ts
│   ├── features/
│   │   ├── auth/
│   │   │   ├── login/                   # Reactive Form + validation
│   │   │   └── register/                # Reactive Form + password match
│   │   ├── products/
│   │   │   ├── product-list/            # Search + category filter
│   │   │   └── product-detail/          # Quantity selector, add to cart
│   │   ├── cart/                        # Template-driven form
│   │   ├── orders/                      # Protected route, expandable rows
│   │   ├── profile/                     # Protected route, localStorage data
│   │   └── not-found/                   # 404 page
│   ├── shared/
│   │   └── components/
│   │       ├── navbar/                  # Auth-aware, cart badge
│   │       └── loading-spinner/
│   ├── app.component.ts
│   ├── app.config.ts                    # provideRouter, provideHttpClient
│   └── app.routes.ts                    # Lazy-loaded routes
├── environments/
│   ├── environment.ts
│   └── environment.prod.ts
├── styles.scss                          # Global design system
└── index.html
db.json                                  # JSON Server data
```

---

## ⚙️ Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Run both servers simultaneously

```bash
npm run dev
```

This runs:
- **Angular dev server** → `http://localhost:4200`
- **JSON Server** → `http://localhost:3000`

Or run them separately:

```bash
# Terminal 1 — Mock API
npm run server

# Terminal 2 — Angular app
npm start
```

---

## 🔑 Demo Account

The `db.json` includes a ready-to-use demo account:

| Field | Value |
|-------|-------|
| Email | `john@example.com` |
| Password | `password123` |

---

## 🌐 API Endpoints (JSON Server)

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/users?email=X&password=Y` | Login lookup |
| `POST` | `/users` | Register new user |
| `GET` | `/products` | All products |
| `GET` | `/products/:id` | Single product |
| `GET` | `/cart?userId=X` | User's cart |
| `POST` | `/cart` | Add cart item |
| `PATCH` | `/cart/:id` | Update quantity |
| `DELETE` | `/cart/:id` | Remove cart item |
| `GET` | `/orders?userId=X` | User's orders |
| `POST` | `/orders` | Place order |

---

## ✅ Features Implemented

- [x] Login with Reactive Form + validation messages
- [x] Register with confirm-password cross-field validation
- [x] Product list with search + category chip filters
- [x] Product detail with quantity selector
- [x] Cart with template-driven form + editable quantity
- [x] Place order → clears cart → redirects to orders
- [x] Order history with expandable rows (protected)
- [x] Profile page from localStorage (protected)
- [x] 404 Not Found page
- [x] Auth Guard on `/orders` and `/profile`
- [x] HTTP Interceptor attaches `Authorization: Bearer {userId}`
- [x] Navbar shows Login/Register when logged out
- [x] Navbar shows Products/Cart/Orders/Profile/Logout when logged in
- [x] Real-time cart count badge via BehaviorSubject
- [x] Free shipping threshold display
- [x] Responsive layout (mobile + desktop)
- [x] TypeScript strict mode, no `any` types
- [x] Lazy-loaded routes
- [x] Standalone components throughout
- [x] Empty state handling on all pages
- [x] Error handling with alert messages
- [x] Loading spinners on all async operations

---

## 🎨 Design System

The app uses a dark luxury aesthetic with:

- **Colors**: Deep black `#0f0e0c` background, gold `#d4a853` accent
- **Typography**: `Fraunces` (serif display) + `DM Sans` (body)
- **Animations**: CSS `fadeIn` with staggered grid delays
- **Responsive**: CSS Grid with auto-fill columns, mobile hamburger menu
