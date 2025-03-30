# Functionality

VEE is a Bash command line script for managing Python virtual environments.

It is inspired by [`virtualenvwrapper`](https://virtualenvwrapper.readthedocs.io/en/latest/) which has the same aim. However, `virtualenvwrapper` requires cognitive thought and attention to operate. One must even know the name of the project one is working on. VEE aims to resolve that, making the management of Python virtual environments as automatic as possible, freeing up a Python programmer's cognitive faculties for Python programming or other forms of deep relaxation.

## Random technical notes
* VEE stores virtual environments in `~/.venv`.
* VEE uses the Python package `venv` for managing virtual environments, not `virtualenv`.
* VEE supports both traditional `requirements.txt` and dependencies defined in `pyproject.toml`.

# Installation

In your `~/.bashrc` or equivalent, add the following line, where `/path/to/vee` is the full path to the `vee` script.

    source /path/to/vee

*Hint: You can also place `vee` in your `$PATH` and just call `source vee`.*

Once `vee` is sourced from your `bashrc`-equivalent, you can call `vee` to start and activate a new virtual environment in a directory that contains a `requirements.txt` or `pyproject.toml` file, like so:

    vee

If a virtual environment for the current directory already exists, it is activated instead of created.

Example output in a project called `example`, containing only a `requirements.txt` file:

    [someuser@good-machine ~/code/example]$ cat requirements.txt 
    python-dotenv
    [someuser@good-machine ~/code/example]$ vee
    Collecting python-dotenv
      Using cached python_dotenv-0.21.0-py3-none-any.whl (18 kB)
    Installing collected packages: python-dotenv
    Successfully installed python-dotenv-0.21.0
    (code.example) [someuser@good-machine ~/code/example]$ 

Note that you did not need to provide a project name, figure out where to store the virtual environment, nor did you have to activate it.

From then on, when you enter the directory, the virtual environment is activated automatically. Example:

    [someuser@good-machine ~/code]$ cd example                # No virtual environment.
    (code.example) [someuser@good-machine ~/code/example]$    # Virtual environment activated.

Note that the virtual environment prompt, in this case "code.example", contains both the project's directory and its parent directory. This is to support a common setup where the code resides in a sub-directory inside the project, for example "project/backend" or such and may result in an unnecessarily long prompt. To remedy this, instead of just typing `vee` without arguments, you may select a custom prompt like so:

    vee start example

The same applies to the `restart` command when you wish to rebuild the virtual environment. At that point, you may also change the prompt like so:

    vee restart example

Both of these will result in the prompt being "example" instead of "code.example".

# Cheat-sheet

*The only command you need to concern yourself with in everyday life is `vee`.*

| Command        | Function                                                                                                                                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `vee`          | Activates the current directory's virtual environment if it exists, but otherwise creates and activates a new one using the required dependencies.         |
| `vee activate` | Only used internally. Activates current directory's virtual environment if available. Automatically run after `cd`, so it doesn't need to be run by user.  |
| `vee start`    | Only used internally and when setting a custom prompt.                                                                                                     |
| `vee restart`  | Deletes the virtual environment, creates a new one, installs dependencies and activates the new virtual environment.                                       |
| `vee upgrade`  | Upgrades dependencies in an already existing virtual environment.                                                                                          |
