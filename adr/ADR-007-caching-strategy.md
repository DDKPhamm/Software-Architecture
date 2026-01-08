# ADR-007: Redis for Caching

## Context and Problem Statement

The CMS needs to deliver fast response times (< 2 seconds) while handling high traffic. Frequently accessed data like problem lists and user profiles should be cached to reduce database load and improve performance.

## Considered Options

* Redis
* Memcached
* Django database cache
* Hazelcast
* Varnish (HTTP-level caching)

## Decision Outcome

Chosen option: "Redis", because it provides sub-millisecond in-memory caching, versatile data structures (strings, lists, sets), pub/sub for real-time features, and serves as message broker for Celery background tasks.

### Consequences

* Good, because in-memory storage provides sub-millisecond response times
* Good, because single tool serves multiple purposes (cache, sessions, Celery broker, pub/sub)
* Good, because TTL support automatically expires temporary data like MFA codes
* Good, because excellent Django integration via django-redis package
* Bad, because all data stored in RAM is more expensive than disk storage
* Bad, because data loss risk on crash without persistence (mitigated by AOF for critical data)

*Note: Designed but not implemented in PoC.*
