# Waulta (Quantum Waulta)

> **Quantum Waulta** — Future-proof your keys with quantum-grade security  
> *(branded “Waulta” throughout docs and tooling)*

---

## 🚀 Features

- **Hierarchical Deterministic (BIP32)** key management  
- **PSBT (BIP174)** support for safe, multi-party transaction signing  
- **Secure key storage** in ATECC608A crypto co-processor  
- **ESP32-based firmware** with Secure Boot & Flash Encryption  
- **Rust-native host apps**:  
    - **CLI** for scripting and automation  
    - **Desktop GUI** (Tauri / egui / Slint)  
    - **Mobile App** (Dioxus Mobile / Slint)  
- **USB CDC-ACM** & **BLE GATT** transports  
- Modular, layered code: HAL → Crypto Interface → Wallet Core → App Logic  

---

## 📂 Repository Layout

    waulta/
    ├── .github/
    │   └── workflows/ci.yml
    ├── docs/
    │   ├── architecture.md
    │   ├── getting_started.md
    │   └── CONTRIBUTING.md
    ├── firmware/
    │   ├── .cargo/config.toml
    │   ├── Cargo.toml
    │   └── src/
    │       ├── main.rs
    │       └── atecc.rs
    ├── host/
    │   ├── cli/            # Rust CLI tool
    │   │   ├── Cargo.toml
    │   │   └── src/main.rs
    │   ├── app-desktop/    # Rust desktop GUI (e.g. Tauri or Slint)
    │   │   ├── Cargo.toml
    │   │   └── src/main.rs
    │   └── app-mobile/     # Rust mobile app (e.g. Dioxus Mobile or Slint)
    │       ├── Cargo.toml
    │       └── src/main.rs
    ├── examples/
    │   └── sign_demo/      # CLI example for PSBT signing
    │       └── README.md
    ├── scripts/
    │   └── setup.sh        # scaffolding script
    ├── LICENSE
    └── README.md

---

## 🛠️ Getting Started

### 1. Clone & Scaffold

    git clone https://github.com/your-org/quantum-waulta.git
    cd quantum-waulta
    bash scripts/setup.sh

### 2. Build Firmware

    cd firmware
    cargo build

### 3. Build & Run CLI

    cd ../host/cli
    cargo build && cargo run -- --help

### 4. Build & Run Desktop GUI

    cd ../host/app-desktop
    # if using Tauri:
    cargo tauri dev
    # or, for Slint/egui:
    cargo run

### 5. Build & Run Mobile App

    cd ../host/app-mobile
    # Dioxus Mobile example:
    # iOS
    cargo dioxus run --target x86_64-apple-ios
    # Android
    cargo dioxus run --target aarch64-linux-android

_For full details and troubleshooting see [docs/getting_started.md](docs/getting_started.md)._

---

## 🔍 Architecture

- **Firmware (ESP32):**  
    - HAL → Crypto Interface (ATECC608A) → Wallet Core (BIP32, PSBT) → Application Logic (UI flow)

- **Host (Rust):**  
    - **CLI:** `waulta-cli` – terminal & scripting  
    - **Desktop GUI:** `waulta-desktop` – Rust + Tauri/egui/Slint  
    - **Mobile App:** `waulta-mobile` – Rust + Dioxus Mobile/Slint  

- **Transport:** USB CDC-ACM & BLE GATT carry PSBT payloads

![Software Architecture](docs/architecture.md)

---

## 📖 Examples

### PSBT Signing Demo (CLI)

    cd examples/sign_demo
    cargo run --example sign

---

## 🤝 Contributing

See [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md) for:

- Issue & PR guidelines  
- Coding standards  
- Testing & CI requirements  

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
