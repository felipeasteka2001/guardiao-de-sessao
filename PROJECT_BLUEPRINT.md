# Guardião de Sessão — Project Blueprint

## 1. Objetivo do Projeto

O Guardião de Sessão é uma Engine Narrativa Persistente, não apenas um GPT de RPG.

Seu objetivo é suportar:

- múltiplos sistemas
- múltiplas campanhas
- múltiplos personagens
- canon persistente
- checkpoints automáticos
- estrutura escalável de arquivos
- futura interface própria
- futura geração de imagens narrativas

A campanha Dante é apenas a primeira campanha da engine.

## 2. Decisão Arquitetural Principal

O projeto deve separar claramente:

### Engine

Responsável por:

- arquitetura
- regras gerais
- templates
- sistemas
- convenções
- ações administrativas
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

Exemplos de campanhas futuras:

- Dante
- Vampiro São Paulo
- Vampiro New York
- Forgotten Realms
- Cthulhu

## 3. Roadmap Oficial

### Fase 0 — Blueprint

Status: em andamento.

Objetivo:

Definir a visão, arquitetura, estrutura e regras principais do projeto antes de expandir funcionalidades.

### Fase 1 — Actions Administrativas

Status: em implementação.

Objetivo:

Permitir que o Agent consiga administrar o repositório com segurança.

Actions planejadas:

- GET /api/tree
- GET /api/read-any-file
- GET /api/search
- POST /api/create-file
- POST /api/create-directory
- POST /api/update-file
- POST /api/move-file
- POST /api/rename-file

### Fase 2 — Multi-Campanha

Status: não iniciado.

Objetivo:

Permitir múltiplas campanhas isoladas dentro da engine.

### Fase 3 — Multi-Sistema

Status: não iniciado.

Objetivo:

Permitir múltiplos sistemas narrativos, como:

- guardiao
- vampiro
- dnd
- cthulhu

Cada campanha deve apontar para um sistema.

### Fase 4 — Templates

Status: não iniciado.

Objetivo:

Criar modelos reutilizáveis para campanhas, personagens e sistemas.

### Fase 5 — Interface Web

Status: futuro.

Objetivo:

Criar painel visual próprio para gerenciamento narrativo.

### Fase 6 — Imagens Narrativas

Status: futuro.

Objetivo:

Gerar imagens persistentes de cenas, personagens e momentos narrativos.

## 4. Regra de Prioridade

Nenhuma funcionalidade de interface, imagem ou experiência visual possui prioridade maior que a conclusão da Engine até a Fase 4.

Prioridade atual:

1. Blueprint
2. Actions Administrativas
3. Multi-Campanha
4. Multi-Sistema
5. Templates
6. Interface
7. Imagens

## 5. Estrutura Alvo do Repositório

O repositório principal permanecerá com o nome:

guardiao-de-sessao

Estrutura alvo:

guardiao-de-sessao/

- PROJECT_BLUEPRINT.md
- systems/
  - guardiao/
  - vampiro/
  - dnd/
- campaigns/
  - dante/
    - CAMPAIGN_CONFIG.md
    - 01_CAMPAIGN_STATE.md
    - 02_PERSONAGEM_E_PODERES.md
    - 03_LEDGER_NUMERICO.md
    - 04_SESSION_LOGS_DETALHADOS.md
    - 05_INDICE_DE_CANON.md
    - 06_SEGREDOS_DO_MESTRE.md
    - 07_BESTIARIO_E_DUNGEONS.md
    - 08_ACTIONS_E_CHECKPOINTS.md
  - vampiro_sp/
- checkpoints/
  - dante/
  - vampiro_sp/
- templates/
  - campaign_template/
  - character_template/
  - system_template/
- shared/
  - README.md
  - conventions.md

## 6. Decisão Sobre Checkpoints

Checkpoints não devem ficar dentro da pasta da campanha.

Errado:

campaigns/dante/checkpoints/

Correto:

campaigns/dante/

e

checkpoints/dante/

Motivos:

- checkpoints crescem muito
- facilita busca
- facilita backup
- não polui arquivos canônicos
- separa estado consolidado de histórico bruto

## 7. CAMPAIGN_CONFIG.md

Cada campanha deve possuir um arquivo CAMPAIGN_CONFIG.md.

Exemplo:

Campaign Name: Dante  
System: guardiao  
Status: active  
Created: 2026-06

Objetivo:

Permitir que o Agent descubra rapidamente:

- qual sistema usar
- se a campanha está ativa
- qual configuração carregar
- quais arquivos canônicos pertencem à campanha

## 8. Decisão Sobre Agents

Não criar outro Agent agora.

Primeiro construir a Engine.

Depois criar separação entre:

### Guardião Dev

Agent com poderes administrativos.

Pode:

- reorganizar repositório
- criar campanhas
- mover arquivos
- criar sistemas
- criar templates
- ajustar estrutura

### Guardião Produção

Agent narrador.

Pode:

- ler contexto
- narrar campanha
- salvar checkpoints

Não pode:

- reorganizar arquitetura
- mover arquivos estruturais
- alterar sistemas sem autorização

## 9. API Atual

API:

guardiao-api

Hospedagem:

Vercel

Integração:

GitHub API

Endpoints já existentes:

- healthCheck
- saveCheckpoint
- readFile
- updateFile
- getRepositoryTree
- createFile

## 10. Bloqueios Resolvidos

O problema de autorização GPT → API foi resolvido.

Causa provável:

GUARDIAO_API_KEY precisava estar alinhada entre:

- Vercel Environment Variables
- Authentication da Action no Custom GPT

A Action createFile foi testada com sucesso criando TEST_AGENT_WRITE.md.

## 11. Próximas Actions Administrativas

Próximas Actions necessárias:

1. createDirectory
2. readAnyFile
3. moveFile
4. renameFile

Delete não deve ser implementado agora.

## 12. Próxima Meta

Criar a estrutura base da Engine:

- systems/
- campaigns/
- templates/
- shared/
- checkpoints/dante/

Depois migrar os arquivos atuais da raiz para:

campaigns/dante/

E mover checkpoints atuais para:

checkpoints/dante/

## 13. Regra de Segurança

Toda alteração estrutural deve exigir autorização explícita do usuário.

Actions administrativas devem registrar:

- path afetado
- motivo
- tipo de operação
- confirmação explícita
- resultado retornado pelo GitHub

Nunca apagar conteúdo sem autorização explícita.



## Separação de Instruções Narrativas

As instruções centrais do Agent não devem conter tom, tema ou canon específico de uma campanha.

A Engine deve separar:

- regras globais do Agent
- regras do sistema narrativo
- perfil narrativo da campanha
- estado canônico da campanha

As Instructions centrais do Custom GPT devem definir o comportamento geral do Agent, regras de segurança, uso de Actions, persistência, checkpoints e prioridade de fontes.

O tom, tema, ritmo, atmosfera, limites narrativos e estilo de narração devem ser definidos por campanha em um arquivo próprio:

campaigns/{campaign_id}/00_NARRATIVE_PROFILE.md

O arquivo CAMPAIGN_CONFIG.md deve definir configuração técnica da campanha, como nome, status, sistema usado e paths principais.

O sistema usado pela campanha deve definir regras gerais em:

systems/{system_id}/SYSTEM_RULES.md

Durante uma narração, o Agent deve carregar e respeitar, nesta ordem:

1. CAMPAIGN_CONFIG.md
2. 00_NARRATIVE_PROFILE.md
3. SYSTEM_RULES.md
4. arquivos canônicos da campanha
5. checkpoints relevantes

A campanha define o sabor narrativo.
O sistema define a lógica de funcionamento.
A Engine define persistência, segurança, estrutura e comportamento técnico.

Exemplo:

Dante deve ter seu próprio 00_NARRATIVE_PROFILE.md com tom frio, sombrio, calculado e persistente.

Uma campanha de Vampiro pode ter outro perfil, como noir urbano, político, predatório e claustrofóbico.

Uma campanha de D&D pode ter outro perfil, como fantasia épica, exploração e aventura.

Nenhum tom específico de campanha deve ser tratado como regra global da Engine.


## 14. Estado Atual das Actions Administrativas (Atualizado)

Actions existentes e funcionais:

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

Actions já testadas com sucesso:

- createFile
- readFile
- readAnyFile
- updateFile
- getRepositoryTree
- createDirectory
- moveFile
- renameFile
- saveCheckpoint
- healthCheck

Próximas Actions:

- searchRepository (planejada)
- deleteFile (adiada por segurança)

A seção anterior de "Próximas Actions Administrativas" deve ser considerada superada pelo estado operacional atual acima.
