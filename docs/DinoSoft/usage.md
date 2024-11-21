# Using DinoSoft

This guide shows you how to perform common tasks with DinoSoft.

## Basic Usage

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

## Advanced Examples

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

## Error Handling

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