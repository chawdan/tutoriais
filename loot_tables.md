# loot_tables

- [loot_tables](#loot_tables)
  - [functions](#functions)
    - [apply_bonus](#apply_bonus)
    - [copy_name](#copy_name)
    - [copy_nbt](#copy_nbt)
    - [copy_state](#copy_state)
    - [enchant_randomly](#enchant_randomly)
    - [enchant_with_levels](#enchant_with_levels)
    - [exploration_map](#exploration_map)
    - [explosion_decay](#explosion_decay)
    - [furnace_smelt](#furnace_smelt)
    - [fill_player_head](#fill_player_head)
    - [limit_count](#limit_count)
    - [looting_enchant](#looting_enchant)
    - [set_attributes](#set_attributes)
    - [set_contents](#set_contents)
    - [set_count](#set_count)
    - [set_damage](#set_damage)
    - [set_lore](#set_lore)
    - [set_name](#set_name)
    - [set_nbt](#set_nbt)
    - [set_stew_effect](#set_stew_effect)
  - [conditions](#conditions)
    - [alternative](#alternative)
    - [block_state_property](#block_state_property)
    - [damage_source_properties](#damage_source_properties)
    - [entity_properties](#entity_properties)
    - [entity_scores](#entity_scores)
    - [inverted](#inverted)
    - [killed_by_player](#killed_by_player)
    - [location_check](#location_check)
    - [match_tool](#match_tool)
    - [random_chance](#random_chance)
    - [random_chance_with_looting](#random_chance_with_looting)
    - [reference](#reference)
    - [survives_explosion](#survives_explosion)
    - [table_bonus](#table_bonus)
    - [time_check](#time_check)
    - [tool_enchantment](#tool_enchantment)
    - [weather_check](#weather_check)

## functions

### apply_bonus
Aplica uma fórmula de bônus predefinida.
- **enchantment**: ID do encantamento
- **formula**:
  - > **binomial_with_bonus_count** para uma distribuição binomial (*level+extra,probability*)
  - > **uniform_bonus_count** para distribuição uniforme (de '0' para *'level\*bonusMultiplier'*) 
  - > **ore_drops** para uma função especial usada para drops de minério no jogo (*Count\*(max(0;random(0..Level+2)-1)+1)*)
- **parameters**: valores necessários para a fórmula.
  - **extra**: para a fórmula 'binomial_with_bonus_count', o valor 'extra'.
  - **probability**: para a fórmula 'binomial_with_bonus_count', a 'probability'.
  - **bonusMultiplier**: Para a fórmula 'uniform_bonus_count', o 'bonusMultiplier'.
### copy_name
- **source**
### copy_nbt
### copy_state 
### enchant_randomly
### enchant_with_levels
### exploration_map
### explosion_decay
### furnace_smelt
### fill_player_head
### limit_count
### looting_enchant
### set_attributes
### set_contents
### set_count
### set_damage
### set_lore
### set_name
### set_nbt
### set_stew_effect

## conditions
### alternative
### block_state_property 
### damage_source_properties 
### entity_properties 
### entity_scores
### inverted 
### killed_by_player 
### location_check 
### match_tool 
### random_chance 
### random_chance_with_looting 
### reference 
### survives_explosion 
### table_bonus 
### time_check
### tool_enchantment 
### weather_check