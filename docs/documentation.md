# DinoSoft Documentation

DinoSoft is a Python library for paleontological data analysis, specializing in dinosaur fossil processing and ecological modeling.

## Documentation Types

### Tutorials

Learn DinoSoft step-by-step

[Start Learning](#getting-started-with-dinosoft)

### How-To Guides

Task-focused guides for specific goals

[View Guides](#installing-dinosoft)

### Reference

Complete API and configuration documentation

[Read Reference](#core-features-reference)

### Roadmap

Understand roadmap and support options

[Learn More](#roadmap-and-support)

## Key Features

### Fossil Analysis

Process and analyze fossil specimens using our advanced ML pipeline

[Get Started](#getting-started-with-dinosoft)

### Genetic Studies

DNA preservation analysis and ancient genome reconstruction

[Learn More](#core-features-reference)

### Morphology

Complete morphological analysis and comparison tools

[Explore](#core-features-reference)

### Statistics

Statistical analysis and visualization tools

[View Details](#using-dinosoft)

[Install DinoSoft today](#installing-dinosoft)

## Getting Started with DinoSoft

This tutorial will guide you through your first fossil analysis using DinoSoft.

```python
import dinosoft as ds

# Load a fossil specimen
specimen = ds.load_specimen('KU45690')
analysis = ds.analyze_specimen(specimen)
ds.visualize(analysis)
```

### Next Steps

Once you've completed your first analysis, learn about:

- [Configuring analysis settings](#configuration-reference)
- [Working with populations](#core-features-reference)
- [Creating custom visualizations](#advanced-examples)

## Core Features Reference

DinoSoft offers three primary data structures:

`Species`

Represents a single dinosaur species with complete taxonomic and ecological data
    
```python
tyrannosaurus = ds.Species({
    "name": "Tyrannosaurus rex",
    "period": "Late Cretaceous",
    "diet": "Carnivore",
    "mass_kg": 7000
})
```

`Population`

Models population dynamics and ecological interactions
    
```python
population = ds.Population(tyrannosaurus, 
                         territory_km2=1000, 
                         prey_density=0.5)
```

`Period`

Creates a period using standardized geological time periods

```python
custom_period = ds.Period(
    "Late Triassic",  # Start of period
    "Late Cretaceous",
    freq="1Ma"  # 1 million year intervals
)
```

## Configuration Reference

Create `dinosoft.yml` in your project root:

```yaml
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
| Reset Analysis | Ctrl+R | Cmd+R |
| Export Results | Ctrl+E | Cmd+E |
| Quick Save | Ctrl+S | Cmd+S |

## Installing DinoSoft

This guide walks you through installing DinoSoft for your needs.

### System Requirements

Prerequisites:

- Python 3.8 or higher
- 4GB RAM minimum
- CUDA-compatible GPU recommended

### Installation Methods

#### pip (Recommended)

Set up a virtual environment, or if done simply run `pip`.
```bash
python -m venv dinoenv
source dinoenv/bin/activate  # Linux/Mac
pip install dinosoft
```

Available extras:
```bash
pip install dinosoft[viz]     # Visualization tools
pip install dinosoft[ml]      # Machine learning features
pip install dinosoft[full]    # All optional dependencies
```

#### conda
```bash
conda create -n dinoenv python=3.9
conda activate dinoenv
conda install -c paleochannel dinosoft
```

#### Development
```bash
git clone https://github.com/dinosoft/dinosoft.git
cd dinosoft
pip install -e ".[dev]"
```

Common Issues:

- **ImportError**: Check Python version compatibility
- **GPU not detected**: Verify CUDA installation
- **Memory Error**: Increase available RAM

## Using DinoSoft

This guide shows you how to perform common tasks with DinoSoft.

### Basic Usage

```python
import dinosoft as ds

def analyze_fossil_record(specimen):
    """Process paleontological data"""
    extinction_dates = ds.timeline.mass_extinctions
    diet_analysis = ds.classify_diet(specimen)
    territory = ds.calculate_territory(specimen.size)
    
    return ds.Species(
        specimen.name,
        diet_analysis,
        territory,
        extinction_dates.nearest(specimen.period)
    )
```

### Advanced Examples

#### Species Analysis
```python
# Load and analyze a specimen
specimen = ds.load_specimen(
    "USNM 555000",  # Smithsonian specimen ID
    precision="high"  # Use high-precision analysis
)
```

#### Population Modeling
```python
# Create a population model
pop = ds.Population(
    species=specimen,
    territory_km2=1000,
    prey_density=0.5
)
```

#### Visualization
```python
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

```python
try:
    result = analyze_fossil_record(specimen)
except ds.errors.InvalidPeriodError as e:
    # Handle invalid geological periods
    logger.error(f"Invalid time period: {e}")
except ds.errors.SpecimenError as e:
    # Handle specimen-related errors
    logger.error(f"Specimen error: {e}")
```

## Roadmap and Support

### API Status

- DONE Core Analysis Engine
- DONE Data Import/Export :material-information-outline:{title="Supports all major museum formats"}
- WIP Neural Networks[^1]
- WIP Web Interface

[^1]: Coming in version 2.0

Version History:

- 1.2.0: Added machine learning models
- 1.1.0: Improved analysis speed
- 1.0.0: Initial release

### Support

Need Support?

- :fontawesome-brands-discord: [Join Discord](https://discord.gg/dinosoft){ .tooltip title="Get real-time help" }
- :fontawesome-brands-github: [GitHub](https://github.com/dinosoft/dinosoft)
- :fontawesome-solid-book: [API Docs](../reference/index.md)