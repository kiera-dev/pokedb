Basic Queries:

Retrieve the names and types of all Pokémon in the database.
```
duckdb.sql("SELECT id,name,types FROM pokedex_df")
```
Find the Pokémon with the highest height stat.
```
duckdb.sql("SELECT * FROM pokedex_df ORDER BY height DESC LIMIT 1")
```

List the Pokémon that belong to the Water type.
```
duckdb.sql("SELECT * FROM pokedex_df WHERE 'water' = ANY(types)")
```

Filtering and Sorting:

Display the top 10 Pokémon with the highest HP (Hit Points) in descending order.
```
duckdb.sql("SELECT id, name, hp FROM pokedex_df ORDER BY hp DESC LIMIT 10")
```
Retrieve the names and types of Pokémon that have a base speed stat greater than 90.
```
duckdb.sql("SELECT id, name, speed FROM pokedex_df WHERE speed > 90 ORDER BY speed DESC")
```

List the Pokémon in alphabetical order by their names.
```
duckdb.sql("SELECT * FROM pokedex_df ORDER BY name ASC")
```

Count the number of Pokémon for each type.
```
duckdb.sql("SELECT flattened_type AS type, COUNT(*) AS pokemon_count FROM (SELECT UNNEST(types) AS flattened_type FROM pokedex_df) AS flattened_types GROUP BY flattened_type")
```

Write a query to find all Pokemon that have the move "Thunder" Include the Pokemon name and ID in the result.
```
duckdb.sql("SELECT * FROM pokedex_df WHERE 'thunder' = ANY(moves)")
```

Find the names of Pokemon that have more than one type. Display both the name and the types for these Pokemon.
```
duckdb.sql("SELECT * FROM pokedex_df WHERE ARRAY_LENGTH(types) >1")
```

List the top 10 pokemon by number of moves, and the moves they can learn
```
duckdb.sql("SELECT id, name, moves, ARRAY_LENGTH(moves) AS move_count FROM pokedex_df ORDER BY move_count DESC LIMIT 10")
```

List average of all the stats 
```
duckdb.sql("SELECT AVG(hp) as average_hp, AVG(speed) as average_speed, AVG(height) as average_height, AVG(attack) as average_attack, AVG(defense) as average_defense, AVG(special_attack) as average_special_attack FROM pokedex_df")
```

Write a query to find the top 5 Pokémon with the highest base Attack stat. Include their names and Attack stats in the result.
```
duckdb.sql("SELECT * FROM pokedex_df ORDER BY attack DESC LIMIT 5")
```

Create a query to retrieve the names and types of Pokémon, ordered first by type and then alphabetically within each type.
```
duckdb.sql("SELECT id,name,types FROM pokedex_df ORDER BY types ASC, name ASC")
```

Retrieve the Pokémon with the highest base HP for each type. Include the type, Pokémon name, and HP stat in the result.
```
duckdb.sql("SELECT DISTINCT ON (types) name,hp,types FROM pokedex_df ORDER BY hp DESC")
```

List the most learnable moves in descending order
```
duckdb.sql("SELECT flattened_move AS move, COUNT(*) AS pokemon_count FROM (SELECT UNNEST(moves) AS flattened_move FROM pokedex_df) AS flattened_moves GROUP BY flattened_move ORDER BY 2 DESC")
```


