# itshaker-template-infra

> Template pour projets infrastructure, SRE, Ansible, Docker, monitoring, CMDB.

[![Governance](https://img.shields.io/badge/governance-itshaker-blue)](https://github.com/itshaker/itshaker-copilot-governance)

## Description

Template GitHub pour projets d'infrastructure itshaker. Inclut tout ce que fournit `itshaker-template-base` plus :
- Structure Ansible (`inventory/`, `playbooks/`, `roles/`)
- Structure Docker
- Monitoring (dashboards, alertes)
- CMDB
- Workflows CI/CD dédiés : ansible-lint, docker-build, infrastructure-scan

## Utilisation

```bash
cd itshaker-bootstrap
./scripts/new-project.sh --type infra --name <mon-infra>
```

## Structure spécifique infra

```
.
├── ansible/
│   ├── inventory/   # Inventaires (hosts.yml par environnement)
│   ├── playbooks/   # Playbooks principaux
│   └── roles/       # Rôles réutilisables
├── docker/          # Dockerfiles et docker-compose
├── monitoring/
│   ├── dashboards/  # Grafana / autres dashboards (JSON)
│   └── alerts/      # Règles d'alerte (Prometheus/Alertmanager)
└── cmdb/            # Configuration Management Database
```

## Conventions Ansible

- Chaque rôle suit la structure `tasks/`, `handlers/`, `defaults/`, `templates/`.
- `ansible-lint` obligatoire (voir `.github/workflows/ansible-lint.yml`).
- Les secrets sont gérés via Ansible Vault ou GitHub Secrets — jamais en clair.
- Toutes les tâches doivent être idempotentes.

## Éléments Awesome Copilot spécifiques

| Élément | Type | Usage |
|---------|------|-------|
| `ansible.instructions.md` | Instruction | Conventions Ansible |
| `containerization-docker-best-practices.instructions.md` | Instruction | Best practices Docker |
| `dependency-license-checker` | Hook | Vérifie les licences |
| `attester-import-check` | Hook | Vérifie les imports |
| `agent-supply-chain` | Skill | Analyse supply chain |

## Références

- [itshaker-copilot-governance](https://github.com/itshaker/itshaker-copilot-governance)
