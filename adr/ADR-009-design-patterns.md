# ADR-009: Design Patterns for Code Structure

## Context and Problem Statement

The CMS codebase needs consistent structure for maintainability, testability, and team collaboration. Common challenges include separating business logic from API views, abstracting data access, and handling cross-cutting concerns like authentication.

## Considered Options

* Repository + Service Layer patterns (backend)
* Active Record pattern only
* Anemic domain model
* Container/Presentation + Custom Hooks patterns (frontend)
* Monolithic component structure

## Decision Outcome

Chosen option: "Repository + Service Layer patterns for backend, Container/Presentation + Custom Hooks for frontend", because these patterns provide clear separation of concerns, enable unit testing in isolation, and follow Django and React best practices.

### Consequences

* Good, because Service Layer encapsulates business logic separate from API views
* Good, because Repository Pattern abstracts data access, making database changes easier
* Good, because Strategy Pattern enables multiple notification channels (email, SMS)
* Good, because React Custom Hooks enable reusable stateful logic across components
* Good, because Middleware Pattern handles multi-tenant routing transparently
* Bad, because additional abstraction layers increase initial development time
* Bad, because team needs training on pattern usage and when to apply them
