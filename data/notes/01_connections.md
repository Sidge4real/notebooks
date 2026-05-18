## Connections  
*By Lukas Van der Spiegel (Author)*

In this chapter, you will learn how backend systems connect to PostgreSQL databases, what parameters are required, how clients authenticate, and why connection pooling is essential for performance and scalability.

---

## Database Clients

Different tools exist to connect to PostgreSQL. Each has its strengths depending on your workflow.

### psql (CLI)
- Fast, scriptable, ideal for automation and CI/CD  
- Perfect for DevOps, DBAs, SSH environments  
- No GUI, requires command‑line experience  

### pgAdmin (GUI)
- Visual interface, admin wizards, dashboards  
- Great for teaching and demonstrations  
- Heavier, PostgreSQL‑only  

### DBeaver (GUI, Multi‑DB)
- Works with many database engines  
- ERD generation, schema compare, data export  
- Fewer PostgreSQL‑specific admin features  



## Host vs Database Server

A **host** is the machine running the PostgreSQL server.

- **localhost** → database runs on your own PC/VM  
- **external host** → database runs on LAN, datacenter, or cloud  

You always connect to a **host** on a **port** where PostgreSQL is listening (default: 5432).



## Database Connection Fundamentals

A backend connects to a database using a set of required parameters.

### Required Parameters

- **Host** — IP or DNS of the database server  
- **Port** — Listening port (e.g., 5432 or custom ports like 6543)  
- **Database Name** — The initial database to connect to  
- **Username** — The account used for authentication  
- **Password** — Secret credential for the user  
- **Driver** — Library used by your backend (e.g., psycopg2, pg, pgx)  
- **SSL Mode** — Whether the connection must be encrypted  
- **Connection String** — A single URI bundling all parameters  

Example connection string:  
postgresql://app_user:secret@db.mycompany.com:5432/app_database?sslmode=require



## Example Database Environments

Real‑world systems often use multiple database environments:

| Purpose                     | Host                     | Port | Database     | User        | SSL      |
|----------------------------|--------------------------|------|-------------|------------|----------|
| Local development          | localhost                | 5432 | app_dev     | dev_user   | optional |
| Staging environment        | staging.db.mycompany.com | 5432 | app_staging | staging_user | require |
| Production environment     | prod.db.mycompany.com    | 5432 | app_prod    | app_user   | require |
| Production (pooling endpoint) | pool.db.mycompany.com | 6432 | app_prod    | pool_user  | require |

These are **generic examples** used in industry.



## Registering a New Server (pgAdmin)

1. Open pgAdmin  
2. Register a new server  
3. Give it a meaningful name  
4. Enter connection details (host, port, database, username)  
5. Add SSL settings (usually: Require)  
6. Save  



## Connecting via psql

psql "host=db.mycompany.com port=5432 dbname=app_database user=app_user sslmode=require"

psql will prompt you for your password.



## Connection Pooling

Connection pooling allows many short‑lived client sessions to reuse a small, fixed set of persistent database connections.

### Why pooling matters
- Creating direct connections is expensive  
- Pooling reduces overhead  
- Pooling protects the database from overload  
- Pooling improves performance and scalability  

Always release a connection when you’re done.

The connection string looks normal, but you authenticate using a **pooling user** (e.g., pool_user).

#### Without pooling:
```mermaid
flowchart LR
    subgraph Clients
        A1[Client 1]
        A2[Client 2]
        A3[Client 3]
        A4[Client 4]
    end

    subgraph Database
        DB[(PostgreSQL Server)]
    end

    A1 --> DB
    A2 --> DB
    A3 --> DB
    A4 --> DB
```

#### With pooling:
```mermaid
flowchart LR
    subgraph Clients
        C1[Client 1]
        C2[Client 2]
        C3[Client 3]
        C4[Client 4]
        C5[Client 5]
    end

    subgraph PoolingServer[Connection Pool]
        P1[(Conn 1)]
        P2[(Conn 2)]
        P3[(Conn 3)]
    end

    subgraph Database
        DB[(PostgreSQL Server)]
    end

    C1 --> PoolingServer
    C2 --> PoolingServer
    C3 --> PoolingServer
    C4 --> PoolingServer
    C5 --> PoolingServer

    P1 --> DB
    P2 --> DB
    P3 --> DB
```

##### Lifecycle 
```mermaid
sequenceDiagram
    participant Client
    participant Pool as Connection Pool
    participant DB as PostgreSQL

    Client->>Pool: Request connection
    Pool->>Pool: Check for available connection
    Pool-->>Client: Provide pooled connection

    Client->>DB: Execute query
    DB-->>Client: Return results

    Client->>Pool: Release connection
    Pool->>Pool: Mark connection as available
```

## Pooling Types

### Session Pooling
- Each pooling connection maps to one database connection  
- Connection is returned to the pool when closed  

### Transaction Pooling
- Each transaction uses a shared database connection  
- Connection is released after the transaction ends  
- You cannot rely on session state  

### Statement Pooling
- Each SQL statement uses a shared connection  
- Highest throughput, lowest cost  
- Explicit transactions become meaningless  



## Pooling in Practice

A typical workflow for using pooling in a backend:

1. Create a dedicated **pooling user** with limited permissions  
2. Configure your backend to connect through a pooling server  
3. Set a maximum number of connections (e.g., 10–50)  
4. Ensure connections are released back to the pool  
5. Monitor pool usage and adjust limits as needed  

Example connection string for a pooling server:  
postgresql://pool_user:secret@pool.db.mycompany.com:6432/app_database?sslmode=require



## Backend Engineering Considerations

Real backend systems must also handle:

- Connection pooling (server‑side or client‑side)  
- Timeout settings  
- Retry logic for transient failures  
- Secure storage of credentials (environment variables)  
- ORM configuration  
- Connection lifecycle management  
- Monitoring and logging  
- Load balancing and read replicas  
- Connection limits and resource management  

These principles ensure stable, scalable, and secure database‑backed applications.