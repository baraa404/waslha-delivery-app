# Waslha — Delivery App

<div align="center">

**[English](README.md)** · **[العربية](README.ar.md)**

<br>

<img src="screenshots/logo.png" width="120" alt="Waslha logo" />

<br>

**وصلة** — a two-sided delivery marketplace for Jordan (and Egypt).

Customers post point-to-point deliveries. Nearby drivers claim them, complete them with a QR scan, and get rated. Operations run the platform from a web admin panel. Sales reps grow the network with referral codes.

<br>

`Arabic · English` · `Flutter` · `Firebase` · `Riverpod` · `#FB3C04`

</div>

---

> **Note:** The source code for this project is proprietary and closed-source. This repository is a portfolio showcase of the product, features, and UI — not the application source.

---

## Live links

| | |
|---|---|
| Public site | [waslha-application.web.app](https://waslha-application.web.app) |
| Privacy | [Privacy policy](https://waslha-application.web.app/privacy) |
| Terms | [Terms of use](https://waslha-application.web.app/terms) |
| Delete account | [Account deletion](https://waslha-application.web.app/delete-account) |

---

## Screenshots

> Screenshots coming soon — drop files into `screenshots/` and they will appear here.

<!--
<div align="center">
  <img src="screenshots/customer-home.png" width="30%" alt="Customer home" />
  <img src="screenshots/create-order.png" width="30%" alt="Create delivery" />
  <img src="screenshots/driver-available.png" width="30%" alt="Driver available jobs" />
</div>

<br>

<div align="center">
  <img src="screenshots/order-detail.png" width="30%" alt="Order detail" />
  <img src="screenshots/qr-complete.png" width="30%" alt="QR completion" />
  <img src="screenshots/admin-dashboard.png" width="30%" alt="Admin dashboard" />
</div>
-->

---

## Overview

Waslha (وصلة — “connection”) links anyone who needs a delivery with nearby drivers. It is built for general parcel / point-to-point transport — not food delivery only.

**Roles**

| Role | What they do |
|------|----------------|
| **Customer** | Shops or individuals — create single or bulk deliveries, track status, confirm pickup, show QR at drop-off |
| **Driver** | Go online, claim matching jobs, scan QR to complete, earn from delivery fees |
| **Sales rep** | Admin-provisioned — share a referral code, earn commission on referred drivers & merchants |
| **Admin** | Web panel — approve drivers, manage orders, pricing, commissions, and platform config |

---

## Product highlights

### Mobile (customers & drivers)

- Full **Arabic / English** UI (Cairo typeface, RTL-ready)
- Sign in with **Google**, email & password, email verification, and **SMS phone OTP**
- Country-aware accounts (**Jordan** / **Egypt**) with matching currency labels
- Map pickup & drop-off via pin picker, current location, or pasted **Google Maps links**
- Route preview with distance and ETA
- Timing options: urgent / later today / within 2 days (with configurable surcharges)
- **Bulk deliveries**: one pickup, up to 10 drop-offs, one driver for the batch
- Fee preview before confirm (distance-based or Amman flat-zone pricing)
- Order lifecycle with accept / reject driver, release, cancel, and ratings
- **QR completion** — customer shows code; driver scans to finish (not a bare button)
- Driver online/offline feed filtered by vehicle type and dispatch radius
- Spending / earnings stats (today · week · month · all time)
- Referral code redeem once per customer or driver
- Remote app kill-switch for maintenance / emergency lockout

### Sales reps

- Referral dashboard (drivers & merchants)
- Personal shareable referral code
- Commission summary for the current period

### Admin web (Arabic RTL)

- Live overview: orders, revenue, completion rate, “needs action” strip
- Approve / revoke drivers; enable / suspend customers
- Per-driver earnings and per-merchant commission (mark paid + receipts)
- Create & manage sales reps, unlink referrals, mark commissions paid
- Pricing: distance model or Greater Amman flat zone + timing + bulk discounts
- Dispatch radius and 1★ requester-block rules
- Support / WhatsApp / developer contact numbers used in-app

---

## How a delivery works

1. Customer creates a delivery (map + details + vehicle + timing)
2. Nearby matching drivers see it and claim
3. Customer accepts (or rejects) the driver
4. Driver picks up; customer confirms
5. At drop-off, driver scans the customer’s **QR**
6. Trip completes; customer rates the driver

---

## Tech snapshot

| Layer | Stack |
|-------|--------|
| Mobile | Flutter · `hooks_riverpod` · `go_router` · Cairo · AR \| EN |
| Backend | Firebase Auth · Firestore · Storage · Cloud Functions · FCM |
| Maps | Google Maps / Places / Routes · Maps link paste → coords |
| Admin | Next.js · Arabic RTL dashboard |
| Architecture | Feature-first under `lib/features/*` + shared `lib/core/*` |

Order create / update / cancel / batch accept go through **callable Cloud Functions** (server-side fee snapshots). Clients do not write order docs directly.

---

## Trust & safety

- Phone verification + ID document uploads
- Drivers work only after **admin approval**
- QR-gated completion
- Ratings after completed trips
- Optional hide of a customer’s future open jobs from a driver after a 1★
- Customer access suspend with in-app support path

---

## Brand

| | |
|---|---|
| Name | Waslha / وصلة |
| Primary | `#FB3C04` |
| Typeface | Cairo |
| Market focus | Jordan (Egypt supported in-app) |

---

<div align="center">

**[English](README.md)** · **[العربية](README.ar.md)**

<br>

<em>Portfolio showcase — source remains private.</em>

</div>
