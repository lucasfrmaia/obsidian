
### Módulos

-  Todos os módulos ficam na tabelas configurações/dbsysmodulo
-  O cod_modulo de dbsysmodulo tem uma diferença muito grande de numeração (pula de 80   p/ 1 milhão)
-  Siglas de tabelas só podem ter 5 de tamanho.
-  Tabelas ficam armazenadas em configurações/dbsysarquivo
-  Campos ficam armazenados em dbsyscampo

- Campos e tabelas são relacionados por outra tabela, é uma relação n -> n, varias tabela associam a vários campos e vários campos são associados a varias tabelas
	-  Esses dados ficam armazenados em db_sysarqcamp

- Erro na primary key: nable to jump to row 0 on PostgreSQL result index 17

- Chaves estrangeiras ficam em configuracoes/db_sysforkey
	-  Erro chave estrangeira Unable to jump to row 0 on PostgreSQL result index 18

Tabela: indiceS: db_sysindices

Erro ao inserir indices: duplicate key value violates unique constraint &quot;db_sysindices_codi_pk&quot; DETAIL:  Key (codind)=(1008188) already exists