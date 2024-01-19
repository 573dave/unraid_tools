# Installing CrewAI on Unraid

## Introduction
This guide will walk you through the process of installing VS Code Server on an Unraid server and then installing CrewAI in a new project and virtual environment (venv).

## Prerequisites
Before you begin, make sure you have the following prerequisites:
- An Unraid server set up and running.

## Step 1: Install VS Code Server
1. Open the Unraid web interface and go to the "Apps" tab.
2. Search for "VS Code Server" and click on the "Install" button. linuxserver:code-server is typically a good choice.
3. Follow the on-screen instructions to complete the installation. Set your password and sudo password for security, change the port if need be, and hit apply. By default the container mounts the configuration folder to /mnt/user/appdata/code-server and stores your workspace there as well in /workspace.
4. Open VS Code Server by accessing it through your web browser (http://server:8443 if you used the default port, default password is 'password').

## Step 2: Udpate and Install Python3 and Pip
1. Click View, Terminal at the top.
2. Run sudo apt-get update. It will ask for the sudo password you set.
    ``` 
    sudo apt-get update 
    ```
3. Run sudo apt-get upgrade. 
    ``` 
    sudo apt-get upgrade 
    ```
4. Run sudo apt-get install python3 python3-pip. 
    ``` 
    sudo apt-get install python3 python3-pip
    ```

## Step 3: Clone CrewAI OR pip install
### Clone 
##### I prefer cloning as it get's me all of the documentation locally, but CrewAI's readme says use pip. 
1. In the Terminal type:
    ```
    git clone https://github.com/joaomdmoura/crewAI.git
    ```
2. Click File, Open folder, Workspace, CrewAI and click Okay.
### Pip Install
1. In the File Explorer on the left, click the New Folder icon, and name your project. 
2. Click File, Open Folder, and choose Workspace, then your project name.
3. Do Step 4 (Set Up virtual environment) first, then continue.
4. Click Terminal, New Terminal at the top and run pip install crewai.
    ```
    pip install crewai
    ```

## Step 4: Set Up a Virtual Environment
1. From the CrewAI workspace, click View, Command Palette.
2. Type env and select Python:Create Environment, then Venv, then select the /usr/bin/python3 interpreter.
    - This will take some time as the venv processes crewai's pyproject.toml and installs the necessary packages to run successfully.

## Step 5: Configuration
1. Follow the [documentation](https://github.com/joaomdmoura/CrewAI/wiki) of CrewAI to configure it according to your needs.

## Unraid-CrewAI-Sample.py
1. Using the code from CrewAI's README, you can build a sample project to see how to the system works. In their example you'll need to install duckduckgo-search, langchain-commuity, and set your OpenAI API key from [here](https://platform.openai.com/api-keys). 
    ```
    pip install -U duckduckgo-search langchain-community
    ```
2. In the Explorer pane, click the New file... button and name it app.py. Copy the code from their README and paste it into the new file. I've added a slightly modified version [here](Unraid-CrewAI-Sample.py) as well.
3. On line 6, change "YOUR KEY" to the key you generated at OpenAI.
4. Press the play button (Run Python File) in the top right corner of your screen and watch as the AI iterates in your terminal.



## Resources
- [CrewAI Wiki](https://github.com/joaomdmoura/CrewAI/wiki)
