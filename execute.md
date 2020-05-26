# Novo execute da 1.13
> última atualização desse documento: <26 de maio - 2020>

- Novos recursos:
  - 1.14: [data](#data)
  - 1.15: [`storage`](#storage) [`predicate`](#predicate)

- [Novo execute da 1.13](#novo-execute-da-113)
- [Execute](#execute)
  - [Align](#align)
  - [Anchored](#anchored)
  - [As](#as)
  - [At](#at)
  - [Facing](#facing)
      - [`entity`](#entity)
      - [`~ ~ ~`](#)
  - [If/unless](#ifunless)
      - [`block`](#block)
      - [`blocks`](#blocks)
      - [`data`](#data)
      - [`entity`](#entity-1)
      - [`score`](#score)
      - [`predicate`](#predicate)
  - [In](#in)
  - [Positioned](#positioned)
      - [`as`](#as-1)
      - [`~ ~ ~`](#-1)
  - [Rotated](#rotated)
  - [Run](#run)
  - [Store](#store)
      - [`block`](#block-1)
      - [`bossbar`](#bossbar)
      - [`entity`](#entity-2)
      - [`score`](#score-1)
      - [`storage`](#storage)

---

# Execute
O comando `/execute` faz executar outros comandos em seguida, podendo adicionar várias condições e/ou instruções;

```
/execute as @a at @s if block ~ ~-1 ~ minecraft:dirt run particle minecraft:happy_villager
```

**O que mudou:**
- A diferença é que há a possibilidade de adicionar várias condições e instruções em sequência.
  - 1.12: `execute @a ~ ~ ~ ...`
  - 1.13: `execute as ... at ... if ... in ... run ...`

## Align
  - Instrução para alinha o comando em relação a coordenada `x`,`y`e`z`.
O `align` pode ser usado como: `(x|xy|zx|...|xzy|)` 
> Não precisa ser na ordem "xyz".
```
/execute as @a at @s align xz positioned ~0.5 ~ ~0.5 run summon minecraft:armor_stand
```

## Anchored
  - Instrução para ancorar aos olhos ou pés da entidade que executa.
  > Sempre use comandos com o "^ ^ ^" (relação à visão).

  > Por padrão já é alinhado ao pé das entidade.

```
/execute as @a at @s anchored eyes run particle minecraft:happy_villager ^ ^ ^3 0 0 0 0 1
```

## As
  - Instrução para indicar "quem" vai executar o comando.
  - Isso não vai ser executado no local da entidade e sim como a entidade

```
/execute as @a run say olá
```

## At
  - Instrução para indicar "onde" vai ser executado
  > Um grande número de pessoas tem dificuldade em diferencias o "as" do "at" no início. Lembre-se que o "at" é para localização. 

```
/execute at @a run setblock ~ ~ ~ minecraft:stone
```

## Facing
  - Instrução para executar com a visão rotacionada para `entity`(entidade) ou `~ ~ ~`(localização do bloco),

#### `entity`
  - olhando para entidade (olho ou pés);
    - ... `(eyes/feet)`

```
/execute facing entity @p feet run particle minecraft:happy_villager ^ ^ ^2 0 0 0 0 1
```

> Suporte de armadura olhando para a entidade próxima:

```
/execute as @e[type=minecraft:armor_stand] at @s facing entity @p feet run tp @s ~ ~ ~
```

#### `~ ~ ~`
  - olhando para o bloco;

```
/execute facing 10 60 -10 run particle minecraft:happy_villager ^ ^ ^1 0 0 0 0 1
```

## If/unless
  - Condições "se" e "se não":
    - `(block|blocks|data|entity|score)`.

#### `block`
  - detecta se bloco está na posição;
    - ... `<posição>` `<bloco>`

```
/execute as @a at @s if block ~ ~-1 ~ minecraft:stone run gamemode survival @s
```

#### `blocks`
  - compara blocos;
    - ...`<início>` `<fim>` `<destinado>` `(all|masked)`

```
/execute if blocks 0 20 4 0 21 4 0 20 6 masked run effect give @a minecraft:speed
```

#### `data`
  - indintifica "nbt" (dados) da entidade, bloco ou dados armazenados;
    - ...`bloco` `<posição>` `<trajetoNBT>`
    - ...`entidade` `<alvo>` `<trajeto>`
    - ...`storage` `<nomeStorage>` `<trajetoNBT>`

```
/execute as @a if data entity @s SelectedItem.tag.Enchantments run playsound minecraft:block.enchantment_table.use master @a
```

#### `entity`
  - detecta se há a entidade;
    - ... `<alvo>`

```
/execute if entity @e[type=minecraft:creeper] run kill @e[type=minecraft:creeper]
```

#### `score`
  - compara scoreboard da entidade com outra entidade ou número;
    - ... `<alvo>` `<scoreboardAlvo>` `(<|<=|=|>=|>)` `<ponto>` `<scoreboardReferência>`
    - ... `<alvo>` `<scoreboardAlvo>` `matches` `<ponto>`

```
/execute if score %fantasma tempo matches 60.. run scoreboard players set %fantasma tempo 0
```

#### `predicate`
  - compara um predicato em um arquivo .json no datapack

```
/execute if predicate predicate custom:shift run summon fireball
```

## In
  - Instrução do mundo que vais ser executado.

```
/execute in minecraft:the_end run tp @a 0 60 0
```

## Positioned
  - Instrução para indicar onde vai ser posicionado:
    - `(as|<posição>)`. 


#### `as`
  - na entidade;

```
/execute positioned as @s run summon minecraft:rabbit
```

#### `~ ~ ~`
  - na posição;

```
/execute as @a at @s positioned ~ 10 ~ run tp @s ~ ~ ~
```

## Rotated
  - Instrução a rotação da visão em relação a outra entidad.

> Sempre use comando com "^ ^ ^" (relação à visão).

```
/execute rotated as @p run particle minecraft:cloud ^ ^ ^2 0 0 0 0 1
```

## Run
  - Instrução para executar o comando. Usado como última instrução. Só há posibilidade de adicionar um `run`.

```
/execute run weather clear
```

## Store
  - Instrução para registrar resultado em `(block|bossbar|entity|score)`.
    - ... `(result|success)` `(block|bossbar|entity|score)`
      - `result`: registra o resultado;
      - `success`: registra se funcionou ou não.

#### `block`
  - registra no nbt do bloco;
    - ... `<posição>` `<trajetoNBT>` `(byte|short|int|long|float|double)` `<multiplicador>`

```
/execute store success block ~ ~ ~ Items[{Slot:0b}].Count byte 1 run scoreboard players get %fantasma tempo
```

#### `bossbar`
  - registra na barra de chefão;
    - ... `<barra>` `(max|value)`

```
/execute store result bossbar minecraft:tempo value run scoreboard players get %fantasma tempo
```

#### `entity`
  - registra no nbt da entidade;
    - ... `<alvo>` `<trajetoNBT>` `(byte|short|int|long|float|double)` `<multiplicador>`

```
/execute as @e[type=minecraft:armor_stand] at @s store success entity @s NoGravity byte 1 if entity @p[distance=..3]
```

#### `score`
  - registra no scoreboard;
    - ... `<alvo>` `<scoreboardAlvo>`

```
/execute as @a store result score @s dinheiro run clear @s minecraft:diamond 0
```

#### `storage`
  - registra dados em armagenamento;
    - ...`<nomeStorage>` `<trajetoNBT>`

```
/execute as @a store storage custom:jogadores.online if entity @a
```