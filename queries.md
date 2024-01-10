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
