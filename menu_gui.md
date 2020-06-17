# Menu gui
> Esse tutorial é um exemplo breve de como você pode criar menu rapidamente.

## Summon
   1. Inicialmente crie um `function` para sempre pegar o ovo de gerar o menu:
   ```js
   summon minecraft:item ~ ~ ~ {Item:{id:"minecraft:zombie",Count:1b,tag:{EntityTag:{id:"minecraft:armor_stand",Marker:0b,Invisible:1b,PersistenceRequired:1b,Tags:["menu","menu_gerar"]}}}}
   ```
   1. Crie outra `function` para gerar o menu:
   ```js
   execute as @e[tag=menu_gerar] at @s run function mg:menu/gerar
   ```
   1. Para gerar> `function mg:menu/gerar`
   ```js
   setblock ~ ~ ~ minecraft:barrel
   function mg:menu/set
   ```
   1. Para setar os itens: `function mg:menu/set`
   ```js
   replaceitem block ~ ~ ~ container.0 minecraft:ghast_tear
   replaceitem block ~ ~ ~ container.1 minecraft:oak_sapling
   replaceitem block ~ ~ ~ container.2 minecraft:bucket
   ```
   1. Para testar os itens: `function mg:menu/click`
   ```js
   execute unless data block ~ ~ ~ Items[{Slot:0b,id:"minecraft:ghast_tear"] run say hello world!
   execute unless data block ~ ~ ~ Items[{Slot:1b,id:"minecraft:oak_sapling"] run replaceitem block ~ ~ ~ container.1 minecraft:oak_sapling
   execute unless data block ~ ~ ~ Items[{Slot:2b,id:"minecraft:bucket"] run function mg:menu/exemplo
   ```
   1. function com tick: `function mg:tick`
   ```js
   execute as @e[type=armor_stand,tag=menu] at @s run function mg:menu/click
   execute as @e[type=armor_stand,tag=gerar_menu] at @s run function mg:menu/gerar
   ```