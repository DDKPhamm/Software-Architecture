# ADR-008: Celery for Background Tasks

## Context and Problem Statement

The CMS has operations that should not block API responses including email notifications, SMS sending, report generation, and scheduled tasks like daily statistics calculation.

## Considered Options

* Celery with Redis broker
* RQ (Redis Queue)
* AWS SQS + Lambda
* Dramatiq
* Django background jobs

## Decision Outcome

Chosen option: "Celery with Redis broker", because it provides mature Python-native task processing, automatic retry with exponential backoff, scheduled tasks via Celery Beat, and proven reliability at scale (Instagram, Reddit).

### Consequences

* Good, because asynchronous processing keeps API response times under 2 seconds
* Good, because automatic retry logic handles transient failures for external services
* Good, because Celery Beat enables scheduled tasks like daily reports and cleanup
* Good, because Django integration via django-celery-beat is straightforward
* Bad, because adds infrastructure complexity (workers, scheduler, monitoring)
* Bad, because task arguments must be JSON-serializable (pass IDs not objects)

*Note: Designed but not implemented in PoC.*
