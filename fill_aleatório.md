# Fill aleatório
Usar o comando ``/fill`` no minecraft com blocos aleatórios

---

  1. Crie um **predicate** no seu datapack: `nome_do_datapack/data/seu_datapack/predicates/seu_predicate.json`;
  ```json
  {
  "condition": "minecraft:random_chance",
  "chance": 0.5
  }
  ```
  2. Crie uma **function** no seu datapack:
  `nome_do_datapack/data/seu_datapack/functions/sua_function.mcfunction`;
  ```js
  execute if predicate seu_datapack:nome_do_predicate run setblock ~ ~ ~ bricks
  execute if predicate seu_datapack:nome_do_predicate run setblock ~ ~ ~ cobblestone
  execute if block ~ ~ ~ command_block run function seu_datapack:sua_function
  ```
  3. Digite o comando no jogo:
  ```js
  /fill 10 20 10 -10 20 -10 command_block{auto:1b,Command:"function seu_datapack:sua_function"}
  ```

> você pode mudar a porcentagem no predicate "chance", 50% = 0.5, 10% = 0.1 assim em diante