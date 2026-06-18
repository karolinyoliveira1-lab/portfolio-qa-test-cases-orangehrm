# Mapeamento de Cenários de Teste: Fluxo de Login (OrangeHRM) 🎯

Este repositório foi criado com o objetivo de apresentar o **mapeamento de cenários de teste** para a funcionalidade de autenticação (Login) da plataforma OrangeHRM Demo. 

O foco deste projeto é demonstrar a aplicação prática de técnicas de testes manuais (Caixa-Preta) bem estruturadas, que servirão como base sólida para uma futura automação de testes funcionais E2E.

---

## 🧠 Estratégia de Testes & Técnicas Utilizadas

Para garantir a qualidade e a cobertura eficiente do fluxo de login sem redundâncias, foram aplicadas as seguintes abordagens de Engenharia de QA:

*   **Particionamento de Equivalência:** Técnicas utilizadas para validar o comportamento do sistema diante de classes de dados válidas, inválidas.
*   **Testes Positivos e Negativos:** Mapeamento desde o "Cenário Feliz" (autenticação com sucesso) até o tratamento de exceções (validação de mensagens de erro como 'Required' e 'Invalid credentials').
*   **Validação de Campos Obrigatórios:** Verificação do comportamento do sistema quando campos obrigatórios não são preenchidos.

---

## 📋 Casos de Teste Mapeados

| ID | Título | Objetivo | Pré-Condição | Passos | Dados de Entrada | Resultado Esperado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CT-LOGIN-01** | Login com senha inválida | Validar mensagem de erro para senha incorreta | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Informar usuário válido<br>3. Informar senha inválida<br>4. Clicar em "Entrar" | **Usuário:** Admin<br>**Senha:** admin1 (inválido) | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Invalid credentials'. |
| **CT-LOGIN-02** | Login com usuário inválido | Validar mensagem de erro para usuário inválido | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Informar usuário inválido<br>3. Informar senha válida<br>4. Clicar em "Entrar" | **Usuário:** Administrator (inválido)<br>**Senha:** admin123 | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Invalid credentials'. |
| **CT-LOGIN-03** | Login com usuário e senha inválidos | Validar mensagem de erro para ambos os campos inválidos | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Informar usuário inválido<br>3. Informar senha inválida<br>4. Clicar em "Entrar" | **Usuário:** Administrator (inválido)<br>**Senha:** admin1 (inválido) | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Invalid credentials'. |
| **CT-LOGIN-04** | Login com credenciais válidas | Validar acesso com sucesso (Cenário Feliz) | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Informar usuário válido<br>3. Informar senha válida<br>4. Clicar em "Entrar" | **Usuário:** Admin<br>**Senha:** admin123 | Usuário é autenticado com sucesso.<br>Sistema redireciona para a página inicial. |
| **CT-LOGIN-05** | Campos vazios | Validar obrigatoriedade de preenchimento | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Deixar campos de usuário e senha em branco<br>3. Clicar em "Entrar" | **Usuário:** (vazio)<br>**Senha:** (vazio) | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Required' abaixo de ambos os campos. |
| **CT-LOGIN-06** | Usuário vazio | Validar obrigatoriedade apenas do campo usuário | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Deixar campo de usuário em branco<br>3. Informar senha válida<br>4. Clicar em "Entrar" | **Usuário:** (vazio)<br>**Senha:** admin123 | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Required' abaixo do campo de usuário. |
| **CT-LOGIN-07** | Senha vazia | Validar obrigatoriedade apenas do campo senha | Usuário cadastrado no sistema | 1. Acessar a tela de Login<br>2. Informar usuário válido<br>3. Deixar campo de senha em branco<br>4. Clicar em "Entrar" | **Usuário:** Admin<br>**Senha:** (vazio) | Usuário permanece na tela de Login.<br>A autenticação não é realizada.<br>Exibir mensagem: 'Required' abaixo do campo de senha. |

---

## Cobertura dos Cenários

| Cenário | Status |
|----------|----------|
| Login com credenciais válidas | ✅ |
| Usuário inválido | ✅ |
| Senha inválida | ✅ |
| Usuário e senha inválidos | ✅ |
| Campos vazios | ✅ |
| Usuário vazio | ✅ |
| Senha vazia | ✅ |

---

## 🛠️ Próximos Passos (Roadmap de Automação)
- [ ] Configuração do ambiente de testes automatizados.
- [ ] Criação dos scripts de automação utilizando **Cypress** e **JavaScript**.
- [ ] Geração de relatórios de execução de testes.
