# Repro state
I used this state to reproduce the bug.
```
$ pip list
Package                  Version
------------------------ --------------------------------------------------
mypy                     0.640+dev.7ae1b530ccf85c0f48bf3e28b852ca94807675c7
mypy-extensions          0.4.1
pip                      18.1
setuptools               40.4.3
typed-ast                1.1.0
typedpkg-namespace.alpha 1.0.0
```

# Error outputs
```
$ mypy imp_as.py
imp_as.py:1: error: Cannot find module named 'typedpkg_namespace'
imp_as.py:1: note: (Perhaps setting MYPYPATH or using the "--ignore-missing-imports" flag would help)
imp_as.py:3: error: Argument 1 has incompatible type "int"; expected "bool"

$ mypy imp_as.py --namespace-packages
imp_as.py:1: error: Cannot find module named 'typedpkg_namespace'
imp_as.py:1: note: (Perhaps setting MYPYPATH or using the "--ignore-missing-imports" flag would help)
imp_as.py:3: error: Argument 1 has incompatible type "int"; expected "bool"

$ mypy not_from_imp.py
not_from_imp.py:1: error: Cannot find module named 'typedpkg_namespace'
not_from_imp.py:1: note: (Perhaps setting MYPYPATH or using the "--ignore-missing-imports" flag would help)

$ mypy not_from_imp.py --namespace-packages
not_from_imp.py:1: error: Cannot find module named 'typedpkg_namespace'
not_from_imp.py:1: note: (Perhaps setting MYPYPATH or using the "--ignore-missing-imports" flag would help)
```
