# 📧AI Email Assistant (n8n Workflow)
![n8n](https://img.shields.io/badge/n8n-workflow-orange)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4.1--mini-blue)
![License](https://img.shields.io/badge/license-MIT-green)

An AI-powered email automation workflow built with n8n that automatically reads incoming customer emails, understands their intent, and replies with intelligent, context-aware responses — all without any manual effort.

---

## 🚀 What It Does

This workflow acts as a 24/7 AI sales and support assistant for a lighting business. It:

- Monitors the Gmail inbox every minute for new emails
- Passes the email to an AI agent (GPT-4.1 mini) that understands the customer's intent
- Automatically replies to the customer with a professional, personalised response
- Manages customer bookings and product enquiries via Google Sheets
- Handles new WooCommerce/store orders by sending order confirmation emails automatically

---

## ⚙️ Workflow Overview

```
Gmail Trigger (every 1 min)
        ↓
AI Email Agent (GPT-4.1 mini)
   ├── Reads product stock from Google Sheets
   ├── Reads / adds / deletes customer details in Google Sheets
   └── Maintains conversation memory (last 25 messages)
        ↓
Gmail Reply Node (auto-replies to original email)
```

---

## 🧠 AI Agent Capabilities

The AI agent is prompted to act as a professional sales and support representative for **Sheraton Lighting**. It can:

| Capability | Details |
|---|---|
| Product enquiries | Fetches relevant in-stock products from Google Sheets and recommends 3–4 options |
| Customer onboarding | Collects customer name, phone number, and requirements before proceeding |
| Booking management | Saves bookings (name, phone, product, date) to Google Sheets |
| Booking cancellation | Deletes a customer's booking row from Google Sheets on request |
| New order handling | Detects new orders from email subject, extracts order details, and sends confirmation |
| Conversation memory | Remembers the last 25 messages in the conversation for context |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **n8n** | Workflow automation platform |
| **Gmail API (OAuth2)** | Trigger on new emails + send replies |
| **OpenAI GPT-4.1 mini** | AI language model powering the agent |
| **Google Sheets API** | Product stock, customer details, bookings |
| **n8n Memory Buffer** | Stores conversation context (window of 25 messages) |

---

## 📊 Google Sheets Structure

This workflow connects to two Google Sheets:

**Sheet 1 — SalesLead (Customer Details tab)**
| Column | Description |
|---|---|
| customer name | Full name of the customer |
| customer phone number | Contact number |
| customer's ordered product | Product they booked |
| customer's product booking date | Date of booking |

**Sheet 2 — Sheraton Lighting Stock**
| Column | Description |
|---|---|
| Product name | Name of the lighting product |
| Stock status | In stock / Out of stock |
| Other product details | Specs, pricing etc. |

---

## 📥 How to Import This Workflow

1. Download the `Sharan_s_email_assistant_V3__final.json` file
2. Open your n8n instance
3. Click **"+"** to create a new workflow
4. Click the **3 dots menu (⋯)** → **"Import from file"**
5. Select the downloaded `.json` file
6. Set up your own credentials (see below)

---

## 🔑 Credentials You Need to Set Up

Before running this workflow, replace the following credentials with your own:

- **Gmail OAuth2** — connect your Gmail account under `Credentials → Gmail OAuth2`
- **OpenAI API** — add your OpenAI API key under `Credentials → OpenAI`
- **Google Sheets OAuth2** — connect your Google account and update the Sheet IDs to point to your own sheets

> ⚠️ Never share your credentials or commit them to GitHub. The workflow JSON contains credential **names only**, not the actual keys.

---

## 💡 Key Features

- **Fully automated** — no manual intervention needed once active
- **Context-aware replies** — remembers previous messages in the conversation thread
- **Order detection** — automatically identifies new orders from email subject line
- **Smart data handling** — only saves customer data when all required fields are collected
- **Professional tone** — responses are friendly, concise (20–70 words), and on-brand

---

## ⚠️ Known Limitations

- Session memory is currently fixed to a single key — works best for 
  single-threaded email conversations
- No spam filtering — all incoming emails trigger the agent
- Google Sheets will hit performance limits at high volume

---

## ✅ Prerequisites

- A running n8n instance (cloud or self-hosted)
- A Gmail account with OAuth2 enabled
- An OpenAI API key
- Two Google Sheets set up matching the structure below

---


## 👨‍💻 Built By

**Sharan** — n8n Certified (Level 1 & 2) | AI Automation Engineer  
📍 Thiruvananthapuram, Kerala, India
