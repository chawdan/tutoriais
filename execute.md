# Novo execute da 1.14+
Esse comandos valem para a versão 1.13 do minecraft, exceto alguns itens.

*ùltima atualização: 26 de agosto - 2019*

## Tabela de comandos
* [execute](#execute)
* [align]
* [anchored]
* [as]
* [at]
* [facing]
* [if]
* [in]
* [positioned]
* [rotated]
* [run]
* [storne]
* [unless]

---

## Execute
O comando `execute` faz executar outros comandos em seguida, sendo que pode haver várias condições:

**Comando:**
```
execute as @a at @s if block ~ ~-1 ~ minecraft:dirt run particle minecraft:happy_villager
```

**na 1.12:** `execute @a ~ ~ ~` `...`

**na 1.13+:** `execute` `as @a` `at @s` `if block` `run` `...`

*A diferença do execute das versões inferiores à 1.13 é que há a possibilidade de adicionar várias condições seguidas*
