# 🧪 FreshMarket Global — Local Testing & Running Guide

This comprehensive guide provides step-by-step instructions for running, testing, and verifying **FreshMarket Global** locally on **Windows**, **macOS**, and **Linux** environments.

---

## 📋 Table of Contents
1. [Prerequisites](#1-prerequisites)
2. [Quick Start (All Platforms)](#2-quick-start-all-platforms)
3. [Windows Setup Guide (CMD, PowerShell, Git Bash & WSL2)](#3-windows-setup-guide)
4. [macOS Setup Guide (Intel & Apple Silicon M1/M2/M3)](#4-macos-setup-guide)
5. [Linux Setup Guide (Ubuntu, Debian, Fedora, Arch)](#5-linux-setup-guide)
6. [Testing & QA Checklist for Testers](#6-testing--qa-checklist-for-testers)
7. [Troubleshooting & Common Issues](#7-troubleshooting--common-issues)

---

## 1. Prerequisites

Before starting, ensure your system has the following installed:

- **Node.js**: Version `18.0.0` or higher (Recommended: Node `v20.x` LTS)
- **Package Manager**: `npm` (bundled with Node.js) or `bun` / `pnpm`
- **Git**: Version `2.30+` (for cloning repository)
- **Modern Web Browser**: Google Chrome, Mozilla Firefox, Microsoft Edge, or Apple Safari

### How to Check Installed Versions:
Open your terminal or command prompt and run:
```bash
node -v
npm -v
git --version
```

---

## 2. Quick Start (All Platforms)

If you already have Node.js installed, execute these steps:

```bash
# 1. Clone or download project repository
git clone <repository-url>
cd freshmarket-global

# 2. Setup environment variables
# On Windows PowerShell / CMD:
copy .env.example .env

# On macOS / Linux:
cp .env.example .env

# 3. Install project dependencies
npm install

# 4. Start the local development server
npm run dev
```

Navigate to **`http://localhost:3000`** in your browser.

---

## 3. Windows Setup Guide

### 🪟 Method A: Using Windows PowerShell or Command Prompt (CMD)

1. **Install Node.js & Git:**
   - Download Node.js LTS installer from [nodejs.org](https://nodejs.org/).
   - Download Git installer from [git-scm.com](https://git-scm.com/).
   - Follow standard setup prompts (ensure *"Add to PATH"* is checked).

2. **Open PowerShell as Administrator (if execution policy error occurs):**
   If PowerShell blocks npm scripts with an `Execution_Policies` error, run:
   ```powershell
   Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
   ```

3. **Navigate to Project Directory:**
   ```powershell
   cd C:\path\to\freshmarket-global
   ```

4. **Prepare `.env` File:**
   ```powershell
   copy .env.example .env
   ```

5. **Install Dependencies & Launch Server:**
   ```powershell
   npm install
   npm run dev
   ```
   Open `http://localhost:3000`.

---

### 🪟 Method B: Using Git Bash for Windows

1. Right-click inside your project folder and select **"Git Bash Here"**.
2. Execute standard commands:
   ```bash
   cp .env.example .env
   npm install
   npm run dev
   ```

---

### 🪟 Method C: Using WSL2 (Windows Subsystem for Linux)

1. Open WSL terminal (e.g. Ubuntu on Windows).
2. Install Node.js v20 via NVM:
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
   source ~/.bashrc
   nvm install 20
   nvm use 20
   ```
3. Run the application:
   ```bash
   cp .env.example .env
   npm install
   npm run dev
   ```

---

## 4. macOS Setup Guide

### 🍎 Intel & Apple Silicon (M1/M2/M3) Macs

1. **Install Node.js via Homebrew (Recommended):**
   ```bash
   # Install Homebrew if not installed
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

   # Install Node.js
   brew install node
   ```

   *Alternatively, download the `.pkg` installer from [nodejs.org](https://nodejs.org/).*

2. **Open Terminal & Navigate to Project:**
   ```bash
   cd ~/Downloads/freshmarket-global
   ```

3. **Copy Environment File & Install:**
   ```bash
   cp .env.example .env
   npm install
   ```

4. **Launch Local Server:**
   ```bash
   npm run dev
   ```
   Access the app at `http://localhost:3000`.

---

## 5. Linux Setup Guide

### 🐧 Ubuntu / Debian / Mint

```bash
# Update package manager and install Node.js v20
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs git

# Navigate to project
cd freshmarket-global

# Copy environment file
cp .env.example .env

# Install dependencies and start server
npm install
npm run dev
```

---

### 🐧 Fedora / RHEL / CentOS

```bash
sudo dnf install -y nodejs git
cp .env.example .env
npm install
npm run dev
```

---

### 🐧 Arch Linux / Manjaro

```bash
sudo pacman -S nodejs npm git
cp .env.example .env
npm install
npm run dev
```

---

## 6. Testing & QA Checklist for Testers

When conducting QA and functional testing, verify the following core modules:

### 🛍️ Storefront & Browsing
- [ ] **Lagos Market Product Catalog**: Verify items load with NGN (`₦`) prices and accurate local sources (Mile 12 Market, Epe Farms, Benue Yams).
- [ ] **Category Filter & Search**: Test category pills (Grains, Tubers, Peppers, Meats, Oils) and search input responsiveness.
- [ ] **Unit Selection**: Test selecting different package sizes (e.g., 50kg Bag vs 20kg Bag vs 5kg Bag) on product cards and in detail modals.

### 🛒 Cart & Promo System
- [ ] **Cart Drawer**: Add items to cart, test quantity increments/decrements, and remove items.
- [ ] **Promo Coupons**: Enter test codes:
  - `LAGOSFREE` (Free delivery within Lagos)
  - `DIASPORA10` (10% off International Export Orders)

### 💳 Checkout & Export Care Packages
- [ ] **Local Lagos Delivery**: Select local zones (Lekki, Ikeja, Victoria Island, Yaba) and verify delivery fees and estimated times update dynamically.
- [ ] **Diaspora Export Order**: Select **"International Export Air Cargo (UK, USA, Europe)"**, check *"Send as Diaspora Care Package / Family Gift"*, and enter recipient name & gift message.
- [ ] **Payment Methods**: Test Paystack/Card option, Bank Transfer details, and Cash on Delivery.

### 🧾 Order Tracking & PDF Receipts
- [ ] **Visual Stepper**: Track an order using the generated order ID and verify progress stages.
- [ ] **Receipt Generation**: Click **"Download PDF Receipt"** or **"Print Receipt"** to verify printable layout formatting.

### 🔐 Admin Store Management Portal
- [ ] **Admin Login**: Click **"Admin Portal"** in footer or top menu.
- [ ] **Default Admin Passcode**: Enter `admin123` or `freshmarket2026`.
- [ ] **Order Management**: Change order statuses (Pending ➔ Processing ➔ Shipped ➔ Delivered) and verify real-time status updates.
- [ ] **Product Manager**: Add a test product or adjust stock levels.

---

## 7. Troubleshooting & Common Issues

### ❌ Error: `Port 3000 is already in use`

#### On Windows (PowerShell):
```powershell
# Find process using port 3000
netstat -ano | findstr :3000

# Kill process by PID (replace <PID> with number from netstat)
taskkill /PID <PID> /F
```

#### On macOS / Linux:
```bash
# Find and kill process on port 3000
lsof -i :3000
kill -9 $(lsof -t -i:3000)
```

---

### ❌ Error: `npm scripts disabled on Windows`
If you get `File C:\...\npm.ps1 cannot be loaded because running scripts is disabled`:
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

---

### ❌ Error: `vite: command not found` or `Module not found`
Reinstall node modules:
```bash
rm -rf node_modules package-lock.json
npm install
```
*(On Windows CMD: `rmdir /s /q node_modules` then `del package-lock.json` then `npm install`)*

---

### 🧪 Verification Command (Build Check)
To test if production bundling works without errors on your machine:
```bash
npm run build
npm start
```
This builds static assets into `dist/`, compiles `server.ts` into `dist/server.cjs`, and starts the production node server.
