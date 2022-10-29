# Functionality

VEE is a Bash command line script for managing Python virtual environments.

It is inspired by [`virtualenvwrapper`](https://virtualenvwrapper.readthedocs.io/en/latest/) which has the same aim. However, `virtualenvwrapper` requires cognitive thought and attention to operate. One must even know the name of the project one is working on. VEE aims to resolve that, making the management of Python virtual environments as automatic as possible, freeing up a Python programmer's cognitive faculties for Python programming or other forms of deep relaxation.

## Random technical notes
* VEE stores virtual environments in `~/.venv`.
* VEE uses the Python package `venv` for managing virtual environments, not `virtualenv`.

# Installation

In your `~/.bashrc` or equivalent, add the following line, where `/path/to/vee` is the full path to the `vee` script.

    source /path/to/vee

*Hint: You can also place `vee` in your `$PATH` and just call `source vee`.*

Once `vee` is sourced from your `bashrc`-equivalent, you can call `vee` to start and activate a new virtual environment in a directory that contains a `requirements.txt` file, like so:

    vee

Example output in a project called `example`, containing only a `requirements.txt` file:

    [someuser@good-machine ~/example]$ cat requirements.txt 
    python-dotenv
    [someuser@good-machine ~/example]$ vee
    Collecting python-dotenv
      Using cached python_dotenv-0.21.0-py3-none-any.whl (18 kB)
    Installing collected packages: python-dotenv
    Successfully installed python-dotenv-0.21.0
    (example) [someuser@good-machine ~/example]$ 

Note that you did not need to provide a project name, figure out where to store the virtual environment, nor did you have to activate it.

From then on, when you enter the directory, the virtual environment is activated automatically. Example:

    [someuser@good-machine ~]$ cd example          # No virtual environment.
    (example) [someuser@good-machine ~/example]$   # Virtual environment activated.


From then on, you may call `vee` from the command line, regardless of whether the script itself is in the `$PATH` or not.

# Cheat-sheet

*The only command you need to concern yourself with in everyday life is `vee`.*

| Command        | Function                                                                                                                                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `vee`          | Creates and activates a virtual environment for the current directory, located in `~/.venv`. If `requirements.txt` is present, its packages are installed. |
| `vee restart`  | Deletes the virtual environment, creates a new one, installs packages in `requirements.txt` and re-activate the virtual environment.                       |
| `vee activate` | Only used internally. Activates current directory's virtual environment if available. Automatically run after `cd`, so it doesn't need to be run by user.  |
| `vee start`    | Only used internally. This is what calling `vee` without a command actually does.                                                                          |
