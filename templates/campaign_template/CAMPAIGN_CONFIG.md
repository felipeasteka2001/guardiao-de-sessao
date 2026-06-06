# CAMPAIGN_CONFIG.md

## Identificação

campaign_id: {{campaign_id}}
campaign_name: {{campaign_name}}
system_id: {{system_id}}
status: {{status}}

---

## Arquivos principais

Perfil narrativo:
- 00_NARRATIVE_PROFILE.md

Estado da campanha:
- 01_CAMPAIGN_STATE.md

Personagens e poderes:
- 02_PERSONAGEM_E_PODERES.md

Ledger numérico:
- 03_LEDGER_NUMERICO.md

Logs detalhados:
- 04_SESSION_LOGS_DETALHADOS.md

Índice de canon:
- 05_INDICE_DE_CANON.md

Segredos do mestre:
- 06_SEGREDOS_DO_MESTRE.md

Bestiário e dungeons:
- 07_BESTIARIO_E_DUNGEONS.md

Actions e checkpoints:
- 08_ACTIONS_E_CHECKPOINTS.md

---

## Checkpoints

Diretório de checkpoints:
- checkpoints/{{campaign_id}}/

---

## Configuração técnica

Ordem de carregamento sugerida:
1. CAMPAIGN_CONFIG.md
2. 00_NARRATIVE_PROFILE.md
3. systems/{{system_id}}/SYSTEM_RULES.md
4. arquivos canônicos da campanha
5. checkpoints relevantes

---

## Observações

Este arquivo define a configuração técnica da campanha. Tom, tema e estilo narrativo devem ficar em 00_NARRATIVE_PROFILE.md. Regras sistêmicas devem ficar em systems/{{system_id}}/SYSTEM_RULES.md.
