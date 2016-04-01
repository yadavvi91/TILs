## Running a `module` as a script as well as allowing to `import` the `module`.


A `module` is a file containing Python definitions and statements.
Within a module, the module's name is available as the value of the global variable `__name__`.

A `module` can contain executable statements as well as function definitions. The statements are
intended to initialize the module. They are executed only the *first* time the module name is
encountered in an import statement.

    # fibo.py
    # Fibonacci numbers module

    def fib(n):    # write Fibonacci series up to n
        a, b = 0, 1
        while b < n:
            print(b, end=' ')
            a, b = b, a+b
        print()

    def fib2(n): # return Fibonacci series up to n
        result = []
        a, b = 0, 1
        while b < n:
            result.append(b)
            a, b = b, a+b
        return result



### Executing modules as scripts

When you run a Python module with

    python fibo.py <arguments>

the code in the module will be executed, just as if you imported it, but with the `__name__` set to `__main__`.
This means that by adding this code at the end of our module:

    if __name__ == "__main__"
        import sys
        fib(int(sys.argv[1]))

we can make the file usable as a script as well as an importable module, because the code that parses the
command line only runs if the module is executed as the "main" file:

    $ python fibo.py 50
    1 1 2 3 5 8 13 21 34


If the module is imported, the code is not run:

    >>> import fibo
    >>> 

This is often used either to provide a convenient user interface to a module, or for testing purposes
(running the module as a script executes a test suite).


### Standard Modules

Python comes with a library of standard modules (see more: Python Library Reference).
Some modules are built into the interpreter; these provide access to operations that are not a part
of the language but are built in, for providing access to OS primitives like system calls or for
efficiency.


One such module is `sys` which is built-in into every Python interpreter. The variables `sys.ps1` and
`sys.ps2` define the strings used as primary and secondary outputs.

    >>> import sys
    >>> sys.p1
    '>>> '
    >>> sys.p2
    '... '


These two variables are only defined when the interpreter is in interactive mode.

The variable `sys.path` is a list of string that determines the interpreter's search path for modules.
It is initialized to the default path taken from the environment variable PYTHONPATH or from a built-in
default if PYTHONPATH is not set. We can modify it using standard list operations:

    >>> import sys
    >>> sys.path.append('/home/<username>/spyder/bin')



## Learning more about the modules.

### The `dir()` Function

The built-in function `dir()` is used to find out the names a module defines. It returns a sorted list
of strings:


    >>> import fibo, sys
    >>> dir(fibo)
    ['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__',
    '__package__', '__spec__', 'fib', 'fib2']
    >>> dir(sys)
    ['__displayhook__', '__doc__', '__egginsert', '__excepthook__',
    '__interactivehook__', '__loader__', '__name__', '__package__', '__plen',
    '__spec__', '__stderr__', '__stdin__', '__stdout__', '_clear_type_cache',
    '_current_frames', '_debugmallocstats', '_getframe', '_home', '_mercurial',
    '_xoptions', 'abiflags', 'api_version', 'argv', 'base_exec_prefix',
    'base_prefix', 'builtin_module_names', 'byteorder', 'call_tracing',
    'callstats', 'copyright', 'displayhook', 'dont_write_bytecode', 'exc_info',
    'excepthook', 'exec_prefix', 'executable', 'exit', 'flags', 'float_info',
    'float_repr_style', 'getallocatedblocks', 'getcheckinterval',
    'getdefaultencoding', 'getdlopenflags', 'getfilesystemencoding', 'getprofile',
    'getrecursionlimit', 'getrefcount', 'getsizeof', 'getswitchinterval',
    'gettrace', 'hash_info', 'hexversion', 'implementation', 'int_info', 'intern',
    'last_traceback', 'last_type', 'last_value', 'maxsize', 'maxunicode',
    'meta_path', 'modules', 'path', 'path_hooks', 'path_importer_cache',
    'platform', 'prefix', 'setcheckinterval', 'setdlopenflags', 'setprofile',
    'setrecursionlimit', 'setswitchinterval', 'settrace', 'stderr', 'stdin',
    'stdout', 'thread_info', 'version', 'version_info', 'warnoptions']


Without arguments, `dir()` lists the names we have defined currently.

    >>> a = [1, 2, 3, 4, 5]
    >>> import fibo
    >>> fib = fibo.fib
    >>> dir()
    ['__builtins__', 'a', 'fib', 'fibo', 'sys']


Note that it lists all types of names: variables, modules, functions etc.


`dir()` does NOT list the names of built-in functions and variables. If we want a list of those,
they are defined in the standard module `builtins`:

    >>> import builtins
    >>> dir(builtins)
    ['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException',
    'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning',
    'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError',
    'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning',
    'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False',
    'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning',
    'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError',
    'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError',
    'KeyboardInterrupt', 'LookupError', 'MemoryError', 'NameError', 'None',
    'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError',
    'OverflowError', 'PendingDeprecationWarning', 'PermissionError',
    'ProcessLookupError', 'ReferenceError', 'ResourceWarning', 'RuntimeError',
    'RuntimeWarning', 'StopIteration', 'SyntaxError', 'SyntaxWarning',
    'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError',
    'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError',
    'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning',
    'ValueError', 'Warning', 'ZeroDivisionError', '_', '__build_class__',
    '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__',
    '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'bytearray', 'bytes',
    'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits',
    'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'execfile',
    'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals',
    'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance',
    'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max',
    'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print',
    'property', 'quit', 'range', 'repr', 'reversed', 'round', 'runfile', 'set',
    'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple',
    'type', 'vars', 'zip']



## Arranging modules into packages.

### Packages 

Packages are a way of structuring Python's module namespace by using "dotted module names".
For example, the module name `A.B` designates a submodule name `B` in a package named `A`.

Using dotted module names helps the author avoid name conflicts while importing modules
like NumPy and Python imaging Library.

Example of a Python package structure

    sound/                          Top-level package
          __init__.py               Initialize the sound package
          formats/                  Subpackage for file format conversions
                  __init__.py
                  wavread.py
                  wavwrite.py
                  aiffread.py
                  aiffwrite.py
                  auread.py
                  auwrite.py
                  ...
          effects/                  Subpackage for sound effects
                  __init__.py
                  echo.py
                  surround.py
                  reverse.py
                  ...
          filters/                  Subpackage for filters
                  __init__.py
                  equalizer.py
                  vocoder.py
                  karaoke.py
                  ...

When importing the package, Python searches through the directories on `sys.path` looking for
the package sub-directory.

The `__init__.py` files are required to make Python treat the directories as containing packages;
this is done to prevent the directories with a common name, such as `string`, from unintentionally
hiding valid modules that occur later in the module search path.

In the simplest case, `__init__.py` can just be an empty file, but it can also execute
initialization code for the package or set the `__all__` variable.


Users of the package can import in the following ways - 

 * Import individual modules from the package:

       import sound.effects.echo

   This loads the submodule `sound.effects.echo`. It must be referenced with its full name

       sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)

 * An alternative way of import the module is:

       from sound.effects import echo

   This also loads the submodule `echo` and makes it available without its package prefix,

       echo.echofilter(input, output, delay=0.7, atten=4)

 * Or, we can directly import the desired function or variable directly:

       from sound.effects.echo import echofilter

   This loads the submodule `echo`, but this makes its function `echofilter()` directly available:

       echofilter(input, output, delay=0.7, atten=4)


**NOTE:** When using `from package import item`, the item can be a package or a submodule or even a
function, class or variable. However, when using `import item.subitem.subsubitem`, ***each item
except the last must be a package***; the last item can be a module or a package but **CANNOT** be a
class or function or variable.

If there is some problem while importing an `ImportError` is raised.


### Importing * from a package

See [Python docs](https://docs.python.org/2/tutorial/modules.html#importing-from-a-package)

When a user does an `from sound.effects import *`, all the submodules are not imported, however,
it is ensured that package `sound.effects` has been imported.

To avoid any complications(for the lack of a better word), if the applications' package has an
`__init__.py`, a list `__all__` can be defined which can be the list of submodules that should
be imported when `from sound.effects import *`.

For example, the file `sound/effects/__init__.py` could contain the following code:

    __all__ = ["echo", "surround", "reverse"]

This would mean that `from sound.effects import *` would import three named submodules of the
`sound` package.

