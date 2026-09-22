# Testes de Software & QA - SauceDemo

> **Projeto de Portfólio de Qualidade de Software (QA)**  
> Este repositório contém a documentação completa do ciclo de testes manuais para a funcionalidade de **Login** da aplicação [SauceDemo](https://www.saucedemo.com).

---

## Autor

* **Nome:** Jessica Vieira
* **Cargo:** QA Analyst / Test Analyst
* **GitHub:** [@jessicavieiradev](https://github.com/jessicavieiradev)

---

## Visão Geral do Projeto

O objetivo deste projeto é demonstrar a aplicação prática de conceitos fundamentais de **Garantia de Qualidade (QA)** e **Engenharia de Testes**, cobrindo desde o planeamento estratégico até a execução, rastreabilidade e reporte formal de defeitos.

A aplicação testada foi o **SauceDemo**, um e-commerce fictício amplamente utilizado na comunidade de QA para simulação de cenários reais de testes funcionais e de interface (UI).

---

## Entregáveis do Projeto

O projeto está estruturado em **3 documentos principais**, cobrindo todo o ciclo de vida de testes:

| Documento | Descrição | Link de Acesso |
| :--- | :--- | :--- |
| **1. Plano de Testes** | Planeamento estratégico, escopo, ambiente, critérios de entrada/saída, riscos e Tabela de Decisão. | [Acessar o Plano](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/testPlan.md) |
| **2. Casos de Teste & Execução** | Suíte de testes com rastreabilidade, passos a passo, resultados esperados vs. obtidos e matriz de cobertura. | [Acessar a Execução](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/testCases.md) |
| **3. Relatório de Bug (Bug Report)** | Documentação técnica detalhada do defeito visual (UI/Overflow) encontrado durante a execução. | [Acessar o Bug Report](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/bugReport.md) |

---

## Metodologias e Técnicas Aplicadas

* **Técnicas de Design de Testes (Caixa-Preta):**
  * **Tabela de Decisão:** Mapeamento de 7 regras de negócio para garantir a cobertura total de combinações de entradas (usuário/senha válidos, bloqueados, inválidos e vazios).
  * **Particionamento de Equivalência:** Divisão das entradas em classes válidas, inválidas e de estado para evitar testes redundantes.
* **Tipos e Níveis de Teste:**
  * **Smoke Test (Critério de Suspensão):** Validação crítica do fluxo principal (`standard_user`) antes da execução da suíte completa.
  * **Teste Funcional:** Validação de regras de negócio, mensagens de erro obrigatórias e bloqueio de acesso.
  * **Teste de Interface (UI/UX):** Validação de máscaras de senha e exibição visual dos elementos na tela.
* **Documentação & Rastreabilidade:**
  * Matriz de Rastreabilidade cobrindo Itens do Escopo e Regras da Tabela de Decisão.
  * Reporte padronizado de Bugs (`BUG-01`) com severidade, prioridade, passos para reproduzir e evidências combinadas.
  
---

## Defeito Encontrado (Highlight)

Durante a execução da suíte de testes, foi identificado um bug de layout/UI comum a múltiplos cenários de credenciais inválidas:

* **ID do Bug:** `BUG-01`
* **Tipo:** UI / Layout (Text Overflow & Padding desalinhado)
* **Severidade:** Baixa | **Prioridade:** Média
* **Resumo:** A mensagem de erro `"Epic sadface: Username and password do not match any user in this service"` é disparada pela regra de negócio, mas é exibida com o texto cortado nas margens superior/inferior e com desalinhamento no container vermelho.

---

## Ferramentas Utilizadas

* Markdown (Documentação)
* Git & GitHub (Controle de versão e hospedagem do portfólio)
* Firefox for Arch Linux
