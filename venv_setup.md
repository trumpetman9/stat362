# Python Virtual Environment Setup with Poetry

This guide will help you set up a Python virtual environment for your project using [Poetry](https://python-poetry.org/). Follow these steps to ensure a smooth development experience in VS Code.

---

## 1. Install Poetry (One-Time Setup)

### Official Installation 

Before getting started, please note: when you open a new terminal, your command prompt may start with **`(base)`**.  

This indicates that the **Conda base environment** is being automatically activated. If you previously installed Conda on your laptop, this auto-activation can cause conflicts with system or course-specific packages.  

Since we will **not** be using Conda to manage the environment for this course, and to ensure proper isolation, please disable Conda’s automatic base activation permanently by running:  

```bash
conda config --set auto_activate_base false
```

#### For macOS/Linux:

1. Run the automatic installation script:

    ```bash
    curl -sSL https://install.python-poetry.org | python3 -
    ```

2. Ensure the Poetry executable is in your `PATH`. Add the following line to your `~/.zshrc` or `~/.bash_profile` (above any `pyenv` lines):

    ```bash
    export PATH="$HOME/.local/bin:$PATH"
    ```

    > **Note:** You may need to restart your terminal or run `source ~/.zshrc` for changes to take effect.

3. Configure Poetry to create virtual environments inside your project root:

    ```bash
    poetry config virtualenvs.in-project true
    ```

#### For Windows (PowerShell):

1. Run the following command:

    ```powershell
    (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
    ```

2. Make sure the Poetry executable is in your `PATH` (see the [official docs](https://python-poetry.org/docs/#installing-with-the-official-installer)).

  > **Note:** You may need to restart your terminal or VS code for changes to take effect

#### Verify Installation:

1. Run the following command:
   

    ```powershell
    poetry --version
    ```
    
    If it prints the installed version, you’re ready to proceed!
---

## 2. Set Up Your Project Environment

1. **Clone this GitHub repository** (if you haven't already):

    ```bash
    git clone <this-repo-url>
    cd <this-project-folder>
    ```
    > *If `git` is not installed, you may need to run `sudo apt install git` (Linux) or use Homebrew on macOS.*

2. **Configure poetry to use `.venv` in project directionary** 

    ```bash
    poetry config virtualenvs.in-project true
    ```   
3. **Install project dependencies** (from the folder containing `pyproject.toml`):

    ```bash
    poetry install --no-root
    ```

4. **Verify the Python interpreter**:

    ```bash
    poetry run which python
    ```
    This should point to the `.venv` folder under your project root.

5. **Restart VS Code** and select the Python interpreter from `.venv` for the best experience.

6. **Test your torch environment**:

    ```bash
    poetry run python test_torch_env.py
    ```
    If this runs without errors, your environment is set up correctly.
7. **Run the end-to-end check**
   
   Open and run the `test_env.ipynb` (Run All Cells)

   Confirm that all cells finish without errors.
---

You are now ready to use VS Code for development!

