# Portal Conecta - Backend Case Study

Portal Conecta is a modular academic platform developed by multiple teams in the WEG/CentroWEG-SENAI Systems Development Apprenticeship Program.

My work was concentrated on the central backend and shared platform concerns rather than claiming ownership of every feature module.

## Situation

Feature teams needed the same identity, course, class, room, membership, permission, and notification data. If each module maintained its own version of those rules, the system would accumulate duplicated state and inconsistent authorization.

## Task

Help define and implement a central Hub Core that acts as the source of truth for shared academic data and authorization, while giving feature teams explicit integration contracts and common operational tooling.

## Technical scope

- Hub Core domain and lifecycle rules;
- contextual authorization and permission boundaries;
- OpenAPI contracts;
- synchronous HTTP integrations;
- RabbitMQ event flows;
- Spring Cloud Gateway routing and security;
- correlation IDs and W3C Trace Context propagation;
- reusable servlet/reactive access logging;
- Grafana, Loki, Prometheus, Tempo, Alloy, and OpenTelemetry.

## Representative initiative - administrative imports

### Problem

Administrators needed to create users and classes from operational spreadsheets. A direct bulk insert would bypass the same permission, duplicate, validation, and event rules used by the normal API.

### Decision

Treat each import row as an application-level operation:

- accept CSV and XLSX;
- expose a dry-run mode;
- support explicit `REJECT` and `SKIP` behavior for existing records;
- reuse existing creation use cases;
- return a result per row;
- avoid notifications before transaction commit.

### Result

The imports added a bulk administrative workflow without creating a separate rule path around the domain.

Representative PRs:

- [User import with CSV/XLSX, dry-run, and conflict policies](https://github.com/Portal-Conecta/core-backend/pull/293)
- [Class import reusing the existing class creation use case](https://github.com/Portal-Conecta/core-backend/pull/296)

## Representative initiative - observability boundary

### Problem

A request could cross the gateway, Hub Core, database, and feature integrations. Without shared correlation and telemetry, a failure would appear as disconnected logs and local symptoms.

### Decision

Create a common operational path:

- gateway correlation ID handling;
- W3C trace propagation;
- reusable access logging for servlet and reactive services;
- OpenTelemetry Java Agent instrumentation;
- Prometheus metrics;
- Grafana dashboards;
- Loki logs and Tempo traces through Alloy.

Representative PR:

- [Database trace instrumentation with the OpenTelemetry Java Agent](https://github.com/Portal-Conecta/core-backend/pull/280)

## Result and evidence

A Hub Core release was validated by:

```text
682 Maven tests
0 failures
0 errors
```

This is a team-system release result. It is not presented as an individual test count.

The platform boundary allowed feature teams to integrate through:

1. one central identity and academic-data backend;
2. explicit HTTP and event contracts;
3. one public gateway boundary;
4. reusable request logging;
5. shared metrics, logs, traces, and dashboards.

## Additional engineering decisions

### Separate account state from academic-link state

Closing a class or academic relationship should not silently redefine the lifecycle of a person's account. The model separates account availability from course/class membership so authorization and administration can evolve independently.

### Reuse use cases during imports

Bulk operations should not bypass domain behavior for convenience. Reusing existing use cases preserves permissions, duplicate checks, events, and validation.

### Gateway is not the only security boundary

The gateway performs ingress authentication and routing, while downstream services retain independent security checks where required.

### Operational telemetry is part of the platform

Logging, tracing, metrics, and dashboards were treated as shared backend capabilities rather than debugging added after feature work.

## What I would improve

- publish consumer-driven contract tests for module integrations;
- track integration compatibility and release evidence in one dashboard;
- define SLOs for central APIs and asynchronous delivery;
- add automated trace assertions for critical cross-service flows;
- measure administrative import throughput and row-level failure distribution;
- document incident and rollback exercises, not only successful releases.

## STAR summary

**Situation:** multiple feature teams depended on the same academic and identity rules.  
**Task:** establish a central backend and explicit integration boundary.  
**Action:** worked across Hub Core rules, imports, contracts, gateway behavior, messaging, reusable logging, and observability.  
**Result:** feature teams integrated through shared platform capabilities, and one Hub Core release was validated by 682 Maven tests with no failures or errors.

[Back to profile](../README.md)
