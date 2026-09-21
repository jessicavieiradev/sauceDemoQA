# Plano de Teste - Funcionalidade de Login
**Projeto:** SauceDemo Teste de Login \
**Responsável:** Jessica Vieira \
**Data:** 21/09/2026

## 1. Objetivo
Garantir a eficácia do mecanismo de autenticação, validando que o acesso ao sistema seja concedido exclusivamente mediante a inserção de credenciais válidas. Adicionalmente, verificar se o sistema lida de forma adequada com dados de entrada inválidos ou incorretos, exibindo as devidas mensagens de erro e impedindo acessos indevidos.

## 2. Histórico de revisões
| Versão | Data | Descrição | Autor(a) |
| :--- | :--- | :--- | :--- |
| 1.0 | 21/09/2026 | Criação do plano de teste | Jessica Vieira |
| 1.1 | 21/09/2026 | Adicionados Tabela de Decisão, Estimativas, Itens de teste, Critérios de suspensão e retomada, Dados de teste, Referências e Glossário | Jessica Vieira |

## 3. Escopo
### 3.1 No escopo
* Login com credenciais válidas
* Login com usuário bloqueado
* Login com usuário e/ou senha inválidos
* Login com campos de usuário e/ou senha vazios
* Validação das mensagens de erro na tela de login
* Redirecionamento para a página de produtos (/inventory.html) após login válido
* Máscara de senha

### 3.2 Fora de escopo
* Fluxo de recuperação de senha ("Esqueci minha senha")
* Funcionalidade "Lembrar meu usuário"
* Criação de novos usuários / Auto-cadastro
* Validação de bloqueio dinâmico por múltiplas tentativas incorretas
* Login por mídia social
* Teste de segurança (SQL Injection, XSS, etc.)
* Teste de performance e carga
* Teste em outro navegador ou sistema operacional
* Validação de comportamentos anômalos pós-login associados aos perfis especiais do Sauce Demo (problem_user, performance_glitch_user, error_user e visual_user), uma vez que o processo de autenticação para estes usuários segue o fluxo padrão.

## 4. Itens de teste
| Item | Descrição |
| :--- | :--- |
| Tela de login | Página inicial do SauceDemo (https://www.saucedemo.com), versão web |
| Campos de entrada | Usuário e senha |
| Mensagens de erro | Mensagens exibidas em falhas de autenticação |
| Redirecionamento | Acesso a /inventory.html após login válido |

## 5. Equipe
Como este plano de teste faz parte de um projeto pessoal com o objetivo de demonstrar habilidades em testes de software, a única pessoa envolvida no desenvolvimento é Jessica Vieira.

## 6. Riscos e Mitigações
| Risco Identificado | Impacto | Ação de Mitigação |
| :--- | :--- | :--- |
| Indisponibilidade do ambiente público do Sauce Demo durante a execução. | Alto | Confirmar a estabilidade da URL (https://www.saucedemo.com/) antes de iniciar a sessão de testes. |
| Falha no redirecionamento do usuário válido (standard_user). | Crítico | Priorizar a execução do cenário de sucesso com o Smoke Test. |

## 7. Estratégia de testes
A abordagem de validação será baseada exclusivamente em **testes manuais de caixa-preta**, focando no cumprimento dos requisitos funcionais da tela de autenticação e no comportamento do sistema perante entradas do usuário.

### 7.1 Resumo da Estratégia

| Nível de Teste | Tipo de Teste | Técnicas de Teste | Forma de Execução |
| :--- | :--- | :--- | :--- |
| Teste de Sistema, Teste de Interface (UI) | Smoke Test, Funcional, Caixa-Preta | Particionamento de Equivalência, Tabela de Decisão | Manual |

### 7.2 Abordagem de Execução

1. **Smoke Test (Teste de Fumaça):**
   * Antes de iniciar a suíte completa de testes, será executado manualmente um único cenário crítico: login bem-sucedido com o usuário `standard_user`.
   * **Objetivo:** Garantir a estabilidade e acessibilidade do ambiente do Sauce Demo. Se este cenário falhar, a execução da suíte completa será suspensa.

2. **Testes Funcionais e Regras de Negócio:**
   * Execução guiada por Casos de Teste pré-definidos para validar fluxos de acesso, usuários bloqueados, credenciais inválidas e validações de campos obrigatórios.

3. **Técnicas Aplicadas:**
   * **Particionamento de Equivalência:** Divisão das entradas de dados em classes válidas (sucesso), inválidas (credenciais incorretas) e de estado (usuário bloqueado), evitando testes redundantes.
   * **Tabela de Decisão:** Mapeamento das combinações de entrada (usuário e senha) e dos resultados esperados.

| Regra | Usuário | Senha | Resultado esperado |
| :--- | :--- | :--- | :--- |
| R1 | Válido | Válida | Redireciona para /inventory.html |
| R2 | Bloqueado | Válida | Erro: usuário bloqueado (locked out) |
| R3 | Inexistente | Preenchida | Erro: usuário e senha não correspondem |
| R4 | Válido | Inválida | Erro: usuário e senha não correspondem |
| R5 | Vazio | Preenchida | Erro: usuário obrigatório (Username is required) |
| R6 | Preenchido | Vazia | Erro: senha obrigatória (Password is required) |
| R7 | Vazio | Vazia | Erro: usuário obrigatório (Username is required) |

## 8. Critérios
### 8.1 Critérios de entrada
* Casos de teste definidos e revisados
* Ambiente de teste pronto

### 8.2 Critérios de saída
* Todos os casos de teste executados
* Todos os defeitos encontrados documentados
* Evidências registradas para todos os casos que falharam

### 8.3 Critérios de suspensão
* Falha no Smoke Test (login com standard_user)
* Site do SauceDemo indisponível

### 8.4 Critérios de retomada
* Smoke Test executado com sucesso
* Ambiente estável novamente

## 9. Ambiente de testes
| Componente | Detalhes |
|------------|----------|
| **URL da aplicação** | https://www.saucedemo.com |
| **Navegador** | Mozilla Firefox 156.0 (64 bits) para Arch Linux |
| **Sistema operacional** | Arch Linux |
| **Rede** | Wi-Fi residencial |
| **Dispositivo** | Desktop |
| **Ferramentas de teste** | GitHub, Markdown |

## 10. Dados de teste
| Perfil | Usuário | Senha |
| :--- | :--- | :--- |
| Válido | standard_user | secret_sauce |
| Bloqueado | locked_out_user | secret_sauce |
| Inválido | usuario_invalido | senha_invalida |
| Vazio | (em branco) | (em branco) |

## 11. Estimativas
| Atividade | Esforço estimado |
| :--- | :--- |
| Elaboração dos casos de teste | 2h |
| Execução do Smoke Test | 10 min |
| Execução da suíte completa | 1h |
| Registro de bugs e evidências | 1h |
| **Total** | **~4h10** |

**Cronograma:** 21/09/2026 a 23/09/2026

## 12. Entregáveis
* Plano de teste
* Casos de teste
* Relatório de bugs
* Evidências de teste

## 13. Referências
* SauceDemo: https://www.saucedemo.com
* ISO/IEC/IEEE 29119-3: Software and systems engineering, Software testing, Test documentation

## 14. Glossário
| Termo | Definição |
| :--- | :--- |
| Smoke Test | Teste rápido para verificar se as funcionalidades críticas estão operacionais antes da suíte completa |
| Caixa-preta | Técnica que valida o comportamento sem considerar o código interno |
| Particionamento de Equivalência | Técnica que agrupa entradas em classes que se comportam da mesma forma |
| Tabela de Decisão | Técnica que mapeia combinações de entradas e suas saídas esperadas |
