
---
layout: single
title: "IQ Test – Raven Matrices (Android Application)"
permalink: /raven-iq-test/
excerpt: "Technical implementation, rendering engine, gameplay system, data storage, monetization modules and auxiliary services of an Android application based on Raven-style matrices."
author_profile: true
toc: true
toc_label: "Contents"
toc_sticky: true
---

This project is an Android application implementing **Raven-style cognitive matrices**, with:

- dynamic matrix generation  
- rendering and layout engine  
- multi-mode gameplay  
- scoring and evaluation system  
- on-device database  
- in-app currency and unlockables  
- monetization via Google Play Billing and AdMob  
- analytics and crash diagnostics  
- multilingual interface  

The app is distributed on Google Play with **130k+ downloads**, **~500 reviews**, and an average rating of **4.5/5**, used globally across many device classes.

➡️ **Google Play page:**  
[IQ Test – Raven Matrices on Google Play](https://play.google.com/store/apps/details?id=com.onebit.iqtestraven)


This page focuses exclusively on the technical aspects of the implementation.

---

# 1. Application Structure

The application is developed in **Java** using Activities and XML layouts.  

Portrait orientation is enforced across the entire app.

---

## 1.1 Matrix Rendering Layer

The rendering engine dynamically composes:

- a 3×3 matrix with one missing tile  
- 2–8 answer options (default: 4)  
- vector-based shapes (VectorDrawable)  
- image-based elements  
- colored cells and line patterns  

Key characteristics:

- resolution-independent vector drawing  
- adaptive layout for varying DPI and screen sizes  
- efficient view invalidation (only changed regions are redrawn)  
- portrait-only rendering logic  

---

## 1.2 Dynamic Matrix Generation

Matrices are **not static**.  
A generation module creates items at runtime using internal templates and rule sets.

Generation features:

- deterministic + randomized components  
- difficulty scaling based on user progression  
- pattern generation for:
  - geometric shapes  
  - colored grids  
  - line-based patterns  
  - mixed visual components  
- internal parameters used as seeds  
- fast loading through local SQLite caching of complex patterns.

The internal generation logic is designed as a modular rule-based system and is not exposed publicly.

---

## 1.3 Test Logic

Each test session includes:

- a sequence of generated or predefined matrices  
- metadata per item:
  - difficulty  
  - category  
  - pattern type  
  - correct answer  
- timers or timer-free behavior (depending on mode)  
- validation of user selections  

Supported transformation families:

- rotations  
- mirroring  
- arithmetic progression  
- symmetry  
- positional logic  
- repetition-based rules  
- color transformations  
- additional internal pattern classes used by the generation module

---

## 1.4 Scoring Module

Local scoring includes:

- correct answer count  
- difficulty-based mapping  
- normalization for the final score  

All evaluation is **offline**, with no network dependency.

---

## 1.5 Persistence Layer

Two systems are used:

### **SharedPreferences**
- feature toggles  
- app settings  
- cached utility data  

### **SQLite (SQLiteOpenHelper)**
- history of completed sessions  
- cached complex patterns for generation  
- level progression  
- stored game statistics (score, time, correct answers, etc.)

All data remains on-device; no personal data is stored.

---

# 2. Gameplay Modes

## 2.1 Standard Mode
- increasing difficulty  
- new levels unlocked sequentially  
- coins awarded for completing matrices  
- dynamic generation for higher levels  

## 2.2 Training Mode
- no timer  
- all hints available  
- designed for practicing pattern recognition  
- unlimited matrix retries  

## 2.3 Survival Mode
- continuous chain of matrices  
- time added for each correct answer  
- failure on incorrect selection or timeout  
- internal leaderboard for consecutive correct items  

---

# 3. In-App Currency and Tools

The app includes a coin-based utility system.

### Users earn coins by:
- solving matrices  
- watching rewarded ads  

### Coins can be exchanged for:
- **50% reduction** (removes half the answers)  
- **Solution** (reveals the correct tile)  
- **Hint** (explanation of the pattern)  
- **Time Boost** (increase the time) 

---

# 4. Achievement & Redeem Systems

## 4.1 Achievement System
Achievements include:

- daily challenges  
- monthly challenges  
- long-term progression goals  
- hint usage tasks  
- correct-answer milestones  

Rewards include coins and unlockables.

## 4.2 Redeem Codes
A dedicated section allows users to enter external codes to obtain:

- coins  
- bonuses  
- hidden rewards  

Codes can be distributed manually or obtained by completing hidden objectives.

---

# 5. Monetization & External Services

## 5.1 Google Play Billing
Supports:

- ad removal purchase  
- optional coin packages  

Billing implementation includes:

- BillingClient
- purchase acknowledgment  
- signature verification  
- consumable and non-consumable products  

## 5.2 AdMob
Supported formats:

- interstitial ads  
- rewarded video ads  

Ad placement uses non-intrusive rules and frequency control.

## 5.3 Firebase Services
Integrated modules:

- **Firebase Crashlytics** for crash diagnostics  
- **Firebase Analytics** for performance and feature usage tracking  

No personal analytics are collected.

---

# 6. Data Storage Details

### **SharedPreferences**
Used for:

- settings  
- configuration flags
- utility caching  

### **SQLite Database**
Used for:

- historical test results  
- cached pattern definitions for faster generation  
- progression data  
- game statistics (levels unlocked, scores, timings, correct answers)  

# 7. Technology Stack

### **Languages**
- Java  

### **Android Components**
- Activities  
- XML layouts  
- Canvas-based custom drawing  
- VectorDrawable rendering  
- SQLiteOpenHelper (custom database helper)  
- SharedPreferences  

### **Libraries**
- Google Play Billing (in-app purchases)  
- Google Play Services (Games, Auth)  
- AdMob (interstitial + rewarded ads)  
- Firebase Analytics  
- Firebase Crashlytics  
- MPAndroidChart (for charts and statistics)  
- Toasty (enhanced toast notifications)  

### Build Configuration
- Based on **Java 17**
- Uses **AndroidX AppCompat** and **Material Components**
- Configured with **MultiDex** support for larger method counts
- Supports a wide range of Android versions (from Android 6.0 upwards)

---

# 8. Reliability & Compatibility

Engineering considerations include:

- consistent rendering across multiple DPI categories  
- efficient handling of vector resources to reduce memory usage  
- prevention of accidental multi-taps  
- stable timer behavior under activity lifecycle events  
- optimized drawing pipeline to avoid unnecessary redraws  
- compatibility across:
  - low-end devices  
  - tablets  
  - non-standard aspect ratios  
  - high-DPI screens  

Crash telemetry is continuously monitored through **Firebase Crashlytics**, allowing quick identification of stability issues on real devices.

---

# 9. Adoption Metrics & User Feedback

### **Installations**
- **130,000+ total downloads**  
- Used globally in regions with multiple language support  

### **Languages Supported**
- English (en)  
- Arabic (ar)  
- German (de)  
- Spanish (es)  
- French (fr)  
- Hindi (hi)  
- Italian (it)  
- Japanese (ja)  
- Korean (ko)  
- Portuguese (pt)  
- Russian (ru)  
- Turkish (tr)  
- Chinese simplified & traditional:
  - zh-rCN  
  - zh-rHK  
  - zh-rSG  
  - zh-rTW  

### **Rating**
- Average rating: **4.5 / 5**  

### **~500 Real User Reviews**
Examples of actual Play Store feedback (quoted verbatim):

- 🇬🇧 **David Jenner** — “Just how a good Raven test should be: starting off easy and getting harder to a standard well beyond the grasp of many, and (in keeping with the original concept) no time limit. A good test of abstract thinking. Love the "insane" icon at 150+! Do remember, however, that it is only a game!!”

- 🇮🇹 **Antonio Cicognara** — “Divertentissima. Il fatto che i pattern siano generati da A.I. li rende spesso dotati di elementi caratteristicamente disorientanti, quindi tali da richiedere molta flessibilità.”

- 🇪🇸 **Henry Jimenez** — “Muy buena aplicación para ejercitar la mente y conocer más de nuestra capacidad mental...”

- 🇩🇪 **N.** — “Best Raven game ever !!! Sämtliche Schwierigkeitsgrade dabei. Wirklich ein tolles Spiel!”

- 🇫🇷 **Bienfait Rukundo** — “Une très bonne application pour jouer et tester sor IQ”

- 🇵🇹 **João Paulo Machado Gomes** — “Absolutamente desafiante. Aconselho vivamente. Parabéns ao programador.”

- 🇷🇺 **Ruslan Khasanov** — “Хорошее приложение, помогает развивать абстрактный интеллект.”

- 🇵🇱 **Adam Mickiewicz** — “Bardzo fajnie zrobiona aplikacja, można sprawdzać swoje IQ”

- 🇯🇵 **中研ロボ太郎** — “まぁまぁ頭の体操になります。”

Reviews come from a wide variety of regions and languages, reflecting global usage.

---

# 10. Deployment

The application is distributed via Google Play.

Deployment details include:

- Gradle-managed versioning (`versionCode` / `versionName`)  
- ProGuard / R8 rules for optimized builds  
- Crashlytics symbol upload during release  
- MultiDex for large method counts  
- ongoing compatibility updates for new Android releases  
- support for both ARM and x86 architectures  

No external backend infrastructure is required; all logic, storage, and gameplay are fully local to the device.

---

# 11. User-Focused Development

The application is actively maintained with a user-feedback-driven approach.  
Feature adjustments, difficulty tuning, and new tools (such as additional hints or training modes) are based on:

- direct user messages  
- Play Store reviews  
- analytics patterns  
- crash and stability reports  

Every update is designed to improve usability, clarity of patterns, and performance across devices, following a continuous refinement process.

---

This section completes the technical overview of the application, covering stack, reliability, usage metrics, and deployment details.
