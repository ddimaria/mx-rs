# mx-rs

A Rust SDK for interacting with the [MX API](https://www.mx.com/). This client library is automatically generated from the MX OpenAPI specification using [progenitor](https://github.com/oxidecomputer/progenitor).

Documentation: https://docs.rs/crate/mx-rs/latest

## Overview

MX is a financial data platform that provides APIs for account aggregation, transaction data, financial insights, and more. This SDK provides a type-safe Rust interface to interact with all MX API endpoints.

## Installation

Add this to your `Cargo.toml`:

```toml
[dependencies]
mx-rs = "0.1.0"
```

## Usage

### Basic Example

```rust
use mx_rs::Client;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Create a new client with your API credentials
    let client = Client::new("https://api.mx.com")?;
    
    // Use the client to make API calls
    // Example: List accounts
    let accounts = client.accounts_list().await?;
    
    Ok(())
}
```

### Authentication

The MX API typically requires authentication via API keys or OAuth tokens. Configure your client with the appropriate credentials:

```rust
use mx_rs::Client;
use reqwest::header::{HeaderMap, HeaderValue, AUTHORIZATION};

let mut headers = HeaderMap::new();
headers.insert(
    AUTHORIZATION,
    HeaderValue::from_str(&format!("Bearer {}", api_key))?,
);

let client = Client::new_with_client(
    "https://api.mx.com",
    reqwest::Client::builder()
        .default_headers(headers)
        .build()?,
);
```

## Features

This SDK provides access to all MX API endpoints, including:

- **Accounts** - Create, read, update, and delete financial accounts
- **Transactions** - Access and manage transaction data
- **Members** - Manage connections to financial institutions
- **Users** - User management and authentication
- **Institutions** - Search and retrieve information about financial institutions
- **Holdings** - Investment holdings data
- **Categories** - Transaction categorization
- And more...

## Dependencies

- `progenitor-client` - Core client functionality
- `reqwest` - HTTP client
- `serde` / `serde_json` - Serialization
- `bytes` / `futures-core` - Async streaming support

## Development

### Building

```bash
cargo build
```

### Running Tests

```bash
cargo test
```

## Documentation

For detailed MX API documentation, refer to the [official MX API documentation](https://docs.mx.com/).

For docmentation of this crate: https://docs.rs/crate/mx-rs/latest

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Disclaimer

This is an unofficial SDK. For official MX SDKs and support, please visit [MX Developer Portal](https://www.mx.com/developers/).

## Related Projects

- [progenitor](https://github.com/oxidecomputer/progenitor) - The OpenAPI client generator used to create this SDK