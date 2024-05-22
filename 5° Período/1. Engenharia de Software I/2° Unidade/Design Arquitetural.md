
## Bloqueio de Usuário Após Tentativas de Login

**Driver**: O Sistema bloqueará por 30min o usuário após 5 tentativas de login
#### Contexto

**Contexto:** O sistema de autenticação de usuários para um portal online, onde os usuários podem fazer login utilizando um nome de usuário e senha. O sistema precisa ser seguro para proteger contra ataques de força bruta e acessos não autorizados.

#### Estímulo

**Estímulo:** Um usuário tenta fazer login no sistema utilizando um nome de usuário e senha incorretos repetidas vezes.
#### Resposta

**Resposta:** Após 5 tentativas de login falhadas consecutivas, o sistema bloqueará o usuário, impedindo novas tentativas de login por um período específico de tempo.
#### Medida de Resposta

**Medida de Resposta:** O sistema deve bloquear o usuário imediatamente após a quinta tentativa de login falhada e manter o bloqueio por um período de 30 minutos antes de permitir novas tentativas de login.

---
### Trade-offs

1. **Usabilidade**
3. **Performance
---
#### Componentes Principais
1. **Cliente:** Interface de usuário onde as credenciais são inseridas.
2. **Serviço de Login:** Processa as tentativas de login, verifica as credenciais e aplica o bloqueio quando necessário.
3. **Banco de Dados de Usuários:** Armazena informações dos usuários, incluindo contadores de tentativas de login falhadas e status de bloqueio.
4. **Serviço de Auditoria:** Registra todas as tentativas de login para análise e auditoria.
#### Fluxo de Trabalho
1. O usuário insere o nome de usuário e senha na interface do cliente.
2. O serviço de login recebe e verifica as credenciais:
    - Se as credenciais estiverem corretas, o usuário é autenticado com sucesso.
    - Se as credenciais estiverem incorretas, o contador de tentativas falhadas é incrementado.
3. Após a quinta tentativa falhada, o serviço de login atualiza o status do usuário para "bloqueado" no banco de dados.
4. O serviço de auditoria registra cada tentativa de login, incluindo sucesso, falha e bloqueio.
### Escolha de Tecnologias
1. **Frontend:** React.js para a interface do cliente.
2. **Backend:** Node.js com Express para o serviço de login.
3. **Banco de Dados:** PostgreSQL para armazenar informações dos usuários.
4. **Auditoria:** ELK Stack (Elasticsearch, Logstash, Kibana) para registrar e analisar as tentativas de login.

---

## Criptografia de Dados Sensíveis de Usuários

**Driver**: "o sistema deve criptografar dados sensives de usuários antes de salvar no banco de dados"
#### Contexto

**Contexto:** Um sistema de gerenciamento de usuários que armazena informações sensíveis, como números de cartões de crédito e senhas, em um banco de dados. A segurança dos dados é uma prioridade para proteger a privacidade dos usuários e cumprir regulamentações como a LGPD (Lei Geral de Proteção de Dados) e GDPR (General Data Protection Regulation).
#### Estímulo
**Estímulo:** O sistema recebe uma solicitação para criar ou atualizar dados sensíveis de um usuário, como senha ou informações de pagamento.
#### Resposta

**Resposta:** Antes de salvar os dados no banco de dados, o sistema deve criptografá-los utilizando um algoritmo de criptografia forte, como AES-256.

#### Medida de Resposta

**Medida de Resposta:** Os dados devem ser criptografados em menos de 100 ms para cada solicitação e a chave de criptografia deve ser gerenciada de forma segura.

---
### Raciocínio

Para implementar esse cenário, consideramos vários fatores:

1. **Segurança:** A criptografia de dados sensíveis é crucial para proteger a privacidade dos usuários e cumprir regulamentações de proteção de dados.
2. **Desempenho:** A criptografia deve ser rápida para não afetar a experiência do usuário.
3. **Gerenciamento de Chaves:** As chaves de criptografia devem ser protegidas contra acesso não autorizado e gerenciadas de forma segura.
4. **Escalabilidade:** O sistema deve ser capaz de criptografar dados de maneira eficiente, mesmo sob alta carga.

---
### Trade-offs

1.  **Desempenho:** 
2.  **Manutenibilidade**

### Componentes Principais

1. **Cliente:** Interface de usuário onde os dados sensíveis são inseridos.
2. **Serviço de Aplicação:** Processa as solicitações de criação ou atualização de dados sensíveis.
3. **Serviço de Criptografia:** Responsável por criptografar os dados antes de salvá-los no banco de dados.
4. **Banco de Dados:** Armazena os dados sensíveis de forma criptografada.
5. **Serviço de Gerenciamento de Chaves (KMS):** Armazena e gerencia as chaves de criptografia de forma segura.

### Design Arquitetural
#### Fluxo de Trabalho

1. O usuário insere dados sensíveis na interface do cliente.
2. O serviço de aplicação recebe a solicitação e envia os dados para o serviço de criptografia.
3. O serviço de criptografia utiliza a chave de criptografia gerenciada pelo KMS para criptografar os dados.
4. Os dados criptografados são enviados para o banco de dados e armazenados de forma segura.
5. As chaves de criptografia são gerenciadas pelo KMS, garantindo que estejam protegidas contra acesso não autorizado.
#### Escolha de Tecnologias
1. **Frontend:** React.js para a interface do cliente.
2. **Backend:** Node.js com Express para o serviço de aplicação.
3. **Serviço de Criptografia:** Biblioteca de criptografia como `crypto` em Node.js.
4. **Banco de Dados:** PostgreSQL com suporte a dados criptografados.
5. **Gerenciamento de Chaves:** AWS KMS (Key Management Service) ou um módulo de segurança de hardware (HSM) para gerenciar as chaves de criptografia.

---


## Controle de Acesso Baseado em Permissões

**Contexto:** Um sistema de gerenciamento de projetos que permite a colaboração de diferentes usuários com diferentes níveis de acesso. O sistema deve garantir que cada usuário tenha acesso apenas às funcionalidades e dados para os quais tem permissão.

**Estímulo:** Um usuário tenta acessar uma funcionalidade do sistema que está além de suas permissões atribuídas.

**Resposta:** O sistema verifica as permissões do usuário e, se ele não tiver as permissões necessárias, bloqueia o acesso à funcionalidade e retorna uma mensagem de erro apropriada.

**Medida de Resposta:** O sistema deve bloquear o acesso à funcionalidade de forma imediata (dentro de 100 ms) e registrar o evento de tentativa de acesso não autorizado.

### Trade-offs
1. **Performance: e Manutenibilidade:**

---
#### Componentes Principais

1. **Usuários:** Interagem com o sistema através da interface de usuário.
2. **Serviço de Autenticação:** Verifica a identidade do usuário.
3. **Interface de Usuário:** Onde os usuários acessam as funcionalidades do sistema.
4. **Serviço de Autorização:** Verifica as permissões do usuário para acessar funcionalidades específicas.
5. **Serviço de Funcionalidade Específica:** Implementa a funcionalidade solicitada, mas só é acessível se o usuário tiver a permissão necessária.
6. **Banco de Dados de Permissões:** Armazena as permissões de cada usuário.
7. **Registro de Tentativas de Acesso:** Armazena logs de tentativas de acesso não autorizado para auditoria.

#### Fluxo de Trabalho

1. O usuário tenta acessar uma funcionalidade através da interface de usuário.
2. A interface de usuário envia uma solicitação ao serviço de autorização para verificar as permissões do usuário.
3. O serviço de autorização consulta o banco de dados de permissões.
    - Se o usuário tiver permissão, a solicitação é encaminhada ao serviço de funcionalidade específica.
    - Se o usuário não tiver permissão, o acesso é bloqueado e um evento de tentativa de acesso não autorizado é registrado.
4. O serviço de funcionalidade específica processa a solicitação e retorna a resposta à interface de usuário.

### Escolha de Tecnologias

1. **Frontend:** React.js para a interface de usuário.
2. **Backend:** Node.js com Express para os serviços de autenticação, autorização e funcionalidade específica.
3. **Banco de Dados:** PostgreSQL para armazenar permissões e logs de tentativas de acesso.
4. **Autenticação e Autorização:** Uso de OAuth 2.0 e JWT (JSON Web Tokens) para autenticação e autorização.