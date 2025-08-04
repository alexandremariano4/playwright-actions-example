## 🧪 Execução de Testes E2E (Playwright) via GitHub Actions

Este projeto possui um workflow de integração contínua (CI) no **GitHub Actions** para executar os testes End-to-End (E2E) utilizando **Playwright**.

O workflow é acionado automaticamente nas seguintes situações:

- Push nas branches `main` ou `master`
- Pull Requests direcionados para `main` ou `master`
- Execução manual via interface do GitHub Actions (workflow_dispatch)

### 🔄 Fluxo do CI (playwright.yml)

1. **Checkout do código-fonte** do repositório.
2. **Instalação do Node.js 18**.
3. **Instalação das dependências do projeto** via `npm install`.
4. **Instalação dos navegadores do Playwright** (Chromium, Firefox, Webkit).
5. **Execução dos testes E2E** com `npx playwright test`.
6. **Geração e publicação do relatório HTML** como artefato no GitHub Actions (válido por 30 dias).

### 📂 Relatórios de Testes

Após a execução dos testes, é gerado um relatório HTML acessível na aba **Actions > (Job Run) > Artifacts** com o nome `playwright-report`.

### 📄 Arquivo de configuração

O arquivo de workflow do GitHub Actions está localizado em:

```yaml
.github/workflows/playwright.yml
```

## 🧩 Explicação do `playwright.yml` (GitHub Actions)

Esse workflow configura uma **pipeline CI/CD no GitHub Actions** para rodar os testes **E2E (End-to-End)** com **Playwright** sempre que houver:

1. **Push** nas branches `main` ou `master`
2. **Pull Request** direcionado para `main` ou `master`
3. Ou for executado manualmente via **workflow_dispatch**

---

### 🔄 Fluxo do Job (e2e-tests)

| Etapa | O que faz? |
| --- | --- |
| **Get code** | Faz o checkout do repositório no runner da GitHub Action. |
| **Install Node 22.11.0** | Configura a versão 22.11.0 do Node.js para ser usada no job. |
| **Install dependencies** | Instala as dependências do projeto via `npm install`. |
| **Install Playwright Browsers** | Faz o download dos navegadores e dependências necessários para o Playwright (`chromium`, `firefox`, etc.). |
| **Run E2E tests** | Executa os testes Playwright com o comando `npx playwright test`. |
| **Publish HTML Report** | Publica o relatório HTML gerado pelos testes como um artefato no GitHub Actions (válido por 7 dias). |

### 🚀 Execução Manual dos Testes Localmente

Para rodar os testes localmente:

```bash
pm install
npx playwright install
npx playwright test
```