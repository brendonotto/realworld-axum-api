# RealWorld Axum API

A Rust implementation of the RealWorld API specification using Axum web framework.

## 🚀 Features

- **Fast & Lightweight**: Built with Axum, a high-performance async web framework
- **Type-Safe**: Written in Rust with full type safety and memory safety guarantees
- **Database Integration**: PostgreSQL with SQLx for compile-time verified queries
- **Migration Support**: Database schema versioning with SQLx migrations
- **Health Checks**: Built-in health endpoint for monitoring database connectivity

## 📋 Prerequisites

- Rust 1.75+ (2024 edition)
- PostgreSQL 12+
- Git

## 🛠️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd realworld-axum-api
   ```

2. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env and update DATABASE_URL with your PostgreSQL connection string
   ```

3. **Install dependencies**
   ```bash
   cargo build
   ```

4. **Run database migrations**
   ```bash
   # Make sure PostgreSQL is running and accessible
   sqlx migrate run
   ```

5. **Start the server**
   ```bash
   cargo run
   ```

The server will start on `http://0.0.0.0:3000`

## 📁 Project Structure

```
realworld-axum-api/
├── src/
│   ├── handlers/          # HTTP request handlers
│   │   ├── health.rs      # Health check endpoint
│   │   └── mod.rs
│   ├── models/            # Data models and database entities
│   │   ├── users.rs       # User model (placeholder)
│   │   └── mod.rs
│   ├── main.rs           # Application entry point
│   └── state.rs          # Application state and database connection
├── migrations/           # Database migration files
├── Cargo.toml           # Rust dependencies and project config
├── .env.example         # Environment variables template
└── README.md
```

## 🔧 Configuration

### Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_URL` | PostgreSQL connection string | `postgresql://username:password@localhost:5432/database_name` |

## 📡 API Endpoints

### Health Check
- **GET** `/health` - Returns server and database status

Response:
```json
{
  "status": "ok",
  "database": "connected"
}
```

## 🗄️ Database Schema

### Users Table
- `id` (UUID, Primary Key)
- `username` (VARCHAR, Unique)
- `email` (VARCHAR, Unique)
- `password_hash` (VARCHAR)
- `bio` (TEXT, Optional)
- `image` (VARCHAR, Optional)
- `created_at` (TIMESTAMP)
- `updated_at` (TIMESTAMP)

## 🧰 Technology Stack

- **Framework**: [Axum 0.8](https://github.com/tokio-rs/axum) - Modern async web framework
- **Runtime**: [Tokio 1.0](https://tokio.rs/) - Async runtime for Rust
- **Database**: [SQLx 0.8](https://github.com/launchbadge/sqlx) - Async SQL toolkit with compile-time verification
- **Serialization**: [serde_json 1.0](https://github.com/serde-rs/json) - JSON serialization
- **Environment**: [dotenvy 0.15](https://github.com/allan2/dotenvy) - Environment variable loading
- **UUID**: [uuid 1.0](https://github.com/uuid-rs/uuid) - UUID generation and parsing
- **DateTime**: [chrono 0.4](https://github.com/chronotope/chrono) - Date and time handling

## 🚀 Development

### Running in Development
```bash
cargo run
```

### Running Tests
```bash
cargo test
```

### Database Migrations
```bash
# Create a new migration
sqlx migrate add <migration_name>

# Run migrations
sqlx migrate run

# Revert last migration
sqlx migrate revert
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Resources

- [RealWorld Spec](https://realworld-docs.netlify.app/docs/specs/backend-specs/introduction)
- [Axum Documentation](https://docs.rs/axum/latest/axum/)
- [SQLx Documentation](https://docs.rs/sqlx/latest/sqlx/)
- [Rust Book](https://doc.rust-lang.org/book/)