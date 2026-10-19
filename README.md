# ⚡ Multi-Payment Method Dispatcher & Consolidation

[![n8n workflow](https://img.shields.io/badge/n8n-Workflow-orange.svg)](https://n8n.io)
[![Sequence](https://img.shields.io/badge/Sequence-%2304-blue.svg)](#)
[![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-green.svg)](#)
[![Status](https://img.shields.io/badge/Status-Production--Ready-brightgreen.svg)](#)

> **Workflow Sequence #04** in the [Maheen Azhar n8n Workflow Collection](https://github.com/maheenazhar/n8n-workflows-collection).

---

## 📖 Overview

Processes payment records through multiple payment gateways/methods via Switch node routing, merging disparate execution streams and dispatching consolidated confirmation emails.

### 🎯 Key Use Case
Handling diverse billing types (e.g., Stripe, PayPal, Wire, Crypto) in a unified automated order-processing flow.

---

## 🏗️ Architecture & Flow

```mermaid
graph TD
  N0_Google_Sheets_Trigger["Google Sheets Trigger<br><i>(googleSheetsTrigger)</i>"]
  N1_Switch["Switch<br><i>(switch)</i>"]
  N2_Send_a_message["Send a message<br><i>(gmail)</i>"]
  N3_Send_a_message1["Send a message1<br><i>(gmail)</i>"]
  N4_Send_a_message2["Send a message2<br><i>(gmail)</i>"]
  N5_Merge["Merge<br><i>(merge)</i>"]
  N6_Send_a_message3["Send a message3<br><i>(gmail)</i>"]
  N0_Google_Sheets_Trigger --> N1_Switch
  N1_Switch -->|branch 1| N2_Send_a_message
  N1_Switch -->|branch 2| N3_Send_a_message1
  N1_Switch -->|branch 3| N4_Send_a_message2
  N2_Send_a_message --> N5_Merge
  N3_Send_a_message1 --> N5_Merge
  N4_Send_a_message2 --> N5_Merge
  N5_Merge --> N6_Send_a_message3
```

---

## 🧩 Nodes in this Workflow

| # | Node Name | Type | Version |
|---|-----------|------|---------|
| 1 | **Google Sheets Trigger** | `n8n-nodes-base.googleSheetsTrigger` | v1 |
| 2 | **Switch** | `n8n-nodes-base.switch` | v3.4 |
| 3 | **Send a message** | `n8n-nodes-base.gmail` | v2.2 |
| 4 | **Send a message1** | `n8n-nodes-base.gmail` | v2.2 |
| 5 | **Send a message2** | `n8n-nodes-base.gmail` | v2.2 |
| 6 | **Merge** | `n8n-nodes-base.merge` | v3.2 |
| 7 | **Send a message3** | `n8n-nodes-base.gmail` | v2.2 |

---

## 🔑 Prerequisites & Credentials

Before running this workflow, ensure you have the following configured in your n8n environment:

- [ ] **Google Sheets trigger source**
- [ ] **Gmail credential**
- [ ] **Multi-payment tracking spreadsheet**

> [!NOTE]
> All credentials are decoupled from this export file for security. When importing into your n8n workspace, re-assign your local credentials in the respective node configuration panels.

---

## 🚀 Setup & Installation

1. **Clone or Download:**
   ```bash
   git clone https://github.com/maheenazhar/n8n-04-multi-payment.git
   cd n8n-04-multi-payment
   ```
2. **Import into n8n:**
   - Open your n8n canvas.
   - Click the top-right menu `...` -> **Import from File**.
   - Select `workflow.json` from this repository.
   - *(Alternative)*: Open `workflow.json`, copy the entire JSON contents, and paste directly (`Ctrl+V`) onto the n8n canvas.
3. **Configure Credentials:**
   - Open each integration node marked with a red credential prompt.
   - Select or configure your accounts (e.g., Google OAuth, Groq API, Supabase, SMTP).
4. **Activate / Test:**
   - Click **Test step** or **Execute Workflow** to verify end-to-end functionality.
   - Toggle the workflow to **Active** for live production use.

---

## 📄 File Structure

```
04-multi-payment/
├── workflow.json   # Full exportable n8n workflow definition
├── README.md       # Comprehensive documentation and architecture
└── .gitignore      # Standard Git exclusions
```

---

## 👤 Author & Repository

- **Author:** [Maheen Azhar](https://github.com/maheenazhar)
- **Workflow ID:** `VjFNiMxp7Yp2YoUJ`
- **Created Date:** `2026-10-08 03:22:59.418`
- **Last Modified:** `2026-10-08 03:51:19.564`
- **Repository:** [`https://github.com/maheenazhar/n8n-04-multi-payment`](https://github.com/maheenazhar/n8n-04-multi-payment)

---

*Part of the [n8n Workflows Collection](https://github.com/maheenazhar/n8n-workflows-collection) by Maheen Azhar.*
