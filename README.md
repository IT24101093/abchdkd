<div align="center">

**A comprehensive enterprise-grade platform for gemstone trading and automated valuation — built with Spring Boot, Java, and AI (FastAPI/TensorFlow)**

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)

---

*Automate gem valuations, verify authenticity with AI, browse the marketplace, and manage secure orders & payments in one unified system.*

</div>

---

## 📖 Table of Contents
- [Overview](#-overview)
- [Team Members & Contributions](#-team-members--contributions)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Database Models](#-database-models)
- [License](#-license)

---

## 🔎 Overview
**Online Gem Buy and Sell System** is a modular enterprise application developed as a university group project. It provides a robust backend ecosystem to streamline gemstone trading. The system handles everything from automated, AI-driven inventory appraisal and mathematical carat estimations to a fully functioning marketplace, order lifecycle management, and secure payment processing.

The project is divided into **4 core components**, independently developed by the team and seamlessly integrated using a Spring Boot architecture.

---

## 👥 Team Members & Contributions
This project was collaboratively built by a team of 4 members. Each member was responsible for a specific domain, handling the database design, business logic, and RESTful APIs for their respective component.

---

### 1️⃣ Inventory Management & AI Analysis
**👤 [Your Name]** — *[Student ID]*

> Core system foundation — handles gem stock, manual and automated descriptions, mathematical weight/price estimations, and AI-powered authenticity detection.

| Layer | Files |
|---|---|
| **Backend — Models** | `InventoryItem.java`, `ValidationReport.java`, `SpecificGravity.java`, `YieldFactor.java` |
| **Backend — Services** | `InventoryItemService.java`, `SmartAnalysisEngineService.java`, `SmartAnalysisDetectService.java` |
| **Backend — Controllers** | `InventoryItemController.java`, `SmartAnalysisController.java` |
| **AI — Detection** | Connects to Python FastAPI via `RestTemplate` with multipart image uploads |

**Key Features Implemented:**
- 📦 Inventory lifecycle management (In Stock, Pending, Published, Sold, Removed)
- 🧮 **Mathematical Engine (Java):** Calculates estimated carat weight and value based on volume, specific gravity, and shape factor.
- 🤖 **AI Gem Authenticity:** Classifies uploaded gem images (Real vs. Fake) using a custom TensorFlow MobileNetV2 model via FastAPI.

---

### 2️⃣ Marketplace Management
**👤 [Team Member 2 Name]** — *[Student ID]*

> The storefront engine — manages listings, drafts, jewellery items, gem variants, and user-facing browse capabilities.

| Layer | Files |
|---|---|
| **Backend — Models** | `MarketplaceListing.java`, `JewelleryItem.java`, `GemCaratVariant.java` |
| **Backend — Services** | `MarketplaceService.java`, `JewelleryService.java` |
| **Backend — Controllers** | `MarketplaceController.java`, `AdminMarketplaceController.java` |

**Key Features Implemented:**
- 🏪 Public marketplace for browsing gems and jewellery
- 📝 Draft system for sellers to prepare listings before publishing
- 💎 Variant management (handling different carats, cuts, and color tones)
- 🛡️ Admin controls for marketplace moderation

---

### 3️⃣ Order Management
**👤 [Team Member 3 Name]** — *[Student ID]*

> The logistics and order lifecycle — handles customer orders, courier configurations, insurance, and delivery tracking.

| Layer | Files |
|---|---|
| **Backend — Models** | `Order.java`, `Customer.java`, `DeliveryService.java`, `CourierShippingConfig.java` |
| **Backend — Services** | `OrderService.java`, `CustomerService.java`, `DeliveryServiceService.java` |
| **Backend — Controllers** | `OrderController.java`, `DeliveryServiceController.java`, `FinanceController.java` |

**Key Features Implemented:**
- 🛒 End-to-end order processing and tracking
- 🚚 Delivery and courier service integrations and configurations
- 🛡️ Insurance and risk calculation for high-value gemstone shipping
- 👥 Customer profile and shipping detail management

---

### 4️⃣ Payment Processing
**👤 [Team Member 4 Name]** — *[Student ID]*

> The financial gateway — securely logs, verifies, and manages payment transactions for marketplace orders.

| Layer | Files |
|---|---|
| **Backend — Models** | `PaymentTransaction.java` |
| **Backend — Services** | `PaymentService.java` |
| **Backend — Controllers** | `PaymentController.java` |

**Key Features Implemented:**
- 💳 Secure payment transaction logging
- 🔄 Payment status lifecycle tracking (Pending, Success, Failed, Refunded)
- 🔗 Direct integration with the Order Management module to confirm purchases

---

## 🧠 Deep Dive: Inventory Smart Analysis

The Inventory component features a dual-layered automated appraisal system.

### 🧮 1. Mathematical Engine (Java)
A custom Java service (`SmartAnalysisEngineService.java`) acts as an **Automatic Weight and Price Calculator**. Based on constants fetched from the database (Specific Gravity, Shape Factors, Yield Percents, Multipliers), it dynamically calculates exact volume, estimated carats, and fair market value.

<div align="center">
  <!-- ⚠️ ACTION NEEDED: Replace the src below with your actual image path -->
  <img src="./path/to/your/calculator_image.png" alt="Automatic Weight and Price Calculator" width="700"/>
</div>

### 🤖 2. Artificial Intelligence (Gem Authenticity)
To prevent fraud, an AI model classifies images as **Real or Fake**. 
- **Tech Stack:** FastAPI, TensorFlow, MobileNetV2
- **Supported Gems:** Ruby, Turquoise, Emerald

#### 📊 Kaggle Dataset
The model was trained on a dataset of **6,043 images**, split across Train, Test, and Validation sets.

**Source:** [Gemstones Dataset on Kaggle](https://www.kaggle.com/datasets/muhammadmuzamil5500/gemstones)

| Gem Type | Real Images (Train/Test/Val) | Fake Images (Train/Test/Val) |
| :--- | :--- | :--- |
| **Emerald** | 507 / 250 / 250 | 500 / 250 / 250 |
| **Ruby** | 500 / 250 / 250 | 536 / 250 / 250 |
| **Turquoise**| 500 / 250 / 250 | 500 / 250 / 250 |

*The model utilizes MobileNetV2 for transfer learning and achieves an accuracy of ~95%.*

#### 📓 Model Training
The AI model was trained using Google Colab. View the interactive code and training outputs here:

🔗 **[Insert Link to your Google Colab Notebook Here]**

---

## 🛠️ Tech Stack

### Backend (REST API)
| Technology | Purpose |
|---|---|
| **Java 17** | Core programming language |
| **Spring Boot 3.x** | Application framework |
| **Spring Data JPA** | ORM and database interactions |
| **MySQL** | Relational database management |
| **Flyway** | Database schema migrations |
| **Lombok** | Boilerplate code reduction |

### AI Service (Microservice)
| Technology | Purpose |
|---|---|
| **Python** | AI logic and processing |
| **FastAPI** | High-performance API for model serving |
| **TensorFlow / Keras** | Deep learning framework (MobileNetV2) |

---

## 🏗️ Architecture

```mermaid
graph TD
    Client[Client App / Postman] --> |REST API| SpringBoot[Spring Boot Backend]
    
    subgraph Spring Boot Application
        Auth[Security & Auth]
        Market[Marketplace]
        Order[Order Management]
        Pay[Payment]
        Inv[Inventory]
        
        Auth --> Market
        Market --> Order
        Order --> Pay
        Inv --> Market
    end
    
    SpringBoot --> |JPA / Hibernate| MySQL[(MySQL Database)]
    Inv --> |Multipart HTTP POST| FastAPI[Python FastAPI AI Service]
    
    subgraph AI Microservice
        FastAPI --> TF[TensorFlow Model]
        TF -.-> |MobileNetV2| Predict[Prediction: Real/Fake]
    end
```

---

## 📂 Project Structure

```text
online-gem-buy-sell-system/
├── src/main/java/com/gemtrade/onlinegembuysellsystem/
│   ├── config/              # Security, CORS, Swagger configs
│   ├── common/              # Shared DTOs, Enums, Exceptions, Utils
│   ├── cart/                # Shopping cart functionality
│   ├── inventory/           # [Component 1] Inventory & Smart Analysis
│   │   ├── controller/      
│   │   ├── service/         # Contains SmartAnalysisEngine & DetectService
│   │   └── entity/          
│   ├── marketplace/         # [Component 2] Listings & Storefront
│   │   ├── controller/
│   │   ├── service/
│   │   └── entity/
│   ├── order/               # [Component 3] Orders & Shipping
│   │   ├── controller/
│   │   ├── service/
│   │   └── entity/
│   ├── payment/             # [Component 4] Transactions
│   │   ├── controller/
│   │   ├── service/
│   │   └── entity/
│   ├── seller/              # Seller profile management
│   └── reference/           # System reference data
├── src/main/resources/
│   ├── db/migration/        # Flyway SQL migrations
│   └── application.properties
└── pom.xml                  # Maven dependencies
```

---

## 🗄️ Database Models (High-Level)
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--o{ PAYMENT_TRANSACTION : triggers
    ORDER ||--o{ DELIVERY_SERVICE : uses
    SELLER ||--o{ INVENTORY_ITEM : owns
    INVENTORY_ITEM ||--o| VALIDATION_REPORT : has
    INVENTORY_ITEM ||--o{ MARKETPLACE_LISTING : published_as
    MARKETPLACE_LISTING ||--o{ GEM_CARAT_VARIANT : includes
```

---

## 📄 License
This project is for educational and university purposes.

---

<div align="center">
  **Built with ❤️ as a university group project.**
</div>
