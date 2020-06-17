# Cronômetro de Bossbar
> Esse tutorial é um exemplo breve de como você pode criar barra .

   1. Crie uma scoreboard e um bossbar
   - Configure a bossbar como achar melhor
   - Escolha o valor `max` da bossbar
   ```js
   scoreboard objectives add tempo dummy
   bossbar add barra "barra"
   bossbar set barra players @a
   bossbar set barra max 100
   ```
   1. Coloque esses comandos numa `function` em loop:
      - `scoreboard` com player "fantasma";
      - `execute store` para registrar o **scoreboard** na **bossbar**;
      - `execute if` para resetar o **scoreboard** quando chegar no máximo
   ```js
   scoreboard players add %barra tempo 1
   execute store result bossbar tempo value run scoreboard players get %barra tempo
   execute if score %barra tempo matches 100.. run scoreboard players set %barra tempo 0
   ```