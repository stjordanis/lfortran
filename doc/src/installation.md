# Installation

## Dependencies

End users (and distributions) are encouraged to use the tarball, which only
depends on Python and a few Python packages (`llvmlite`, `pytest`,
`prompt_toolkit` and `antlr4-python3-runtime`). The LFortran standard library
needs to be compiled and it needs a C compiler. Down the road (see our
[roadmap](index.md)), LFortran will be gradually rewritten in C++, so it will
also depend on a C++ compiler.

The tarball is generated automatically by our CI (continuous integration) and
contains some autogenerated files: the parser, which is generated by ANTLR4
(requires Java) and the AST and ASR nodes, which is generated by an ASDL
translator (requires Python). The Java requirement is only needed when using
git directly, the tarball does not depend on Java in any way.

## From a Tarball

This is the easiest way.

Install prerequisites and LFortran (works on both Linux and Mac):
```bash
conda create -n lfortran python=3.7 pytest llvmlite prompt_toolkit
conda activate lfortran
pip install antlr4-python3-runtime
tar xzf lfortran-0.1.tar.gz
cd lfortran-0.1
pip install .
```
Now the `lfortran` environment has the `lfort` compiler available.

Optional: run tests:
```bash
py.test --pyargs lfortran
```


## From Git

This works both on Linux and a Mac:
```bash
conda create -n lfortran python=3.7 pytest llvmlite prompt_toolkit
conda activate lfortran
pip install antlr4-python3-runtime
```
Install Java and then ANTLR, say, into `~/ext`:
```bash
export CLASSPATH="$HOME/ext/antlr-4.7-complete.jar:$CLASSPATH"
```
Build:
```bash
./build.sh
```
Run tests:
```bash
py.test
```
Run an interactive prompt:
```bash
./lfort
```
