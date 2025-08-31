# 🌍 Travel Tracker

![Node.js](https://img.shields.io/badge/Node.js-18.x-green?logo=node.js)
![Express](https://img.shields.io/badge/Express.js-4.x-lightgrey?logo=express)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?logo=postgresql)
![License](https://img.shields.io/badge/License-MIT-yellow)

A simple **Node.js + Express + EJS** app to track the countries you’ve visited on an interactive world map.  
Data is stored in **PostgreSQL** using two tables: all countries and visited countries.

---

## 🖼️ Preview
<img width="1879" height="893" alt="Screenshot 2025-08-31 222211" src="https://github.com/user-attachments/assets/1bca43e2-56d0-47b5-9855-8401dbe0a2b0" />

---

## 🚀 Setup

### 1. Clone & install
```bash
git clone https://github.com/Thejanu/Travel-Tracker.git
cd Travel-Tracker
npm install
```

### 2. Create PostgreSQL database
```bash
createdb world
psql world
```

Run:
```sql
CREATE TABLE countries (
  country_code VARCHAR(2) PRIMARY KEY,
  country_name VARCHAR(100) NOT NULL
);

CREATE TABLE visited_countries (
  id SERIAL PRIMARY KEY,
  country_code VARCHAR(2) REFERENCES countries(country_code) UNIQUE
);
```

### 3. Import CSV data
Inside `psql`:
```sql
\copy countries(country_code, country_name) FROM './database/countries.csv' DELIMITER ',' CSV HEADER;
\copy visited_countries(country_code) FROM './database/visited_countries.csv' DELIMITER ',' CSV HEADER;
```

### 4. Add `.env`
```env
DB_USER=postgres
DB_HOST=localhost
DB_NAME=world
DB_PASSWORD=yourpassword
DB_PORT=5432
```

### 5. Run the app
```bash
node index.js
```

Go to 👉 [http://localhost:3000](http://localhost:3000)

---

## ✨ Features
- Add visited countries
- Highlights them on the map
- Shows total count
- Handles errors & duplicates

---

## 🧑 Author
**Thejanu Shanthusha**  
[GitHub](https://github.com/Thejanu)
