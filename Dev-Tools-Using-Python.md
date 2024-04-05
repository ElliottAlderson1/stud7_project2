**Procedures/Commands**

**Using PIP**

- Update pip using ``pip3 install --upgrade pip --user`` within bash terminal
     - To upgrade pip in venv use ``pip install --upgrade pip``
- Install all python packages listed by entering ``pip3 install -r baseline_requirements.txt --user``
- To view all installed packages use ``pip list``
- Use ``pip freeze > < path to virtual environment/filename`` to save all installed packaged and versions to file
     - Example is ``pip freeze > ./my_venv/requirements.txt``
- To install a specific version of a package use ``pip install < package name >==< version number >``
     - Example is ``pip install requests==2.27.0``
- You can install a list of packages using a file using ``pip install -r < path to file within virtual environment > 
     - Example is ``pip install -r ./my_venv/requirements.txt``
- Show the version and other information for a package using ``pip show < package name >``


**Creating a Jupyter Notebook**

1. Run ``Create: New Jupyter Notebook`` command from the **Command Palette (Ctrl+Shift+P or F1)** or by creating a new ``.ipynb`` file in your workspace
2. Select a kernel using the ``kernel picker`` (top right of jupyter area)
3. The language picker in the bottom right of each code cell with auto update language support by the kernel. If you have an existing Jupyter Notebook it can be opened by right-clicking the file and opening with VS Code or through VS Code File Explorer

**Work with Code Cells**

While working with code cells, a cell can be in three states: **unselected**, **command mode**, and **edit mode**. The current state of a cell is indicated by a vertical bar to the left of a code cell and editor border. When no bar is visible, the cell is unselected.
When a cell is selected, it can be in two different modes. It can be in **command mode** or in **edit mode.** 
When a cell is in **command mode**, a solid vertical bar will appear to the left of the cell and it can be operated on and accept keyboard commands
When you're in **edit mode**, the solid vertical bar is joined by a border around the cell editor and the cell's contents (code or Markdown) can be modified.
To move from edit mode to **command mode**, press the Esc key. To move from **command mode** to **edit mode**, press the Enter key. You can also use the mouse to change the mode by clicking the vertical bar to the left of the cell or out of the code/Markdown region in the code cell.
