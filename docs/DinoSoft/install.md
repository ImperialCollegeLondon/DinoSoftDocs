---
hide:
- toc
---
## Installation Guide

### System Requirements

!!! abstract "Prerequisites"
    - Python 3.8 or higher
    - 4GB RAM minimum
    - CUDA-compatible GPU recommended

### Installation Methods

=== "pip (Recommended)"

    Set up a virtual environment, or if done simply run `pip`.
    ``` bash linenums="1" hl_lines="3"
    python -m venv dinoenv
    source dinoenv/bin/activate  # Linux/Mac
    pip install dinosoft
    ```

    Available extras:
    ``` bash
    pip install dinosoft[viz]     # Visualization tools
    pip install dinosoft[ml]      # Machine learning features
    pip install dinosoft[full]    # All optional dependencies
    ```

=== "conda"
    ``` bash
    conda create -n dinoenv python=3.9
    conda activate dinoenv
    conda install -c paleochannel dinosoft
    ```

=== "Development"
    ```bash
    git clone https://github.com/dinosoft/dinosoft.git
    cd dinosoft
    pip install -e ".[dev]"
    ```


??? tip "Common Issues"
    - **ImportError**: Check Python version compatibility
    - **GPU not detected**: Verify CUDA installation
    - **Memory Error**: Increase available RAM
