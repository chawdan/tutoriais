# Menu gui
> Essa é uma técnica que eu uso de organização por padrão, mas você pode aproveitar dos meus métodos.

Eu divido em x partes:
- [Menu gui](#menu-gui)
  - [Planejamento](#planejamento)
  - [Preparação](#preparação)
  - [Mecânica](#mecânica)

## Planejamento
  1. **Funções**
     - Quais funções terão no menu-gui?
  2. **Páginas**
     - Pense na navegação
     - Quantas páginas?
  3. **Display**
     - Procure itens que represente cada função
     - ex: *sol = girasol*
  4. **Plataforma**
     - Onde vai ficar displonível?
       - [ ] Báu
       - [x] Barril *(recomendo usar esse para inicir)*
       - [ ] Minecart Chest
       - [ ] Dispenser
       - [ ] Funil
  5. **Chamar o Gui**
     - Como invocar o gui?
       - [ ] Dropando item
       - [ ] Clicando com um item
       - [ ] Trigger
       - [x] Com ovo *(recomendo usar esse para iniciar)*

## Preparação
  1. **Criar datapack**
     - Pensar em uma **"sigla"** *(Nome longo dificulta)*
  2. **Criar scoreboards**
     - Para cada categoria de página

## Mecânica
  1. **Invocar/remover**
     1. Invocar
        - Gerar o barril
        - Colocar os itens
        - Variáveis e Inteiros
          - Scoreboard (das páginas)
          - Tags
     2. Remover
        - Deletar bloco 
        - Matar entidade 
  2. **Cliques**
     - Detectar cliques
       - Executar comandos
         - Executar funções planejadas
         - Recolocar item clicado
         - *Se não spama*
  3. **Mudar de página**
     - Definir scoreboar da página
     - Recolocar itens
     - *Se não buga com outra página*
  4. **Dropar itens errados**
     - Se colocar um item que não é do menu gui, ele dropa

```
summon minecraft:item ~ ~ ~ {Item:{id:"minecraft:zombie",Count:1b,tag:{EntityTag:{id:"minecraft:armor_stand",Marker:0b,Invisible:1b,PersistenceRequired:1b,Tags:["menu","menu_gerar"]}}}}
```
```
execute as @e[tag=menu_gerar] at @s run function mg:menu/gerar
```
```
setblock ~ ~ ~ minecraft:barrel
function mg:menu/set
```
```
replaceitem block ~ ~ ~ container.0 minecraft:ghast_tear
replaceitem block ~ ~ ~ container.1 minecraft:oak_sapling
replaceitem block ~ ~ ~ container.2 minecraft:ghast_tear
```
```
execute unless data block ~ ~ ~ Items[{Slot:0b,id:"minecraft:ghast_tear"] run say hello world!
execute unless data block ~ ~ ~ Items[{Slot:0b,id:"minecraft:ghast_tear"] run replaceitem block ~ ~ ~ container.0 minecraft:ghast_tear
```