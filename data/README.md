# Local MLS Data Setup

This directory contains documentation only. Do not add raw MLS data, CSV exports, SQL dumps, database files, credentials, or generated embeddings to this repository.

## Expected local tables

- `rets_property`: active MLS listings.
- `california_sold`: historical closed transactions and comparable sales.

## Local import outline

1. Obtain the authorized SQL datasets outside this repository.
2. Create a local MySQL database named `idx_exchange`.
3. Import both datasets directly from their external local location.
4. Verify that both tables exist and check their row counts.
5. Store database credentials only in the root `.env` file.

Example commands, using paths outside the repository:

```bash
mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS idx_exchange CHARACTER SET utf8mb4;"
mysql -u root -p idx_exchange < /path/outside/repository/rets_property.sql
mysql -u root -p idx_exchange < /path/outside/repository/california_sold.sql
```

Verification query:

```sql
SELECT
  (SELECT COUNT(*) FROM rets_property) AS active_listings,
  (SELECT COUNT(*) FROM california_sold) AS sold_comps;
```

Do not paste row-level MLS records or credentials into documentation, issues, commits, or screenshots.
