# Core Features Reference :fontawesome-solid-dna:

DinoSoft offers three primary data structures:

`Species`{ .annotate }

:   Represents a single dinosaur species with complete taxonomic and ecological data
    
    ``` python
    tyrannosaurus = ds.Species({
        "name": "Tyrannosaurus rex",
        "period": "Late Cretaceous",
        "diet": "Carnivore",
        "mass_kg": 7000
    })
    ```

`Population`{ .annotate }

:   Models population dynamics and ecological interactions
    
    ``` python
    population = ds.Population(tyrannosaurus, 
                             territory_km2=1000, 
                             prey_density=0.5)
    ```

`Period`{ .annotate }

:   Creates a period using standardized geological time periods

    ```python
    custom_period = ds.Period(
        "Late Triassic",  # Start of period
        "Late Cretaceous",
        freq="1Ma"  # 1 million year intervals
    )
    ```

## Configuration Reference

Create `dinosoft.yml` in your project root:

``` yaml linenums="1"
analysis:
  settings:
    precision: high     # Analysis precision
    units: metric      # Measurement units
  visualization:
    style: journal     # Publication style
    colormap: viridis  # Default colormap
```

### Keyboard Shortcuts

| Action | Windows/Linux | MacOS |
|--------|--------------|-------|
| Reset Analysis | ++ctrl+r++ | ++cmd+r++ |
| Export Results | ++ctrl+e++ | ++cmd+e++ |
| Quick Save | ++ctrl+s++ | ++cmd+s++ |