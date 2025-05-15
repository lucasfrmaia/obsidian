
##  **1. `pg_stat_statements`: Monitoramento detalhado de consultas no PostgreSQL**

A extensão `pg_stat_statements` é uma ferramenta fundamental para **monitoramento de desempenho no PostgreSQL**. Ela coleta estatísticas agregadas sobre todas as consultas executadas no banco de dados, permitindo análises detalhadas sobre _quais queries estão mais lentas, mais chamadas ou consomem mais recursos_. Isso facilita a identificação de gargalos de performance e o ajuste de SQLs problemáticos.

###  **Objetivo**

A `pg_stat_statements` agrupa estatísticas por uma versão "normalizada" da query (com os valores literais removidos), permitindo medir **quantidade de execuções**, **tempo gasto**, **acessos a blocos**, **uso de cache**, **geração de WAL**, entre outras métricas.

---

### 🧾 **Colunas da visão `pg_stat_statements` (detalhadas)**

#### 🔐 **Informações gerais**

- `userid`: OID do usuário que executou a consulta (referência a `pg_authid.oid`)
    
- `dbid`: OID do banco de dados onde a consulta foi executada (referência a `pg_database.oid`)
    
- `toplevel`: `true` se a consulta foi executada diretamente (não dentro de uma função/plano maior)
    

#### 📋 **Identificação da query**

- `queryid`: Hash que identifica consultas logicamente equivalentes (mesmo comando, diferentes valores)
    
- `query`: Texto da consulta representativa
    

#### 🧠 **Planejamento (se `track_planning` estiver ativado)**

- `plans`: Quantas vezes a consulta foi planejada
    
- `total_plan_time`: Tempo total gasto no planejamento
    
- `min_plan_time`, `max_plan_time`, `mean_plan_time`, `stddev_plan_time`: Estatísticas descritivas do tempo de planejamento
    

#### ⚙️ **Execução**

- `calls`: Número de vezes que a consulta foi executada
    
- `total_exec_time`: Tempo total gasto na execução
    
- `min_exec_time`, `max_exec_time`, `mean_exec_time`, `stddev_exec_time`: Estatísticas descritivas da execução
    

#### 📊 **Linhas afetadas**

- `rows`: Total de linhas retornadas ou modificadas
    

#### 📦 **Acessos a blocos**

- `shared_blks_*`: Acesso a blocos compartilhados (cache de dados global)
    
    - `hit`: blocos já em cache
        
    - `read`: blocos lidos do disco
        
    - `dirtied`: blocos modificados na memória
        
    - `written`: blocos escritos no disco
        
- `local_blks_*`: Acessos locais (em tabelas temporárias locais)
    
- `temp_blks_*`: Acessos a arquivos temporários
    

#### 🕓 **Tempos de I/O (se `track_io_timing` ativado)**

- `*_blk_read_time` / `*_blk_write_time`: Tempo gasto em leitura/gravação de blocos (compartilhados, locais ou temporários)
    

#### 🔄 **WAL - Write-Ahead Logging**

- `wal_records`: Registros de WAL gerados
    
- `wal_fpi`: Full Page Images geradas
    
- `wal_bytes`: Total de bytes escritos no WAL
    

#### ⚡ **JIT (Just-In-Time Compilation)**

- `jit_functions`, `jit_deform_count`: Número de funções JIT compiladas
    
- `jit_generation_time`, `jit_deform_time`, etc.: Tempo gasto com geração, otimização e emissão de código
    

#### ⏳ **Coleta de estatísticas**

- `stats_since`: Quando a coleta geral começou
    
- `minmax_stats_since`: Quando os valores min/max foram coletados desde o último reset com `pg_stat_statements_reset(minmax_only := true)`
    

---

## 💡 **2. `pg_hint_info`: Monitoramento de _hints_ de otimização**

### 🔍 O que são **hints**?

_Hints_ (ou **dicas**) são instruções opcionais que podem ser inseridas nas queries SQL para **influenciar diretamente o otimizador de consultas** do banco de dados. Eles indicam, por exemplo, que se deve usar um índice específico, um tipo de join ou uma ordem de execução preferencial.

Exemplo:

```sql
SELECT /*+ HashJoin(t1 t2) */ * FROM t1 JOIN t2 ON t1.id = t2.id;
```

Esse hint sugere ao PostgreSQL (via `pg_hint_plan`) que use um `Hash Join` ao invés de um `Nested Loop`, por exemplo.

---


Sem explain:

1. Carrega todas as linhas de tabela1 (menor) e cria uma hash table.
2. Faz um Seq Scan em tabela2.
3. Para cada linha de tabela2:
    a. Extrai chave de junção.
    b. Aplica função de hash.
    c. Busca na hash table.
4. Se encontrar, retorna resultado.

Com Explain

1. Escaneia tabela1 onde id < 100.
2. Para cada linha em tabela1 (ex: id = 42):
    a. Usa índice para buscar em tabela2 onde id_tabela1 = 42.
    b. Se encontrar, retorna par.
3. Repete para cada linha de tabela1.




---

### Hints de Join

|                   |                                        |
| ----------------- | -------------------------------------- |
| `NestLoop(t1 t2)` | Força um Nested Loop entre `t1` e `t2` |
|                   |                                        |
| `HashJoin(t1 t2)` | Força um Hash Join                     |
|                   |                                        |
