# MobilePe — Aamby Valley City Cashless Wallet

> A city-wide cashless payment system built for Aamby Valley. Guests register with their phone number, load cash at any outlet, and pay across restaurants, hotels, and attractions — no card, no app, no hassle. Every transaction is logged and confirmed via WhatsApp instantly.

---

## What It Does

MobilePe is an internal e-wallet system deployed across Aamby Valley City. Instead of carrying cash, guests load money into their wallet at any registered outlet. From that point, their phone number becomes their payment method — staff enter the number at billing, the amount is deducted, and the guest receives a WhatsApp confirmation in seconds.

---

## Modules

| Module | Description |
|--------|-------------|
| **Registration** | Staff registers a new guest using their phone number. If the number already exists in the system, a popup shows the guest's full details and wallet balance instead of re-registering. |
| **Top Up** | Staff loads cash into a guest's wallet. Balance is updated in real time in the database. |
| **Deduct / Pay** | At any billing counter, staff enters the guest's phone number and bill amount. If balance is sufficient, it is deducted instantly. If not, the system blocks the transaction and shows an insufficient balance error. |
| **Check Balance** | Instantly look up how much balance a guest has using their phone number. |
| **View History** | Full transaction history for any guest — every top up, deduction, and refund with date, time, and location. |
| **Refund** | If a guest was incorrectly charged, staff can refund the amount back to their wallet. All refunds are logged. |

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | ASP.NET 6.8 |
| Backend API | ASP.NET 6.8 |
| Database | Microsoft SQL Server (SSMS) |
| Notifications | WhatsApp Message Logs |
| Environment | TEST — `http://10.3.1.110:443/MobilePe/` |
| Version | Beta v1.2.0 |

---

## Database

**Database Name:** `MobilePe`

| Table | Purpose |
|-------|---------|
| `AppUsers` | Staff and admin user accounts |
| `WalletRegistrations` | All registered guests and their wallet balance |
| `WalletTransactions` | Every transaction — top up, deduction, refund |
| `History` | Full activity log |
| `OutletMaster` | Registered outlets across Aamby Valley |
| `OTPVerifications` | OTP records for verification flows |
| `tblIDStransactions` | ID-based transaction records |
| `WhatsAppMessageLogs` | Log of every WhatsApp confirmation sent |

---

## How It Works — Guest Flow

```
1. Guest arrives at Aamby Valley
         ↓
2. Staff registers guest with phone number
         ↓
3. Guest hands cash → Staff tops up wallet
         ↓
4. Guest visits restaurant / attraction / hotel
         ↓
5. Staff enters phone number + bill amount → clicks Deduct
         ↓
6. Balance checked → deducted if sufficient
         ↓
7. Guest receives WhatsApp confirmation instantly
```

---

## Key Business Rules

- A phone number can only be registered **once** — duplicate check runs before every registration
- Wallet balance **can never go negative** — system blocks deduction if balance is insufficient
- Every single transaction is logged in the database — **no exceptions**
- All amounts are in **Indian Rupees (INR)**
- Phone numbers are stored as **10 digits** without spaces or country code

---

## Deployment Info

| Item | Details |
|------|---------|
| Project Name | MobilePe |
| Environment | Testing / Live |
| Version | Beta |
| Deployment Date | 1st June 2026 |
| Server IP | 10.3.1.110 |
| Database Server | 10.20.1.17 |
| Prepared By | Shalini Muthukumar |
| Approved By | EJ Sudheer |

---

## Validation Checklist

- ✅ Application URL accessible
- ✅ Login functionality working
- ✅ API health check passed
- ✅ Database connectivity confirmed
- ✅ Logs generating correctly

---

## Team

| Role | Name |
|------|------|
| Deployment Engineer | Shalini Muthukumar |

---

*Built exclusively for Aamby Valley City · Internal Use Only*
