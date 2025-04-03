# Create a new Rust project:
`cargo new mempool-server`
<br>
`cd mempool-server`
# Add dependencies in `Cargo.toml`: <br>
`[dependencies]` <br>
`axum = "0.6"` <br>
`tokio = { version = "1", features = ["full"] }`  <br>
`serde = { version = "1.0", features = ["derive"] }`  <br>
`serde_json = "1.0"`  <br>

# Simple API in src/main.rs:

```
use axum::{routing::get, Json, Router};
use serde::{Serialize, Deserialize};
use std::net::SocketAddr;
use tokio::net::TcpListener;

#[derive(Serialize, Deserialize)]
struct Transaction {
    txid: String,
    fee: u64,
    size: u64,
}

async fn get_transactions() -> Json<Vec<Transaction>> {
    let transactions = vec![
        Transaction { txid: "txid_123".to_string(), fee: 120, size: 300 },
        Transaction { txid: "txid_456".to_string(), fee: 250, size: 200 },
    ];
    Json(transactions)
}

#[tokio::main]
async fn main() {
    let app = Router::new().route("/transactions", get(get_transactions));
    let addr = SocketAddr::from(([127, 0, 0, 1], 3000));
    println!("Listening on {}", addr);
    axum::Server::bind(&addr).serve(app.into_make_service()).await.unwrap();
}

```
# Run the server:
`cargo run`

### Now visit http://127.0.0.1:3000/transactions to see mock data.
