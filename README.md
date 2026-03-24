ystem Overview

DaimaPay is a comprehensive airtime and mobile payment ecosystem that enables businesses, resellers, and individuals to purchase and distribute airtime efficiently. The system integrates with M-Pesa (Safaricom Daraja API) and Africa's Talking for airtime fulfillment, providing a seamless experience across multiple platforms.

### Key Capabilities
- **Airtime Distribution**: Single and bulk airtime purchases
- **Multi-Platform Access**: Web portal, mobile wallet app, and admin dashboard
- **Payment Processing**: M-Pesa STK Push, C2B payments, and wallet-based transactions
- **Commission Management**: Automated commission calculation and withdrawal for resellers
- **Float Management**: Real-time tracking of Safaricom and AfricasTalking float balances
- **Offline Support**: Manual transaction entry and reconciliation
- **Data Bundles**: Integration with Bingwa Sokoni USSD gateway for data bundle sales

---

## Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         DaimaPay Ecosystem                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │   Web Portal │  │ Wallet App   │  │ Admin Panel  │         │
│  │  (React/JS)  │  │  (React PWA) │  │   (React)    │         │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘         │
│         │                 │                 │                  │
│         └─────────────────┼─────────────────┘                  │
│                           │                                     │
│                  ┌────────▼────────┐                           │
│                  │  DaimaPayServer │                           │
│                  │   (Node.js/     │                           │
│                  │    Express)     │                           │
│                  └────────┬────────┘                           │
│                           │                                     │
│         ┌──────────────────┼──────────────────┐                  │
│         │                  │                  │                  │
│  ┌──────▼──────┐  ┌───────▼──────┐  ┌───────▼──────┐          │
│  │  Firebase   │  │  M-Pesa      │  │  Africas     │          │
│  │  Firestore  │  │  Daraja API  │  │  Talking API │          │
│  └─────────────┘  └──────────────┘  └──────────────┘          │
│                                                                 │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │         Bingwa USSD Gateway (Android App)               │  │
│  │         (For Data Bundle Sales)                          │  │
│  └──────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```

### Technology Stack

**Backend Server (DaimaPayServer)**
- Node.js with Express.js
- Firebase Admin SDK (Firestore)
- M-Pesa Daraja API (STK Push, C2B, B2C, Reversals)
- Africa's Talking API (Airtime)
- Winston Logger
- Nodemailer (Email notifications)
- Node-cron (Scheduled tasks)

**Web Portal (DaimaPay Web/AirtimePortal)**
- Vanilla JavaScript
- Firebase SDK
- Progressive Web App (PWA)

**Wallet Application (DaimaWallet)**
- React 18.2.0
- React Router DOM
- Firebase SDK (Auth, Firestore, Storage)
- Material-UI & Heroicons
- Tailwind CSS
- PWA Support

**Admin Dashboard (daimaAdmin)**
- React 19.1.0
- React Router DOM
- Firebase SDK
- Recharts (Analytics)
- jsPDF (Report generation)
- Tailwind CSS
