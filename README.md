# Adflow Analytics

**Enterprise Transaction Reporting & Cash-Flow Intelligence Portal**

A full-stack finance analytics dashboard built for account officers and financial analysts to monitor corporate transaction streams, track liquidity, and audit transactional data across client portfolios.

## Project Overview

Adflow Analytics is designed as an internal banking portal rather than a retail personal-finance app. It supports high-volume transaction monitoring through an interactive tabular ledger and rich data visualization, backed by a relational SQL database and a RESTful API.

**Target users:** Account officers, corporate relationship managers, financial analysts

## Dashboard Views

**Executive Analytics View (Visualizer Page)**
- KPI summary cards — Total Processed Volume, Net Liquidity Position, Transaction Success Rate (%)
- Time-series line chart — inflows vs. outflows over daily/monthly scales
- Channel distribution donut chart — volume by channel (Wire, POS, API)

**Transaction Ledger View (DataTable Page)**
- Interactive table with sorting, search, and pagination
- Dropdown filters — date range, settlement status, transaction direction

## Technology Stack

| Layer | Tool |
|---|---|
| Frontend | React.js + Tailwind CSS |
| Tables | DataTables.js |
| Charts | Chart.js |
| Backend | Node.js + Express |
| Database | PostgreSQL |
| Version Control | Git + GitHub |

## System Architecture

```
Browser (React) → Axios → Express Router → Controller Layer → PostgreSQL
     ↑                                                              │
     └──────────────── JSON Response → DataTables.js / Chart.js ────┘
```
<img width="2121" height="559" alt="architecture-diagram" src="https://github.com/user-attachments/assets/144b4c6a-8ebf-495e-9a4e-4797b94c71e3" />


## Entity Relationship Diagram

<img width="2121" height="777" alt="erd-diagram" src="https://github.com/user-attachments/assets/e2b340bb-f1e5-4d8e-9c8d-c4795f475daf" />



**Tables**
- `users` — user_id (UUID, PK), company_name, email (unique), password_hash
- `accounts` — account_id (UUID, PK), user_id (FK), account_number, current_balance (NUMERIC 15,2)
- `categories` — category_id (INT, PK), name, type (credit/debit), description
- `transactions` — transaction_id (UUID, PK), account_id (FK), category_id (FK), amount, direction, channel, status, timestamp

**Relationships**
```
USERS       ||--o{  ACCOUNTS      : owns
ACCOUNTS    ||--o{  TRANSACTIONS  : records
CATEGORIES  ||--o{  TRANSACTIONS  : classifies
```

## Project Structure

```
adflow-analytics/
├── client/                    # React frontend
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
├── server/                    # Node.js + Express backend
│   ├── routes/
│   ├── controllers/
│   └── index.js
├── database/                  # SQL schema and seed files
│   └── schema.sql
├── docs/                      # Diagrams and design assets
│   ├── architecture-diagram.png
│   └── erd-diagram.png
└── README.md
```

## Getting Started

**1. Clone the repo**
```
git clone https://github.com/legacycodine/Adflow-Analytics.git
```

**2. Install backend dependencies**
```
cd server && npm install
```

**3. Install frontend dependencies**
```
cd client && npm install
```

**4. Start development servers**
```
npm run dev
```

## Status

**Phase 1 — Conceptual Design.** Repository initialized; implementation begins in Phase 2 following tutor feedback.
