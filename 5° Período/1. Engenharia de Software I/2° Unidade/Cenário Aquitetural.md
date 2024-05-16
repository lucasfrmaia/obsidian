
**ID**: CA-01
**Nome**: Suporte a ataques DDoS
**Atributo de Qualidade**: Segurança

**Driver:** "O sistema está recebendo constantes ataques DDoS, para contornar isso foi implmentado um firewall para bloquear esses ataques, visando suportar até 10 mill ataques DDSs"

- **Estímulo**: Ataques DDoS direcionados ao sistema.
- **Fonte de Estímulo**: Atacantes externos maliciosos.
- **Artefato**: Sistema “TabNews”.
- **Ambiente**: Ambiente de produção, com alta carga de tráfego e possibilidade de ataques.
- **Resposta**: O sistema deve continuar funcionando mesmo sob ataques DDoS.
- **Medida de Resposta**: O sistema é considerado bem-sucedido se permanecer disponível ao receber até 10 mill ataques DDoS

**Decisões de Design (Táticas):**

1. **Firewall e Filtros de Tráfego:**
    - **Decisão:** Utilizar firewalls e filtros de tráfego para bloquear ataques DDoS conhecidos.

**Suposições:**
- Os servidores têm capacidade de processamento e largura de banda suficientes para lidar com os ataques.

**Escala:**
- O sistema deve ser dimensionado para suportar 10.000 ataques DDoS simultâneos.
- A infraestrutura deve ser capaz de lidar com picos de tráfego sem degradação significativa.

**Raciocínio:**
- A combinação de balanceamento de carga, redundância de servidores e monitoramento em tempo real garante alta disponibilidade.
- Os filtros de tráfego e escalabilidade automática ajudam a mitigar ataques DDoS.
- Os testes de estresse validam a capacidade do sistema.

**Trade-offs:**
* Escalabilidade

---
**ID**: CA-02
**Nome**: Criptografia de dados sensitives no cadastro

**Driver**: "Ao fazer o cadastro no sistema, o sistema deve os criptografar dados sensitives, visando manter a segurança dos dados"

- **Estímulo:** Um usuário realiza o cadastro no sistema, fornecendo dados sensíveis (por exemplo, senha, número de CPF, informações bancárias).
- **Fonte de Estímulo:** O próprio usuário ou um agente externo que interage com o sistema.
- **Artefato:** O módulo responsável pelo gerenciamento de autenticação e armazenamento de dados do usuário.
- **Ambiente:** Ambiente de produção do sistema, incluindo servidores, banco de dados e comunicação de rede.
- **Resposta:** O sistema deve criptografar os dados sensíveis do usuário antes de armazená-los no banco de dados.
- **Medida de Resposta:** A resposta é considerada satisfatória se os dados sensíveis estiverem protegidos contra acesso não autorizado.

1. **Decisões de Design (Táticas):**
    
    - **Criptografia de Dados Sensíveis:**
        - **Decisão:** Utilizar criptografia forte (por exemplo, AES-256) para proteger os dados sensíveis do usuário, como senhas, informações de pagamento e dados pessoais.
    
2. **Suposições:**
    - Os usuários fornecem informações sensíveis durante o cadastro, como nome, endereço, número de telefone e dados de pagamento.
    - O sistema deve ser capaz de lidar com milhares de solicitações de registro simultâneas.
    
1. **Escala:**
    - A escalabilidade horizontal (adicionar mais servidores) é preferível para lidar com picos de tráfego.
    
1. **Raciocínio:**
    - A criptografia e o gerenciamento de chaves são essenciais para proteger os dados do usuário.
    - A escolha de algoritmos e protocolos deve ser baseada em padrões de segurança reconhecidos.
    
1. **Trade-offs:**
    - **Desempenho** 

---

**ID**: CA-03

**Driver**: "Ao navegar pelo sistema, o usuário deve ser impedindo de acessar rotas que não possui permissão, visando a integridade do sistema"

**Driver: Controle de Acesso Baseado em Permissões do Usuário**
1. **Estímulo:** Um usuário tenta acessar um recurso protegido no sistema 
2. **Fonte de Estímulo:** O próprio usuário ou um componente do sistema que solicita o acesso.
3. **Artefato:** O sistema ou subsistema que gerencia as permissões de acesso.
4. **Ambiente:**  Ambiente de produção do sistema
5. **Resposta:** O sistema verifica as permissões do usuário para o recurso solicitado e concede ou nega o acesso com base nas regras de permissão.
6. **Medida de Resposta:** A resposta é considerada satisfatória se o acesso é concedido apenas a usuários autorizados e negado a usuários não autorizados.
#### Decisões de Design (Táticas):

1. **Autenticação e Autorização:**
    - Implementar um sistema de autorização baseado em papéis (RBAC) para definir permissões específicas para cada usuário (por exemplo, administrador, editor, leitor).
#### Suposições:
- As permissões são definidas em nível de usuário e/ou grupo.
#### Escala:
- A escalabilidade horizontal (adicionar mais servidores) pode ser necessária para atender à demanda.
#### Raciocínio:
- A separação de responsabilidades entre autenticação e autorização permite flexibilidade na implementação.
#### Trade-offs:
- Granularidade.


