# 🚀 Offline UPI Mesh — Secure Payment Simulation

> A Spring Boot backend simulating **offline UPI payments using mesh networking + cryptographic security**

---

## 🌍 Concept Overview

```
📱 Sender (Offline)
      │
      ▼
🔐 Encrypt (RSA + AES-GCM)
      │
      ▼
📦 Mesh Packet
      │
      ▼
📡 Device-to-Device Gossip
      │
      ▼
📱📱📱 Intermediate Devices
      │
      ▼
🌐 Bridge Device (Internet)
      │
      ▼
☁️ Backend Server
      │
      ▼
💰 Settlement
```

---

## 🏗️ System Architecture

```
┌──────────────────────────────┐
│ 📱 Sender Device             │
│------------------------------│
│ Create Payment               │
│ Encrypt Data 🔐              │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ 📦 Mesh Packet               │
│------------------------------│
│ TTL ⏳                       │
│ Ciphertext 🔒               │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ 📡 Mesh Network              │
│------------------------------│
│ 📱 → 📱 → 📱 → 📱            │
│ Gossip Protocol 🔁           │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ 🌐 Bridge Node               │
│------------------------------│
│ Upload Packet ⬆️             │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│ ☁️ Spring Boot Backend              │
│------------------------------------│
│ Hash → Deduplicate ⚡              │
│ Decrypt 🔓                         │
│ Validate ✔️                        │
│ Settle 💰                         │
└──────────────────────────────────────┘
```

---

## 🔐 Security Flow

```
📄 Payment Data
   │
   ▼
🔑 Generate AES Key
   │
   ▼
🔐 Encrypt Payload (AES-GCM)
   │
   ▼
🔒 Encrypt AES Key (RSA)
   │
   ▼
📦 Final Packet:
[ RSA Key ][ IV ][ Ciphertext ]
```

✔ Tamper-proof  
✔ Confidential  
✔ Authenticated  

---

## ⚡ Transaction Pipeline

```
📥 Packet Received
      │
      ▼
🔍 Hash (SHA-256)
      │
      ▼
⚡ Idempotency Check
      │
      ├── ❌ Duplicate → Drop
      │
      ▼
🔓 Decrypt
      │
      ▼
⏱️ Validate Timestamp
      │
      ▼
💰 Settle Transaction
      │
      ▼
📜 Store in Ledger
```

---

## 🔁 Mesh Gossip Flow

```
Round 1:
📱 A → 📱 B → 📱 C

Round 2:
📱 A → 📱 B → 📱 C → 📱 D → 📱 E

Result:
✔ All devices hold packet
```

---

## 🧠 Problems & Solutions

### ❗ Untrusted Devices
```
📱 Stranger Device
   ❌ Cannot read data
   ❌ Cannot modify data
```
✔ Solution → Encryption 🔐

---

### ❗ Duplicate Transactions
```
📡 Bridge 1 → Backend
📡 Bridge 2 → Backend
📡 Bridge 3 → Backend
```
✔ Solution:
```
Hash → Atomic Check → Only 1 Processed
```

---

### ❗ Replay Attacks
```
Old Packet → Resent ❌
```
✔ Solution:
- Timestamp validation ⏱️  
- Unique nonce 🔑  

---

## 🗄️ Project Structure

```
📦 upi-offline-mesh
│
├── 📁 controller        → API layer
├── 📁 service           → Business logic
├── 📁 model             → Data
├── 📁 crypto            → Encryption 🔐
├── 📁 config            → Setup ⚙️
│
├── 📄 UpiMeshApplication.java  → Entry point 🚀
├── 📄 application.properties   → Config
```

---

## ⚙️ Tech Stack

```
Backend     → Spring Boot
Language    → Java 17
Database    → H2 (In-memory)
Security    → RSA + AES-GCM
Build Tool  → Maven Wrapper
```

---

## 🚀 How to Run

```bash
# Windows
mvnw.cmd spring-boot:run

# Mac/Linux
./mvnw spring-boot:run
```

---

## 🌐 Access

```
http://localhost:8080
```

---

## 🧪 Demo Flow

```
1️⃣ Inject Payment
2️⃣ Run Gossip
3️⃣ Bridge Upload
4️⃣ Settlement
```

---

## 🔗 API Overview

```
GET    /                  → Dashboard
GET    /api/accounts      → Accounts
POST   /api/demo/send     → Send Payment
POST   /api/mesh/gossip   → Gossip
POST   /api/mesh/flush    → Upload
POST   /api/bridge/ingest → Core API
```

---

## ⚠️ Limitations

```
❌ No real bank integration
❌ No real Bluetooth
❌ No authentication
❌ Offline double-spend possible
```

---

## 🚀 Future Improvements

```
✅ Redis for idempotency
✅ Real BLE communication
✅ Authentication (JWT)
✅ Cloud deployment
```

---

## 🎯 Interview Pitch

```
Built a Spring Boot backend simulating offline UPI transactions 
using mesh networking, hybrid encryption (RSA + AES-GCM), and 
idempotent transaction processing for secure and reliable settlement.
```

---

## ⭐ Highlights

```
✔ Distributed System Design
✔ Cryptography Implementation
✔ Concurrency Handling
✔ Real-world Use Case
```

---

## 🏁 Summary

```
Offline → Secure → Distributed → Reliable
```
