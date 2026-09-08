# bookish-palm-tree
V&amp;V, 2026/2, Exercício E3.


## Egg

### Máquina de estados


![Egg State Machine](http://www.plantuml.com/plantuml/proxy?cache=no&fmt=svg&src=https://raw.githubusercontent.com/masmangan/bookish-palm-tree/refs/heads/main/Egg/egg.iuml)

### Casos de teste

| Caso | Caminho | Resultado |
|------|---------|-----------|
| CT1  | BUILD_COOP | COOP |


### Árvore de caminhos

```plantuml
@startuml
top to bottom direction

rectangle "Empty_0" as E0
rectangle "Coop_0" as C0

E0 --> C0 : BUILD_COOP

@enduml

## Tomato

## Carrot

## Wheat

## Milk
