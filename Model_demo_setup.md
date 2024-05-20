# GT4SD Generative AI Model Demonstration Setup

<img width="596" alt="genai" src="https://github.com/acceleratedscience/Demonstrations/assets/30096303/8f5dd95f-15a8-4307-84fe-bf518ac76f31">


1.  **Step 0: Before you start**<br>
Ensure you're running Python 3.10 or 3.11. There's multiple ways of updating Python, we'll use pyenv.

    > **Note:** Due to an issue with one of our dependencies, Python 3.12 is not yet supported.

        git clone https://github.com/pyenv/pyenv.git ~/.pyenv
        pyenv install 3.10

1.  **Step 1: Set up your virtual environment** (optional)<br>

        python -m venv ~/ad-venv
        source ~/ad-venv/bin/activate

    > **Note:** To exit the virtual environment, you can run `deactivate`

2.  **Step 2: Installation**

         pip install -U git+https://github.com/acceleratedscience/open-ad-toolkit.git@new_models

   To Check if you have access to aws run :
   `sky check`

   it should tell you what services ar eenabled, for this demonstration we are working with aws. If you do not have aws cli enabled then make sure it is before runnign th ecommand.

<br>

# Getting Started - CLI

-   **Enter the virtual environment**
    
    > **Note:** If you just installed OpenAD, you probably already activated the virtual environment.

        source ~/ad-venv/bin/activate

-   **Enter the command shell**

        openad

    <!-- ![Landing](assets/screenshot-landing.png) -->
    <!-- <a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/screenshot-landing.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/screenshot-landing.png" /></a> -->

-   **Exit the command shell**<br>
    Hit `ctrl+c` or run:

        exit

-   **Run a single command from outside the command shell**

        openad <command>

-   **Exit the virtual environment**<br>

        deactivate

<br>

# Getting Started - Jupyter

## Setting up Jupyter

The following commands only need to be run once after installation:

1.  **Activate your virtual environment**

    > **Note:** If you just installed OpenAD, you probably already activated the virtual environment.

        source ~/ad-venv/bin/activate

1.  **Create an iPython kernel**<br>
    This ports your virtual environment to Jupyter.

        python -m ipykernel install --user --name=ad-venv
    
    > **Note:** To list your installed iPython kernels, you can run `jupyter kernelspec list`, and to remove the kernel you can run `jupyter kernelspec uninstall ad-venv`

1.  **Install the magic commands**<br>
    This enables OpenAD commands to be run within a Jupyter Notebook.

        init_magic
    
    <details>
    <summary><b>Alternative:</b> Manually add magic commands</summary>
    <div markdown="block">

    If you don't want to activate magic commands in all Notebooks, you can instead activate them for individual Notebooks.
    - Run `init_examples`
    - Copy the file `~/openad_notebooks/openad.ipynb` to the same directory as the Notebook you wish to activate.
    - In your Notebook, run this inside a code cell: `!run openad.ipynb`
	
    </div>
    </details>


2.  **Install example Notebooks**<br>
    This installs our example Notebooks at `~/openad_notebooks`.
    
        init_examples

## Launching OpenAD in Jupyter

1.  **Open any Notebook**<br>
    The following command will open up the example Notebook:

        jupyter lab ~/openad_notebooks/Table_of_Contents.ipynb

2.  **Select the kernel**<br>
    Make sure to select the "ad-venv" iPython kernel. You can do this under _Kernel > Change Kernel_, or in the latest versions of Jupyter by clicking the kernel name in the top right hand corner. If you don't see your iPython kernel, make sure you followed the Jupyter Setup instructions listed above.

<figure>
    <a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/jupyter-notebook-kernel.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/jupyter-notebook-kernel.png"></a>
    <figcaption align="center" style="font-size:0.9em;opacity:.6;margin-top:-30px;margin-bottom:50px"><i>Jupyter Notebook</i></figcaption>
</figure>
<figure>
    <a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/jupyter-lab-kernel.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/jupyter-lab-kernel.png"></a>
    <figcaption align="center" style="font-size:0.9em;opacity:.6;margin-top:-30px;margin-bottom:50px"><i>Jupyter Lab</i></figcaption>
</figure>

1.  **Magic Commands**<br>
    Magic commands let you run terminal commands from within Jupyter. They are invoked by the `%openad` prefix. All OpenAD CLI commands can be accessed like this. For example:<br>

        %openad list files

<br>

# Interacting with the Toolkits

OpenAD integrates with `DS4SD`, `RXN`, and has placeholder support for `GT4SD` and `ST4SD`.

<div class="notice" style="margin-top: 16px;" markdown="block">

**&#x26A0; Reminder:** when running commands from Jupyter, prepend them with `%openad`

</div>

### Registration

Before you can interact with the toolkits, you'll need to register with each individual toolkit.

<details>
<summary>Register with DS4SD (Deep Search)</summary>
<div markdown="block">

1. First, you'll need to generate an API key on the Deep Search website.

    - Visit the Deep Search website and create an account:<br>
      [deepsearch-experience.res.ibm.com](https://deepsearch-experience.res.ibm.com)<br>
    - Once logged in, click the Toolkit/API icon in the top right hand corner, then open the HTTP section
    - Click the "Generate new API key" button<br>
      <br>
      <!-- ![Landing](assets/ds4sd-api-key.png) -->
      <a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/ds4sd-api-key.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/ds4sd-api-key.png" /></a>

1. Once inside the OpenAD client, you'll be prompted to authenticate when activating the Deep Search (DS4SD) toolkit. When running `set context ds4sd` :

   - **Hostname:** [https://sds.app.accelerate.science](https://sds.app.accelerate.science)
   - **Email:** Your email
   - **API_key:** The DS4SD API key you obtained following the instructions above.

1. You should get a message saying you successfully logged in.

    > **Note:** Your DS4SD auth config file is saved as `~/.openad/deepsearch_api.cred`. If you ever want to reset your DS4SD login information you can run `set context ds4sd reset`, or you can delete this file.<br>

</div>
</details>

<details>
<summary>Register with RXN</summary>
<div markdown="block">

1. First, you'll need to generate an API key on the RXN website.

    -   Sign up for an RXN account at [rxn.app.accelerate.science](https://rxn.app.accelerate.science)
    -   Obtain your API key by clicking the user profile icon in the top right hand corner and select "My profile".<br>
        <br>
        <!-- ![Landing](assets/rxn-api-key.png) -->
        <a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/rxn-api-key.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/rxn-api-key.png" /></a>

1. When setting the context to RXN using `set context rxn` you'll be prompted to create a new auth configuration file:

    -   **Hostname:** [https://rxn.app.accelerate.science](https://rxn.app.accelerate.science)<br>
    -   **API_key:** The RXN API key you obtained following the instructions above.

1. You should get a message saying you successfully logged in.<br>

    > **Note:** Your RXN auth config file is saved as `~/.openad/rxn_api.cred`. If you ever want to reset your RXN login information you can run `set context rxn reset`, or you can delete this file.<br>

</div>
</details>

### Adding a Toolkit

First install the toolkit, then set the context to this toolkit.

    add toolkit ds4sd
    set context ds4sd

### Sample Commands

    # DS4SD
    display all collections

    # RXN
    list rxn models

### Running Bash Commands (CLI)

To run a command in bash mode, prepend it with `openad` and make sure to escape quotes.

    openad show molecules using file \'base_molecules.sdf\'

<br>

# AI Assistant

To enable our AI assistant, you'll need an account with OpenAI. There is a one month free trial.

> **Note:** watsonx coming soon

1. Go to [platform.openai.com](https://platform.openai.com) and create an account

2. Click on the profile icon in the top right and choose "View API keys"

3. Create a new key

4. Run `tell me` to be prompted for your OpenAI API credentials


<!-- ![Landing](readme/openai-api-key.png) -->

<a href="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/openai-api-key.png" target="_blank"><img src="https://raw.githubusercontent.com/acceleratedscience/open-ad-toolkit/main/assets/openai-api-key.png" /></a>

<br>

# For Developers

OpenAD is fully open source and we encourage contributions. We plan to provide documentation on how to integrate your own toolkits in the future.

If you have any questions in the meantime, please [reach out]({% link about.md %}).

## Installation for Development

<details>
<summary>Install using the setup wizard (uses poetry)</summary>
<div markdown="block">

1.  **Step 1: Download the repo**

        git clone https://github.com/acceleratedscience/open-ad-toolkit.git

    > **Note:** To download a specific branch, you can run instead:<br>
    `git clone -b <branch_name> https://github.com/acceleratedscience/open-ad-toolkit.git`

1.  **Step 2: Launch the setup wizard**

        cd open-ad-toolkit
        ./setup.sh

</div>
</details>

<details>
<summary>Install using pip</summary>
<div markdown="block">

1.  **Step 0: Before you start**<br>
Ensure you're running Python 3.10.10 or above. There's multiple ways of doing this, we'll use pyenv.

        git clone https://github.com/pyenv/pyenv.git ~/.pyenv
        pyenv install 3.10

1.  **Step 1: Set up your virtual environment** (optional)<br>

        python -m venv ~/ad-venv
        source ~/ad-venv/bin/activate

    > **Note:** To exit the virtual environment, you can run `deactivate`

1.  **Step 2: Download the repo**

        git clone https://github.com/acceleratedscience/open-ad-toolkit.git

    > **Note:** To download a specific branch, you can run instead:<br>
    `git clone -b <branch_name> https://github.com/acceleratedscience/open-ad-toolkit.git`

1.  **Step 2: Install the requirements**

        cd open-ad-toolkit
        pip install -e .
    
    > **Note:** The -e flag stands for "editable". This means that instead of copying the package's files to the Python site-packages directory as in a regular installation, pip creates a symbolic link (symlink) from your package's source code directory into your Python environment.<br>This way you can make changes to the source code of the package, and those changes are immediately reflected in your Python environment. You don't need to reinstall the package every time you make a change.

</div>
</details>


## Testing a branch

To do a regular install from a particular branch, you can run:

    pip install git+https://github.com/acceleratedscience/open-ad-toolkit.git@<branch_name>

<br>

# Installing on Windows

In order to run OpenAD on Windows 11, you will need to install the Ubuntu WSL package ("Windows Subsystem for Linux").

## Before you start

-   **Verify Windows version**<br>
    To check if you are running Windows 11 or later, press `Win` + `R`, type "winver", and press `Enter`. A window will open showing your Windows version.

-   **Verify WSL**<br>
    To check if you already have WSL installed, run `wsl -l -v` into the terminal. To see more information about your current version of Ubuntu, run `lsb_release -a`

## Installing WSL

Install WSL and create a user called 'openad' or one of your choosing.

    wsl --install Ubuntu-22.04

**Optional:** To setup an Ubuntu Python environment from scratch, continue to [Linux Notes](#linux-notes)

<br>

# Linux Notes

If you wish to setup an Ubuntu Python environment from scratch, run:

    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt update
    sudo apt install python3.11-full
    sudo apt install python3-pip
    sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 100
    sudo pip install pip --upgrade

If you get an error when running `init_magic`, you may first need to setup the default iPython profile for magic commands.

    ipython profile create
