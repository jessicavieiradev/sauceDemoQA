### BUG-01: Defeito de exibição e transbordamento de texto (padding) na mensagem de erro de login inválido

| Campo | Valor |
| :--- | :--- |
| **Caso de Teste** | LT03-R3, LT04-R4, LT09-R3 |
| **Descrição** | Ao tentar realizar login com credenciais inválidas (usuário/senha inválidos, usuário válido/senha incorreta ou usuário em maiúsculas), a mensagem de erro é exibida, porém apresenta uma falha visual de UI: o texto está cortado no topo e na base (transbordamento/overflow de texto) e o espaçamento interno (padding) da caixa vermelha está desalinhado. |
| **Pré-condições** | O usuário está na página de login (https://www.saucedemo.com) |
| **Passos** | **Cenário A (LT03-R3):**<br>1. Digitar `usuario_invalido` no campo Username.<br>2. Digitar `senha_invalida` no campo Password.<br>3. Clicar no botão "Login".<br><br>**Cenário B (LT04-R4):**<br>1. Digitar `standard_user` no campo Username.<br>2. Digitar `senha_invalida` no campo Password.<br>3. Clicar no botão "Login".<br><br>**Cenário C (LT09-R3):**<br>1. Digitar `STANDARD_USER` no campo Username.<br>2. Digitar `secret_sauce` no campo Password.<br>3. Clicar no botão "Login". |
| **Resultado Esperado** | O login é bloqueado e a mensagem de erro `"Epic sadface: Username and password do not match any user in this service"` deve ser exibida totalmente legível, centralizada e com margens/paddings corretos. |
| **Resultado Obtido** | O login é bloqueado corretamente, mas a mensagem de erro apresenta uma falha de layout na UI: o texto fica cortado na parte superior e inferior (overflow de texto) e o container vermelho fica com o padding desalinhado nos 3 cenários. |
| **Ambiente** | Arch Linux, Firefox |
| **Severidade** | Baixa |
| **Prioridade** | Média |
| **Status** | Aberto |
| **Reportado por** | Jessica Vieira |
| **Evidência** | <img width="881" height="652" alt="usuario invalido, senha invalida" src="https://github.com/user-attachments/assets/f2b1924e-a611-427e-bd30-5c9d027e5e3d" /> <img width="905" height="656" alt="usuario valido, senha invalida" src="https://github.com/user-attachments/assets/d930c238-6351-4bfb-92f3-29a7e6a5a7d2" /> <img width="894" height="652" alt="usuario com letras maiusculas, senha valida" src="https://github.com/user-attachments/assets/4a3d0207-a3e4-4e25-9ac2-ffa184940d0a" />

|
