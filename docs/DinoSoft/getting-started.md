# Getting Started with DinoSoft

This tutorial will guide you through your first fossil analysis using DinoSoft.

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

## Next Steps

Once you've completed your first analysis, learn about:

- [Configuring analysis settings](reference.md#configuration-reference)
- [Working with populations](reference.md#core-features-reference-fontawesome-solid-dna)
- [Creating custom visualizations](usage.md#advanced-examples)