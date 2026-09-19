# Timly Suite

An offline-first productivity suite built with Flutter and backed by a common FastAPI + PostgreSQL service.

```
                         ┌──────────────────────┐
                         │     Timly Suite      │
                         └──────────┬───────────┘
                                    │
           ┌────────────────────────┴────────────────────────┐
           ▼                                                 ▼
┌─────────────────────────┐                       ┌─────────────────────────┐
│       timly_todo        │                       │     timly_calendar      │
│  Offline-first task     │                       │  Schedule, timeline &   │
│  management, focus mode │                       │  system calendar sync   │
└────────────┬────────────┘                       └────────────┬────────────┘
             │                                                 │
             └──────────────────────┬──────────────────────────┘
                                    │ REST API
                                    ▼
                         ┌──────────────────────┐
                         │       crystal        │
                         │   FastAPI backend    │
                         │    & PostgreSQL      │
                         └──────────────────────┘
```

---

## Repositories

* **[`timly_todo`](https://github.com/Timly-Suite/timly_todo)**  
  Task and checklist manager. Supports priority grouping, tags, Pomodoro focus sessions, local notifications, and instantaneous local SQLite caching.

* **[`timly_calendar`](https://github.com/Timly-Suite/timly_calendar)**  
  Full-featured calendar application with month and timeline views, category tagging, and two-way synchronization with native Apple and Google calendars.

* **[`crystal`](https://github.com/Timly-Suite/crystal)**  
  Core backend service providing Google OAuth authentication, JWT issuance, task/event cloud synchronization, and PostgreSQL database migrations via Alembic.

---

## Design Principles

1. **Offline First**: All user actions are committed immediately to local device SQLite storage. The UI never freezes or waits for network requests.
2. **Encrypted Credentials**: Auth tokens and sensitive sessions are saved strictly inside the platform Keychain (iOS/macOS) and KeyStore (Android) using `flutter_secure_storage`.
3. **Adaptive Connectivity**: Background sync gracefully detects connection states via `connectivity_plus`, bypassing network calls when offline without timeout lag.
4. **Shared Backend**: A single microservice (`crystal`) serves all client applications under the suite with multi-tenant data isolation.

---

## Quickstart

For local development setup across all apps and the database, check the setup instructions in the [main workspace documentation](https://github.com/Timly-Suite/timly_todo#readme).
