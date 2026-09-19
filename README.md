# 🚚 Waslha — Delivery App

<div align="center">
  <p>
    <strong><a href="README.md">English</a></strong> · <strong><a href="README.ar.md">العربية</a></strong>
  </p>
  <img src="screenshots/logo.png" width="120" alt="Waslha logo" />
  <p>A production-ready, Arabic-first delivery marketplace built with Flutter.</p>
  <p>
    <strong>Point-to-Point • QR Completion • Bulk Drops • Feature-First</strong>
  </p>
</div>

---

> 🔒 **Note:** The source code for this project is proprietary and closed-source. This repository serves purely as a portfolio showcase of the architecture, features, and user interface.

---

## 📲 Download

<div align="center">

[![Download APK](https://img.shields.io/badge/Download-Android%20APK-FB3C04?style=for-the-badge&logo=android&logoColor=white)](https://github.com/baraa404/waslha-delivery-app/releases/latest/download/Waslha.apk)

[All releases](https://github.com/baraa404/waslha-delivery-app/releases/latest)

</div>

Android APK · v1.0.0 · sideload install (allow unknown sources).

---

## 📸 Screenshots

> Screenshots coming soon.

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

## 🌟 Overview

Waslha (وصلة — “connection”) is a two-sided delivery marketplace for shops and anyone sending or receiving a parcel. Customers post a pickup and drop-off. Nearby drivers claim the job, complete it with a QR scan, and get rated. An operations team runs the whole thing from an Arabic RTL admin panel. Sales reps grow the network with referral codes.

This is not a food-delivery clone. It is engineered for **general point-to-point transport** — with server-side fees, vehicle matching, bulk drops, and a real approval pipeline before a driver ever sees work.

---

## 🧠 The features that make it different

### 🗺️ 1. Create a delivery without fighting the map
Pickup and drop-off can be set three ways: paste a **Google Maps link**, drop a pin, or use current location. The app resolves the link to coordinates, draws the route, and shows distance + ETA before the customer confirms.

* **Timing that prices itself:** urgent, later today, or within 2 days — each with a surcharge the platform controls.
* **Bulk in one shot:** one pickup, up to 10 drop-offs, one driver for the whole batch. Extra drops can be discounted automatically.
* **Edit while it's open:** change the route, add/remove drops, or cancel a single leg — surviving legs get re-priced on the server.

### 💰 2. Fees the client cannot fake
Order create / update / cancel / batch-accept go through **callable Cloud Functions**. The server reads live pricing config, snapshots the fee, and writes the order. Clients never create order documents directly.

* **Distance model:** base fee + per km (road distance, straight-line fallback).
* **Flat zone:** inside Greater Amman vs outside — one number, no km math.
* **Country-aware money:** Jordanian dinar or Egyptian pound, following the account country.

### ✅ 3. Completion is a QR scan, not a button
After pickup is confirmed, the customer shows a QR. The driver scans it to close the drop. That is the completion event — not a tap that anyone can mash.

* Customer can **accept or reject** the driver who claimed the job.
* Either side can call the other from the order screen.
* After the trip: rate the driver. A 1★ can hide that customer's future open jobs from that driver.

### 🛵 4. Drivers only see work they can actually do
Go online, and the feed is already filtered: vehicle type, dispatch radius, and (optionally) blocked requesters. Bulk jobs land as one card — drop count + total fee — accepted all-or-nothing.

* Pending screen until **admin approval**. No unvetted driver on the road.
* Today km + earnings at a glance, with full stats (today / week / month / all time).
* ID, license, and conduct documents uploaded during setup.

### 🖥️ 5. Ops actually run the platform
The admin is a Next.js Arabic RTL dashboard, not a Firebase console with extra steps.

* Dashboard: orders today, revenue from completed fees, completion rate, a “needs action” strip (pending drivers, suspended customers, open orders).
* Approve / revoke drivers. Enable / suspend customers.
* Per-driver earnings. Per-merchant commission with receipts and payment history.
* Live switches for pricing model, timing surcharges, bulk discount, dispatch radius, and in-app support numbers.

### 📣 6. Growth is a referral code, not a spreadsheet
Admin-provisioned **sales reps** get a personal code, a dashboard of referred drivers and merchants, and a commission period they can actually collect on. Customers and drivers redeem a code once. Admin can unlink and re-attribute.

---

## 🛠 Tech Stack & Architecture

* **Framework:** Flutter (Dart) — Arabic & English, Cairo typeface, RTL-ready
* **State Management:** `hooks_riverpod`
* **Navigation:** `go_router` with a 4-gate redirect (onboarding → auth → role → setup)
* **Backend:** Firebase Auth, Firestore, Storage, Cloud Functions, FCM
* **Maps:** Google Maps / Places / Routes — plus Maps-link paste → coordinates
* **Admin:** Next.js, Arabic RTL
* **Architecture:** Feature-first (`lib/features/*`) + shared infra (`lib/core/*`)

Auth is Google, email & password (with email-verify gate), and SMS OTP. Phone verification and document uploads sit in front of real work. A remote kill-switch can lock the app if something goes wrong in production.

---

<div align="center">
  <p>
    <strong><a href="README.md">English</a></strong> · <strong><a href="README.ar.md">العربية</a></strong>
  </p>
  <i>Crafted for real operations, not a demo marketplace.</i>
</div>
