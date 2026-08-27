# Thepphithak Patchanthuek

Backend engineer in Bangkok. Currently Senior Software Engineer at Krungsri.
Before that SCB, Allianz Ayudhya, and CP All (Gosoft).

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![Java](https://img.shields.io/badge/Java-E76F00?style=flat-square&logo=openjdk&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![Filebeat](https://img.shields.io/badge/Filebeat-005571?style=flat-square&logo=beats&logoColor=white)
![Kibana](https://img.shields.io/badge/Kibana-005571?style=flat-square&logo=kibana&logoColor=white)

Five years in retail, banking and life insurance. Most of that work was taking
systems that already existed and moving them somewhere they could be deployed and
watched properly: containers, CI/CD, centralized logs, metrics and alerts.

## Vertex

A multi-domain app I build and run on my own. iOS client, four Go services, a GraphQL
BFF, and the Kubernetes setup underneath. It runs on an actual cluster with CI/CD and
alerting, not docker-compose on my laptop.

| repo | what it is |
| --- | --- |
| [vertex-bff](https://github.com/thepphithakp/vertex-bff) | GraphQL BFF. gqlgen, depth and query-cost limits, an LLM endpoint |
| [vertex-auth-service](https://github.com/thepphithakp/vertex-auth-service) | JWT with asymmetric keys, RBAC, Google sign-in |
| [pet-service](https://github.com/thepphithakp/pet-service) | First domain. Transactional outbox, ETag avatar caching |
| [vertex-event-service](https://github.com/thepphithakp/vertex-event-service) | Where the other services publish their events |
| [vertex-backoffice](https://github.com/thepphithakp/vertex-backoffice) | Admin UI, Preact + Vite behind nginx |
| [vertex-migrations](https://github.com/thepphithakp/vertex-migrations) | Flyway migrations, run as a Kubernetes Job |
| [vertex-observability](https://github.com/thepphithakp/vertex-observability) | Filebeat/Elasticsearch/Kibana for logs, Prometheus/Grafana/Alertmanager for the rest |
| [vertex-app](https://github.com/thepphithakp/vertex-app) | iOS client, SwiftUI + Apollo |

[All of them in one list](https://github.com/thepphithakp?tab=repositories&q=topic%3Avertex-superapp)

Three things that broke along the way:

- The pet list response was 10 MB because avatars were base64'd into every item.
  Moved them to their own endpoint with ETag caching, list is about 4 KB now.
- p95 latency jumped and I spent a while looking at the database. It was a CPU limit
  throttling bcrypt.
- `/metrics` had been returning 500 in production for weeks and nothing complained.
  Pods were Ready, CI was green, the dashboards just showed no data. Fiber returns a
  string backed by a buffer it reuses between requests, and Prometheus had stored that
  as a label key, so the method label had turned into garbage like `GETETE`.

## Work

| | |
| --- | --- |
| Krungsri | Senior Software Engineer, 2026 to now. API and interface design, gateway and core banking integration. |
| SCB | Backend Developer, 2024 to 2026. Digital account opening. Moved 1990s PowerBuilder desktop apps onto Kubernetes. Led the ELK rollout. |
| Allianz Ayudhya | Full-stack Developer, 2022 to 2024. Payment gateways (Omise, SCB, KBANK, PromptPay QR), eKYC, OAuth2, incident automation. |
| CP All / Gosoft | Software Engineer, 2020 to 2022. Retail systems behind 7-Eleven Thailand. Message queues at over a million messages a day, SAP and CRM integration. |

## Tools

| | |
| --- | --- |
| Languages | Go, Java (Spring Boot, Spring Batch), TypeScript |
| APIs | REST, OpenAPI, OAuth2, JWT with asymmetric keys, RBAC |
| Data | PostgreSQL, MySQL, Oracle, MongoDB, Redis, Flyway |
| Platform | Kubernetes, Helm, Docker, GitHub Actions, Jenkins |
| Observability | Prometheus, Grafana, Alertmanager, Filebeat, Elasticsearch, Kibana |
| Messaging | RabbitMQ, MQTT, transactional outbox |

thepphithak.ph@gmail.com · [LinkedIn](https://www.linkedin.com/in/thepphithak-patchanthuek/)
