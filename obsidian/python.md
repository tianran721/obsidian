```
Python has been installed as

  /usr/local/bin/python3

Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to

`python3`, `python3-config`, `pip3` etc., respectively, have been installed into

  /usr/local/opt/python@3.11/libexec/bin

  

You can install Python packages with

  pip3 install <package>

They will install into the site-package directory

  /usr/local/lib/python3.11/site-packages

  

tkinter is no longer included with this formula, but it is available separately:

  brew install python-tk@3.11

  

gdbm (`dbm.gnu`) is no longer included in this formula, but it is available separately:

  brew install python-gdbm@3.11

`dbm.ndbm` changed database backends in Homebrew Python 3.11.

If you need to read a database from a previous Homebrew Python created via `dbm.ndbm`,

you'll need to read your database using the older version of Homebrew Python and convert to another format.

`dbm` still defaults to `dbm.gnu` when it is installed.

  

For more information about Homebrew and Python, see: https://docs.brew.sh/Homebrew-and-Python
```

```
WARNING: You are using pip version 21.2.4; however, version 23.3.2 is available.

You should consider upgrading via the '/Library/Developer/CommandLineTools/usr/bin/python3 -m pip install --upgrade pip' command.
```

```
  WARNING: The scripts pip, pip3, pip3.11 and pip3.9 are installed in '/Users/feng/Library/Python/3.9/bin' which is not on PATH.

  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```

