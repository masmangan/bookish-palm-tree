# Árvore de Caminhos - Cenoura

A Árvore em questão foi projetada percorrendo as transições que ocorrem na Máquina de Estados da Cenoura a partir do estado inicial, percorrendo as transições de acordo com as tabelas de Cobertura de Estados e Transições até os estados finais.

```mermaid
graph TD
    Root(("Início")) -- "T1 (início)" --> S1["SementeDisponivel"]
    
    S1 -- "T2 (PLANT)" --> S2["Plantada"]
    
    %% Transições: Plantada
    S2 -- "T3 (WATER)" --> S2
    S2 -- "T4 (idade >= 2 dias)" --> S3["Colhivel"]
    S2 -- "T5 (2 dias sem regar)" --> E1["Erva"]
    
    %% Transições: Colhivel
    S3 -- "T6 (WATER/FERTILIZE)" --> S3
    S3 -- "T7 (HARVEST)" --> S4["Colhida"]
    S3 -- "T8 (decaimento / 2 dias sem regar)" --> E2["Erva"]
    
    %% Transições: Venda
    S4 -- "T9 (DROP)" --> S5["NoGalpao"]
    S5 -- "T10 (SELL)" --> S6["Vendida"]
    S6 -- "T12 (fim)" --> End1(("
Fim"))
   
    %% Transições: Descarte
    E1 -- "T11 (DIG)" --> R1["Removida"]
    R1 -- "T13 (fim)" --> End2(("Fim"))
    
    E2 -- "T11 (DIG)" --> R2["Removida"]
    R2 -- "T13 (fim)" --> End3(("Fim"))
```
