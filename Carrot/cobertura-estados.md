# Cobertura de Estados - Cenoura

Objetivo: exercitar um conjunto de testes que visite **todos os 8 estados**
do modelo pelo menos uma vez.

Estados do modelo: SementeDisponivel, Plantada, Colhivel, Colhida,
NoGalpao, Vendida, Erva, Removida.

## Casos de teste

### CT-E1 - Ciclo de venda bem-sucedido
Sequência de eventos: PLANT → WATER → (idade >= 2 dias) → HARVEST → DROP → SELL

Estados visitados:
SementeDisponivel → Plantada → Colhivel → Colhida → NoGalpao → Vendida

### CT-E2 - Perda da planta por falta de rega
Sequência de eventos: PLANT → (2 dias sem regar) → DIG

Estados visitados:
SementeDisponivel → Plantada → Erva → Removida

## Verificação da cobertura

| Estado            | Coberto por |
|-------------------|-------------|
| SementeDisponivel | CT-E1, CT-E2 |
| Plantada          | CT-E1, CT-E2 |
| Colhivel          | CT-E1       |
| Colhida           | CT-E1       |
| NoGalpao          | CT-E1       |
| Vendida           | CT-E1       |
| Erva              | CT-E2       |
| Removida          | CT-E2       |

Os dois casos de teste juntos visitam todos os 8 estados -> cobertura de
estados completa.
