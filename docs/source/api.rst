Core Class & Methods
====================

Toolrunner Functions
--------------------
Static functions, independent of Tools instances.

.. autofunction:: toolrunner.run(args, new_proc: bool = False, **kwargs)

.. autofunction:: toolrunner.get_argv(index: int)

Tools Class
-----------
.. autofunction:: toolrunner.Tools(target: str = None, output_dir: str = None, config: dict = dict(), verbose: bool = True)

Tools Methods
^^^^^^^^^^^^^
- Additional keyword arguments (*kwargs*) are passed to subprocess.run() or subprocess.Popen(), for your tweaking convenience. 
- When calling any of the *run* commands, setting *output=False* will cause the results to be printed to the console instead of being written to a file. Setting output=True on *gui* tools will just create an empty file *name*.txt file.

Command-line Interface Tools - *cli*
""""""""""""""""""""""""""""""""""""
Executables, tools, CMD/Shell commands, etc.

Default: Target file appended to the end of the command arguments, results output to *name*.txt, spawned as a child process.

.. autofunction:: toolrunner.Tools.cli(name: str, path: str, args: list = [])

.. autofunction:: toolrunner.Tools.run_cli(input_target: bool = True, output: bool = True, new_proc: bool = False, **kwargs)

Graphical User Interface Tools - *gui*
""""""""""""""""""""""""""""""""""""""
Default: Target file appended to the end of the command arguments, no output produced, spawned in its own independent process.

.. autofunction:: toolrunner.Tools.gui(name: str, path: str, args: list = [])

.. autofunction:: toolrunner.Tools.run_gui(input_target: bool = True, output: bool = False, new_proc: bool = True, **kwargs)

Run All
"""""""
.. autofunction:: toolrunner.Tools.run_all(**kwargs)

Get Configuration Dictionary
""""""""""""""""""""""""""""
Prints the instance's current tool configuration, so that it may be copy and pasted.
Loading the tools via a dictionary is cleaner and allows for differenct configurations to be
managed more easily.

.. autofunction:: toolrunner.Tools.print_config()

