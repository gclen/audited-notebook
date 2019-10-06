# audited-notebook
Jupyter notebook fork which allows auditing of code sent to the kernel

### Installation

Note that you may need to remove existing jupyter installations first. E.g.

```
pip uninstall jupyter-core
```

To install from this git repo

```
pip install https://github.com/gclen/audited-notebook/archive/6.0.1_pypi_with_mods.zip
```
### Usage

Using the configs in the example config directory will output a jupyter.log file

```
jupyter-notebook --kernel-logger example_configs/audit_logger.conf
```

This config is just a standard python logging config so you can change the format to suit your requirements. The only requirement is that it needs
a logger called ```kernel_logger```