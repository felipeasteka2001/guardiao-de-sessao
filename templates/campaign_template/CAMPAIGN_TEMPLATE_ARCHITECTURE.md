# CAMPAIGN_TEMPLATE_ARCHITECTURE.md

## Filosofia Oficial

O campaign_template deve seguir a filosofia:

base obrigatória enxuta + módulos opcionais + extensões por sistema

O objetivo é impedir que toda campanha futura seja obrigada a copiar integralmente a estrutura da campanha Dante.

Cada campanha deve nascer com o mínimo necessário para funcionar na Engine, podendo ativar módulos adicionais conforme o sistema, o tom, o estilo e a complexidade da campanha.

---

## Arquivos Obrigatórios para Toda Campanha

Toda campanha deve possuir:

- CAMPAIGN_CONFIG.md
- 00_NARRATIVE_PROFILE.md
- 01_CAMPAIGN_STATE.md
- 03_LEDGER_NUMERICO.md
- 05_INDICE_DE_CANON.md

### Função dos obrigatórios

CAMPAIGN_CONFIG.md
- Define configuração técnica da campanha.
- Indica campaign_id, system_id, status e arquivos principais.

00_NARRATIVE_PROFILE.md
- Define tom, tema, atmosfera, ritmo e limites narrativos.

01_CAMPAIGN_STATE.md
- Define o estado atual da campanha.
- Deve permitir retomar a campanha sem depender apenas do chat.

03_LEDGER_NUMERICO.md
- Registra valores, recursos, contadores, progressão e mudanças rastreáveis.

05_INDICE_DE_CANON.md
- Mantém o índice de fatos confirmados, hipóteses, pendências e elementos canônicos.

---

## Arquivos Opcionais ou Recomendados

Estes arquivos podem ser usados conforme a necessidade da campanha:

- 02_PERSONAGEM_E_PODERES.md
- 04_SESSION_LOGS_DETALHADOS.md
- 06_SEGREDOS_DO_MESTRE.md
- 07_BESTIARIO_E_DUNGEONS.md
- 08_ACTIONS_E_CHECKPOINTS.md

### Função dos opcionais

02_PERSONAGEM_E_PODERES.md
- Útil quando a campanha possui personagens complexos, poderes, habilidades, fichas ou progressão individual detalhada.

04_SESSION_LOGS_DETALHADOS.md
- Útil quando a campanha precisa de histórico narrativo extenso por sessão.

06_SEGREDOS_DO_MESTRE.md
- Útil quando há informações ocultas, mistérios, antagonistas secretos ou revelações planejadas.

07_BESTIARIO_E_DUNGEONS.md
- Útil para campanhas com monstros, locais perigosos, dungeons, encontros, ameaças ou regiões exploráveis.

08_ACTIONS_E_CHECKPOINTS.md
- Útil para registrar interações técnicas, checkpoints relevantes, uso de Actions e histórico operacional da campanha.

---

## Extensões por Sistema

Cada sistema pode exigir arquivos adicionais além do template base.

Essas extensões devem ser definidas em:

systems/{system_id}/

ou em documentação específica da campanha quando forem particulares daquele cenário.

---

## Exemplos de Extensões por Sistema

### Vampiro

Campanhas inspiradas em horror político e social podem exigir módulos como:

- relações políticas
- clãs ou linhagens
- território
- refúgio
- dívidas
- favores
- influência social
- facções
- recursos sociais persistentes

### Cthulhu

Campanhas investigativas podem exigir módulos como:

- pistas
- sanidade
- entidades
- investigação
- linha do tempo
- documentos descobertos
- conexões entre evidências

### D&D

Campanhas de fantasia de aventura podem exigir módulos como:

- grupo de aventureiros
- quests
- inventário
- regiões
- NPCs
- encontros
- facções
- mapas ou locais exploráveis

---

## Regra de Não Acoplamento

O campaign_template não deve copiar obrigatoriamente a estrutura completa da campanha Dante.

A campanha Dante é uma implementação inicial e um playtest da Engine, não o modelo rígido para todas as campanhas futuras.

Quando uma nova campanha for criada, o Guardião Dev deve escolher:

1. arquivos obrigatórios
2. módulos opcionais necessários
3. extensões específicas do sistema
4. arquivos particulares do cenário

---

## Critério de Conclusão da Estrutura de Campanha

Uma campanha mínima é considerada estruturalmente válida quando possui:

- configuração técnica
- perfil narrativo
- estado atual
- ledger numérico
- índice de canon
- diretório de checkpoints correspondente
- referência a um sistema existente

Arquivos adicionais devem ser adicionados apenas quando houver necessidade real.
