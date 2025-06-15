## 🔗 Project Title: Dmoney API Chaining with JMeter

### 📝 Project Summary

This project demonstrates a robust **API Chaining** strategy using **Apache JMeter**, tailored for testing the Dmoney financial system. The test flow simulates a realistic chain of operations where:

- An **Admin** logs in and generates a token (executed once)
- **Agents** perform deposit transactions for customers
- **Customers** send money to other customers
- **Customers** make payments to merchants

All actions are connected via dynamic data and token sharing, emulating real-life transaction flows in a fintech environment. The system uses **CSV test data**, **JSON extractors**, and **response assertions** to ensure correctness and reliability of each chained request.

---

### 🔧 Technologies & Tools Used

| Tool/Platform          | Purpose                                       |
|------------------------|-----------------------------------------------|
| **Apache JMeter**      | Performance testing and API chaining          |
| **CSV Data Config**    | External dynamic data for roles & accounts    |
| **JSON Extractor**     | Extract tokens for authorization              |
| **Response Assertion** | Validates response status and body content    |
| **HTML Report**        | Summary and statistics of test executions     |

---
### 🧾 Test Plan Overview

- 🧵 **Threads**: 3 (Deposit, SendMoney, Payment)
- ⏱️ **Ramp-up Time**: 120 seconds per group
- 🔁 **Loops**: Configurable (default: 1)
- 🔐 **Token Auth**: Extracted via JSON Extractor, passed via Header Manager
- 📈 **Assertions**: Ensure all transactions return status `200` and success messages

---
### ⚙️ How to Run This Project

#### 1. 📥 Clone the Repository

```bash
git clone https://github.com/your-username/dmoney-api-chaining.git
cd dmoney-api-chaining
```

#### 2. 🧪 Open with Apache JMeter

1. Open JMeter (v5.6.3 or later)
2. Load the `dmoney.jmx` file
3. Ensure `deposit.csv`, `sendMoney.csv`, and `payment.csv` are in the same folder

#### 3. 🛠️ Execute the Test Plan

- The **Admin login request** runs once and shares a token across all threads
- The test plan consists of 3 chained Thread Groups:
- `Deposit Thread Group` (5 agents → 10 customers)
- `SendMoney Thread Group` (5 senders → 10 receivers)
- `Payment Thread Group` (5 customers → 2 merchants)
- Each group uses its corresponding CSV file

---
### 🔄 API Chaining Logic

1. **Login as Admin → Extract Token**
2. **Use Token in Header → Start Deposit Thread Group**
3. **Continue to SendMoney Thread Group**
4. **Complete with Payment Thread Group**
5. All requests assert success response (`200 OK` + expected message)

---

### 📂 Repository Contents

| File/Folder              | Description                                      |
|--------------------------|--------------------------------------------------|
| `dmoney.jmx`             | Main JMeter test plan with API chaining logic    |
| `deposit.csv`            | Agent and customer accounts for deposits         |
| `sendMoney.csv`          | Sender and receiver accounts                     |
| `payment.csv`            | Customer and merchant data for payments          |
| `reports/html-report/`   | JMeter-generated HTML report                     |
| `screenshots/`           | Screenshots of test summary and performance data |

---
### 🖼️ Sample Report Screenshot

![image](https://github.com/user-attachments/assets/eb55d6d6-3bd0-46d8-949e-bbcdda7324e6)

---
### 🤝 Contributors

- **[Md Rafsan Mahmud](https://github.com/MdRafsanMahmud)** – Creator, QA Tester  
- **[Salman Rahman](https://github.com/salmansrabon)** – Reviewer / Contributor [LinkedIn](https://www.linkedin.com/in/kmsalmanrahman/)
---
### 👤 Author

- **Md Rafsan Mahmud** 🔗 [LinkedIn](https://www.linkedin.com/in/mdrafsanmahmud/)
- ✉️ [Email](mailto:mdrafsanmahmud99@gmail.com)
---

### ⭐ Final Notes

This project highlights strengths in:

- API chaining using JMeter
- Test data design and dynamic token reuse
- Assertions and report generation
- Real-world scenario simulation for fintech systems

