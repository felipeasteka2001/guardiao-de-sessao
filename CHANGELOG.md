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


### 2026-06-05 — Criação do SYSTEM_RULES.md do sistema Guardião

Tipo: sistema | estrutura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- systems/guardiao/SYSTEM_RULES.md
- CHANGELOG.md

Motivo:
Estabelecer as regras gerais do sistema Guardião e completar a estrutura mínima prevista pelo Blueprint para separação entre Engine, Sistema e Campanha.

Alteração realizada:
Criado o arquivo systems/guardiao/SYSTEM_RULES.md contendo princípios de persistência, canon, checkpoints, progressão e separação de responsabilidades.

Risco:
Baixo

Impacto:
Permite que campanhas utilizem um conjunto formal de regras sistêmicas independente de tom narrativo ou canon específico.

Reversão:
Remover ou substituir o arquivo por versão anterior.

Status:
Concluído


### 2026-06-05 — Migração dos arquivos canônicos para campaigns/dante

Tipo: migração | campanha

Operador: usuário / Guardião Dev

Action usada: moveFile

Arquivos afetados:
- 01_CAMPAIGN_STATE.md -> campaigns/dante/01_CAMPAIGN_STATE.md
- 02_PERSONAGEM_E_PODERES.md -> campaigns/dante/02_PERSONAGEM_E_PODERES.md
- 03_LEDGER_NUMERICO.md -> campaigns/dante/03_LEDGER_NUMERICO.md
- 04_SESSION_LOGS_DETALHADOS.md -> campaigns/dante/04_SESSION_LOGS_DETALHADOS.md
- 05_INDICE_DE_CANON.md -> campaigns/dante/05_INDICE_DE_CANON.md
- 06_SEGREDOS_DO_MESTRE.md -> campaigns/dante/06_SEGREDOS_DO_MESTRE.md
- 07_BESTIARIO_E_DUNGEONS.md -> campaigns/dante/07_BESTIARIO_E_DUNGEONS.md
- 08_ACTIONS_E_CHECKPOINTS.md -> campaigns/dante/08_ACTIONS_E_CHECKPOINTS.md

Motivo:
Alinhar a estrutura real do repositório ao Blueprint consolidado e iniciar oficialmente a fase Multi-Campanha.

Alteração realizada:
Os arquivos canônicos da campanha Dante foram removidos da raiz e migrados para campaigns/dante/.

Risco:
Baixo

Impacto:
A campanha Dante passa a possuir estrutura própria e isolada dentro da Engine.

Reversão:
Mover os arquivos de volta para a raiz utilizando moveFile.

Status:
Concluído


### 2026-06-05 — Migração dos checkpoints da campanha Dante

Tipo: migração | campanha

Operador: usuário / Guardião Dev

Action usada: moveFile

Arquivos afetados:
- checkpoints/S01-C003.md -> checkpoints/dante/S01-C003.md
- checkpoints/S01-CAUTO-001.md -> checkpoints/dante/S01-CAUTO-001.md

Motivo:
Concluir a separação estrutural entre campanha e histórico de checkpoints conforme definido no Blueprint consolidado.

Alteração realizada:
Os checkpoints existentes da campanha Dante foram migrados para checkpoints/dante/.

Risco:
Baixo

Impacto:
A estrutura de checkpoints passa a seguir o modelo multi-campanha da Engine, mantendo histórico separado dos arquivos canônicos.

Reversão:
Mover os checkpoints de volta para a raiz da pasta checkpoints utilizando moveFile.

Status:
Concluído


### 2026-06-06 — Alinhamento do Blueprint com o estado real da Engine

Tipo: documentação | arquitetura

Operador: usuário / Guardião Dev

Action usada: updateFile

Arquivos afetados:
- PROJECT_BLUEPRINT.md
- CHANGELOG.md

Motivo:
Eliminar inconsistências entre o roadmap documentado e o estado real do repositório após a implementação inicial das fases Multi-Campanha e Multi-Sistema.

Alteração realizada:
Atualizados os status das fases do roadmap. Registrado oficialmente que a campanha Dante já está estruturada em campaigns/dante/, que os checkpoints foram migrados para checkpoints/dante/ e que o sistema guardiao já possui SYSTEM_RULES.md funcional. A fase Templates foi definida como próxima etapa oficial.

Risco:
Baixo

Impacto:
O Blueprint passa a refletir corretamente o estado atual da Engine e volta a ser uma fonte confiável de verdade para planejamento.

Reversão:
Restaurar versão anterior do PROJECT_BLUEPRINT.md através do histórico Git.

Status:
Concluído


### 2026-06-06 — Criação dos templates mínimos da Fase 4

Tipo: template | estrutura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/campaign_template/TEMPLATE_STRUCTURE.md
- templates/system_template/TEMPLATE_STRUCTURE.md
- templates/character_template/TEMPLATE_STRUCTURE.md
- CHANGELOG.md

Motivo:
Iniciar oficialmente a Fase 4 (Templates) após a consolidação do Blueprint.

Alteração realizada:
Criados documentos de estrutura mínima para campanha, sistema e personagem, definindo os artefatos obrigatórios esperados pela Engine.

Risco:
Baixo

Impacto:
A Engine passa a possuir uma primeira referência formal para criação padronizada de campanhas, sistemas e personagens.

Reversão:
Remover os arquivos de template ou substituí-los por versões mais completas.

Status:
Concluído


### 2026-06-06 — Criação dos primeiros templates funcionais de campanha

Tipo: template | estrutura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/campaign_template/CAMPAIGN_CONFIG.md
- templates/campaign_template/00_NARRATIVE_PROFILE.md
- CHANGELOG.md

Motivo:
Transformar a Fase 4 de uma estrutura conceitual para uma base funcional reutilizável.

Alteração realizada:
Criados modelos padronizados para configuração técnica da campanha e perfil narrativo, incluindo placeholders para reutilização em futuras campanhas.

Risco:
Baixo

Impacto:
Novas campanhas passam a possuir um ponto de partida consistente e alinhado à arquitetura definida no Blueprint.

Reversão:
Remover ou substituir os templates por versões revisadas.

Status:
Concluído


### 2026-06-06 — Criação do template funcional genérico de sistema

Tipo: template | sistema

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/system_template/SYSTEM_RULES.md
- CHANGELOG.md

Motivo:
Estabilizar a arquitetura Multi-Sistema antes de expandir os templates de campanha, mantendo a separação entre Engine, Sistema e Campanha.

Alteração realizada:
Criado um modelo genérico de SYSTEM_RULES.md utilizando placeholders para identificação, princípios centrais, método de resolução, progressão, recursos, checkpoints e restrições narrativas. O template foi projetado para suportar sistemas com ou sem dados, horror investigativo, fantasia, vampiro, sci-fi e outros estilos.

Risco:
Baixo

Impacto:
Fornece uma base reutilizável para criação padronizada de novos sistemas sem acoplamento ao sistema Guardião.

Reversão:
Remover ou substituir o template por uma versão revisada.

Status:
Concluído


### 2026-06-06 — Estrutura oficial inicial do sistema Vampiro

Tipo: sistema | estrutura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- systems/vampiro/SYSTEM_RULES.md
- systems/vampiro/CHARACTER_TEMPLATE.md
- systems/vampiro/REFERENCES.md
- CHANGELOG.md

Motivo:
Preparar a Engine para suportar campanhas inspiradas em Vampiro: A Máscara V20 mantendo separação entre Engine, Sistema e Campanha e respeitando restrições de conteúdo protegido.

Alteração realizada:
Criados arquivos de integração sistêmica, ficha modular e política de referências para o sistema Vampiro. Os documentos utilizam placeholders e orientações genéricas sem reproduzir regras, tabelas, disciplinas ou texto protegido.

Risco:
Baixo

Impacto:
A Engine passa a possuir uma base oficial para campanhas do sistema Vampiro, permitindo evolução futura sem acoplamento ao cenário Dante.

Reversão:
Remover os arquivos criados ou substituí-los por versões revisadas.

Status:
Concluído


### 2026-06-06 — Definição oficial da arquitetura do campaign_template

Tipo: template | arquitetura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/campaign_template/CAMPAIGN_TEMPLATE_ARCHITECTURE.md
- CHANGELOG.md

Motivo:
Evitar acoplamento da Engine à estrutura específica da campanha Dante e estabelecer uma política oficial para campanhas futuras.

Alteração realizada:
Documentada a arquitetura baseada em base obrigatória enxuta, módulos opcionais e extensões por sistema. Definidos os arquivos obrigatórios, opcionais e a política de extensões específicas para sistemas como Vampiro, Cthulhu e D&D.

Risco:
Baixo

Impacto:
Permite que novas campanhas sejam criadas com diferentes necessidades sem herdar obrigatoriamente toda a estrutura da campanha Dante.

Reversão:
Remover ou substituir a documentação por uma versão revisada.

Status:
Concluído


### 2026-06-06 — Criação dos templates obrigatórios mínimos de campanha

Tipo: template | campanha

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/campaign_template/01_CAMPAIGN_STATE.md
- templates/campaign_template/03_LEDGER_NUMERICO.md
- templates/campaign_template/05_INDICE_DE_CANON.md
- CHANGELOG.md

Motivo:
Completar a base obrigatória mínima de uma campanha conforme a arquitetura oficial definida para o campaign_template.

Alteração realizada:
Criados modelos reutilizáveis para estado da campanha, ledger numérico e índice de canon utilizando placeholders genéricos e independentes de sistema.

Risco:
Baixo

Impacto:
Uma campanha mínima agora pode ser criada utilizando apenas os arquivos obrigatórios definidos pela arquitetura oficial da Engine.

Reversão:
Remover ou substituir os templates por versões revisadas.

Status:
Concluído


### 2026-06-06 — Criação dos templates opcionais de campanha

Tipo: template | campanha

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- templates/campaign_template/02_PERSONAGEM_E_PODERES.md
- templates/campaign_template/04_SESSION_LOGS_DETALHADOS.md
- templates/campaign_template/06_SEGREDOS_DO_MESTRE.md
- templates/campaign_template/07_BESTIARIO_E_DUNGEONS.md
- templates/campaign_template/08_ACTIONS_E_CHECKPOINTS.md
- CHANGELOG.md

Motivo:
Completar os módulos opcionais previstos na arquitetura oficial do campaign_template.

Alteração realizada:
Criados templates reutilizáveis para personagens e poderes, logs detalhados, segredos do mestre, bestiário e dungeons, além de actions e checkpoints.

Risco:
Baixo

Impacto:
A estrutura de campanha agora cobre tanto a base mínima obrigatória quanto os módulos opcionais recomendados pela Engine.

Reversão:
Remover ou substituir os templates por versões revisadas.

Status:
Concluído


### 2026-06-06 — Protocolo obrigatório de criação de personagem para Vampiro

Tipo: sistema | arquitetura

Operador: usuário / Guardião Dev

Action usada: createFile

Arquivos afetados:
- systems/vampiro/CHARACTER_CREATION_PROTOCOL.md
- CHANGELOG.md

Motivo:
O playtest identificou uma falha de fluxo onde a narrativa foi iniciada antes da conclusão da ficha do personagem.

Alteração realizada:
Criado protocolo formal determinando que campanhas novas de Vampiro devem passar por apresentação da crônica, contexto da cidade, conceito, criação de ficha, revisão e registro canônico antes de qualquer prólogo ou cena jogável.

Risco:
Baixo

Impacto:
Padroniza a sessão zero e evita que campanhas futuras iniciem a narrativa sem personagem devidamente construído.

Reversão:
Remover ou revisar o protocolo conforme futuras versões da Engine.

Status:
Concluído


### 2026-06-06 — Correção do protocolo de criação de ficha Vampiro

Tipo: sistema | correção de fluxo

Operador: usuário / Guardião Dev

Motivo:
O playtest identificou que o fluxo estava solicitando Geração antes da etapa de Antecedentes e misturando construção narrativa com construção mecânica.

Correção canônica adotada:
- Geração não deve ser perguntada durante o conceito do personagem.
- Geração deve permanecer no valor padrão da crônica até a distribuição dos Antecedentes.
- Alterações de geração devem ocorrer através do Antecedente apropriado ou da regra utilizada pela mesa.
- O fluxo de criação deve separar conceito narrativo e construção mecânica.

Novo fluxo recomendado:
1. Conceito
2. Natureza
3. Comportamento
4. Escolha do método de criação da ficha
5. Atributos
6. Habilidades
7. Disciplinas
8. Antecedentes
9. Valores derivados (incluindo geração quando aplicável)
10. Revisão
11. Registro canônico
12. Início da narrativa

Impacto:
Evita perguntas prematuras sobre geração e melhora a compatibilidade do protocolo com o processo tradicional de criação de personagens em Vampiro.

Status:
Concluído


## 2026-06-10 — Interface Narrativa Obrigatória da Campanha Dante

Motivo:
- Adicionar painel de status ao final de cada cena narrada.

Arquivos afetados:
- campaigns/dante/00_NARRATIVE_PROFILE.md

Impacto:
- Toda narração da campanha Dante deverá exibir HP, Mana, Status, Invocações, Pactos, Cooldowns, Itens Relevantes e Objetivos Ativos ao final da cena.

Risco:
- Baixo. Alteração restrita ao comportamento narrativo da campanha Dante.

Reversão:
- Remover a seção 'Interface Narrativa Obrigatória' do perfil narrativo da campanha.


## 2026-06-10 — Ondas de Calamidade e Limites de Nível

Motivo:
- Formalizar a estrutura narrativa das Ondas de Calamidade na campanha Dante.
- Definir limite padrão de nível para personagens jogáveis.

Arquivos afetados:
- campaigns/dante/09_LORE_ESTRUTURAL.md
- systems/guardiao/SYSTEM_RULES.md

Impacto:
- Introduzidas Ondas de Calamidade como fundamento do mundo.
- Calamidades passam a ser ameaças mundiais canônicas.
- Primeira Calamidade definida como nível 80.
- Nível máximo padrão dos personagens estabelecido em 100.
- Entidades especiais podem ultrapassar o limite padrão.

Risco:
- Baixo. Expansão controlada da lore e do sistema.

Reversão:
- Remover o arquivo de lore estrutural e a seção de limites de nível do sistema.


## 2026-06-10 — Personagens Estruturais e Escala de Poder

Motivo:
- Definir lideranças mundiais, elite da Organização e invocados de referência.

Arquivos afetados:
- campaigns/dante/10_PERSONAGENS_ESTRUTURAIS.md

Impacto:
- Escala de poder mundial definida.
- Conselho Central da Organização definido.
- Divisão de Elite (Vanguarda) definida.
- Invocados de destaque definidos.
- Referência de níveis para futuras narrativas estabelecida.

Risco:
- Baixo. Estrutura expansível.

Reversão:
- Remover ou revisar o arquivo de personagens estruturais.


## 2026-06-10 — Profundidade Narrativa dos Personagens Estruturais

Motivo:
- Adicionar segredos, histórico e potencial de conflito aos líderes mundiais.

Arquivos afetados:
- campaigns/dante/10_PERSONAGENS_ESTRUTURAIS.md

Impacto:
- Magnus Vhalor passa a ter ligação direta com Ondas anteriores.
- Lideranças ganham conhecimento oculto e potencial para futuros conflitos narrativos.
- Possibilidade de antagonistas surgirem de posições de autoridade estabelecidas.

Risco:
- Baixo.

Reversão:
- Remover a seção de Segredos Estruturais.
