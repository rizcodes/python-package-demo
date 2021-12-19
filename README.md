# Python custom package
Demo for creating a custom python package

###### https://packaging.python.org/en/latest/tutorials/packaging-projects/

### Initial project structrure
```shell
.
├── LICENSE
├── pyproject.toml
├── README.md
├── setup.cfg
├── src
│   ├── pydemo
│   │   ├── demo.py
│   │   └── __init__.py
└── tests
```
### Installation
+ Local installation `pip install .`

```text
Processing /data/codes/python/python-package-demo
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
    Preparing wheel metadata ... done
Building wheels for collected packages: pydemo
  Building wheel for pydemo (PEP 517) ... done
  Created wheel for pydemo: filename=pydemo-0.1.0-py3-none-any.whl size=2472 sha256=0a4316934bc1d3a74152ffd2478dc18b0643417e6957a6df331eb4a71bfa7e20
  Stored in directory: /home/riztron/.cache/pip/wheels/b4/b1/28/942174e40759b4a12063ef042408d98a06bcbb34f98d395c9d
Successfully built pydemo
Installing collected packages: pydemo
  Attempting uninstall: pydemo
    Found existing installation: pydemo 0.1.0
    Uninstalling pydemo-0.1.0:
      Successfully uninstalled pydemo-0.1.0
Successfully installed pydemo-0.1.0
```
### Test Package
```python
>>> from pydemo.demo import square_num
>>> square_num(10)
100
>>>
```

### Build
1. Make sure `build` is installed - `python3 -m pip install --upgrade build`.
2. Run build in root dir, where pyproject.toml is present `python3 -m build`.

### Final project structure
```shell
.
├── dist
│   ├── pydemo_pkg_rizcodes-0.1.0-py3-none-any.whl
│   └── pydemo-pkg-rizcodes-0.1.0.tar.gz
├── LICENSE
├── pyproject.toml
├── python-package-demo.iml
├── README.md
├── setup.cfg
├── src
│   ├── pydemo
│   │   ├── demo.py
│   │   └── __init__.py
│   └── pydemo_pkg_rizcodes.egg-info
│       ├── dependency_links.txt
│       ├── PKG-INFO
│       ├── SOURCES.txt
│       └── top_level.txt
└── tests

```

### Uploading package distribution
1. Install twine `python3 -m pip install --upgrade twine`
2. Make sure you have account in `testpypi`.
3. Upload to testpypi - `python3 -m twine upload --repository testpypi dist/*`

### Install package
1. Install - `pip install -i https://test.pypi.org/simple/ pydemo-pkg-rizcodes`
```text
Looking in indexes: https://test.pypi.org/simple/
Collecting pydemo-pkg-rizcodes
  Downloading https://test-files.pythonhosted.org/packages/e7/94/9fb276177ec5beb146cefd255fc561d1b65b6d04838a26bad2261294798a/pydemo_pkg_rizcodes-0.1.0-py3-none-any.whl (3.1 kB)
Installing collected packages: pydemo-pkg-rizcodes
Successfully installed pydemo-pkg-rizcodes-0.1.0
```
2. Validate
```python
>>> import pydemo
>>> pydemo.__version__
'0.1.0'
>>> from pydemo import demo
>>> demo.square_num(2)
4
>>>
```
