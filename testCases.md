# Casos de Teste - Funcionalidade de Login
**Projeto:** SauceDemo Teste de Login \
**Responsável:** Jessica Vieira \
**Data:** 22/09/2026 \
**Documento de referência:** Plano de Teste - Funcionalidade de Login (v1.2)

## Convenções

* **ID:** LT (Login Test) + número sequencial + regra da Tabela de Decisão do plano (quando aplicável). Ex.: `LT01-R1`.
* **Prioridade:** Baixa, Média, Alta ou Crítica.
* **Status:** Não executado, Passou ou Falhou.

**Pré-condições gerais (valem para todos os casos):** navegador aberto em https://www.saucedemo.com, tela de login carregada com os campos vazios, ambiente conforme a seção 10 do plano de teste. Dados de teste: seção 11 do plano de teste.

## Casos de Teste

| ID | Sumário | Prioridade | Steps | Resultado esperado | Resultado obtido | Status | Bug / Issue |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **LT01-R1** | Login com credenciais válidas (Smoke Test) | Crítica | 1. Digitar `standard_user` no campo Username.<br>2. Digitar `secret_sauce` no campo Password.<br>3. Clicar em Login. | Redireciona para `/inventory.html` e exibe a página de produtos ("Products"), sem mensagem de erro. | Redireciona para `/inventory.html` e exibe a página de produtos ("Products"), sem mensagem de erro. | Passou | |
| **LT02-R2** | Login com usuário bloqueado | Alta | 1. Digitar `locked_out_user` no campo Username.<br>2. Digitar `secret_sauce` no campo Password.<br>3. Clicar em Login. | Acesso negado, permanece na tela de login, exibe `"Epic sadface: Sorry, this user has been locked out."` | Acesso negado, permanece na tela de login, exibe `"Epic sadface: Sorry, this user has been locked out."` | Passou | |
| **LT03-R3** | Login com usuário inexistente e senha preenchida | Alta | 1. Digitar `usuario_invalido` no campo Username.<br>2. Digitar `senha_invalida` no campo Password.<br>3. Clicar em Login. | Acesso negado, permanece na tela de login, exibe `"Epic sadface: Username and password do not match any user in this service."` | O login foi bloqueado corretamente e a mensagem foi exibida, porém a mensagem de erro exibe falha de UI: o texto está cortado no topo e na base (overflow de texto) e a caixa vermelha apresenta padding desalinhado. | Falhou | BUG-01 |
| **LT04-R4** | Login com usuário válido e senha incorreta | Alta | 1. Digitar `standard_user` no campo Username.<br>2. Digitar `senha_invalida` no campo Password.<br>3. Clicar em Login. | Acesso negado, permanece na tela de login, exibe `"Epic sadface: Username and password do not match any user in this service."` | O login foi bloqueado corretamente e a mensagem foi exibida, porém a mensagem de erro exibe falha de UI: o texto está cortado no topo e na base (overflow de texto) e a caixa vermelha apresenta padding desalinhado. | Falhou | BUG-01 |
| **LT05-R5** | Login com usuário vazio e senha preenchida | Alta | 1. Manter o campo Username vazio.<br>2. Digitar `secret_sauce` no campo Password.<br>3. Clicar em Login. | Acesso negado, exibe `"Epic sadface: Username is required."` | Acesso negado, exibe `"Epic sadface: Username is required."` | Passou | |
| **LT06-R6** | Login com usuário preenchido e senha vazia | Alta | 1. Digitar `standard_user` no campo Username.<br>2. Manter o campo Password vazio.<br>3. Clicar em Login. | Acesso negado, exibe `"Epic sadface: Password is required."` | Acesso negado, exibe `"Epic sadface: Password is required."` | Passou | |
| **LT07-R7** | Login com usuário e senha vazios | Alta | 1. Manter os campos Username e Password vazios.<br>2. Clicar em Login. | Acesso negado, exibe `"Epic sadface: Username is required"`. | Acesso negado, exibe `"Epic sadface: Username is required"`. | Passou | |
| **LT08** | Máscara do campo de senha | Média | 1. Clicar no campo Password.<br>2. Digitar `secret_sauce`.<br>3. Observar como os caracteres são exibidos. | Caracteres exibidos mascarados (pontos ou asteriscos); a senha não fica legível na tela. | Caracteres exibidos mascarados (pontos ou asteriscos); a senha não fica legível na tela. | Passou | |
| **LT09-R3** | Login com usuário em letras maiúsculas | Média | 1. Digitar `STANDARD_USER` no campo Username.<br>2. Digitar `secret_sauce` no campo Password.<br>3. Clicar em Login. | Acesso negado, exibe `"Epic sadface: Username and password do not match any user in this service."` | O login foi bloqueado corretamente e a mensagem foi exibida, porém a mensagem de erro exibe falha de UI: o texto está cortado no topo e na base (overflow de texto) e a caixa vermelha apresenta padding desalinhado. | Falhou | BUG-01 |
| **LT10** | Fechar a mensagem de erro | Baixa | 1. Clicar em Login com os campos vazios para gerar a mensagem de erro.<br>2. Clicar no ícone X ao lado da mensagem de erro. | A mensagem de erro deixa de ser exibida; usuário permanece na tela de login. | A mensagem de erro deixa de ser exibida; usuário permanece na tela de login. | Passou | |
## Rastreabilidade

### Itens do escopo x casos de teste
| Item do escopo (seção 3.1 do plano) | Casos de teste |
| :--- | :--- |
| Login com credenciais válidas | LT01-R1 |
| Login com usuário bloqueado | LT02-R2 |
| Login com usuário e/ou senha inválidos | LT03-R3, LT04-R4, LT09-R3 |
| Login com campos vazios | LT05-R5, LT06-R6, LT07-R7 |
| Validação das mensagens de erro | LT02-R2 a LT07-R7, LT09-R3, LT10 |
| Redirecionamento para /inventory.html | LT01-R1 |
| Máscara de senha | LT08 |

### Regras da Tabela de Decisão x casos de teste
| Regra | Caso de teste |
| :--- | :--- |
| R1 | LT01-R1 |
| R2 | LT02-R2 |
| R3 | LT03-R3, LT09-R3 |
| R4 | LT04-R4 |
| R5 | LT05-R5 |
| R6 | LT06-R6 |
| R7 | LT07-R7 |

## Observações

* As mensagens de erro seguem o comportamento observado do SauceDemo; confirmar o texto exato na execução, já que o sistema não possui especificação formal.
* Ordem sugerida de execução: LT01-R1 (Smoke Test) primeiro. Se falhar, a execução da suíte é suspensa (critério 9.3 do plano de teste).
