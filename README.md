# Continuous Actions 🚀

**Implemente CI/CD básico em seus projetos de forma rápida e simples!**

Este repositório oferece um conjunto de GitHub Actions reutilizáveis e prontas para uso, projetadas para quem deseja adicionar pipelines de CI/CD essenciais aos seus projetos sem complicação.

## 📋 O que este projeto oferece

Se você está começando com CI/CD ou precisa de workflows básicos e confiáveis para seus projetos, este repositório é para você. Disponibilizamos actions compostas que cobrem as principais necessidades de automação:

- ✅ **Linting** - Validação automática de código com pre-commit
- 🔒 **Security Scan** - Análise de vulnerabilidades em dependências
- 🔀 **Merge Conflict Detection** - Verificação de conflitos antes do merge
- 📝 **Draft Check** - Validação de pull requests em modo rascunho
- 📄 **Documentation Check** - Verificação de documentação
- 🏷️ **Tag Release** - Geração automática de tags e releases
- ✔️ **Template Validation** - Validação de templates de projeto

## 🎯 Para quem é este projeto?

- Desenvolvedores que querem adicionar CI/CD básico rapidamente
- Equipes que precisam de workflows padronizados
- Projetos que estão começando com automação
- Quem busca boas práticas de CI/CD sem complexidade

## 🚀 Como usar

As actions estão disponíveis no diretório `templates/` e podem ser facilmente integradas aos seus workflows do GitHub Actions. Cada action é independente e pode ser usada conforme a necessidade do seu projeto.

Documentação detalhada sobre como implementar e configurar cada action será disponibilizada em breve nos diretórios `templates/` e `.github/`.

## 🛠️ Tecnologias

- GitHub Actions
- Python 3.13
- UV (gerenciador de pacotes Python)
- Pre-commit
- Pip-audit

## 📦 Actions Disponíveis

| Action            | Descrição                                   | Localização                    |
| ----------------- | ------------------------------------------- | ------------------------------ |
| Linting           | Executa validações de código com pre-commit | `templates/lint/`              |
| Security Scan     | Analisa vulnerabilidades com pip-audit      | `templates/security_scan/`     |
| Check Conflicts   | Detecta conflitos de merge                  | `templates/check_conflicts/`   |
| Check Merge       | Verifica marcadores de conflito no código   | `templates/check_merge/`       |
| Check Draft       | Valida status de PR                         | `templates/check_draft/`       |
| Check Docs        | Verifica documentação                       | `templates/check_docs/`        |
| Tag Release       | Cria tags e releases automaticamente        | `templates/tag_release/`       |
| Template Validate | Valida templates do projeto                 | `templates/template_validate/` |

## 📝 Licença

Este projeto está sob a licença especificada no arquivo [LICENSE](LICENSE).

## 👤 Autor

**Jhones Bomfim**

---

⭐ Se este projeto foi útil para você, considere dar uma estrela no repositório!

CI/CD for all Templates
