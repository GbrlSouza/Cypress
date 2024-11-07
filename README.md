# Cypress + GitHub Actions

Este repositório está configurado para utilizar **Cypress** para testes automatizados de front-end e **GitHub Actions** para integração contínua (CI). 

## Configuração do Cypress

[Cypress](https://www.cypress.io/) é uma ferramenta de teste de front-end poderosa que permite testar aplicações web em diferentes navegadores e em diferentes cenários.

### Instalação

1. Clone este repositório:

   ```bash
   git clone https://github.com/GbrlSouza/Cypress.git
   cd Cypress
   ```

2. Instale as dependências:

   ```bash
   npm install
   ```

### Executando os Testes Locais

Para rodar os testes localmente, use o comando:

```bash
npx cypress open
```

Isso abrirá a interface do Cypress onde você pode selecionar os testes a serem executados.

### Testes em Cabeça de Execução

Se preferir rodar os testes no terminal sem a interface gráfica, use o comando:

```bash
npx cypress run
```

## GitHub Actions

O repositório está configurado com **GitHub Actions** para rodar os testes automaticamente sempre que houver push ou pull request no repositório.

### Arquivo de Configuração do GitHub Actions

O arquivo de configuração está localizado em `.github/workflows/ci.yml`. Este arquivo define a pipeline de integração contínua, onde os testes do Cypress são executados em ambientes virtuais.

### Workflow de CI

O workflow inclui as seguintes etapas:

1. **Instalação das dependências**: Instala as dependências do projeto, incluindo o Cypress.
2. **Execução dos testes do Cypress**: Roda os testes automatizados com Cypress.
3. **Relatórios de Testes**: (Opcional) Se configurado, os relatórios podem ser enviados para um serviço como o [Cypress Dashboard](https://dashboard.cypress.io/).

Exemplo de execução do GitHub Actions:

![GitHub Actions](https://user-images.githubusercontent.com/12345678/ci-actions-example.png)

### Como Configurar o Workflow

O arquivo de workflow `.github/workflows/ci.yml` pode ser configurado da seguinte forma:

```yaml
name: Run Cypress Tests

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  cypress:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '16'

      - name: Install dependencies
        run: |
          npm install

      - name: Run Cypress Tests
        run: |
          npx cypress run
```

## Contribuindo

Sinta-se à vontade para contribuir para este projeto! Se você encontrar algum erro ou quiser sugerir melhorias, fique à vontade para abrir uma *issue* ou um *pull request*.

