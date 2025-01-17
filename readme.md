# Setting Up a Data Science or Machine Learning Project with VSCode, Conda, and Git/GitHub

This is a beginner's guide that will walk you through the process of setting up a scientific data science or machine learning project using Visual Studio Code (VSCode), Conda (Anaconda), and Git/GitHub. This setup ensures reproducibility and easy collaboration, making it ideal for both beginners and professionals.


## **1. Install the Required Tools**

Before you start, make sure you have the following tools installed on your machine:

1. **Visual Studio Code (VSCode)**: Download and install from [VSCode official website](https://code.visualstudio.com/).
2. **Anaconda (or Miniconda)**: Download and install from [Anaconda website](https://www.anaconda.com/). Miniconda is a lighter version if you prefer a more minimal setup.
3. **Git**: Download and install from [Git official website](https://git-scm.com/).


## **2. Set Up Your Project Directory**

Organizing your project structure is important for readability and collaboration. Follow these steps to create a clean project directory in VSCode:

1. Create a directory for your project, e.g., `my_project`.
2. Open VSCode.
3. Click on **File** -> **Open Folder** and select your project directory (`path/to/my_project`).

Create the following folder structure inside your project directory:

```
my_project/
│
├── data/               # Raw and processed data
├── notebooks/          # Jupyter notebooks
├── src/                # Source code
│   ├── __init__.py     # Makes src a package
├── tests/              # Test scripts
├── results/            # Analysis results
├── environment.yml     # Conda environment file (we'll create this later)
├── .gitignore          # Files to ignore in Git (we'll create this later)
├── README.md           # Project overview
├── LICENSE             # Project license
└── requirements.txt    # Pip dependencies (we'll create this later)
```


## **3. Create a Conda Environment**

Conda helps manage your project’s dependencies and ensures a consistent development environment. Here’s how to create a Conda environment for your project:

**Before starting**: If Conda is properly installed it will be recognized by VSCode. This can be checked by opening a new terminal in VSCode and running `conda --version`. If Conda is not recognized, you may need to add the Conda path to your system environment variables.

1. Open the **Terminal** in VSCode by clicking **Terminal** -> **New Terminal**.
2. Create a new Conda environment:

   ```bash
   conda create --name my_project_env python=3.11
   ```

   Replace `my_project_env` with a name of your choice, and select the Python version (e.g., 3.11).

3. Activate the environment:

   ```bash
   conda activate my_project_env
   ```

4. Verify the environment is activated:

   ```bash
   conda info --envs
   ```

   The activated environment will have a `*` next to its name:

   ```bash
    conda environments:

        base           /home/username/Anaconda3
        my_project_env   * /home/username/Anaconda3/envs/myenvironment
   ```
   
   If the base environment is still active(`*` is next to `base`), run the following command to initialize Conda:

   ```bash
   conda init
   ```

   Then close the terminal, open a new one, reactivate the environment, and verify again. For the last two steps run:

    ```bash
    conda activate my_project_env
    conda info --envs
    ```

5. Install essential Python packages for data science and machine learning:

   ```bash
   conda install numpy pandas matplotlib scikit-learn scipy
   pip install jupyterlab
   ```

6. Verify the installed packages:

   ```bash
   conda list
   ```

   This will list all the installed packages in your environment.


## **4. Select the Conda Interpreter**

VSCode needs to know which Python interpreter to use (in this case, the one in your Conda environment):

1. Press `Ctrl+Shift+P` to open the Command Palette.

2. Search for `Python: Select Interpreter`.

3. Choose your Conda environment from the list (it will have a Python version, environment name, and a path like .../envs/my_project_env/bin/python).

> Note: An environment is a heavyweight object that includes the Python interpreter, packages, and dependencies. It’s a good practice to create an environment only when needed. One environment can be used for multiple projects if they have the same dependencies but it requires careful management.


## **5. Initialize a Git Repository**

Version control helps track changes and facilitates collaboration. Follow these steps to set up Git for your project:

1. Initialize a Git repository:

   ```bash
   git init
   ```

2. Create a `.gitignore` file to exclude unnecessary files from version control. Here’s an example:

   ```
   __pycache__/
   *.pyc
   *.ipynb_checkpoints
   data/
   results/
   ```

3. Add and commit your project files:

   ```bash
   git add .
   git commit -m "Initial commit"
   ```


## **6. Push to GitHub**

Now that your project is version-controlled, it’s time to upload it to GitHub for sharing and collaboration:

1. Create a new repository on [GitHub](https://github.com/).
2. Link your local repository to GitHub:

   ```bash
   git remote add origin https://github.com/yourusername/project_name.git
   git branch -M main
   git push -u origin main
   ```

> **Note**: Change `yourusername` to your GitHub username and `project_name` to your repository name.

3. Your project is now live on GitHub, ready for collaboration!

> **Tip**: You can also use VSCode’s built-in Git support for easy GitHub integration. Just press **Ctrl+Shift+G** to access the Source Control panel.


## **7. Export Environment Files**

To ensure that others can replicate your environment, export your environment configuration:

1. Export the Conda environment:

   ```bash
   conda env export --no-builds > environment.yml
   ```

2. For pip-installed packages, generate a `requirements.txt` file:

   ```bash
   pip freeze > requirements.txt
   ```

3. Commit the environment files to Git:

   ```bash
   git add environment.yml requirements.txt
   git commit -m "Add environment files"
   git push
   ```
    or by using VSCode's Source Control panel.

> **Tip**: Be sure to update these files whenever you add or remove packages.


## **8. Useful Resources**

Here are some resources to help you learn more:

1. Learn more about Conda environments: [Conda Getting Started Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html)
2. Explore more about GitHub: [GitHub Hello World Guide](https://docs.github.com/en/get-started/start-your-journey/hello-world)
3. Learn how to use Git source control in VSCode: [VSCode Source Control Guide](https://code.visualstudio.com/docs/sourcecontrol/overview)