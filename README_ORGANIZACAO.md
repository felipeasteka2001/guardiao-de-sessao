# Organização da Base Externa — Guardião de Sessão

## Arquivos gerados

1. `00_REGRAS_DO_AGENT.md` — instruções operacionais do Guardião.
2. `01_CAMPAIGN_STATE.md` — estado atual jogável da campanha.
3. `02_PERSONAGEM_E_PODERES.md` — personagem, dons, pactos, técnicas, classes e HUD.
4. `03_LEDGER_NUMERICO.md` — números, XP, almas, inventário, encontros e alterações.
5. `04_SESSION_LOGS_DETALHADOS.md` — histórico narrativo detalhado com IDs.
6. `05_INDICE_DE_CANON.md` — mapa de busca rápida.
7. `06_SEGREDOS_DO_MESTRE.md` — metaplot e verdades ocultas.
8. `07_BESTIARIO_E_DUNGEONS.md` — NPCs, locais, facções, inimigos e dungeons.
9. `08_ACTIONS_E_CHECKPOINTS.md` — guia de automação com Actions/API.

## Como usar

### Sem automação

- Faça upload dos `.md` como fontes de Projeto ou base externa.
- Jogue com o Guardião.
- A cada 3 envios, ele gera checkpoint.
- Ao fim da sessão, peça `Encerrar sessão e consolidar`.
- Substitua os `.md` antigos pelos novos/patches gerados.

### Com automação por Actions

- Configure uma API externa.
- Adicione endpoints de leitura e escrita.
- Configure a Action no Custom GPT Guardião.
- O Guardião chama `POST /checkpoint` a cada 3 envios.
- O Guardião chama `POST /session/consolidate` ao fim da sessão.

## Observação de canon

Os arquivos enviados tinham a maioria dos `.txt` vazios com “aguardando adição”. O conteúdo real veio de:

- `Instrucoes (1).txt`;
- `patch1 (1).txt`;
- `patch2.txt`;
- `patch3.txt`;
- estado atual colado anteriormente pelo usuário na configuração do Guardião.

Há um avanço de continuidade: os patches enviados terminam no Salão de Invocação/Matriz, mas a configuração atual do Guardião já colocava Dante na Cripta Verdejante após a primeira absorção. Este pacote adotou a Cripta Verdejante como estado mais recente.
