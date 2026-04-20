<div align="center">

<!-- Animated Banner -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=venom&height=200&text=StockPulse&fontSize=80&color=0:0f2027,50:203a43,100:2c5364&stroke=00d4aa&strokeWidth=2&fontColor=00d4aa&animation=fadeIn&fontAlignY=55&desc=Real-Time%20Stock%20Trading%20Platform&descSize=18&descAlignY=75&descColor=ffffff"/>

<br/>

<!-- Badges Row 1 -->
![Java](https://img.shields.io/badge/Java_17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-00758F?style=for-the-badge&logo=mysql&logoColor=white)
![Thymeleaf](https://img.shields.io/badge/Thymeleaf-005F0F?style=for-the-badge&logo=thymeleaf&logoColor=white)

<!-- Badges Row 2 -->
![Alpha Vantage](https://img.shields.io/badge/Alpha_Vantage-FF6B35?style=for-the-badge&logo=databricks&logoColor=white)
![TradingView](https://img.shields.io/badge/TradingView_Charts-131722?style=for-the-badge&logo=tradingview&logoColor=4CAF50)
![Maven](https://img.shields.io/badge/Apache_Maven-C71A36?style=for-the-badge&logo=apache-maven&logoColor=white)
![Gmail SMTP](https://img.shields.io/badge/Gmail_SMTP-EA4335?style=for-the-badge&logo=gmail&logoColor=white)

<br/>

<!-- Stats Badges -->
![Status](https://img.shields.io/badge/Status-Active-00d4aa?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)
![PRs](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)

</div>

---

## 📌 Overview

> **StockPulse** is a full-featured, production-grade stock trading platform built with **Java Spring Boot**. It simulates a real-world brokerage — allowing users to manage portfolios, execute buy/sell orders, track investments with live charts, and automate stop-loss/gain triggers — all powered by real financial market data.

Think **Zerodha** meets **Groww** — built from scratch with Java.

---

## ✨ Feature Highlights

<table>
<tr>
<td width="50%">

### 👤 User Management
- ✅ Secure Registration & Login
- ✅ Email Verification via Gmail SMTP
- ✅ Bcrypt Password Hashing
- ✅ Nominee Management
- ✅ Profile & Account Settings

</td>
<td width="50%">

### 📈 Trading Engine
- ✅ Real-Time Stock Prices (Alpha Vantage)
- ✅ Buy & Sell Orders
- ✅ Live Market Status
- ✅ Stop-Loss & Target Automation
- ✅ Scheduled Price Monitoring

</td>
</tr>
<tr>
<td width="50%">

### 📊 Analytics & Charts
- ✅ TradingView Professional Charts
- ✅ Technical Analysis (RSI, MACD, etc.)
- ✅ Fundamental Analysis Tools
- ✅ Portfolio Performance Charts
- ✅ Investment Breakdown Visuals

</td>
<td width="50%">

### 🗂️ Portfolio & History
- ✅ Real-Time Portfolio Tracking
- ✅ P&L Calculation
- ✅ Full Transaction History
- ✅ DataTables with Search & Sort
- ✅ Email Notifications on Triggers

</td>
</tr>
</table>

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                   CLIENT BROWSER                    │
│         HTML5 · CSS3 · JavaScript · Thymeleaf       │
└─────────────────────┬───────────────────────────────┘
                      │ HTTP Requests
┌─────────────────────▼───────────────────────────────┐
│              SPRING BOOT APPLICATION                │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌───────────┐  │
│  │ Controllers │  │   Services   │  │Schedulers │  │
│  │  (MVC Layer)│  │(Business Logic│  │(Stop Loss)│  │
│  └──────┬──────┘  └──────┬───────┘  └─────┬─────┘  │
│         └────────────────┼────────────────┘        │
│                   ┌──────▼──────┐                   │
│                   │ JDBC Layer  │                   │
│                   └──────┬──────┘                   │
└──────────────────────────┼──────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────┐
│                    MySQL Database                   │
│        Users · Stocks · Orders · Portfolio          │
└─────────────────────────────────────────────────────┘
                           │
        ┌──────────────────┼─────────────────┐
        ▼                  ▼                 ▼
  Alpha Vantage       TradingView        Gmail SMTP
  (Live Prices)       (Charts)           (Alerts)
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Language** | Java 17 |
| **Framework** | Spring Boot |
| **Frontend** | HTML5, CSS3, JavaScript, Thymeleaf |
| **Database** | MySQL |
| **ORM** | JDBC Template |
| **Market Data** | Alpha Vantage API |
| **Charts** | TradingView CDN |
| **Email** | Gmail SMTP |
| **Tables** | DataTables.js |
| **Build Tool** | Apache Maven |
| **Server** | Apache Tomcat 9.0+ |

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

```bash
✔ Java JDK 17+
✔ Apache Maven
✔ MySQL 8.0+
✔ Apache Tomcat 9.0+
✔ Eclipse IDE (or IntelliJ IDEA)
```

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/kishor-23/trading-application.git
cd trading-application
```

**2. Set up the database**
```bash
# Open MySQL Workbench and run:
source /path/to/trading_app.sql
```

**3. Configure `application.properties`**
```properties
# Database
spring.datasource.url=jdbc:mysql://localhost:3306/trading_db
spring.datasource.username=YOUR_DB_USERNAME
spring.datasource.password=YOUR_DB_PASSWORD

# Server
server.port=9000

# Alpha Vantage (Get free key at alphavantage.co)
alphavantage.api.key=YOUR_API_KEY

# Gmail SMTP
spring.mail.username=YOUR_GMAIL
spring.mail.password=YOUR_APP_PASSWORD
```

**4. Build & Run**
```bash
mvn clean install
mvn spring-boot:run
```

**5. Open in browser**
```
http://localhost:9000
```

---

## 📸 Screenshots

> _Add your app screenshots here — Dashboard, Trade Page, Portfolio, Charts_

| Dashboard | Trade Execution | Portfolio |
|-----------|----------------|-----------|
| ![Dashboard](https://via.placeholder.com/280x160/0f2027/00d4aa?text=Dashboard) | ![Trade](https://via.placeholder.com/280x160/0f2027/00d4aa?text=Buy+%2F+Sell) | ![Portfolio](https://via.placeholder.com/280x160/0f2027/00d4aa?text=Portfolio) |

---

## 📄 Documentation

| Resource | Link |
|----------|------|
| 📘 User Manual | [View Google Doc](https://docs.google.com/document/d/1uDWNu_nVZg_WMPRmFp8GpiPK8FkmjQl9L7_3Mycwurc/edit?usp=sharing) |
| 🎯 Presentation | [View Slides](https://docs.google.com/presentation/d/1T7-Wp_bDQAtGXZUVn_fbNRWOEe6S2-QqE0tqOGsPo98/edit?usp=sharing) |
| 📊 Alpha Vantage API | [API Docs](https://www.alphavantage.co/documentation/) |
| 📉 TradingView | [Charts Docs](https://www.tradingview.com/) |

---

## 🤝 Contributing

Contributions are welcome! Here's how:

```bash
# 1. Fork the project
# 2. Create your feature branch
git checkout -b feature/AmazingFeature

# 3. Commit your changes
git commit -m 'Add some AmazingFeature'

# 4. Push to the branch
git push origin feature/AmazingFeature

# 5. Open a Pull Request
```

---

## 📃 License

Distributed under the MIT License. See `LICENSE` for more information.

---

<div align="center">

**Built with ☕ Java & 💚 Spring Boot**

⭐ **Star this repo if you found it helpful!** ⭐

</div>