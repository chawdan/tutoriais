# Novo execute da 1.14+
Esse comandos valem para a versão a partir da 1.13 do minecraft, exceto [data](#if###data).

## Tabela de comandos
* [Execute](#execute)
* [Align](#align)
* [Anchored](#anchored)
* [As](#as)
* [At](#at)
* [Facing](#facing)
* [If](#if/unless)
* [In](#in)
* [Positioned](#positioned)
* [Rotated](#rotated)
* [Run](#run)
* [Store](#store)
* [Unless](#if/unless)

---

## Execute
O comando `execute` faz executar outros comandos em seguida, podendo ter várias condições e instruções;
```
execute as @a at @s if block ~ ~-1 ~ minecraft:dirt run particle minecraft:happy_villager
```
### O que mudou:
A diferença é que há a possibilidade de adicionar várias condições e instruções em sequência.
#### 1.12
`execute @a ~ ~ ~ ...`
#### 1.13
`execute as @a at @s run ...`

## Align
Instrução para alinha o comando em relação a coordenada `x`,`y`e`z`.
O `align` pode ser usado como: `(x|xy|zx|xzy|...)` (Não precisa ser na ordem "xyz").
```
execute as @a at @s align xz positioned ~0.5 ~ ~0.5 run summon minecraft:armor_stand
```

## Anchored
Instrução para ancorar com os olhos ou pés (por padrão já é alinhado ao pé das entidade) a entidade. **Sempre use comando com "^ ^ ^" (relação à visão).**
```
execute as @a at @s anchored eyes run particle minecraft:happy_villager ^ ^ ^3 0 0 0 0 1
```

## As
Instrução para ser executado "como" a entidade, isso não significa que vai ser executado no lugar da entidade.
```
execute as @a run say olá
```

## At
Instrução para indicar onde vai ser executado, isso não significa que vai ser executado "como" a entidade.
```
execute at @a run setblock ~ ~ ~ minecraft:stone
```

## Facing
Instrução para ser executar como a visão rotacionada para `entity`(entidade) ou `~ ~ ~`(bloco),
#### `entity`
olhando para entidade (olho ou pés);
... `(eyes/feet)`
```
execute facing entity @p feet run particle minecraft:happy_villager ^ ^ ^2 0 0 0 0 1
```
```
execute as @e[type=minecraft:armor_stand] at @s facing entity @p feet run tp @s ~ ~ ~
```
- Suporte de armadura olhando para a entidade próxima.
#### `~ ~ ~`
olhando para o bloco;
```
execute facing 10 60 -10 run particle minecraft:happy_villager ^ ^ ^1 0 0 0 0 1
```

## If/unless
Condições "se" e "se não": `(block|blocks|data|entity|score)`.
#### `block`
detecta se bloco está na posição;
... `<posição>` `<bloco>`
```
execute as @a at @s if block ~ ~-1 ~ minecraft:stone run gamemode survival @s
```
#### `blocks`
compara blocos;
...`<início>` `<fim>` `<destinado>` `(all|masked)`
```
execute if blocks 0 20 4 0 21 4 0 20 6 masked run effect give @a minecraft:speed
```
#### `data`
compara `nbt` da entdade ou bloco;
...`block` `<posição>` `<trajetoNBT>`
...`entiy` `<alvo>` `<trajeto>`
```
execute as @a if data entity @s SelectedItem.tag.Enchantments run playsound minecraft:block.enchantment_table.use master @a
```
#### `entiy`
detecta se há a entidade;
... `<alvo>`
```
execute if entity @e[type=minecraft:creeper] run kill @e[type=minecraft:creeper]
```
#### `score`
compara scoreboard da entidade;
... `<alvo>` `<scoreboardAlvo>` `(<|<=|=|>=|>)` `<ponto>` `<scoreboardReferência>`
... `<alvo>` `<scoreboardAlvo>` `matches` `<ponto>`
```
execute if score %fantasma tempo matches 60.. run scoreboard players set %fantasma tempo 0
```

## In
Instrução do mundo que vais ser executado.
```
execute in minecraft:the_end run tp @a 0 60 0
```

## Positioned
Instrução para indicar onde vai ser posicionado: `(as|<posição>)`.
#### `as`
na entidade;
```
execute positioned as @s run summon minecraft:rabbit
```
#### `~ ~ ~`
na posição;
```
execute as @a at @s positioned ~ 10 ~ run tp @s ~ ~ ~
```

## Rotated
Instrução a rotação da visão em relação a outra entidad. **Sempre use comando com "^ ^ ^" (relação à visão).**
```
execute rotated as @p run particle minecraft:cloud ^ ^ ^2 0 0 0 0 1
```

## Run
Instrução para executar o comando. Usado como última instrução. Só há posibilidade de adicionar um `run`.
```
execute run weather clear
```

## Store
Instrução para registrar resultado em `(block|bossbar|entiy|score)`.
... `(result|success)` `(block|bossbar|entiy|score)`
- `result`: registra o resultado;
- `success`: registra se funcionou ou não.
#### `block`
registra no nbt do bloco;
... `<posição>` `<trajetoNBT>` `(byte|short|int|long|float|double)` `<multiplicador>`
```
execute store success block ~ ~ ~ Items[{Slot:0b}].Count byte 1 run scoreboard players get %fantasma tempo
```
#### `bossbar`
registra na barra de chefão;
... `<barra>` `(max|value)`
```
execute store result bossbar minecraft:tempo value run scoreboard players get %fantasma tempo
```
#### `entity`
registra no nbt da entidade;
... `<alvo>` `<trajetoNBT>` `(byte|short|int|long|float|double)` `<multiplicador>`
```
execute as @e[type=minecraft:armor_stand] at @s store success entity @s NoGravity byte 1 if entity @p[distance=..3]
```
#### `score`
registra no scoreboard;
... `<alvo>` `<scoreboardAlvo>`
```
execute as @a store result score @s dinheiro run clear @s minecraft:diamond 0
```
