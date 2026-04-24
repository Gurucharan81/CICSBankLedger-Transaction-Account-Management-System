🏗️ 🔁 COMPLETE FLOW
🔐 1. LOGIN MODULE
Program: IBNKLOG
Validates credentials from User File
On success:
Passes UserID via COMMAREA
Transfers control using XCTL
🏠 2. HOME / DASHBOARD
Program: IBNKHM2
Displays options:
Account Management
Transaction Operations
View History
📋 3. MENU CONTROLLER
Program: IBNKDTL3
Central routing logic:
Based on user input (AID keys / options)
Routes to:
CRUD modules
Transaction module
History module
🔷 🔹 CORE FUNCTIONAL MODULES
💳 4. ACCOUNT MANAGEMENT
➕ Add Account (IBNKADD)
Creates new record in KSDS (IDTFL)
Initial balance set
🔥 ALSO:
Writes entry to Transaction History File
(Event: "ACCOUNT CREATED")
📖 Read Account (IBNKREAD)
Displays:
Account details
Current balance
✏️ Update Account (IBNKUPDT)
READ ... UPDATE
Modify fields → REWRITE
🔥 ALSO:
Logs update event in history
❌ Delete Account (IBNKDEL)
Deletes record
🔥 ALSO:
Logs "ACCOUNT CLOSED" in history file
🔷 🔹 💰 5. TRANSACTION PROCESSING (MISSING PIECE EARLIER)

👉 This is what makes your project complete

💸 Transaction Module (NEW / SHOULD EXIST)

Handles:

Deposit
Withdrawal
Flow:
Read account
Update balance
Rewrite record
Write transaction log
🧾 Transaction Record Example:
Account ID
Transaction Type (CR/DR)
Amount
Timestamp
Balance After Txn
🔷 🔹 📊 6. TRANSACTION HISTORY MODULE

👉 This was missing earlier — VERY IMPORTANT

📜 View History (IBNKHIST - Suggested)
Reads from History File (TSQ / KSDS / ESDS)
Displays:
Last N transactions
Sorted by time
🔷 🔹 🗂️ FILE DESIGN (UPDATED)
1. Account File (KSDS)
File: IDTFL
Key: Account ID
Data:
Name
Balance
Details
2. Transaction History File (NEW)

You can design as:

Option 1: KSDS
Key: AccountID + Timestamp
Option 2: ESDS
Sequential transaction log
Option 3: TSQ (Temporary Storage)
For session-based history display