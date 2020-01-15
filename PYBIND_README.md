# An Overview on Python Bindings in libbdsg

## Python Usage

Using libbdsg in python is straightforward.  After building libbdsg, make sure that the `bdsg.cpython*.so` file is on your `PYTHONPATH` or added through `sys.path`, and run `import libbdsg`.

## Development Usage

Python bindings for libbdsg are generated automatically using [Binder](https://github.com/RosettaCommons/binder) and [pybind11](https://github.com/pybind/pybind11).

### pybind Overview

Pybind exposes C++ code from a given set of *python bindings*.  These bindings are a set of .cpp files that specify information about the objects and methods to be exposed to python.  At compile time, pybind uses these bindings to create a `*.so` file that can be imported into python-- the code to do this has already been incorporated into the `CMakeLists.txt` for this project.

#### When to Update Bindings
 
If changes have only been made to the backend of libbdsg there is no need to make any changes to the python binding code, as it will automatically be incorporated into the linked library on compile-time. It is only necessary to update the binding .cpp files if new methods or objects need to be exposed to python.

#### How to Update Bindings

The included file `make_and_run_binder.py` will automatically download and build Binder (if this has not already been done) and will run binder on libbdsg, outputting the .cpp files in cmake_bindings.  *Note that building Binder is very slow.*

Specific functions/classes/enums can be manually included or excluded from binding by modifying the included `config.cfg`, as specified in the [binder documentation](https://cppbinder.readthedocs.io/en/latest/config.html#config-file-options).
