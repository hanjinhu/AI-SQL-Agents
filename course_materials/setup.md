# Project Setup

## SQL agent prerequisites: Python, SQL, and LLM fundamentals required

To complete this course successfully, you will need knowledge of the following:

* Basic Python programming:
  * Functions and statements
  * Working with libraries and modules
  * DataFrame objects
  * Set and activate a virtual environment
* Basic SQL knowledge
* Basic understanding of LLMs are and their capabilities

## Python environment setup for SQL AI agents: Complete installation guide

Setting up a Python environment is crucial for running the code in this course. This section focuses on two approaches to setting a virtual environment:

* Locally with UV
* Using containerized environments such as Docker with VS Code's Dev Containers extension

If you wish to use a different approach for setting up the virtual environment, you can find the required libraries and their versions listed in the `requirements.txt` file under the `docker` folder:

```markup
./docker/requirements.txt

pandas==2.3.1

numpy==2.3.2

plotly==6.2.0

plotly-express==0.4.1

ollama==0.5.3

ipywidgets==8.1.7

jupyter==1.1.1

duckdb==1.3.2

openai==1.99.5 

pointblank==0.12.0

google-genai==1.29.0

anthropic==0.63.0
```

### Setting up a virtual environment with UV

UV is a new Python package and project manager that is extremely fast. If you don't have UV installed, go to the [UV project documentation](https://docs.astral.sh/uv/getting-started/installation/) and follow the installation guide based on your operating system.

Note that using UV is not a requirement to set up the virtual environment; it is just super fast. If you wish, you can simply use pip instead.

Let's start by setting up the virtual environment with the uv venv command:

`uv venv sql-ai-venv --python 3.11`

In this case, we named the virtual environment sql-ai-venv and the Python version as 3.11.

Next, let's activate the virtual environment:

`source sql-agent-venv/bin/activate`

Last but not least, let's install the required libraries using the `requirements.txt` file under the `docker` folder:

`uv pip install --no-cache-dir -r ./docker/requirements.txt`

You can verify that all the packages were installed by using the following command:

`uv pip list `

Or filter for a specific library with the `grep` command:

`uv pip list | grep openai`

This should return the following output:

```markup
Using Python 3.11.12 environment at: sql-ai-venv

openai                    1.99.5
```

### Setting up a virtual environment with Docker, VS Code, and the Dev Containers extension

In this section, we will walk through the process of setting up the course environment inside a container using Docker and the Dev Containers extension in VS Code.

**Prerequisites**

To launch the course repository inside a container, you will need the following:

* VS Code
* Docker Desktop
* Docker Hub account
* Dev Containers extension for VS Code

**Installing VS Code**

* Visit the VS Code website
* Click the Download button (highlighted in purple in the screenshot)
* Follow the installation instructions for your operating system

![Visual Studio Code website promotes itself as an open source AI code editor. The page features a download button for macOS and a dark-themed code snippet display.](https://media.licdn.com/dms/image/v2/D4E0DAQFb_Xk8tx_D4g/learning-article-inline-scale_1000_2000/B4EZl5K6UUKcAU-/0/1758674528828?e=1773244800&v=beta&t=PpDNKK4hCXKiBR4SmJu8FN8ruaDjbz_P-dy6VMBQCyU)

**Installing the Dev Containers extension**

* In VS Code, click the Extensions icon on the left sidebar (purple arrow in the screenshot)
* In the search bar, type Dev Containers (yellow)
* From the search results, select the extension and review the details
* Click Install (green)

![Screenshot of Visual Studio Code showing the ](https://media.licdn.com/dms/image/v2/D4E0DAQHSPynrbKOZ1g/learning-article-inline-scale_1000_2000/B4EZl5L0UNHEAU-/0/1758674765694?e=1773244800&v=beta&t=cTzH1a__bOcSU0K87EAaOPLSpG33cTKqkDU5wJo1RBk)

**Installing Docker Desktop**

* Visit the Docker website
* Download the appropriate installer for your operating system
* Follow the installation steps

![Web page for installing Docker Desktop on Mac, detailing terms and subscription for large enterprises. Includes download buttons for Apple silicon and Intel chip versions.](https://media.licdn.com/dms/image/v2/D4E0DAQHmL7sU7CQUGQ/learning-article-inline-scale_500_1000/B4EZl5L_6SIQAc-/0/1758674813323?e=1773244800&v=beta&t=02QlJ3jxaCWNKZK4AZellyQCFfnKn9hNXOLS27Pylts)

Note: Docker Desktop is free for personal use but requires a license for commercial use. For further information, please refer to [https://www.docker.com/pricing/](https://www.docker.com/pricing/).

### Creating a Docker Hub account

To pull the course image, you will need a Docker Hub account.

* Go to the [Docker Hub website](https://hub.docker.com/)
* Click Sign Up and follow the instructions to create your account

### Launching the course repo in a container

The course repository includes the following configuration folders:

* `.devcontainer<span> </span>`— Dev Container settings
* `.vscode` — VS Code settings
* `docker` — Docker-specific configuration

![Screenshot of a directory structure with various folders, including ](https://media.licdn.com/dms/image/v2/D4E0DAQHY2J1EZjJmEQ/learning-article-inline-scale_1000_2000/B4EZl5MirBHcAU-/0/1758674955462?e=1773244800&v=beta&t=cDSTfe4fFBrCUPdM3-xAA9PwYnZmoapaDlPUgfIRlRo)

The `devcontainer.json` file inside the `.devcontainer` folder defines:

* Container settings
* VS Code settings and extensions to install
* Environment variables

**Step 1: Verify Docker installation.**

Before launching the repository in a container, ensure that Docker Desktop is installed and running in the background. You can confirm this by running the following command:

`docker --version`

A successful installation should return the Docker version and build, for example:

`Docker version 28.3.3, build 980b856`

**Step 2: Log in to Docker Hub.**

When the Dev Containers extension first launches the repository, it will check for the course image locally. If the image is not found, Docker will attempt to pull it from the default container registry.

To log in to Docker Hub, run:

`docker login`

If successful, you will see output similar to:

```markup
Authenticating with existing credentials... [Username: YOUR_USER_NAME]

i Info → To login with a different account, run 'docker logout' followed
by 'docker login'

Login Succeeded
```

**Step 3: Open the repository in a dev container.**

* Open the course repository folder in VS Code
* Click the `Open a Remote Window` button (purple in the screenshot below)
* From the Dev Containers menu, select `Reopen in Container` (yellow)

![VS Code interface showing a 'Reopen in Container' option highlighted in the command palette. Side icons for file, search, and extensions are visible. The overall tone is technical and professional.](https://media.licdn.com/dms/image/v2/D4E0DAQENPDqPe-cqWg/learning-article-inline-scale_1000_2000/B4EZl5Nf.OIUAU-/0/1758675206413?e=1773244800&v=beta&t=Tl4k4jhH_IgYLVFuKmH9RjIc1O3zXVKpuO2p8moszxE)

**Step 4: Wait for the container to build.**

If this is your first time launching the repository, VS Code will download the course image in the background. This may take several minutes.

Once the container is running, you should see:

* A container status indicator next to the `Open a Remote Window` button (purple, below)
* The course container has a Python virtual environment set, and by default, it is activated (`python-3.11-dev`, yellow)

![A Visual Studio Code terminal window showing a Python 3.11 development environment. The terminal prompt displays the current directory and Git branch.](https://media.licdn.com/dms/image/v2/D4E0DAQGxc8TREo564w/learning-article-inline-scale_1000_2000/B4EZl5N9k3KQAU-/0/1758675327700?e=1773244800&v=beta&t=A7hqTak0orLYiV2Ulmz87H2Z87I6s-B8NMS-D6khy64)

### Course image settings

The course image is published on Docker Hub as:

`docker.io/rkrispin/lang-to-sql`

It is available in two versions:

* `arm64.0.0.1` for machines with ARM processors (for example, Apple silicon)
* `amd64.0.0.1` for machines with Intel x86 processors

Default configuration

By default, the `devcontainer.json` file points to the `arm64.0.0.1` image:

```markup
{

  "image": "docker.io/rkrispin/lang-to-sql:arm64.0.0.1"

}

If you are running on an Intel-based machine, update the image reference
to:

{

"image": "docker.io/rkrispin/lang-to-sql:amd64.0.0.1"

}
```

**Docker configuration files**

The repository also includes Docker configuration files under the docker folder:

* `build_docker.sh` — Bash script to build the Docker image
* `Dockerfile` — Instructions for building the image
* `requirements.txt` — Python dependencies installed in the container

## Codespaces explainer

GitHub Codespaces enables you to open a GitHub repository inside VS Code, running directly in your browser on a GitHub-hosted virtual machine.

This guide provides step-by-step instructions for setting up and running the course repository inside GitHub Codespaces. By default, it launches VS Code with the course configuration inside a container defined by the Dev Containers config file: `.devcontainer/devcontainer.json`.

Important: GitHub Codespaces does not support running LLMs locally with Docker Model Runner.

## Prerequisites

* Fork the course repository (or clone it locally and push it to your own GitHub account)

## Setting

### Step 1: Setting API keys as secrets

Throughout the course, we will use the following LLM APIs:

* OpenAI
* Google Gemini
* Anthropic Claude

GitHub lets you securely store API keys as secrets, which can be accessed by your codespace during runtime.

To add API keys as secrets in your repository:

* Open the `Settings` tab of your repository (marked in yellow)
* Select `Secrets and variables` in the left-hand menu (purple)
* Choose the `Codespaces` submenu (green)
* Click the `New repository secret` button (red)

![Image of a GitHub repository settings page with a dark theme. The ](https://media.licdn.com/dms/image/v2/D4E0DAQFU3cIlDu00MA/learning-article-inline-scale_1000_2000/B4EZl5QjRtHIAU-/0/1758676006437?e=1773244800&v=beta&t=KyMIueKRODmwEJQe_Cu7FEJqf_IMHt7Wm4SiJb7XU0c)

Next:

* Enter a name for your secret (purple)
* Paste the API key in the value field (green)
* Click `Add secret` (yellow)

![Image of a GitHub Codespaces interface for adding a new secret. ](https://media.licdn.com/dms/image/v2/D4D0DAQEnKP7hEZqRfA/learning-article-inline-scale_1000_2000/B4DZnLVGY.HsAY-/0/1760052930714?e=1773244800&v=beta&t=M-Mb4VXxufHtXhjY7nXAf-bEazRWOJbrdVQ5UN0fnLg)

When complete, you should see your secret listed (yellow):

![GitHub settings page showing ](https://media.licdn.com/dms/image/v2/D4E0DAQH7UJsW7h1XVw/learning-article-inline-scale_1000_2000/B4EZl5SFl6GYAU-/0/1758676409339?e=1773244800&v=beta&t=umt7XZqklJCQbmqRhEU48emjDdZnHW76oj_cKzro0G8)

Repeat the same steps to add additional secrets.

### Step 2: Launch the repository inside GitHub Codespaces

Once your API keys are set as Codespaces secrets, you are ready to launch the repository:

* Go to the `Code` tab (purple)
* Click the green `Code` button (yellow)
* Select the `Codespaces` tab (orange)
* Click `Create codespace on main`

![GitHub repository webpage titled ](https://media.licdn.com/dms/image/v2/D4E0DAQELxi1QhWn-Qg/learning-article-inline-scale_1000_2000/B4EZl5SiM8GUAc-/0/1758676526451?e=1773244800&v=beta&t=cpKCTF_3MKRyfMss2GWAcLVfQaJlkLXzjjMnqbWUkDU)

This will open a VS Code instance in your browser.

* The first launch may take several minutes while the course image is pulled from Docker Hub
* You can track progress by clicking the `Building codespace…` link (purple)
* This will open the terminal (green), where you can see the image download progress

![Screenshot of Visual Studio Code showing terminal output with Docker setup details. Highlighted text indicates successful Docker initialization. The interface is dark-themed with a 'Welcome to Copilot' message on the right.](https://media.licdn.com/dms/image/v2/D4E0DAQF0ASStiE0MNg/learning-article-inline-scale_1000_2000/B4EZl5TGCcKUAU-/0/1758676673244?e=1773244800&v=beta&t=F732Ql-GDSLcX5u7Cuhd-J44GNeYXpM4NfrNQpi7rUA)

Once the Codespace is ready, you can start working with the repository.

If you’re using Jupyter notebooks, make sure to select the correct virtual environment:

* Click `Select Kernel` (purple)
* Choose `python-3.11-dev` Python virtual environment (green)

![Image of a code editor showing a document titled ](https://media.licdn.com/dms/image/v2/D4E0DAQE82U1zvqiolQ/learning-article-inline-scale_1000_2000/B4EZl5TbJWGUAU-/0/1758676759914?e=1773244800&v=beta&t=5EZYRfdhIOL4QqCDYq3z5gWJoNQnBqSzUR-UprawC6Y)

### Step 3: Stop or delete a codespace

When you finish working, don’t forget to stop or delete your Codespace to free up resources.

To do this:

* Go to the `Code` tab.
* Click the green `Code` button (purple).
* Under the `Codespaces` tab, you’ll see all active sessions (green).
* Click the … menu next to the active instance.
* Select `Stop codespace` (light blue arrow) or `Delete` (red arrow).

![GitHub repository interface with a file list and branches. A pop-up shows ](https://media.licdn.com/dms/image/v2/D4E0DAQEcmAwqBd2iIQ/learning-article-inline-scale_1000_2000/B4EZl5T7S6IwAU-/0/1758676891332?e=1773244800&v=beta&t=HnbCQUPFVWl54PAjMMkAHehU_5HSIc4PhfEAEYM4NKA)

## API key setup guide: OpenAI, Google Gemini, and Anthropic authentication

Throughout the course, we will review how to use different LLMs via their APIs. In this document, we will review how to set up API keys for authenticating with the following large language model (LLM) APIs:

* OpenAI
* Google Gemini
* Anthropic Claude

*Important: the three API providers are a paid service. The Google Gemini API has a free tier with limited usage. Please check the API documentation for more information.*

### Setting up an OpenAI API key

To create an API key for the OpenAI API:

* Go to the [OpenAI API website](https://openai.com/api/) and log in with your credentials
* Click the Settings button in the top-right corner (green in the screenshot)
* From the left-hand menu, select API keys (yellow)
* Click `+ Create new secret` key (purple)

![A dark-themed API keys management dashboard displaying a list of keys with details like name and date. Highlighted options include creating a new secret key.](https://media.licdn.com/dms/image/v2/D4E0DAQFJUJteTfGv2Q/learning-article-inline-scale_1000_2000/B4EZl8VLrWIUAU-/0/1758727552156?e=1773244800&v=beta&t=d6RMQWP0h68anag7Tn5f40ZWzu12a-uaISMg70xu9ng)

Next, configure your new key:

* (Optional) Add a name: for example, `LinkedIn Learning - SQL AI Agent (purple)`
* Select the project the key belongs to (green)
* Click Create secret key (yellow)

![A dark-themed interface showing an ](https://media.licdn.com/dms/image/v2/D4E0DAQFAvQioJTqilQ/learning-article-inline-scale_1000_2000/B4EZl8VVVaIQAU-/0/1758727591976?e=1773244800&v=beta&t=Z-QyNq8WVPi2o6xOErmy3RXYH-shtxexlFuvGsLk0G0)

Finally, your new API key will be displayed:

* Copy the key using the copy button (yellow)
* Save it in a secure location (for example, password manager or environment variables file)

![A dark-themed web interface showing an API key management page. A pop-up window in the center highlights a newly generated API key with a 'Copy' button next to it, emphasizing security instructions. The background lists existing projects and keys. The tone is technical and informative.](https://media.licdn.com/dms/image/v2/D4D0DAQEoUba47GVLOQ/learning-article-inline-scale_1000_2000/B4DZnLbI3jGsAY-/0/1760054513773?e=1773244800&v=beta&t=AUMuHHzun6dRSa29JTQ-b2-7DHD0bnNtDCAn-6DRwWI)

*Important: After closing this window, you cannot view the key again. If you lose it, delete the old key from the API keys menu and create a new one.*

### Setting up a Google Gemini API key

To create an API key for the Google Gemini API:

* Go to the [Google AI Studio website](https://aistudio.google.com/app/apikey) and log in with your credentials
* Select the API keys on the left menu (yellow in the screenshot)
* Click `+ Create API key` (purple)

![Google AI Studio's API Keys page. Code snippet in dark mode for testing the Gemini API is shown. A ](https://media.licdn.com/dms/image/v2/D4E0DAQELOKnSnG9upQ/learning-article-inline-scale_1000_2000/B4EZl8V24tIoAU-/0/1758727729169?e=1773244800&v=beta&t=J0054vTdcJx-lcZgtX3IZ1godz9EWOGocAw9wun6hSQ)

Next, configure your new key:

* Select the project the key belongs to (yellow)
* Click on the `Create API key in existing project` button (yellow)

![](https://media.licdn.com/dms/image/v2/D4E0DAQE4CBazj07y5A/learning-article-inline-scale_1000_2000/B4EZl8WS3kIIAY-/0/1758727843980?e=1773244800&v=beta&t=dMsOpvyeA-9tpYkFWPcm251w0NaqCl7VUoyTlYMVKC8)

Finally, your new API key will be displayed:

* Copy the key using the copy button (purple)
* Save it in a secure location (for example, password manager or environment variables file)

![A dark-themed Google AI Studio interface displays a generated API key in a dialog box with a ](https://media.licdn.com/dms/image/v2/D4D0DAQHudSJS8ajdow/learning-article-inline-scale_1000_2000/B4DZnLjKW2HsAU-/0/1760056616965?e=1773244800&v=beta&t=EFDYnN4HngtG9MEE24xJoip4SSAdgJo9L3OZAqf0zB8)

*Important: After closing this window, you cannot view the key again. If you lose it, delete the old key from the API keys menu and create a new one.*

### Setting up an Anthropic API key

To create an API key for the Anthropic API:

* Go to the [Anthropic user dashboard](https://console.anthropic.com/dashboard) and log in with your credentials
* Click on the `Get API key` (purple)

![Create a prompt,](https://media.licdn.com/dms/image/v2/D4E0DAQHJiwfN2YLowA/learning-article-inline-scale_1000_2000/B4EZl8uaHYKsAU-/0/1758734164836?e=1773244800&v=beta&t=z_PucYq7Eu-hex9zxxUXi5XML8ThNnZ9UXMEVXEFcgY)

Next, click on the `Create key` button (purple).

![Dashboard displaying API keys for an organization, with key details, creation dates, and costs. A ](https://media.licdn.com/dms/image/v2/D4D0DAQGEr36dJ9w86A/learning-article-inline-scale_1000_2000/B4DZnLjX_YKoAY-/0/1760056672843?e=1773244800&v=beta&t=WP6i5zqMwJd8iKLS5cuSNuI4vFon77Hm-v5Wt9f9GB0)

Next, configure your new key:

* Select the workspace (purple)
* Select the API key name, for example, `LinkedIn Learning - SQL AI Agent` (yellow)
* Click on the `Add` button (yellow)

![API keys](https://media.licdn.com/dms/image/v2/D4E0DAQFO_dXI_01iPA/learning-article-inline-scale_1000_2000/B4EZl8u4X7IwAU-/0/1758734288866?e=1773244800&v=beta&t=IrjSeWycTYNyNdT9uzX6K4T1047u6mW1P-8T6LA3gh8)

Finally, your new API key will be displayed:

* Copy the key using the copy button (green)
* Save it in a secure location (for example, password manager or environment variables file)

![A dark-themed interface displays an API key management page. A central pop-up window shows an API key with a ](https://media.licdn.com/dms/image/v2/D4D0DAQHVQBIXA8cODQ/learning-article-inline-scale_1000_2000/B4DZnLji_XG8AU-/0/1760056717790?e=1773244800&v=beta&t=3KRMT8v9WL0AIcgR5X-AnhK1ruPh6cOTMpPpUWwhWMM)

*Important: After closing this window, you cannot view the key again. If you lose it, delete the old key from the API keys menu and create a new one.*
