# 03 — Ledger Numérico

## Regra deste arquivo

Tudo que tem número, contagem, recurso, alteração objetiva, encontro, inventário, ganho, perda ou custo deve ser registrado aqui.

Se uma cena alterar algo numérico, o checkpoint deve adicionar uma linha neste arquivo.

## Recursos atuais de Dante

| Recurso | Valor atual | Última fonte conhecida | Observação |
|---|---:|---|---|
| Nível | 1 | Criação | Confirmado |
| Vida | 35/35 | Criação / Sessão 01 | Sem ferimento confirmado |
| Mana | 30/30 | Criação / Sessão 01 | Sem gasto confirmado |
| Corrupção | 0 | Criação | Confirmado |
| XP Geral | 1 | Estado mais recente declarado | +1 após primeira absorção |
| XP Sepulcro | 1 | Estado mais recente declarado | +1 após primeira absorção |
| Pontos Sepulcro | 0 | Criação | 10 XP Sepulcro → 1 ponto |
| Almas armazenadas | 1 | Estado mais recente declarado | Primeira absorção confirmada |
| Alma Fraca | 1 | Estado mais recente declarado | Origem: invocado sobrevivente |

## Atributos

| Atributo | Valor |
|---|---:|
| FOR | 1 |
| AGI | 5 |
| INT | 2 |
| CON | 3 |
| ESP | 4 |

## Derivados

| Derivado | Valor |
|---|---:|
| Vida máxima | 35 |
| Mana máxima | 30 |
| Defesa | 13 |
| Iniciativa | 7 |
| Res Física | 4 |
| Res Mental | 6 |
| Carga | 5 |
| Leitura | 6 |

## Perícias

| Perícia | Valor |
|---|---:|
| Mobilidade | 3 |
| Lâminas Leves | 3 |
| Furtividade | 1 |
| Ocultismo | 2 |
| Disparo | 1 |

## Inventário confirmado

| Item | Quantidade | Dado mecânico | Observação |
|---|---:|---|---|
| Adaga Comum | 2 | Dano base 4 | Lâmina leve |
| Capa Escura | 1 | Ocultação leve | Pacote Assassino |
| Roupas Leves | 1 | Sem penalidade | Pacote Assassino |
| Kit de Arrombamento Simples | 1 | — | Pacote Assassino |
| Veneno Fraco | 1 | pequeno enfraquecimento | efeito provisório |
| Bolsa Pequena | 1 | — | Pacote Assassino |

## Alterações registradas

| ID | Sessão | Evento | Campo | Antes | Depois | Motivo |
|---|---|---|---|---:|---:|---|
| CHG-001 | S01 | Pós-invocação | Classe pública | pendente | Assassino Iniciante | Finalização da criação |
| CHG-002 | S01 | Salão de Invocação | Ocultação social | 0 | +2 vantagem social | Simulação de medo/subestimação |
| CHG-003 | S01 | Núcleo dos Fracos | Percepção espiritual | inexistente | incompleta | Concentração de ESP nos olhos |
| CHG-004 | S01+ | Cripta Verdejante | XP Geral | 0 | 1 | Primeira absorção |
| CHG-005 | S01+ | Cripta Verdejante | XP Sepulcro | 0 | 1 | Primeira absorção |
| CHG-006 | S01+ | Cripta Verdejante | Alma Fraca | 0 | 1 | Invocado sobrevivente absorvido |
| CHG-007 | S01+ | Cripta Verdejante | Almas armazenadas | 0 | 1 | Primeira alma armazenada |

## Encontros registrados

| ID | Sessão | Local | Tipo | Participantes | Resultado |
|---|---|---|---|---|---|
| ENC-001 | S01 | Salão de Invocação | social / introdução | Dante, invocados, Sacerdote, Cavaleiros | Dante ocultou postura real |
| ENC-002 | S01 | Salão de Invocação | social | Dante, grupo assustado | núcleo emocional inicial formado |
| ENC-003 | S01 | Salão de Invocação | percepção | Dante, ambiente, altar | Percepção Espiritual Passiva incompleta |
| ENC-004 | S01+ | Cripta Verdejante / corredor lateral | execução / absorção | Dante, invocado sobrevivente | morte, Alma Fraca +1, XP Geral +1, XP Sepulcro +1 |

## Almas

| ID | Tipo | Origem | Sessão | Evento | Status | Efeitos conhecidos | Usada? |
|---|---|---|---|---|---|---|---|
| SOUL-001 | Alma Fraca | invocado sobrevivente | S01+ | ENC-004 | armazenada | XP Geral +1; XP Sepulcro +1; marca incompleta; ressonância inicial | não |

## Bônus e efeitos ativos

| Efeito | Valor | Fonte | Status |
|---|---:|---|---|
| Vantagem social pequena | +2 | Ocultação social / simulação de medo | ativo enquanto a encenação for plausível |
| Subestimação favorecida | — | Estado externo assustado/fraco | ativo/contextual |
| Ocultação social reforçada | — | Núcleo dos Fracos | ativo/contextual |
| Ressonância espiritual inicial | — | Primeira absorção | ativo/oculto |

## Fórmulas e conversões importantes

| Conversão | Resultado |
|---|---:|
| 10 XP Sepulcro | 1 Ponto Sepulcro |
| Buff recebido com Rei Sem Trono | valor dobrado |
| Marca de Ritmo normal | +1 dano, +1 precisão, +1 mobilidade |
| Marca de Ritmo com Rei Sem Trono | +2 dano, +2 precisão, +2 mobilidade |
| 3 Marcas de Ritmo normais | +3 total |
| 3 Marcas de Ritmo com Rei Sem Trono | +6 total |
