# Cobertura de Transições - Cenoura

Objetivo: exercitar um conjunto de testes que percorra **todas as
transições** do modelo pelo menos uma vez.

## Transições do modelo

| ID  | Origem            | Destino           | Evento / Condição              |
|-----|-------------------|-------------------|--------------------------------|
| T1  | [*]               | SementeDisponivel | (início)                       |
| T2  | SementeDisponivel | Plantada          | PLANT                          |
| T3  | Plantada          | Plantada          | WATER                          |
| T4  | Plantada          | Colhivel          | idade >= 2 dias                |
| T5  | Plantada          | Erva              | 2 dias sem regar               |
| T6  | Colhivel          | Colhivel          | WATER / FERTILIZE              |
| T7  | Colhivel          | Colhida           | HARVEST                        |
| T8  | Colhivel          | Erva              | decaimento ou 2 dias sem regar |
| T9  | Colhida           | NoGalpao          | DROP                           |
| T10 | NoGalpao          | Vendida           | SELL                           |
| T11 | Erva              | Removida          | DIG                            |
| T12 | Vendida           | [*]               | (fim)                          |
| T13 | Removida          | [*]               | (fim)                          |

## Casos de teste

### CT-T1 - Ciclo de venda completo-
Eventos: PLANT → WATER → (idade >= 2) → FERTILIZE/WATER → HARVEST → DROP → SELL
Transições exercitadas: T1, T2, T3, T4, T6, T7, T9, T10, T12

### CT-T2 - Perda na fase Plantada
Eventos: PLANT → (2 dias sem regar) → DIG
Transições exercitadas: T2, T5, T11, T13

### CT-T3 - Perda na fase Colhivel
Eventos: PLANT → WATER → (idade >= 2) → (decaimento ou 2 dias sem regar) → DIG
Transições exercitadas: T4, T8, T11

## Verificação da cobertura

| Transição | Coberta por        |
|-----------|--------------------|
| T1        | CT-T1              |
| T2        | CT-T1, CT-T2       |
| T3        | CT-T1              |
| T4        | CT-T1, CT-T3       |
| T5        | CT-T2              |
| T6        | CT-T1              |
| T7        | CT-T1              |
| T8        | CT-T3              |
| T9        | CT-T1              |
| T10       | CT-T1              |
| T11       | CT-T2, CT-T3       |
| T12       | CT-T1              |
| T13       | CT-T2              |

Os três casos de teste juntos exercitam todas as 13 transições ->
cobertura de transições completa.
