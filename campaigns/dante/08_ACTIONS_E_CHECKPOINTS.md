# 08 — Actions, Checkpoints e Base Externa

## Objetivo

Este arquivo define como o Guardião de Sessão deve interagir com uma base externa editável usando Actions/API.

A ideia é:

```text
Jogador envia ações
↓
Guardião narra
↓
A cada 3 envios, Guardião gera checkpoint
↓
Action salva checkpoint fora do ChatGPT
↓
Fim da sessão consolida arquivos .md
```

## Limite importante

O Guardião não deve presumir que consegue editar automaticamente:

- arquivos enviados no Conhecimento do Custom GPT;
- fontes upadas diretamente no Projeto;
- instruções internas do GPT;
- arquivos sem API externa ou permissão de escrita.

Para atualização automática real, use uma base externa editável com Action/API.

## Endpoints recomendados

### `GET /campaign/state`

Retorna o estado atual da campanha.

Uso:

- antes de narrar;
- ao iniciar sessão;
- quando houver dúvida de continuidade.

### `GET /files/{filename}`

Busca o conteúdo de um arquivo específico.

Arquivos esperados:

- `01_CAMPAIGN_STATE.md`
- `02_PERSONAGEM_E_PODERES.md`
- `03_LEDGER_NUMERICO.md`
- `04_SESSION_LOGS_DETALHADOS.md`
- `05_INDICE_DE_CANON.md`
- `06_SEGREDOS_DO_MESTRE.md`
- `07_BESTIARIO_E_DUNGEONS.md`

### `POST /checkpoint`

Salva um checkpoint curto.

Payload recomendado:

```json
{
  "session_id": "S02",
  "checkpoint_id": "S02-C01",
  "player_message_count": 3,
  "events": [],
  "canon_confirmed": [],
  "numeric_changes": {},
  "powers_used": [],
  "npcs_affected": [],
  "locations_affected": [],
  "open_threads": [],
  "files_to_update": []
}
```

### `POST /session/consolidate`

Consolida checkpoints em atualização final de sessão.

Payload recomendado:

```json
{
  "session_id": "S02",
  "mode": "full_update",
  "include_files": [
    "01_CAMPAIGN_STATE.md",
    "02_PERSONAGEM_E_PODERES.md",
    "03_LEDGER_NUMERICO.md",
    "04_SESSION_LOGS_DETALHADOS.md",
    "05_INDICE_DE_CANON.md",
    "06_SEGREDOS_DO_MESTRE.md",
    "07_BESTIARIO_E_DUNGEONS.md"
  ]
}
```

### `PATCH /files/{filename}`

Atualiza um arquivo específico.

Payload recomendado:

```json
{
  "operation": "replace_section",
  "section": "## Estado atual",
  "content": "novo conteúdo em markdown",
  "source_checkpoint": "S02-C01"
}
```

## Regra de uso das Actions

O Guardião deve chamar a Action quando:

- completar 3 envios do jogador;
- ocorrer evento crítico;
- o jogador pedir `salvar checkpoint`;
- o jogador pedir `consolidar sessão`;
- iniciar sessão e precisar buscar estado externo.

## Formato padrão de checkpoint narrativo

```markdown
[CHECKPOINT SXX-CXX]

- Eventos:
  - ...

- Canon confirmado:
  - ...

- Alterações numéricas:
  - XP Geral:
  - XP Sepulcro:
  - Almas:
  - Itens:
  - Vida/Mana:
  - Relações:

- Poderes/técnicas usados:
  - ...

- NPCs, inimigos e locais afetados:
  - ...

- Pendências novas/alteradas:
  - ...

- Arquivos a atualizar:
  - ...
```

## Formato de Update do Projeto

```markdown
# UPDATE DO PROJETO — Sessão XX

## 1. Campaign State atualizado

## 2. Personagem e Poderes atualizado

## 3. Ledger Numérico atualizado

## 4. Session Logs Detalhados atualizado

## 5. Índice de Canon atualizado

## 6. Segredos do Mestre atualizado

## 7. Bestiário e Dungeons atualizado

## 8. Pendências abertas/resolvidas/incertas
```

## Comportamento quando não houver Action disponível

Se a Action não estiver configurada, o Guardião deve:

1. gerar o checkpoint no chat;
2. marcar que não conseguiu salvar automaticamente;
3. continuar a sessão;
4. consolidar tudo no final em `.md` pronto para upload.
