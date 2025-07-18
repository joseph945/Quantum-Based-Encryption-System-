#  Quantum RNG + AES + RSA Encryption System

This project demonstrates an end-to-end encryption workflow using **quantum random number generation (QRNG)** as the foundation for cryptographic key material. It combines **SHA-256 hashing**, **AES encryption**, and **RSA public-key encryption** to deliver layered, modern cryptography.

>  This implementation simulates QRNG using Qiskit's Hadamard-based superposition circuit.

---

##  Features

-  Simulated Quantum Random Number Generation (Qiskit)
- SHA-256 hashing for secure key derivation
-  AES-128 encryption (EAX mode with nonce & tag)
-  RSA encryption of AES key
-  Basic Cryptoanalysis: bit distribution, chi-square test, entropy
-  Self-contained, Python-based

---

## 🛠 Tools & Libraries

- [Qiskit](https://qiskit.org/) – for quantum circuit simulation
- [PyCryptodome](https://pycryptodome.readthedocs.io/en/latest/) – for AES & RSA
- `hashlib` – standard library for SHA-256
- `matplotlib`, `scipy` – for cryptoanalysis & plotting

---

##  How It Works

### 1. Generate QRNG bits (8-bit)
Using Hadamard gates to create a uniform quantum superposition, the measurement results in a **truly random** bitstring.

### 2. Derive AES Key
QRNG output is hashed using **SHA-256**, and the first 16 bytes are used as the AES key (for AES-128).

### 3. Encrypt a message using AES
The AES key encrypts your plaintext using **EAX mode** (for authenticity and confidentiality).

### 4. Encrypt AES key using RSA
The AES key is then encrypted with a **2048-bit RSA public key**.

### 5. Decrypt (RSA → AES)
On the receiver side:
- RSA decrypts the AES key
- AES decrypts the original message

---

##  Cryptoanalysis Performed

-  **Avalanche effect test** (on SHA-256)
-  **Bit distribution**: ratio of 1s/0s in QRNG output
-  **Chi-square test**: statistical randomness test
-  **Shannon entropy** of generated bitstrings



