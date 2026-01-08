# ADR-003: Schema-Based Multi-Tenancy for Data Isolation

## Context and Problem Statement

The CMS must serve multiple organizations (banks, telecom companies) from shared infrastructure while guaranteeing complete data separation. Legal and compliance requirements mandate that one organization's data must never be visible to another.

## Considered Options

* Schema-based multi-tenancy (separate PostgreSQL schema per tenant)
* Shared database with tenant ID column filtering
* Separate database per tenant
* Hybrid approach

## Decision Outcome

Chosen option: "Schema-based multi-tenancy", because it provides database-level data isolation that meets compliance requirements while maintaining cost efficiency of shared infrastructure.

### Consequences

* Good, because database enforces data separation - impossible to accidentally access another tenant's data
* Good, because django-tenants automates schema routing based on subdomain
* Good, because individual tenant backups and data exports are straightforward
* Good, because better query performance without filtering by tenant ID on every query
* Bad, because database migrations must be applied to all tenant schemas
* Bad, because cross-tenant reporting requires special handling
