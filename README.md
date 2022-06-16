# Functionality

VEE is a Bash command line script for managing Python virtual environments.

It is inspired by [`virtualenvwrapper`](https://virtualenvwrapper.readthedocs.io/en/latest/) which has the same aim. However, `virtualenvwrapper` requires cognitive thought and attention to operate. One must even know the name of the project one is working on. VEE aims to resolve that, making the management of Python virtual environments as automatic as possible, freeing up a Python programmer's cognitive faculties for Python programming or other forms of deep relaxation.

## Random technical notes
* VEE stores virtual environments in `~/.venv`.
* VEE uses the Python package `venv` for managing virtual environments, not `virtualenv`.

# Installation

Place the `vee` command in your `$PATH`.

Then, in your `~/.bashrc`, add the following line:

    source vee

Alternatively, you can run the command with the full path of `vee` instead of having it in your `$PATH`. Once it has been sourced by the above-mentioned command, a globally available Bash function has been set, also named `vee`.

From then on, you may call `vee` from the command line, regardless of whether the script itself is in the `$PATH` or not.

This tool should be so simple to use, that a cheat-sheet should suffice to document its operation.

# Cheat-sheet

| Command     | Function                                                                                                                                                   |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `vee start` | Creates and activates a virtual environment for the current directory, located in `~/.venv`. If `requirements.txt` is present, its packages are installed. |
| `vee`       | Activates current directory's virtual environment if available. Automatically run after `cd`, so it doesn't need to be run by user.                        |

VEE commands do not replace single commands that already exist in any environment where VEE might possibly be run. They should just be used normally when used individually. Most notable examples are:

* `deactivate` to deactivate the virtual environment.
* `pip install -r requirements.txt` to install packages. Actually, `vee start` does this for you but only as a part of a command that does more than that, namely figuring out the project's name, creating a virtual environment, activating it and installing requirements if they are available.
