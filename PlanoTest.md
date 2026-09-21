# Plano de teste - Funcionalidade de Login
**Project:** SauceDemo Teste de Login \
**Tester:** Jessica Vieira \
**Date:** 21/09/2026

## 1. Objetivo
Garantir a eficácia do mecanismo de autenticação, validando que o acesso ao sistema seja concedido exclusivamente mediante a inserção de credenciais válidas. Adicionalmente, verificar se o sistema lida de forma adequada com dados de entrada inválidos ou incorretos, exibindo as devidas mensagens de erro e impedindo acessos indevidos.

## 2. Versao

## 3. Escopo
### 3.1 No escopo
* Login com credenciais válidas
* Login com usuário bloqueado
* Login com usuário e/ou senha inválidos
* Login com campos de usuário e/ou senha vazios
* Validação das mensagens de erro na tela de login
* Redirecionamento para a página de produtos (/inventory.html) após login válido
* Mascara de senha
### 3.2 Fora de escopo
* Fluxo de recuperação de senha ("Esqueci minha senha")
* Funcionalidade "Lembrar meu usuário"
* Criação de novos usuários / Auto-cadastro
* Validação de bloqueio dinâmico por múltiplas tentativas incorretas
* Login por mídia social
* Teste de segurança (SQL Injection, XSS, etc.)
* Teste de performance e carga
* Validação de comportamentos anômalos pós-login associados aos perfis especiais do Sauce Demo (problem_user, performance_glitch_user, error_user e visual_user), uma vez que o processo de autenticação para estes usuários segue o fluxo padrão.

## 4. Equipe
Como este plano de testes faz parte de um projeto pessoal com o objetivo de demonstrar habilidades em testes de software, a única pessoa envolvida no desenvolvimento é Jessica Vieira.

## 5. Riscos e Mitigacoes
| Risco Identificado | Impacto | Ação de Mitigação |
| :--- | :--- | :--- |
| Indisponibilidade do ambiente público do Sauce Demo durante a execução. | Alto | Confirmar a estabilidade da URL(https://www.saucedemo.com/) antes de iniciar a sessão de testes. |
| Falha no redirecionamento do usuário válido (standard_user). | Crítico | Priorizar a execução do cenário de sucesso com o Smoke Test |

## 6. Estrategia de testes
A abordagem de validação será baseada exclusivamente em **testes manuais de caixa-preta**, focando no cumprimento dos requisitos funcionais da tela de autenticação e no comportamento do sistema perante entradas do utilizador.

### 6.1. Resumo da Estratégia

| Nível de Teste | Tipo de Teste | Técnicas de Teste | Forma de Execução |
| :--- | :--- | :--- | :--- |
| Teste de Sistema, Teste de Interface (UI) | Smoke Test, Funcional, Caixa-Preta | Particionamento de Equivalência, Tabela de Decisão | Manual |

### 6.2. Abordagem de Execução

1. **Smoke Test (Teste de Fumaça):** 
   * Antes de iniciar a suíte completa de testes, será executado manualmente um único cenário crítico: login bem-sucedido com o utilizador `standard_user`. 
   * **Objetivo:** Garantir a estabilidade e acessibilidade do ambiente do Sauce Demo. Se este cenário falhar, a execução da suíte completa será suspensa.

2. **Testes Funcionais e Regras de Negócio:**
   * Execução guiada por Casos de Teste pré-definidos para validar fluxos de acesso, utilizadores bloqueados, credenciais inválidas e validações de campos obrigatórios.

3. **Técnicas Aplicadas:**
   * **Particionamento de Equivalência:** Divisão das entradas de dados em classes válidas (sucesso), inválidas (credenciais incorretas) e de estado (utilizador bloqueado), evitando testes redundantes.
   * **Tabela de Decisão:** Mapeamento de todas as combinações possíveis de *Inputs* (campo utilizador e campo senha) e os seus respetivos *Outputs* (redirecionamento ou mensagens de erro específicas).

## Criterios
## Ambiente de testes
## Entregaveis de testes
