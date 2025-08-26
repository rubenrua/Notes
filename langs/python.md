PYTHON
======

Python 3 goodness
------------------

 * Types ([PEP 484](https://www.python.org/dev/peps/pep-0484/) and [PEP 526](https://www.python.org/dev/peps/pep-0526/))
 * `True = False` error.
 * https://docs.python.org/3/library/asyncio.html (see uvloop)
 * https://docs.python.org/3/library/enum.html


Asycio links
------------

 * http://www.snarky.ca/how-the-heck-does-async-await-work-in-python-3-5
 * https://www.youtube.com/watch?v=E-1Y4kSsAFc
 * http://lucumr.pocoo.org/2016/10/30/i-dont-understand-asyncio/


Tools
------

 * http://mypy-lang.org
 * https://flake8.pycqa.org/en/latest/
 * https://pypi.python.org/pypi/virtualenv
 * https://black.readthedocs.io/en/stable/
 * https://github.com/charliermarsh/ruff
 * https://lgtm.com/ (saas)
 * https://semgrep.dev/ (multi-lang)

Other
-----

 * https://github.com/vinta/awesome-python
 * https://github.com/faif/python-patterns
 * http://www.labri.fr/perso/nrougier/from-python-to-numpy
 * https://kate.io/blog/2017/08/22/weird-python-integers/
 * http://nuitka.net/

```
>>> import sysconfig
>>> sysconfig.get_path('purelib', vars={'base': ''})
'/lib/python3.10/site-packages'
>>> sysconfig.get_paths()
{'stdlib': '/usr/lib/python3.8', 'platstdlib': '/usr/lib/python3.8', 'purelib': '/usr/lib/python3.8/site-packages', 'platlib': '/usr/lib/python3.8/site-packages', 'include': '/usr/include/python3.8', 'scripts': '/usr/bin', 'data': '/usr'}
```