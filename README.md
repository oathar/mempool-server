#  Competency Test - Demand CLI

## 🧱 Mempool Server – Axum + Rust

This is a simple Rust project using the [Axum](https://github.com/tokio-rs/axum) web framework. It serves a mock list of Bitcoin mempool transactions at the `/transactions` endpoint.

This repository is part of the competency test for the [DMND Pool](https://github.com/demand-open-source/demand-cli), aiming to demonstrate basic proficiency with Rust and Axum.

---

## 📦 Features

- Exposes a GET endpoint `/transactions`
- Returns a static JSON list of mock Bitcoin transactions
- Each transaction contains:
  - `txid`: Transaction ID
  - `fee`: Fee in satoshis
  - `size`: Transaction size in bytes

---

## 📁 Sample Response

```json
[
  {
    "txid": "txid123",
    "fee": 1500,
    "size": 225
  },
  {
    "txid": "txid456",
    "fee": 2500,
    "size": 300
  },
  {
    "txid": "txid789",
    "fee": 1800,
    "size": 280
  }
]

