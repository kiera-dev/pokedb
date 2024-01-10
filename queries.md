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

