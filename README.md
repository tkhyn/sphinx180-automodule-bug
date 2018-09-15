# Sphinx 1.8.0 autodoc bug

This repository highlights a bug in Sphinx 1.8.0's apidoc extension.
Tested on Windows 7 and Windows 10 in a clean Python 3.6 virtual environment.

I could not reproduce it on a linux box.


## Steps to reproduce

```

   python bootstrap.py
   bin\buildout
   bin\sphinx-apidoc -o doc\_apidoc autodoc_bug
   bin\sphinx-build doc doc\_build

```

Output:

```
D:\dev\.env\venv\buildout\Scripts\python.exe D:/dev/sandbox/python/sphinx-1.8.0_bug/bin/sphinx-build-script.py doc doc\_build
Running Sphinx v1.8.0
loading pickled environment... done
building [mo]: targets for 0 po files that are out of date
building [html]: targets for 0 source files that are out of date
updating environment: [] 0 added, 1 changed, 0 removed
reading sources... [100%] _apidoc/sphinx180_bug
Exception occurred:
  File "d:\dev\.env\buildout\eggs\sphinx-1.8.0-py3.6.egg\sphinx\util\__init__.py", line 318, in get_module_source
    eggpath, _ = re.split('(?<=\\.egg)/', filename)
ValueError: not enough values to unpack (expected 2, got 1)
The full traceback has been saved in C:\Users\Thomas\AppData\Local\Temp\sphinx-err-o4loxs60.log, if you want to report the issue to the developers.
Please also report this if it was a user error, so that a better error message can be provided next time.
A bug report can be filed in the tracker at <https://github.com/sphinx-doc/sphinx/issues>. Thanks!

Process finished with exit code 2
```

Now replace `sphinx = 1.8.0` by `sphinx = 1.7.8` in `buildout.cfg`, and run the steps above. It works with no issue.
