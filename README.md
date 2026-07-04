# Adflow-Analytics

Enterprise Transaction Reporting & Cash-Flow Intelligence Portal
A full-stack finance analytics dashboard designed for account officers and financial analysts to monitor corporate transaction streams, track liquidity, and audit transactional data across client portfolios.

Project Overview
Adflow Analytics is built as an internal banking portal, not a retail personal finance app. 
It supports high-volume transaction monitoring with interactive data visualization and tabular ledger auditing.

Target Users: Account officers, corporate relationship managers, financial analysts

Dashboard Views
Executive Analytics View (Visualizer Page)
KPI Summary Cards: Total Volume, Net Liquidity, Transaction Success Rate (%)
Time-Series Line Chart: Inflows vs. Outflows over daily/monthly scales
Channel Distribution Donut Chart: Volume by channel (Wire, POS, API)
Transaction Ledger View (DataTable Page)
Interactive table with sorting, search, and pagination
Dropdown filters: date range, settlement status, transaction direction
Technology Stack
Layer	Tool
Frontend	React.js + Tailwind CSS
Tables	TanStack Table
Charts	Chart.js
Backend	Node.js + Express
Database	PostgreSQL
Version Control	Git + GitHub
System Architecture
Browser (React) → Axios → Express Router → Controller Layer → PostgreSQL → JSON Response → TanStack Table / Chart.js

System Architecture Diagram

Entity Relationship Diagram (ERD)
ERD Diagram

Tables
users — user_id (UUID), company_name, email, password_hash
accounts — account_id (UUID), user_id (FK), account_number, current_balance (NUMERIC 15,2)
categories — category_id (INT), name, type, description
transactions — transaction_id (UUID), account_id (FK), category_id (FK), amount, direction, channel, status, timestamp
Relationships
USERS ||--o{ ACCOUNTS : owns
ACCOUNTS ||--o{ TRANSACTIONS : records
CATEGORIES ||--o{ TRANSACTIONS : classifies
Project Structure
adflow-analytics/
├── client/          # React frontend
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
├── server/          # Node.js + Express backend
│   ├── routes/
│   ├── controllers/
│   └── index.js
├── database/        # SQL schema and seed files
│   └── schema.sql
├── docs/            # Diagrams and design assets
│   ├── architecture-diagram.png
│   └── erd-diagram.png
└── README.md
Getting Started
# Clone the repo
https://github.com/legacycodine/Adflow-Analytics.git

# Install backend dependencies
cd server && npm install

# Install frontend dependencies
cd client && npm install

# Start development servers
npm run dev
