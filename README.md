# 🐍 Octanet Python Development Internship — April 2024

Welcome to the **Octanet Python Development Internship (April 2024)** repository! This repository hosts a command-line terminal application engineered to demonstrate core programming proficiency, dynamic control flows, structured logic routing, and state management in Python.

---

## 📂 Repository Structure

```text
OCTANET_PYTHON_APRIL-2024/
│
└── 🏦 ATM machine interface.py   # Main Python terminal script
```

---

## 🚀 Project Overview

### 🏦 ATM Machine Simulator

A comprehensive terminal-based **ATM Interface** mimicking real-world bank transactions such as secure authentication, account balance inquiry, dynamic withdrawals, deposit tracking, and third-party fund transfers.

**Key Features:**
- **Secure Authentication Shield** — Validates user identity using custom matching index logic against parallel credential lists (`user_ID`, `PIN`, `name`).
- **Terminal ATM Interactive Menu** — Loop-based menu selection system enabling seamless user navigation across all banking operations.
- **Withdrawal Module** — Dynamically evaluates the user's available funds, checks against the desired transaction value, and updates the balance accordingly.
- **Deposit Portal** — Performs validation on incoming amounts before updating active account records.
- **Transfer Channel** — Prompts for third-party recipient IDs to simulate inter-account fund transfers.
- **Transaction Ledger** — Displays a chronological list of all actions taken during the active console session.

---

## ⚠️ Technical Bugs & Recommended Fixes

A deep-dive analysis of the codebase reveals three important logic flow issues with clear recommended solutions:

### 1. Immutable Scope Bug (State Persistence)

**The Issue:** Integers are immutable in Python. When `balance` is passed to `withdraw(balance, transactions)` or `deposit()`, modifying it inside the function (e.g., `balance = balance - amount`) only re-binds it to the local function scope. The value of `balance` inside `main()` is never modified, remaining at its default value (`2000`).

**Recommended Fix:** Update functions to return the newly calculated balance and catch the return value in the driver loop:

```python
# Inside withdraw()
return balance - amount

# Inside main() loop:
balance = withdraw(balance, transactions)
```

---

### 2. Missing Ledger Logging

**The Issue:** The `transactions` list is correctly declared in `main()` as `transactions = []`, but none of the transaction actions (`withdraw`, `deposit`, `transfer`) append items to it. Consequently, selecting option `4` (Transaction History) will always display `"No transactions yet."`.

**Recommended Fix:** Append descriptive transaction records when actions succeed:

```python
transactions.append(f"Withdrew: ${amount:.2f}")
```

---

### 3. Hardcoded Authentication Constraint

**The Issue:** The `authenticate()` routine explicitly checks for the name `'Akash S'` using a hardcoded equality: `if pin == PIN[index] and name[index] == 'Akash S':`. This makes it impossible for other accounts in the lists to be authenticated.

**Recommended Fix:** Remove the hardcoded user check to dynamically support any user in the lists:

```python
if pin == PIN[index]:
    return True
```

---

## 🛠️ Tech Stack & Concepts Demonstrated

| Concept | Tool / Tech | Application in Repository |
| :--- | :--- | :--- |
| **Programming Language** | Python 3.x | Console input/output casting, iterative logic, arrays/lists. |
| **Conditional Controls** | `while True` / `if-elif-else` | Coordinates menu selections, input validation, and boundaries. |
| **Data Alignment** | List Indexing | Correlates relational records (`user_ID` ↔ `PIN` ↔ `name`). |
| **State Management** | Function Parameters | Demonstrates mutable vs immutable scope passing. |

---

## 🚀 Local Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/akash02062005/OCTANET_PYTHON_APRIL-2024.git
cd OCTANET_PYTHON_APRIL-2024
```

### 2. Run the Application

```bash
python "ATM machine interface.py"
```

### 3. Default Login Credentials

| Field | Value |
| :--- | :--- |
| **User ID** | `020605` |
| **PIN** | `2005` |

---

## 📄 License

This repository is licensed under the MIT License - see the LICENSE file for details.
