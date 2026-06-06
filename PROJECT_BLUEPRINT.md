# Guardião de Sessão — Project Blueprint

## 1. Objetivo do Projeto

O Guardião de Sessão é uma Engine Narrativa Persistente.

Objetivos principais:
- múltiplos sistemas
- múltiplas campanhas
- múltiplos personagens
- canon persistente
- checkpoints automáticos
- estrutura escalável de arquivos
- futura interface própria
- futura geração de imagens narrativas

A campanha Dante é apenas a primeira campanha da Engine.

---

## 2. Separação Arquitetural

### Engine
Responsável por:
- arquitetura
- regras gerais
- templates
- sistemas
- convenções
- Actions administrativas
- estrutura reutilizável

### Campanhas
Responsáveis por:
- estado narrativo
- personagens
- poderes
- ledger numérico
- logs
- canon
- segredos
- bestiário
- checkpoints relacionados

---

## 3. Roadmap Oficial

### Fase 0 — Blueprint
Status: concluída

### Fase 1 — Actions Administrativas
Status: concluída para o escopo essencial

### Fase 2 — Multi-Campanha
Status: implementada inicialmente com a campanha Dante

### Fase 3 — Multi-Sistema
Status: implementada inicialmente com o sistema guardiao

### Fase 4 — Templates
Status: próxima etapa

### Fase 5 — Interface Web
Status: futuro

### Fase 6 — Imagens Narrativas
Status: futuro

---

## 4. Prioridade Oficial

1. Blueprint
2. Actions Administrativas
3. Multi-Campanha
4. Multi-Sistema
5. Templates
6. Interface
7. Imagens

Nenhuma funcionalidade visual possui prioridade superior à conclusão da Engine até a Fase 4.

---

## 5. Estrutura Alvo do Repositório

guardiao-de-sessao/

- PROJECT_BLUEPRINT.md
- CHANGELOG.md
- systems/
- campaigns/
- checkpoints/
- templates/
- shared/

Estrutura desejada por campanha:

campaigns/{campaign_id}/
- CAMPAIGN_CONFIG.md
- 00_NARRATIVE_PROFILE.md
- arquivos canônicos da campanha

Checkpoints:

checkpoints/{campaign_id}/

---

## 6. Checkpoints

Checkpoints não devem ficar dentro das campanhas.

Correto:
- campaigns/{campaign_id}/
- checkpoints/{campaign_id}/

Motivos:
- escalabilidade
- backup facilitado
- separação entre canon e histórico
- melhor organização

---

## 7. Configuração de Campanha

Cada campanha deve possuir:

CAMPAIGN_CONFIG.md

Responsável por definir:
- sistema utilizado
- status da campanha
- arquivos principais
- configurações técnicas

---

## 8. Separação de Responsabilidades dos Agents

### Guardião Dev
Pode:
- reorganizar repositório
- criar campanhas
- criar sistemas
- criar templates
- executar Actions administrativas autorizadas

### Guardião Produção
Pode:
- ler contexto
- narrar campanhas
- salvar checkpoints

Não pode:
- alterar arquitetura
- reorganizar estrutura sem autorização

---

## 9. Estado Atual da API

Hospedagem:
- Vercel

Integração:
- GitHub API

### Actions implementadas e funcionais

- healthCheck
- saveCheckpoint
- readFile
- readAnyFile
- updateFile
- getRepositoryTree
- createFile
- createDirectory
- moveFile
- renameFile

### Actions implementadas e testadas

- healthCheck
- saveCheckpoint
- readFile
- readAnyFile
- updateFile
- getRepositoryTree
- createFile
- createDirectory
- moveFile
- renameFile

### Backlog de Actions

- searchRepository

### Actions adiadas por segurança

- deleteFile

---

## 10. Estado Estrutural Atual da Engine

### Multi-Campanha

A fase Multi-Campanha foi implementada inicialmente com a campanha Dante.

Arquivos canônicos da campanha Dante migrados para:
- campaigns/dante/

Arquivos estruturais existentes da campanha Dante:
- campaigns/dante/CAMPAIGN_CONFIG.md
- campaigns/dante/00_NARRATIVE_PROFILE.md
- campaigns/dante/01_CAMPAIGN_STATE.md
- campaigns/dante/02_PERSONAGEM_E_PODERES.md
- campaigns/dante/03_LEDGER_NUMERICO.md
- campaigns/dante/04_SESSION_LOGS_DETALHADOS.md
- campaigns/dante/05_INDICE_DE_CANON.md
- campaigns/dante/06_SEGREDOS_DO_MESTRE.md
- campaigns/dante/07_BESTIARIO_E_DUNGEONS.md
- campaigns/dante/08_ACTIONS_E_CHECKPOINTS.md

Checkpoints da campanha Dante migrados para:
- checkpoints/dante/

### Multi-Sistema

A fase Multi-Sistema foi implementada inicialmente com o sistema guardiao.

Sistema estruturado:
- systems/guardiao/SYSTEM_RULES.md

Sistemas reservados para evolução futura:
- systems/dnd/
- systems/vampiro/

### Templates

A fase Templates é a próxima etapa real da Engine.

Diretórios existentes:
- templates/campaign_template/
- templates/system_template/
- templates/character_template/

Esses templates ainda precisam receber conteúdo mínimo padronizado.

---

## 11. Segurança Operacional

Toda alteração estrutural exige autorização explícita do usuário.

As operações devem registrar:
- motivo
- arquivos afetados
- resultado
- impacto
- possibilidade de reversão

Nunca apagar conteúdo sem autorização explícita.

---

## 12. Separação de Instruções Narrativas

A Engine deve separar:

- regras globais do Agent
- regras do sistema narrativo
- perfil narrativo da campanha
- estado canônico da campanha

Arquivos:

campaigns/{campaign_id}/00_NARRATIVE_PROFILE.md

systems/{system_id}/SYSTEM_RULES.md

campaigns/{campaign_id}/CAMPAIGN_CONFIG.md

Ordem de carregamento durante narração:

1. CAMPAIGN_CONFIG.md
2. 00_NARRATIVE_PROFILE.md
3. SYSTEM_RULES.md
4. arquivos canônicos
5. checkpoints relevantes

A campanha define o estilo narrativo.
O sistema define as regras.
A Engine define persistência, estrutura e comportamento técnico.

---

## 13. Próxima Meta Oficial

Concluir a camada de Engine antes de iniciar interface ou imagens.

Prioridades imediatas:
1. Criar template mínimo de campanha
2. Criar template mínimo de sistema
3. Criar template mínimo de personagem
4. Testar geração manual de uma nova campanha a partir dos templates
5. Somente depois considerar automações adicionais
