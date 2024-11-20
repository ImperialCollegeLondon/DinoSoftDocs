## Quick Start

```python
import dinosoft as ds

# Load a fossil specimen
specimen = ds.load_specimen('KU45690')  # (1)!
analysis = ds.analyze_specimen(specimen)  # (2)!
ds.visualize(analysis)  # (3)!
```

1. :fontawesome-solid-bone: Loads specimen data from common museum catalog formats
2. :fontawesome-solid-microscope: Performs morphological analysis
3. :fontawesome-solid-chart-line: Generates publication-ready visualizations

## Core Features :fontawesome-solid-dna:

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

### Basic Usage

```python linenums="1"
import dinosoft as ds

def analyze_fossil_record(specimen):  # (1)!
    """Process paleontological data"""
    extinction_dates = ds.timeline.mass_extinctions  # (2)!
    diet_analysis = ds.classify_diet(specimen)  # (3)!
    territory = ds.calculate_territory(specimen.size)  # (4)!
    
    return ds.Species(
        specimen.name,
        diet_analysis,
        territory,
        extinction_dates.nearest(specimen.period)
    )
```

1. :fontawesome-solid-bone: Main analysis function
2. :fontawesome-solid-meteor: Loads extinction event database
3. :fontawesome-solid-drumstick-bite: AI-powered diet classification
4. :fontawesome-solid-map: Territory size estimation

### Advanced Examples

=== "Species Analysis"
    ``` python linenums="1"
    # Load and analyze a specimen
    specimen = ds.load_specimen(
        "USNM 555000",  # Smithsonian specimen ID
        precision="high"  # Use high-precision analysis
    )
    ```

=== "Population Modeling"
    ``` python
    # Create a population model
    pop = ds.Population(
        species=specimen,
        territory_km2=1000,
        prey_density=0.5
    )
    ```

=== "Visualization"
    ``` python
    import matplotlib.pyplot as plt

    # Create publication-ready plots
    fig, ax = plt.subplots()
    ds.plot_territory_range(
        specimen, 
        ax=ax, 
        style='journal'
    )
    ```

### Error Handling

```python linenums="1" hl_lines="3 6"
try:
    result = analyze_fossil_record(specimen)
except ds.errors.InvalidPeriodError as e:
    # Handle invalid geological periods
    logger.error(f"Invalid time period: {e}")
except ds.errors.SpecimenError as e:
    # Handle specimen-related errors
    logger.error(f"Specimen error: {e}")
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


## API Status

- [x] Core Analysis Engine
- [x] Data Import/Export :material-information-outline:{title="Supports all major museum formats"}
- [ ] Neural Networks[^1]
- [ ] Web Interface

[^1]: Coming in version 2.0

??? info "Version History"
    - 1.2.0: Added machine learning models
    - 1.1.0: Improved analysis speed
    - 1.0.0: Initial release

!!! tip "Need Support?"
    - :fontawesome-brands-discord: [Join Discord](https://discord.gg/dinosoft){ .tooltip title="Get real-time help" }
    - :fontawesome-brands-github: [GitHub](https://github.com/dinosoft/dinosoft)
    - :fontawesome-solid-book: [API Docs](api/)