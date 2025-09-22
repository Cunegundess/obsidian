# 📑 Documento de Requisitos 

## 1. Introdução
**Objetivo:**  
MoneyFlow é uma aplicação web e mobile para **gerenciamento de finanças pessoais**, incluindo controle de entradas e saídas, análises gráficas, relatórios e notificações inteligentes.  
O sistema também será utilizado como **laboratório de estudos** para aprofundar conceitos de backend, DevOps e observabilidade.  

**Escopo:**  
O sistema contemplará os seguintes módulos:  
- Autenticação  
- Usuários  
- Movimentações  
- Análises  
- Notificações e E-mail  

**Stakeholders:**  
- Usuário final (pessoa física que deseja controlar suas finanças). 
- Desenvolvedor/mantenedor (criador e responsável pelo sistema). 

---

## 2. Arquitetura do Sistema
A aplicação será composta por **3 frentes**:  
- **Mobile (Kotlin)**  
- **Web (NextJS)**  
- **Bot do WhatsApp (Python ou Javascript - ainda a decidir)**  

Todas as frentes se comunicam com o **API Gateway**, que direciona para o **backend**. E cada uma delas será versionada em seus respectivos repositórios no **Github**, seguindo a abordagem **TDD (Test Driven Development)**.

A comunicação entre os serviços será feita de forma híbrida, aproveitando os pontos fortes de cada abordagem:
1. **REST** será utilizado para operações de autenticação, gerenciamento de usuários, movimentações, carteira e envio de notificações/e-mails. Essa escolha garante simplicidade, facilita a integração com serviços externos e assegura consistência em operações de criação, atualização e deleção de dados.
2. **GraphQL** será utilizado para funcionalidades de análises, dashboards, gráficos e relatórios. Com ele, é possível realizar consultas flexíveis, agregando dados de múltiplos módulos em uma única requisição e evitando overfetching ou underfetching de informações no frontend.

![[system-design.png]]

**Tecnologias principais:**  
- Backend: Java + Spring Boot
- Orquestração e Docker: [Kind](https://github.com/kubernetes-sigs/kind)
- Banco de Dados: instância PostgreSQL com bancos de dados para cada micro serviço  
- Cache/Mensageria: Redis, RabbitMQ e Celery 
- Proxy / Redirecionamento: Nginx
- Cloud Provider: AWS (Lambda)
- Observabilidade: (Prometheus + Grafana)

---

## 3. Requisitos Funcionais (RF)

### Autenticação
- RF01 – O sistema deve permitir cadastro de novos usuários com e-mail e senha.  
- RF02 – O sistema deve autenticar usuários via **JWT**.  
- RF03 – O sistema deve permitir login via **SSO** (Google, GitHub).  
- RF04 – O sistema deve permitir recuperação de senha via e-mail.  

### Usuários
- RF05 – O sistema deve permitir listar usuários.  
- RF06 – O sistema deve permitir editar informações do perfil.  
- RF07 – O sistema deve permitir excluir um usuário.  

### Movimentações
- RF08 – O sistema deve permitir cadastrar movimentações (entrada/saída).  
- RF09 – O sistema deve permitir listar movimentações por período.  
- RF10 – O sistema deve notificar o usuário sobre novas movimentações.  

### Carteira
- RF11 – O sistema deve calcular o saldo total do usuário.  
- RF12 – O sistema deve gerenciar despesas e receitas recorrentes.  
- RF13 – O sistema deve enviar alertas sobre limites de gastos.  

### Análise
- RF14 – O sistema deve exibir gráficos das movimentações.  
- RF15 – O sistema deve exportar dados para Excel.  
- RF16 – O sistema deve gerar relatórios financeiros mensais.  

### Notificações e E-mail
- RF17 – O sistema deve enviar notificações push para dispositivos móveis.  
- RF18 – O sistema deve enviar e-mails transacionais (confirmação de conta, alertas, recuperação de senha).  

---

## 4. Requisitos Não Funcionais (RNF)
- RNF01 – O sistema deve ter tempo de resposta < 2s em 95% das requisições.  
- RNF02 – O sistema deve suportar até 1.000 usuários simultâneos.  
- RNF03 – O sistema deve estar disponível 99,9% do tempo.  
- RNF04 – O sistema deve criptografar senhas com algoritmo seguro (bcrypt/argon2).  
- RNF05 – O sistema deve armazenar dados em conformidade com a **LGPD**.  

---

## 5. Regras de Negócio (RN)
- RN01 – Não é permitido cadastrar movimentações sem categoria.  
- RN02 – Despesas recorrentes devem ser aplicadas automaticamente na data definida.  
- RN03 – Usuários só podem excluir suas próprias contas.  

---

## 6. Casos de Uso / Histórias de Usuário
- **CU01 – Cadastrar movimentação**  
  - Como usuário, quero registrar uma nova movimentação (entrada ou saída), para controlar minhas finanças.  

- **CU02 – Gerar relatório**  
  - Como usuário, quero exportar meus dados financeiros para Excel, para analisá-los em planilha.  

- **CU03 – Receber alerta de gastos**  
  - Como usuário, quero ser notificado quando atingir meu limite mensal de despesas, para evitar ultrapassar meu orçamento.  

---

## 7. Testes

### Estratégia de Testes
- **Testes Unitários (CI):**  
  - Cobrir funções isoladas (ex: cálculo de saldo, validação de senha).  
- **Testes de Integração (CI):**  
  - Validação da comunicação entre serviços (ex: Movimentações ↔ Carteira).  
- **Testes End-to-End (CD):**  
  - Fluxos completos do usuário (ex: login → cadastrar movimentação → gerar relatório).  
- **Testes de Performance:**  
  - Avaliar tempo de resposta (<2s em 95% das requisições).  
- **Testes de Segurança:**  
  - Verificação de injeção SQL, XSS, autenticação.  

### Ferramentas
- **Unitário/Integração:** Jest / Pytest / JUnit  
- **E2E:** Cypress / Playwright  
- **Performance:** k6 / Locust  
- **Segurança:** OWASP ZAP  

---

## 8. Wireframes

- **Tela de Login**  
- **Dashboard**  
![[wireframe-dashboard.png]]
- **Tela de Movimentações**  
- **Tela de Carteira**  
- **Tela de Relatórios/Gráficos**  

---

## 9. DevOps & CI/CD

### Pipeline CI/CD
- **CI:**  
  - Rodar lint e testes unitários/integrados.  
  - Buildar imagem Docker.  
  - Publicar no **Amazon ECR**.  

- **CD:**  
  - Deploy automático para ambiente de staging (ECS/Fargate).  
  - Rodar smoke tests.  
  - Deploy manual/automatizado para produção.  

### Infraestrutura como Código
- Terraform / AWS CDK para provisionamento.  

---

## 10. Observabilidade
- **Logs:** Centralização no CloudWatch, estruturados em JSON.  
- **Métricas:**  
  - Requests por segundo  
  - Latência média  
  - Erros por serviço  
- **Tracing:** OpenTelemetry → AWS X-Ray  
- **Alertas:** Integração com SNS/Slack/Email  

---

## 11. Riscos e Premissas
**Premissas:**  
- O usuário terá acesso à internet.  
- O usuário deve possuir um dispositivo compatível (mobile ou desktop).  

**Riscos:**  
- Dependência de serviços de terceiros (Google SSO, AWS SES).  
- Custos da AWS fora do Free Tier.  

---

## 12. Glossário
- **Movimentação:** Entrada (receita) ou saída (despesa).  
- **Carteira:** Conjunto de saldos e transações de um usuário.  
- **SSO:** Single Sign-On (ex: login com Google).  
- **CI/CD:** Continuous Integration / Continuous Delivery.  
- **Observabilidade:** Conjunto de práticas para monitorar, logar e rastrear comportamento do sistema.  

---

	