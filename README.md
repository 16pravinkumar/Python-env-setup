# Python-env-setup

Command                              	Description
python --version	                    Shows the installed Python version.
python script.py	                    Runs the Python file named script.py.
pip install package_name            	Installs the specified Python package.
pip list	                            Lists all installed Python packages.
python -m venv env_name	              Creates a virtual environment.
source env_name/bin/activate (Linux/Mac)
.\env_name\Scripts\activate           (Windows)	Activates the virtual environment.
deactivate	                          Deactivates the virtual environment.
pip freeze > requirements.txt	        Saves current packages to a file.
pip install -r requirements.txt	      Installs packages listed in requirements.txt.
mypy file.py	                        Checks type hints using mypy (if installed).


<pre> ```bash pip install -r requirements.txt python main.py ``` </pre>
