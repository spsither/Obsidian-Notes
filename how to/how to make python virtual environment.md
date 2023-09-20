go to a director and create a `python3` environment
`python3 -m venv .env`

activate the environment
`. .env/bin/activate`
`source .env/bin/activate`

`pip install openpecha`

check if it was installed
`pip show openpecha`

install package in editable mode
`pip install -e .`
The command `pip install -e .` is used to install a local version of a Python package in "editable" mode, meaning that changes made to the source code will be immediately reflected in the installed package without having to re-install it. The `-e` option stands for "editable" and the `.` refers to the current directory, where the package source code is located. This is a common practice in development, where developers want to quickly test and iterate on their code without having to go through the full package installation process each time.

stop using the environment
`deactivate`


# Using Conda

To create an environment
`conda create --name myenv`
`conda create -n myenv`

To create an environment with a specific version of Python
`conda create -n myenv python=3.9`

To activate conda environment
`conda activate myenv`

To deactivate conda environment
`conda deactivate`

Create the environment from the `environment.yml` file
`conda env create -f environment.yml`