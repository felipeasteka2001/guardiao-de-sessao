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


---

### 2026-06-05 — Correção da validação de path do readAnyFile para arquivos .gitkeep

Tipo: Action

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- CHANGELOG.md
- implementação da Action readAnyFile

Motivo:
A validação de path da Action readAnyFile estava rejeitando caminhos válidos contendo arquivos .gitkeep, impedindo a leitura de arquivos existentes do repositório.

Alteração realizada:
Corrigida a validação de path da Action readAnyFile para permitir a leitura de arquivos .gitkeep válidos do repositório, mantendo as restrições de segurança para evitar acesso a paths perigosos ou não autorizados.

Risco:
Baixo

Impacto:
Permite leitura correta de arquivos .gitkeep utilizados para versionamento de diretórios, sem ampliar indevidamente a superfície de acesso da Action.

Reversão:
Restaurar a lógica anterior de validação de path caso seja identificado comportamento inesperado.

Status:
Concluído

## 2026-06-05 - Teste da Action moveFile

- Motivo: Validar a Action `moveFile` com um arquivo não canônico.
- Arquivo afetado: `TEST_AGENT_WRITE.md` → `tests/TEST_AGENT_WRITE.md`
- Impacto: Confirmação operacional da capacidade de movimentação de arquivos no repositório.
- Risco: Baixo. Arquivo de teste não canônico.
- Reversão: Mover `tests/TEST_AGENT_WRITE.md` de volta para `TEST_AGENT_WRITE.md` usando `moveFile`.

## 2026-06-05 - Teste da Action renameFile
- Motivo: Validar a Action renameFile em arquivo não canônico.
- Arquivo afetado: tests/TEST_AGENT_WRITE.md -> tests/TEST_AGENT_WRITE_RENAMED.md
- Impacto: Apenas renomeação de arquivo de teste.
- Risco: Baixo.
- Reversão: Renomear novamente para o nome original.


### 2026-06-05 — Atualização do Blueprint para refletir Actions implementadas

Tipo: documentação | Action

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md
- CHANGELOG.md

Motivo:
O Blueprint estava desatualizado em relação ao estado real das Actions administrativas já implementadas e testadas.

Alteração realizada:
Adicionada seção consolidando as Actions existentes e funcionais (healthCheck, saveCheckpoint, readFile, readAnyFile, updateFile, getRepositoryTree, createFile, createDirectory, moveFile e renameFile), bem como a distinção entre Actions operacionais e futuras.

Risco:
Baixo

Impacto:
A documentação passa a refletir o estado atual da API e das capacidades administrativas da Engine.

Reversão:
Remover a seção adicionada ao Blueprint e restaurar a versão anterior da documentação.

Status:
Concluído


### 2026-06-05 — Consolidação oficial do estado das Actions

Tipo: documentação | Action

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md
- CHANGELOG.md

Motivo:
Eliminar ambiguidades entre seções antigas do Blueprint e o estado operacional real das Actions já implementadas e testadas.

Alteração realizada:
Registrada consolidação oficial declarando healthCheck, saveCheckpoint, readFile, readAnyFile, updateFile, getRepositoryTree, createFile, createDirectory, moveFile e renameFile como Actions implementadas e testadas. searchRepository permanece em backlog e deleteFile permanece adiada por segurança.

Risco:
Baixo

Impacto:
Reduz inconsistências documentais e estabelece uma referência oficial para o estado atual da API administrativa.

Reversão:
Remover a seção de consolidação e revisar manualmente o Blueprint.

Status:
Concluído


### 2026-06-05 — Consolidação completa do PROJECT_BLUEPRINT.md

Tipo: documentação | arquitetura

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md
- CHANGELOG.md

Motivo:
Remover seções obsoletas, redundâncias e referências desatualizadas sobre Actions administrativas, mantendo o Blueprint como fonte única de verdade.

Alteração realizada:
Substituição completa do PROJECT_BLUEPRINT.md por uma versão consolidada contendo arquitetura, roadmap, separação Engine/Campanhas, estado atual das Actions, regras de segurança e prioridades oficiais do projeto.

Risco:
Baixo

Impacto:
Melhora a governança documental, reduz ambiguidades e facilita futuras evoluções da Engine.

Reversão:
Restaurar versão anterior do PROJECT_BLUEPRINT.md a partir do histórico Git.

Status:
Concluído


### 2026-06-05 — Criação dos arquivos iniciais da campanha Dante

Tipo: estrutura | campanha

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- campaigns/dante/CAMPAIGN_CONFIG.md
- campaigns/dante/00_NARRATIVE_PROFILE.md
- CHANGELOG.md

Motivo:
Iniciar a estrutura formal da campanha Dante conforme definido no Blueprint consolidado e preparar a futura migração dos arquivos canônicos.

Alteração realizada:
Criados os arquivos CAMPAIGN_CONFIG.md e 00_NARRATIVE_PROFILE.md dentro de campaigns/dante/, definindo configuração técnica da campanha e perfil narrativo separado da Engine.

Risco:
Baixo

Impacto:
Primeiro passo efetivo da Fase Multi-Campanha, permitindo separar configuração técnica, perfil narrativo e canon da campanha.

Reversão:
Remover os arquivos criados ou restaurar versão anterior da estrutura da campanha.

Status:
Concluído
