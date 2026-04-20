# 📈 EasyTrade — Stock Trading Application

A full-stack stock trading web application built with **Spring Boot**, **MySQL**, and **Thymeleaf**. ChainTrade allows users to register, manage a portfolio, buy/sell stocks, track transactions, and interact with an AI-powered chatbot — all within a clean, session-based web interface.

---

## 🚀 Features

- **User Authentication** — Register, login, and logout with session management and BCrypt password hashing
- **Portfolio Management** — View holdings, track profit/loss per stock, filter by category, and set stop-loss / stop-gain thresholds
- **Stock Trading** — Browse paginated/searchable stock listings, view individual stock details with live chart data, and execute buy/sell transactions
- **Transaction History** — Full transaction ledger per user with email confirmations on each trade
- **Trending Stocks** — Real-time leaderboard of top-bought, top-sold, and most-traded stocks
- **Live Market Data** — Scrapes live NSE India index data using Jsoup
- **AI Chatbot** — Powered by Google Gemini 1.5 Flash; supports text and image inputs
- **Nominee Management** — Add, update, and delete account nominees (name + phone number)
- **Profile Management** — Upload/update profile picture, add wallet funds, view account details
- **Scheduled Jobs** — Automated stop-loss/stop-gain checks run every minute via a stored procedure
- **API Documentation** — Swagger UI available at `/swagger-ui.html`
- **Email Notifications** — Welcome emails on registration, trade confirmation emails via Gmail SMTP

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Java 17, Spring Boot 2.7.18 |
| Web Layer | Spring MVC, Thymeleaf |
| Database | MySQL (Spring JDBC / JdbcTemplate) |
| Security | Spring Security Crypto (BCrypt) |
| Sessions | Spring Session Core |
| Email | Spring Boot Mail (Gmail SMTP) |
| AI Chatbot | Google Gemini API (gemini-1.5-flash) |
| Market Data | Jsoup (NSE India scraping) |
| API Docs | Springfox Swagger 2 |
| Build Tool | Maven |
| Utilities | Lombok, Jackson |

---

## 📋 Prerequisites

- **Java 17+**
- **Maven 3.6+**
- **MySQL 8+**
- A **Gmail account** with App Password enabled (for email features)
- A **Google Gemini API key** (for chatbot features)

---

## ⚙️ Setup & Installation

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd trading-application
```

### 2. Create the MySQL database

```sql
CREATE DATABASE trading_db_1;
```

> The application uses `trading_db_1` by default. Ensure the `checkStopLossAndGain()` stored procedure exists in the database, as it is called every minute by the scheduler.

### 3. Configure `application.properties`

Open `src/main/resources/application.properties` and fill in all the required values:

```properties
# Database
spring.datasource.url=jdbc:mysql://localhost:3306/trading_db_1
spring.datasource.username=YOUR_DB_USERNAME
spring.datasource.password=YOUR_DB_PASSWORD

# Mail (Gmail SMTP)
spring.mail.username=YOUR_GMAIL_ADDRESS
spring.mail.password=YOUR_GMAIL_APP_PASSWORD

# Google Gemini API
google.api.key=YOUR_GEMINI_API_KEY
```

> ⚠️ **Never commit real credentials to version control.** Use environment variables or a secrets manager in production.

### 4. Build and run

```bash
./mvnw spring-boot:run
```

Or build a JAR first:

```bash
./mvnw clean package
java -jar target/tradingapp-0.0.1-SNAPSHOT.jar
```

### 5. Access the application

Open your browser and navigate to:

```
http://localhost:9000
```

---

## 📁 Project Structure

```
trading-application/
├── src/
│   └── main/
│       ├── java/com/chainsys/tradingapp/
│       │   ├── config/          # Swagger configuration
│       │   ├── controller/      # MVC controllers (User, Stock, Portfolio, Transaction, Nominee, Chatbot, MarketData)
│       │   ├── dao/             # DAO interfaces + JDBC implementations
│       │   ├── dto/             # Data Transfer Objects (Portfolio, Profile, Stock, etc.)
│       │   ├── exception/       # Global exception handler, custom exceptions
│       │   ├── mapper/          # Spring JDBC RowMappers
│       │   ├── model/           # Domain models (User, Stock, Portfolio, Transaction, Nominee)
│       │   ├── service/         # Business logic (User, Portfolio, Transaction, Chatbot, Email, etc.)
│       │   ├── validation/      # Input validation utilities
│       │   └── TradingappApplication.java
│       └── resources/
│           ├── application.properties
│           ├── static/          # Frontend assets (images, JS libraries)
│           └── templates/       # Thymeleaf HTML templates
├── pom.xml
└── mvnw / mvnw.cmd
```

---

## 🔗 Key URL Routes

| Route | Method | Description |
|---|---|---|
| `/` | GET | Home page |
| `/register` | GET / POST | User registration |
| `/login` | GET / POST | User login |
| `/logout` | GET | Invalidate session and redirect to login |
| `/profile` | GET | User profile with wallet balance and nominees |
| `/stocks` | GET | Paginated, searchable, filterable stock listing |
| `/stockDetails` | GET | Individual stock detail page |
| `/StockTransaction` | POST | Execute a buy or sell transaction |
| `/transactions` | POST | View transaction history for a user |
| `/portfolio` | GET | Portfolio overview with P&L |
| `/trendingstocks` | GET | Top-bought, top-sold, and most-traded stocks |
| `/liveMarket` | GET | Live NSE market data page |
| `/chatbot` | GET | AI chatbot page (Gemini-powered) |
| `/nominee/add` | POST | Add a nominee |
| `/addMoney` | POST | Add funds to wallet |
| `/swagger-ui.html` | GET | Swagger API documentation |

---

## 🔒 Security Notes

- Passwords are hashed using **BCrypt** via Spring Security Crypto — plain-text passwords are never stored.
- Sessions are invalidated on logout with cache-control headers to prevent back-button access.
- PAN card duplication and invalid inputs are caught by a global exception handler.

---

## 🤖 AI Chatbot

The chatbot is integrated with **Google Gemini 1.5 Flash**. It supports:
- Plain text queries about stocks, trading strategies, or any topic
- Image + text inputs for visual analysis

Set your API key in `application.properties` under `google.api.key`.

---

## 📧 Email Configuration

The app uses Gmail SMTP on port 587 with STARTTLS. To enable it:

1. Enable **2-Step Verification** on your Google account.
2. Generate an **App Password** under Google Account → Security → App Passwords.
3. Use that app password as `spring.mail.password` in `application.properties`.

---

## 🕐 Scheduled Tasks

A background task runs **every minute** and calls the `checkStopLossAndGain()` MySQL stored procedure. This procedure automatically triggers sell orders when a stock in a user's portfolio crosses their configured stop-loss or stop-gain threshold.

Make sure this stored procedure is created in your database before starting the application.

---

## 📖 API Documentation

Swagger UI is available at:

```
http://localhost:9000/swagger-ui.html
```

---

## 🐛 Known Issues / TODO

- Swagger 2 (`springfox`) has a known compatibility issue with Spring Boot 2.6+; `spring.mvc.pathmatch.matching-strategy=ant-path-matcher` is already set as a workaround.
- Market data scraping from NSE India (`Jsoup`) may break if the NSE website structure changes.
- Database credentials and API keys must be configured manually — there is no `.env` file support out of the box.

---

## 📄 License

This project was developed as a demo/training application by **ChainSys**. See the repository for licensing details.
