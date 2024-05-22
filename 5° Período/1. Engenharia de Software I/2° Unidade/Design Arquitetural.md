
## Bloqueio de Usuário Após Tentativas de Login

**Driver**: O Sistema bloqueará por 30min o usuário após 5 tentativas de login

**Contexto:** O sistema de autenticação de usuários para um portal online, onde os usuários podem fazer login utilizando um nome de usuário e senha. O sistema precisa ser seguro para proteger contra ataques de força bruta e acessos não autorizados.

**Estímulo:** Um usuário tenta fazer login no sistema utilizando um nome de usuário e senha incorretos repetidas vezes.

**Resposta:** Após 5 tentativas de login falhadas consecutivas, o sistema bloqueará o usuário, impedindo novas tentativas de login por um período específico de tempo.

**Medida de Resposta:** O sistema deve bloquear o usuário imediatamente após a quinta tentativa de login falhada e manter o bloqueio por um período de 30 minutos antes de permitir novas tentativas de login.

---
**Trade-offs**: Usabilidade e Performance

**Suposição**: O sistema não conseguir bloquear as tentativas, e o usuário conseguir spamar tentativas sobrecarregando o servidor.
#### Raciocínio
1. O usuário insere o nome de usuário e senha na interface do cliente.
2. O serviço de login recebe e verifica as credenciais:
    - Se as credenciais estiverem corretas, o usuário é autenticado com sucesso.
    - Se as credenciais estiverem incorretas, o contador de tentativas falhadas é incrementado.
3. Após a quinta tentativa falhada, o serviço de login atualiza o status do usuário para "bloqueado" no banco de dados.
4. O serviço de auditoria registra cada tentativa de login, incluindo sucesso, falha e bloqueio.
### Decisão de Design
1. **Frontend:** React.js para a interface do cliente.
2. **Backend:** Node.js com Express para o serviço de login.
3. **Banco de Dados:** PostgreSQL para armazenar informações dos usuários.
4. **Auditoria:** ELK Stack (Elasticsearch, Logstash, Kibana) para registrar e analisar as tentativas de login.
---
## Criptografia de Dados Sensíveis de Usuários

**Driver**: "o sistema deve criptografar dados sensives de usuários antes de salvar no banco de dados"

**Contexto:** Um sistema de gerenciamento de usuários que armazena informações sensíveis, como números de cartões de crédito e senhas, em um banco de dados. A segurança dos dados é uma prioridade para proteger a privacidade dos usuários e cumprir regulamentações como a LGPD (Lei Geral de Proteção de Dados) e GDPR (General Data Protection Regulation).

**Estímulo:** O sistema recebe uma solicitação para criar ou atualizar dados sensíveis de um usuário, como senha ou informações de pagamento.

**Resposta:** Antes de salvar os dados no banco de dados, o sistema deve criptografá-los utilizando um algoritmo de criptografia forte, como AES-256.

**Medida de Resposta:** Os dados devem ser criptografados em menos de 100 ms para cada solicitação e a chave de criptografia deve ser gerenciada de forma segura.

---
 **Escalabilidade**: O sistema deve ser capaz de criptografar dados de maneira eficiente, mesmo sob alta carga.

**Trade-offs**:  Desempenho, Manutenibilidade
#### Raciocínio
1. O usuário insere dados sensíveis na interface do cliente.
2. O serviço de aplicação recebe a solicitação e envia os dados para o serviço de criptografia.
3. O serviço de criptografia utiliza a chave de criptografia gerenciada pelo KMS para criptografar os dados.
4. Os dados criptografados são enviados para o banco de dados e armazenados de forma segura.
5. As chaves de criptografia são gerenciadas pelo KMS, garantindo que estejam protegidas contra acesso não autorizado.

**Suposição**: os dados podem não usar uma criptografia adequada e em um possível roubo de dados, essa criptografia ser quebrada.
#### Decisão de Design
1. **Frontend:** React.js para a interface do cliente.
2. **Backend:** Node.js com Express para o serviço de aplicação.
3. **Serviço de Criptografia:** Biblioteca de criptografia como `crypto` em Node.js.
4. **Banco de Dados:** PostgreSQL com suporte a dados criptografados.
5. **Gerenciamento de Chaves:** AWS KMS (Key Management Service) ou um módulo de segurança de hardware (HSM) para gerenciar as chaves de criptografia.

---
## Controle de Acesso Baseado em Permissões

**Driver**: "O sistema deve ter um gerenciamento permissões para permitir/bloquear acesso de usuários em determinados componentes, visando a integridade do sistema"

**Contexto:** Um sistema de gerenciamento que permite a colaboração de diferentes usuários com diferentes níveis de acesso. O sistema deve garantir que cada usuário tenha acesso apenas às funcionalidades e dados para os quais tem permissão.

**Estímulo:** Um usuário tenta acessar uma funcionalidade do sistema que está além de suas permissões atribuídas.

**Resposta:** O sistema verifica as permissões do usuário e, se ele não tiver as permissões necessárias, bloqueia o acesso à funcionalidade e retorna uma mensagem de erro apropriada.

**Medida de Resposta:** O sistema deve bloquear o acesso à funcionalidade de forma imediata (dentro de 100 ms) e registrar o evento de tentativa de acesso não autorizado.

---
 **Trade-off**:  Performance e Manutenibilidade
#### Raciocínio
1. O usuário tenta acessar uma funcionalidade através da interface de usuário.
2. A interface de usuário envia uma solicitação ao serviço de autorização para verificar as permissões do usuário.
3. O serviço de autorização consulta o banco de dados de permissões.
    - Se o usuário tiver permissão, a solicitação é encaminhada ao serviço de funcionalidade específica.
    - Se o usuário não tiver permissão, o acesso é bloqueado e um evento de tentativa de acesso não autorizado é registrado.
4. O serviço de funcionalidade específica processa a solicitação e retorna a resposta à interface de usuário.

**Suposição**: O usuário conseguir acessar um componente sem a devida permissão

**Escalabilidade**: O sistema deve ser capaz de lidar com diversos acessos simultaneos.
### Decisão de Design
1. **Frontend:** React.js para a interface de usuário.
2. **Backend:** Node.js com Express para os serviços de autenticação, autorização e funcionalidade específica.
3. **Banco de Dados:** PostgreSQL para armazenar permissões e logs de tentativas de acesso.
4. **Autenticação e Autorização:** Uso de OAuth 2.0 e JWT (JSON Web Tokens) para autenticação e autorização.