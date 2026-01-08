# ADR-002: PostgreSQL for Database Management

## Context and Problem Statement

The CMS requires a database that supports schema-based multi-tenancy for complete data isolation between organizations, ACID compliance for data integrity, and can scale to handle 20M+ users across all tenants.

## Considered Options

* PostgreSQL
* MySQL
* MongoDB (NoSQL)
* Microsoft SQL Server
* Amazon DynamoDB

## Decision Outcome

Chosen option: "PostgreSQL", because it provides native schema support essential for multi-tenant architecture, JSONB for flexible metadata, full-text search, and excellent Django integration via django-tenants.

### Consequences

* Good, because native schema support enables database-level tenant isolation
* Good, because ACID compliance ensures data integrity for financial/telecom data
* Good, because open-source with no licensing fees and cloud-agnostic deployment
* Good, because JSONB allows flexible problem metadata storage
* Bad, because schema-based multi-tenancy requires careful migration management
* Bad, because more complex to set up than single-tenant databases
