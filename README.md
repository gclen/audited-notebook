# audited-notebook
Jupyter notebook fork which allows auditing of code sent to the kernel

### Vanilla installation

Note that you may need to remove existing jupyter installations first. E.g.

```
pip uninstall jupyter-core
```

To install from this git repo

```
pip install https://github.com/gclen/audited-notebook/archive/6.0.1_pypi_with_mods.zip
```

### Modifying the logging config

If you need to change the logging config (for example to point at a syslog server) do the following:

1. Clone this repo

```
git clone https://github.com/gclen/audited-notebook.git
```

2. Checkout the 6.0.1_pypi_with_mods branch

```
git checkout 6.0.1_pypi_with_mods
```

3. Make your changes to ```notebook/services/kernels/kernel_logging_conf.py```. For example you may want to use the config in example_configs/syslog_audit.py

4. To build the wheel file you should copy all of the code to another directory. This is due the fact the setup.py is configured to rebuild all of the JS/CSS files if there is a .git directory in the current repo.

```bash
mkdir ~/notebook_build_dir
cp -r * ~/notebook_build_dir
cd ~/notebook_build_dir
python setup.py sdist bdist_wheel
```
5. You now have a wheel file that you can pip install

```
pip install dist/audited_notebook-6.0.1-py3-none-any.whl
```

### Notes
This config is just a standard python logging config so you can change the format to suit your requirements. The only requirement is that it needs
a logger called ```kernel_logger```