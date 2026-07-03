# ⚡ WhatsApp Web-X

A lightweight, production-grade WhatsApp Web simulation engineered for real-time messaging latency and seamless device responsiveness. Built with **Next.js 15 (App Router)** and **Node.js/Express**, it interfaces directly with real-time sockets and webhook event streams to deliver full-fidelity chat operations.

---

## 🚀 Key Framework Features

### Frontend Engine

* **Pixel-Perfect Fidelity:** Responsive layout adapting fluently across ultra-wide desktop monitors down to mobile viewports using **Tailwind CSS 4.0** and **shadcn/ui**.
* **Stateful Sync & Indicators:** Instant message state updates, dynamic typing signals, and true delivery tracing: Sent (✓), Delivered (✓✓), Read (✓✓).
* **Interactive UI Layers:** Built-in dark mode toggle, full-text client-side message filtering, native emoji popovers, and layout skeleton pre-loaders.

### Backend & Event Streaming

* **Event-Driven Architecture:** Managed **Socket.IO** server guaranteeing minimal latency overhead for state transitions and user online/offline streams.
* **Flexible Ingestion Webhooks:** Built-in validation schema to process automated payload payloads natively conforming to the official WhatsApp Business API format.
* **Data Persistence Engine:** Structured schema layers in **MongoDB/Mongoose** explicitly indexed by user identifier arrays and Unix timestamps for optimized querying.

---

## 🛠️ Unified Core Stack

### Frontend Architecture

* **Core:** Next.js 15.4.5 (App Router) + React 19.1.0
* **Styles:** Tailwind CSS 4.0 + Radix UI Primitives
* **Sockets:** Socket.IO Client 4.8.1

### Backend Environment

* **Runtime:** Node.js + Express.js 4.18
* **Database:** MongoDB Atlas + Mongoose 8.0
* **Real-time Engine:** Socket.IO 4.7.4

---

## ⚡ Instant Initialization

### 1. Unified Environment Setup

Configure database interfaces and application endpoint routing.

```env
# Backend Environment Settings (.env)
MONGODB_URI=mongodb://localhost:27017/whatsapp_x
PORT=5000
NODE_ENV=development
CORS_ORIGINS=http://localhost:3000

# Optional Webhook Testing Primitives
WEBHOOK_VERIFY_TOKEN=your_token_here

```

```env
# Frontend Environment Settings (.env.local)
NEXT_PUBLIC_API_URL=http://localhost:5000

```

### 2. Execution Run-Commands

#### Local Machine Setup

```bash
# Terminal 1: Spin up the Api & Socket Server
cd backend
npm install
npm run seed     # Populate mockup telemetry
npm run dev      # Hot-reloading server execution

# Terminal 2: Initialize Web Framework
# from the root folder
npm install
npm run dev      # App starts on http://localhost:3000

```

#### Automation Shell Scripting

```bash
# Automated Linux/macOS setup tool
chmod +x setup.sh && ./setup.sh

# Windows Command Line Tool
setup.bat

```

---

## 📡 API Routing Topology

### Core Message Tracing

* `GET /health` ➔ Yields system lifecycle states and DB connectivity verification.
* `GET /api/chats` ➔ Aggregates global thread lists organized by account IDs.
* `GET /api/chats/:wa_id` ➔ Returns sequential chronological message logs.
* `POST /api/send` ➔ Dispatches outgoing text or document objects.
* `POST /api/chats/:wa_id/read` ➔ Forces instant status transitions to **Read**.

### Integration Webhooks

* `GET /webhook` ➔ Intercepts verification challenges from external messaging gateways.
* `POST /webhook` ➔ Processes raw streaming message payloads into storage structures.

---

## 🔄 Live Telemetry Mocking

To validate pipeline efficiency and UI rendering under stress, spin up the background simulation workers:

```bash
cd backend
# Starts standard socket injection telemetry
npm run realtime-demo

# Emits an endless stream of sequential mock transactions
npm run realtime-continuous

```

---

## 🗄️ Normalized Schema Models

### Message Collection (`processed_messages`)

```typescript
{
  id: String,            // Internal unique identifier
  wa_id: String,         // Thread group phone boundary (Indexed)
  text: String,          // Message string body
  type: String,          // Enum: 'incoming' | 'outgoing'
  status: String,        // Enum: 'sent' | 'delivered' | 'read' | 'failed'
  message_type: String,  // Enum: 'text' | 'image' | 'document'
  timestamp: Date        // Message timestamp
}

```

---

## 🚀 Managed Cloud Deployment

1. **Database:** Host instances securely via a **MongoDB Atlas** shared cluster.
2. **Backend Engine:** Connect the `/backend` directory to **Render**, **Railway**, or **Heroku** (inject standard `.env` variables).
3. **Web Client:** Build and host the App Router package natively on **Vercel** with the `NEXT_PUBLIC_API_URL` environment pointer.

---

## 🔒 Security Parameters

* **Targeted CORS:** Locks API surface execution to strict production origin matrices.
* **NoSQL Defenses:** Sanitizes dynamic queries using robust object-relational abstraction mapping.
* **Fail-Safe Logging:** Production runtime traces block trace printouts to shield environmental access vectors.

---

## 📄 License

Distributed entirely under the **MIT License**. Feel free to fork and utilize for educational development blueprints.
