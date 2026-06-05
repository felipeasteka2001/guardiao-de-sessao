# Guardião de Sessão — Changelog

Este arquivo registra alterações estruturais, técnicas e canônicas relevantes do projeto Guardião de Sessão.

O objetivo do changelog é permitir auditoria, revisão, rastreabilidade e recuperação caso alguma alteração cause erro, perda de contexto ou inconsistência no repositório.

## Regras do Changelog

Toda alteração relevante feita no projeto deve ser registrada aqui.

Alterações que devem ser registradas:

- criação, edição, movimentação ou renomeação de arquivos importantes
- criação de pastas estruturais
- alterações em Actions
- alterações no schema OpenAPI
- mudanças na arquitetura do repositório
- migração de arquivos entre pastas
- mudanças em regras da Engine
- mudanças em sistemas narrativos
- mudanças em templates
- alterações canônicas consolidadas
- correções após erro do Agent ou da API

Alterações pequenas, temporárias ou testes isolados podem ser registradas de forma resumida.

## Formato Obrigatório de Entrada

Cada entrada deve seguir este modelo:

### YYYY-MM-DD — Título curto da alteração

Tipo: documentação | estrutura | API | Action | campanha | sistema | template | correção | migração | teste

Operador: usuário | Guardião Dev | Guardião Produção | manual

Action usada: nome da Action usada ou "manual"

Arquivos afetados:
- path/do/arquivo.md
- path/da/pasta/

Motivo:
Explique por que a alteração foi feita.

Alteração realizada:
Explique objetivamente o que mudou.

Risco:
Baixo | Médio | Alto

Impacto:
Explique o que essa alteração permite, corrige ou modifica.

Reversão:
Explique como desfazer ou revisar a alteração caso algo dê errado.

Status:
Planejado | Em andamento | Concluído | Revertido | Parcial

---

## Entradas

### 2026-06-05 — Criação do PROJECT_BLUEPRINT.md

Tipo: documentação

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md

Motivo:
Criar uma fonte oficial para registrar a visão, arquitetura, roadmap, decisões principais e estrutura alvo da Engine Narrativa Persistente.

Alteração realizada:
Criado o arquivo PROJECT_BLUEPRINT.md na raiz do repositório.

Risco:
Baixo

Impacto:
O projeto passa a ter uma fonte oficial para decisões arquiteturais e planejamento da Engine.

Reversão:
Remover PROJECT_BLUEPRINT.md ou substituir por uma versão anterior, se necessário.

Status:
Concluído

---

### 2026-06-05 — Criação do CHANGELOG.md

Tipo: documentação

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- CHANGELOG.md

Motivo:
Criar um histórico auditável das alterações estruturais, técnicas e canônicas relevantes do projeto.

Alteração realizada:
Criado o arquivo CHANGELOG.md na raiz do repositório com regras de registro, formato obrigatório de entrada e primeiras entradas do projeto.

Risco:
Baixo

Impacto:
Toda alteração futura poderá ser rastreada com motivo, impacto, risco e possibilidade de reversão.

Reversão:
Remover CHANGELOG.md ou substituir por uma versão anterior, se necessário.

Status:
Concluído



---

### 2026-06-05 — Validação de leitura e atualização do changelog

Tipo: teste

Operador: usuário

Action usada: readFile + updateFile

Arquivos afetados:
- CHANGELOG.md

Motivo:
Validar a capacidade de leitura e escrita controlada do arquivo de changelog.

Alteração realizada:
Adicionada uma entrada de teste registrando a validação bem-sucedida da leitura e atualização do CHANGELOG.md.

Risco:
Baixo

Impacto:
Confirma o funcionamento do fluxo de auditoria e atualização documental.

Reversão:
Remover esta entrada de teste caso ela não seja mais necessária.

Status:
Concluído


---

### 2026-06-05 — Decisão sobre perfis narrativos por campanha

Tipo: arquitetura

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md
- CHANGELOG.md

Motivo:
Evitar que o tom e o canon da campanha Dante contaminem a Engine global e permitir múltiplas campanhas com estilos narrativos diferentes.

Alteração realizada:
Registrada a regra de que tom, tema, ritmo, atmosfera e estilo de narração devem ficar em campaigns/{campaign_id}/00_NARRATIVE_PROFILE.md, enquanto regras do sistema ficam em systems/{system_id}/SYSTEM_RULES.md.

Risco:
Baixo

Impacto:
A Engine passa a suportar campanhas com identidades narrativas diferentes sem misturar regras globais, sistema e canon específico.

Reversão:
Remover ou revisar a seção “Separação de Instruções Narrativas” no PROJECT_BLUEPRINT.md.

Status:
Concluído
