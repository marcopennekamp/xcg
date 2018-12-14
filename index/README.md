# Adding new content to the game
index is where you define your specific macros and components to the game. If you are adding a new component or macro, instead of overwriting an existing one, you will need to specify your additions here.  Do note, you have to start your path from `extensions`

## Bad

```xml
    <entry name="xcg_prod_gen_glass_macro" value="assets\structures\production\macros\xcg_prod_gen_glass_macro"/>
```

## Good
```xml
    <entry name="xcg_prod_gen_glass_macro" value="extensions\XCG\assets\structures\production\macros\xcg_prod_gen_glass_macro"/>
```

## macros.xml
Used for adding new macro assets to the game. These generally consist of metadata about what youre adding to the game, and reference components.  If you don't have any new art or models, you can reuse components.

## components.xml
Used for adding new component assets to the game.  These generally consist of models, art, etc.  
