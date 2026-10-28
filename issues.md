# Static Code Analysis Issues

| Issue | Type | Line(s) | Description | Fix Approach |
|---|---|---:|---|---|
| `subprocess` module usage | Security | 1, 24 | Bandit B404 identified the subprocess module as a potential security risk. | Removed the unnecessary subprocess dependency and replaced it with a simple print statement. |
| SQL injection through string construction | Security | 9 | Bandit B608 identified a possible SQL injection vulnerability because SQL was constructed using an f-string. | Replaced string interpolation with a parameterized SQL query using `?` placeholders. |
| `shell=True` in subprocess call | Security | 24 | Bandit B602 identified a high-severity security issue because a subprocess was executed with `shell=True`. | Removed the subprocess call entirely because it was only being used to display a message. |
| Use of `assert` | Security / Reliability | 38 | Bandit B101 identified the use of `assert` for program validation. Assertions can be disabled when Python is optimized. | Replaced the assertion with an explicit conditional check that raises `ValueError`. |
| Missing module docstring | Code Quality | 1 | Pylint C0114 reported that the module did not contain a module-level docstring. | Added a module docstring. |
| Missing function docstrings | Code Quality | Multiple | Pylint C0116 reported missing documentation for functions. | Added docstrings to the functions. |
| Non-snake-case function names | Style | Multiple | Pylint C0103 reported names such as `enrollRider` and `feeCollected` as invalid naming style. | Renamed functions using Python snake_case conventions. |
| Unused `driver` argument | Code Quality | 13 | Pylint W0613 reported that the `driver` argument was never used. | Removed the unused argument. |
| File opened without encoding | Style | 18 | Pylint W1514 reported that the file encoding was not explicitly specified. | Added `encoding="utf-8"` to the file operation. |
| File resource not managed with `with` | Code Quality | 18 | Pylint R1732 recommended using a context manager for file operations. | Replaced manual file handling with a `with open(...)` context manager. |
| Long lines and whitespace violations | Style | Multiple | Pylint and Flake8 reported line-length and whitespace problems. | Reformatted the code according to Python style conventions. |
| Missing final newline | Style | End of file | Flake8 W292 reported that the file did not end with a newline. | Added the required final newline and removed trailing whitespace. |