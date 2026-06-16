<div align="center">
  <h1>💎 Online Gem Buy and Sell System</h1>
  <p><i>University Project</i></p>
</div>

## 📖 Overview

The **Online Gem Buy and Sell System** is a comprehensive platform developed as a university project. It facilitates the trading of gemstones while utilizing advanced mathematical models and Artificial Intelligence to evaluate gems automatically and verify their authenticity.

## 👥 Team & Components

The system is built with a modular architecture, divided into four core components. The development responsibilities were shared among the team members as follows:

| Component | Developer Name | Description |
| :--- | :--- | :--- |
| **Inventory Management** | `[Your Name/Team Member Name]` | Handles gem stock, AI image analysis, and automated price/weight calculations. |
| **Marketplace** | `[Team Member Name]` | The storefront where users can browse, search, and view available gems. |
| **Order Management** | `[Team Member Name]` | Manages the lifecycle of an order, from placement to delivery. |
| **Payment Processing** | `[Team Member Name]` | Securely handles transactions and payment verification. |

*(Note: The feedback component is excluded from this iteration).*

---

## 🧠 Inventory Component Highlights

The **Inventory Management** component is the core engine of the system, heavily relying on automated evaluations and Artificial Intelligence to ensure the authenticity and proper pricing of the gemstones.

### 🧮 1. Mathematical Engine (Java)
The system includes a custom Java-based math engine that acts as an **Automatic Weight and Price Calculator**. Based on factors such as specific gravity, volume, shape factor, and cut dimensions, the system dynamically estimates the carat weight and fair market value.

<div align="center">
  <!-- Replace the src below with the actual path or URL to your AI generated image -->
  <img src="./path/to/your/calculator_image.png" alt="Automatic Weight and Price Calculator Visual" width="700"/>
</div>

### 🤖 2. Artificial Intelligence (Gem Authenticity)
To assist in fraud prevention, the inventory system integrates an AI model that classifies uploaded gem images to determine if they are **Real or Fake**. 

- **Tech Stack:** FastAPI, TensorFlow, MobileNetV2
- **Supported Gems:** Ruby, Turquoise, Emerald

#### 📊 Dataset
The model was trained using a Kaggle dataset consisting of **6,043 images**, split across Train, Test, and Validation sets.

**Dataset Source:** [Gemstones Dataset on Kaggle](https://www.kaggle.com/datasets/muhammadmuzamil5500/gemstones)

| Gem Type | Real Images (Train/Test/Val) | Fake Images (Train/Test/Val) |
| :--- | :--- | :--- |
| **Emerald** | 507 / 250 / 250 | 500 / 250 / 250 |
| **Ruby** | 500 / 250 / 250 | 536 / 250 / 250 |
| **Turquoise**| 500 / 250 / 250 | 500 / 250 / 250 |

*Note: The model utilizes MobileNetV2 for feature extraction and achieves an accuracy of ~95% in classifying real vs. fake gemstones.*

#### 📓 Model Training (Google Colab)
The AI model was trained in the cloud using Google Colab. You can view the training process, data augmentation steps, and the model architecture in the notebook linked below:

🔗 **[Insert Link to your Google Colab Notebook Here]**

---
<div align="center">
  <i>Developed for University Project Purposes</i>
</div>
