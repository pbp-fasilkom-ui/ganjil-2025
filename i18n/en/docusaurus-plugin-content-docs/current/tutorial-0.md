---
sidebar_label: Tutorial 0
sidebar_position: 2
Path: docs/tutorial-0
---

# Tutorial 0: Configuration and Installation of Git and Django

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understand basic Git commands necessary for working on an application project.
- Use basic Git commands necessary for working on an application project.
- Create a local Git repository and a remote GitHub repository.
- Add a remote between a local Git repository and a remote GitHub repository.
- Understand the concept of branching in Git and be able to perform merge request/pull request.

## Tutorial: Introduction to Git and GitHub (Skip if you already have an account)

### Introduction to Git and GitHub

This overview will introduce you to the basics of Git and the web-based platform known as GitHub.

#### Git: A Strong Version Control System

- **Git** is a version control system that allows you to track all changes made to your project over time.
- With Git, you can track all changes made to your project over time.

#### GitHub: Git-Based Collaboration Platform

- **GitHub** is a web-based platform that allows you to store, manage, and collaborate on projects using Git.
- This provides a safe way to host your project and interact with your teammates through Git.

#### Why does it matter?

- Git and GitHub plays an important role in the development of modern software and collaboration.
- Both allow teams to track changes in code, save versions, and collaborate effectively in a structured manner.

With the basic understanding of Git and GitHub, you are ready to move forward in the world of software development that is collaborative and structured.

### Step 1: Creating an Account on GitHub

The next step is to create an account on GitHub, which will allow you to start collaborating on projects using Git.

1. Open the GitHub website
    - Open your web browser and access the [GitHub](https://github.com/) website.

2. Create an Account
    - On the homepage of GitHub, find the **`Sign up`** button in the upper right corner of the page.
    - Click the button to start the registration process.

3. Fill in the Registration Form
    - Fill in the registration form with the required information, such as the username you want to use, a valid email address, and a safe password.
    - Make sure to save this information safely so that you can log in to your account in the future.

4. Verify Account via Email
    - After filling in the form, GitHub will send a verification email to the email address you provided.
    - Open the email and follow the instructions to verify your account.

5. Your GitHub Account is Ready
    - After the verification is complete, you will have a GitHub account that is ready to be used for collaboration in the project and tracking changes using Git.

:::note

- A GitHub account is a gateway for collaboration in the project and storing your project on this platform.
- Make sure the registration information you provide is accurate and safe.
:::

### Congratulations, You Have Created an Account on GitHub

You have now created an account on GitHub that can be used to store the project, collaborate with others, and more.

## Tutorial: Installing an IDE

IDE (Integrated Development Environment) is a software that helps developers write, edit, and manage code. Here are the steps to install an IDE to your system.

### Step 1: Choosing a Text Editor or IDE

Choose a text editor or IDE that matches your preferences. Some popular options that you can consider include:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Sublime Text](https://www.sublimetext.com/)
- [PyCharm](https://www.jetbrains.com/pycharm/)
- [Neovim](https://neovim.io/)

### Step 2: Installing the IDE

1. Go to the official website of the IDE you have chosen.
2. Follow the instructions provided to download the installer of the IDE.
3. Run the installer and follow the instructions on the screen to complete the installation process.

### Step 3: Getting Started with the IDE

1. After the installation process is complete, open the IDE that has been installed.
2. Explore the user interface and features provided by the IDE to help you develop your project.

:::note

- Make sure you choose an IDE that matches the type of project you will be working on.
- Don't forget to explore the features and capabilities of the IDE (e.g., extensions or plugins) and use the resources available for free, such as documentation and tutorials, to improve your software development productivity.
:::

## Tutorial: Installing and Configuring Git

### Step 1: Installing Git

If Git is not installed on your system, you can follow the steps below to install it.

1. Open the Git website [here](https://git-scm.com/downloads).
2. Choose the operating system that matches (Windows, macOS, or Linux) and download the installer that matches.
3. Run the installer that has been downloaded and follow the instructions on the screen to complete the installation process.
4. In addition, don't forget to select "Git Credential Manager Core" to make Git integration with GitHub easier.

![Image of Git Credential Manage Core option](https://user-images.githubusercontent.com/5658207/140082529-1ac133c1-0922-4a24-af03-067e27b3988b.png)

### Step 2: Initial Git Configuration

After Git is installed, the following steps will help you set up your initial configuration before using Git.

1. Create a new folder/directory to store your Git project, then enter the directory.
2. Copy the path to the directory you just created.
3. Open the terminal or command prompt on your system, then navigate to the directory you just created by running the `cd <path_directory>` command.
4. Initiate a new repository with the `git init` command. This will create an empty Git repository in the directory you specified.

### Step 3: Configuring Username and Email

Before you start contributing to the repository, configure your username and email address to be associated with your commit.

Set your username and email that will be associated with your job to the repository Git you initiated with the following commands. Adjust with your username and email that you use on [GitHub](https://github.com).

```bash
git config --global user.name "<NAME>"
git config --global user.email "<EMAIL>"
```

Example:

```bash
git config --global user.name "pakbepe"
git config --global user.email "pak.bepe@cs.ui.ac.id"
```

It is important to note that the `--global` flag will change the global configuration for the entire system.

:::note
- Make sure to replace `<NAME>` and `<EMAIL>` with your information
:::

### Step 4: Configuring Authentication

To connect your Git account with your GitHub account, there is an extra configuration that you need to add. You only need to run the two commands below:

**Windows**
```bash
git credential-manager configure
git config --global credential.credentialStore wincredman
```

**Unix (macOS, Linux)**
```bash
git credential-manager configure
git config --global credential.credentialStore keychain
```

If the `git credential-manager` command doesn't work, you can try `git-credential-manager` or `git-credential-manager-core` instead.

### Step 5: Verifying Configuration

To ensure that the configuration has been set correctly on the local repository, you can run the following command.

```bash
git config --list
```
## Tutorial: Basic Git Usage

**Repository** is a place for storing software projects, which includes all revisions and changes made to the code. To execute Git commands, you can do so on the repository on GitHub, a collaborative platform for managing projects using Git.

### Step 1: Initiatilzing a Repository on GitHub

The first step in using Git is initiating a repository on GitHub to start tracking changes on your project.

1. Open the [GitHub](https://github.com) website through your web browser.

2. Create a New Repository
	- On the homepage of GitHub, create a new repository with the name `my-first-repo`.
	- Open the newly created repository. Make sure to set the project visibility as "Public" and leave the other settings at their default values.

3. Set Up Local Directory
	- Choose the local directory on your computer that has been initialized with Git. This is where you will store the local version of your project.

4. Add a `README.md` File
	- Create a new file with the name `README.md` in the local directory of your project.
	- Fill in the `README.md` file with information such as name, NPM, and class. Example:
		```md
		Name: Pak Bepe

		NPM: 2201234567

		Class: PBP KKI
		```

5. Check Status and Tracking
	- Open the command prompt or terminal, then run the `git status` command in the directory that you have chosen. The command will display the untracked files.
	- Use the `git add README.md` command to mark the README.md file as a file to be committed (tracked).

6. Commit Changes
	- Run the `git status` command again and ensure that the README.md file is marked as a file to be committed.
	- Continue with running the `git commit -m "<YOUR COMMENT>"` command to create a commit with a comment that matches the changes you have made.

:::note
This step will help you start tracking changes on your project using Git.
:::
:::tip
- **Good practice** in giving a commit comment is to explain in short what you have done on that specific commit. Usually, commit comments are written in English. One example of a commit comment that you can use for this example is `Create README.md file`.
- A good commit comment can help you and your team members understand the purpose of the change.
- **Avoid** commit comments that are too common or ambiguous, such as `Fix bugs` or `Update file`.
:::

### Step 2: Connecting Local Repository with GitHub Repository

After initializing the local repository, the next step is to connect it with the GitHub repository so that you can collaborate and store the changes on the platform.

1. Create New Main Branch
	- In the terminal or command prompt, run the `git branch -M main` command to create a new main branch with the name "main".
	- Make sure the "M" in the `-M` command is **capitalized**.

2. Connect with GitHub Repository
	- Use the `git remote add origin <URL_REPO>` command to connect the local repository with the GitHub repository.
	- Replace `<URL_REPO>` with the HTTPS URL of the repository that you have created on GitHub. Example:
		```bash
		git remote add origin https://github.com/pakbepe/test.git
		```
3. Do your First Push to GitHub
	- Finally, do your first push to GitHub with the `git push -u origin main` command.
	- This command will send all the changes that exist in the current branch (in this case, the main branch) from the local repository to the main branch on the GitHub repository.
	- If this is your first time pushing to GitHub and you are using Windows, after installing, you should see a window asking you to sign in to GitHub. Click "Sign in with your browser", then follow the instructions in the window.

4. Do a Double Check
	- Do a refresh on the repository page on GitHub, you should see the `README.md` file on your GitHub repository.

:::note
- This step is important to maintain consistency between the local repository and the GitHub repository.
- This process allows you to start collaborating and storing the project structure on the GitHub platform.
:::

### Step 3: Cloning a Repository

**Cloning** a repository is a process of duplicating all the content from the repository on the GitHub platform to the local computer. The steps are as follows.

1. Open the repository page on [GitHub](https://github.com) that you have created previously.

2. Copy the Clone URL
	- Click the **`Code`** button on the right corner of the repository page on GitHub.
	- Select the HTTPS option to copy the Clone URL.

3. Clone the Repository to the Local Computer
	- Open the terminal or command prompt in the **different** directory from the location of the local repository previously.
	- Run the `git clone <URL_CLONE>` command (replace URL_CLONE with the URL that you copied).
	- This command will duplicate all the repository to the local computer.

Currently, you have three repositories:

1. The **original repository** on your local computer.
2. The **remote repository** on GitHub that is connected to the local repository.
3. **New repository from cloning** that is connected to the GitHub repository.

:::note
- This step allows you to work with the repository in various places easily.
:::

### Step 4: Pushing Changes to a Repository

As mentioned earlier (Step 2), **push** is the process of sending changes that you have made in the local repository to the GitHub repository. The steps are as follows.

1. Open the **local repository** that you first created.

2. Change the contents of the `README.md` file by adding the Hobby attribute. For example:

	```md
	Name : Pak Bepe

	NPM : 2201234567

	Class : PBP KKI

	Hobby : Sleeping
	```

3. Do a Push to the GitHub Repository
	- Open the terminal or command prompt, then enter the local repository that you have changed.
	- Run the `git status` command to see the changes that have been made.
	- Run the `git add README.md` command to add the change to the stage that will be committed.
	- Do a commit with the `git commit -m "<YOUR COMMENT>"` command to provide a short description of the changes that you have made.
	- Finally, run the `git push -u origin <NAME_OF_BRANCH>` command to send the changes to the branch that has been chosen on the GitHub repository (replace "Name of Branch" with the target branch, for example, `main`).

4. Do a Double Check
	- Do a refresh on the page you are on, you should see the `README.md` file on your GitHub repository has been changed.

:::tip
If you want to take **all** the changes that have not been staged (marked for entry into the commit) **from the entire project directory**, run `git add .`.
:::

### Step 5: Pulling Changes from a Repository

**Pull** on a repository is the process of pulling the latest changes from the GitHub repository and merging them with the local repository.

1. Open the **local repository that you have cloned previously** in the terminal or command prompt.

2. Run the Pull Command
	- Run the `git pull origin main` command to pull the latest changes from the GitHub repository and merge them with the local repository.

3. Do a Double Check
	- Check the `README.md` file in the local repository again. You should see that your `README.md` file has displayed your hobby.

:::note
This step ensures that the local repository is always updated with the latest changes from the GitHub repository.
:::
:::tip
Doing a pull regularly is important to avoid conflicts and ensure that you work with the latest version of the project.
:::

### Step 6: Using Branches on a Repository

In this step, you will learn about the use of branches in Git. Using branches allows you to develop a feature or fix a bug in a isolated environment before merging it back to the main branch.

**What is a Branch in Git?**

- Branch in Git is an isolated part of the source code that allows independent development from features or changes.
- This allows the team to work on a feature or fix a bug without interfering with the code in the main branch.

1. Creating and Replacing a New Branch
	- In the original local repository directory (not the one that is cloned), run the `git checkout -b <NAME_OF_BRANCH>` command in the terminal or command prompt to create and switch to a new branch. Example: `git checkout -b major_branch`
	- Add the class attribute to the `README.md` file. Example:

		```md
		Name : Pak Bepe

		NPM : 2201234567

		Class : PBP KKI

		Hobby : Sleeping

		Major : Computer System Information
		```

2. Saving Changes and Pushing to GitHub
	- After adding the major attribute, save the file.
	- Do a `add`, `commit`, and `push` to GitHub with the commands that you have been using previously.
	- Run the `git push -u origin <NAME_OF_BRANCH>` command. Make sure to replace `<NAME_OF_BRANCH>` with the name of the new branch that you created.

3. Merging Branches Using Pull Requests

	- Open the page of your repository on GitHub again.
	- Automatically, a pop-up with the **`Compare & pull request`** button will appear. If not, you can press the **`Pull Request`** button and then choose the **`New pull request`** option.
	- After that, GitHub will compare the changes that exist in both branches that you want to merge.
	- If there is no conflict, press the **`Merge pull request`** button that will merge the changes from the branch that you want to merge into the main branch (`main`).
	- With the steps above, all changes from both branches will be integrated into the main branch, creating a process between the changes.

:::note
- If you want to switch between branches that already exist, run the `git checkout <NAME_OF_BRANCH>` command in the terminal. The `-b` flag in the command before the previous one was used to create a new branch and switch to it in one step.
- **Conflict** occurs when changes made to one branch conflict with changes made to another branch. For example, if two developers change the same part of the same file at the same time, Git cannot automatically decide which change should be applied.
- If there is a conflict or changes that are being merged, the platform will ask you to determine which change should be taken.
- It is **Important** to understand the concept of branching in Git, because it allows **organized and isolated development**, before all changes are combined back into the main code.
:::

## Tutorial: Installing Django and Initializing a Django Project

**Django** is a popular framework for web application development with the Python programming language. In this tutorial, you will learn the steps to install Django and initialize a demo project as a starter.

### Step 1: Creating a Directory and Enabling the Virtual Environment

1. Create a new directory with the name `mental-health-tracker` and enter it.
2. Inside the directory, open the command prompt (Windows) or terminal shell (Unix).
3. Create a virtual environment by running the following command.

	```bash
	python -m venv env
	```

4. The **virtual environment** is useful for isolating the package and dependencies from the application to avoid conflicts with other versions of the same on your computer. You can activate the virtual environment with the following command.

	- Windows:

		```bash
		env\Scripts\activate
		```

	- Unix (Mac/Linux):

		```bash
		source env/bin/activate
		```

5. The virtual environment will be activated, indicated with `(env)` on the terminal input line.

### Step 2: Setting Up Dependencies and Creating a Django Project

**Dependencies** are components or modules that a software needs to function, including libraries, frameworks, or packages. This allows developers to use existing code, speed up development, but also requires careful management to ensure the compatibility of versions between components. The use of virtual environment helps to isolate dependencies between different projects.

1. Inside the same directory, create a `requirements.txt` file and add some dependencies.

	```text
	django
	gunicorn
	whitenoise
	psycopg2-binary
	requests
	urllib3
	```

2. Install the dependencies with the following command. Don't forget to run the virtual environment first before running the command.

	```bash
	pip install -r requirements.txt
	```

3. Create a Django project named `mental_health_tracker` with the following command.

	```bash
	django-admin startproject mental_health_tracker .
	```

	:::note
	Make sure the `.` character is written at the end of the command.
	:::

### Step 3: Configuring the Project and Running the Server

1. Add the following two strings to the `ALLOWED_HOSTS` in the `settings.py` for deployment needs:

	```python
	...
	ALLOWED_HOSTS = ["localhost", "127.0.0.1"]
	...
	```

   In the context of deployment, `ALLOWED_HOSTS` works as a list of allowed hosts to access the web application. By setting the value above, you allow access from the local host, which means that only you can access it from your network. But if you are planning to deploy your application to a server, make sure to add your server's host to `ALLOWED_HOSTS`.

2. Ensure that `manage.py` file is in the active directory on your terminal. Run the Django server with the following command:

	- Windows:

		```bash
		python manage.py runserver
		```

	- Unix:

		```bash
		python3 manage.py runserver
		```

3. Open http://localhost:8000 on your web browser to see the rocket animation as a sign of the Django application that you have created successfully.

### Step 4: Stopping the Server and Deactivating the Virtual Environment

1. To stop the server, press `Ctrl+C` (Windows/Linux) or `Control+C` (Mac) on the terminal.
2. Deactivate the virtual environment with the following command:

	```bash
	deactivate
	```

	Congratulations! You have successfully created a Django application from scratch.

## Tutorial: Uploading the Project to GitHub Repository

1. Create a new GitHub repository named `mental-health-tracker` with the visibility set to public.

2. Initiate the local directory `mental-health-tracker` as a Git repository.

	:::tip
	_Hint: Remember the previous tutorial step_
	:::

3. Add a `.gitignore` file

	- Add a `.gitignore` file and fill it with the following text.

		```yaml
		# Django
		*.log
		*.pot
		*.pyc
		__pycache__
		db.sqlite3
		media

		# Backup files
		*.bak

		# If you are using PyCharm
		# User-specific stuff
		.idea/**/workspace.xml
		.idea/**/tasks.xml
		.idea/**/usage.statistics.xml
		.idea/**/dictionaries
		.idea/**/shelf

		# AWS User-specific
		.idea/**/aws.xml

		# Generated files
		.idea/**/contentModel.xml

		# Sensitive or high-churn files
		.idea/**/dataSources/
		.idea/**/dataSources.ids
		.idea/**/dataSources.local.xml
		.idea/**/sqlDataSources.xml
		.idea/**/dynamic.xml
		.idea/**/uiDesigner.xml
		.idea/**/dbnavigator.xml

		# Gradle
		.idea/**/gradle.xml
		.idea/**/libraries

		# File-based project format
		*.iws

		# IntelliJ
		out/

		# JIRA plugin
		atlassian-ide-plugin.xml

		# Python
		*.py[cod]
		*$py.class

		# Distribution / packaging
		.Python build/
		develop-eggs/
		dist/
		downloads/
		eggs/
		.eggs/
		lib/
		lib64/
		parts/
		sdist/
		var/
		wheels/
		*.egg-info/
		.installed.cfg
		*.egg
		*.manifest
		*.spec

		# Installer logs
		pip-log.txt
		pip-delete-this-directory.txt

		# Unit test / coverage reports
		htmlcov/
		.tox/
		.coverage
		.coverage.*
		.cache
		.pytest_cache/
		nosetests.xml
		coverage.xml
		*.cover
		.hypothesis/

		# Jupyter Notebook
		.ipynb_checkpoints

		# pyenv
		.python-version

		# celery
		celerybeat-schedule.*

		# SageMath parsed files
		*.sage.py

		# Environments
		.env
		.venv
		env/
		venv/
		ENV/
		env.bak/
		venv.bak/

		# mkdocs documentation
		/site

		# mypy
		.mypy_cache/

		# Sublime Text
		*.tmlanguage.cache
		*.tmPreferences.cache
		*.stTheme.cache
		*.sublime-workspace
		*.sublime-project

		# sftp configuration file
		sftp-config.json

		# Package control specific files Package
		Control.last-run
		Control.ca-list
		Control.ca-bundle
		Control.system-ca-bundle
		GitHub.sublime-settings

		# Visual Studio Code
		.vscode/*
		!.vscode/settings.json
		!.vscode/tasks.json
		!.vscode/launch.json
		!.vscode/extensions.json
		.history
		```

	- The `.gitignore` file is a configuration file used in the Git repository to specify the files and directories that should be ignored by Git.
	- The files listed in the `.gitignore` file **will not** be added to the Git control.
	- This file is created because sometimes there are files that should not be added to Git, such as temporary files, files generated during compilation, or personal configuration files.

4. Do a `add`, `commit`, and `push` from the local repository directory.

:::note
- The **`mental-health-tracker`** repository that you just created will become a starting point for the following tutorials. **The repository will continue to be used** and evolve as you follow the tutorials.
- At the end of the semester, you will see that the tutorial repository has evolved into an application that you have created yourself.
- Therefore, make sure to manage the repository properly and follow the subsequent tutorials to develop your skills in platform-based development.
:::

## Tutorial: Creating an Account and Deployment through PWS (Pacil Web Service)

The full documentation of the PWS can be accessed [here](https://docs.pbp.cs.ui.ac.id).

1. Access the PWS page at https://pbp.cs.ui.ac.id. You will be redirected to the login page.

	![Login Page of PWS](/img/0-login-pws.png)

2. Access the register page by clicking the `Register Here` button. On the page, please fill in your data according to the instructions.

3. After the registration process is complete, you can return to the login page. Please enter your newly registered username and password, and then log in.

4. After the login process is successful, you will be redirected to the PWS home page.

	![Home Page of PWS](/img/0-home-pws.jpg)

5. Create a new project by clicking the `Create New Project` button. You will be redirected to the page to create a new project. On the page, enter `Project Name` with `mentalhealthtracker`. After that, press the `Create New Project` button below.

	![Project Page of PWS](/img/0-project-pws.png)

	:::info
	In the process of creating other projects such as individual or group assignments, you can name your projects however you like. But there is a limitation that the project name must consist of only alphanumeric characters.
	:::

6. You will see two new informations, Project Credentials and Project Command. Save the credentials that you receive in a safe place, because you will not be able to see this information again. **Do not run the Project Commmand instruction yet**.

7. On the `settings.py` file of the Django project that you have just created, add the PWS deployment URL to the `ALLOWED_HOSTS` field.

	:::info
	The PWS deployment URL has the format `<sso-username>-<project name>.pbp.cs.ui.ac.id`. If your SSO username contains a dot (.), replace the dot with a hyphen (-). For example, if the SSO username is `pak.bepe24` and the project name is `mentalhealthtracker`, the PWS deployment URL is `pak-bepe24-mentalhealthtracker.pbp.cs.ui.ac.id`.
	:::


	```python
	...
	ALLOWED_HOSTS = ["localhost", "127.0.0.1", "<Your PWS deployment URL>"]
	...
	```
	This step needs to be done so that the Django project can be accessed through the PWS deployment URL. Do a `git add`, `commit`, and `push` change to the GitHub repository you have created.

8. Run the information in the Project Command on the PWS page. After that, run the following command to change the branch name to `main`.

	```bash
	git branch -M main
	```

9. On the PWS site's side bar, click on the project that you have created. You can see the current deployment status of your project. If the status is `Building`, it means that your project is still in the deployment process. If the status is `Running`, then your project is ready to be accessed at the deployment URL. You can press the `View Project` button that is located on your project page.

	:::info
	Currently, the PWS deployment URL is not yet accessible using the HTTPS protocol. If there is a problem with the deployment, try checking your deployment URL. If your URL starts with `https://`, try changing it to `http://`. Your deployed application should now be accessible. If it isn't, try accessing your deployment on incognito mode.
	:::

10. If there are any changes made to the Django project that you want to push to PWS, you only need to run
	```
	git push pws main:master
	```
	**after doing `add` and `commit`**. You do not need to run the commands in the Project Command again.

	:::note
	On the next tutorial, you will learn how to configure so that the push of the code changes you make to PWS can be done automatically together with the push to GitHub.
	:::

### Extras: PWS Troubleshooting

If you encounter issues such as a failed build, "Build Not Found," or other similar problems, there are a few solutions you can try:

- Take another look at the structure of your Django project. Sometimes the "Build Not Found" message or similar issues indicate that the files in your Django project are incomplete, causing your project not to be detected by PWS.
- If you are confident that your Django project's file structure is complete but the deployment still fails, try adding a file named Procfile (without a file extension) with the following content:

```Procfile
Procfile
release: python3 manage.py migrate --noinput
web: gunicorn mental_health_tracker.wsgi
```

## Closing

Congratulations! You have successfully completed the tutorial about using Git, GitHub, IDE installation, Django project development, and deployment to PWS!

Additionally, make sure you understand each code you write. **Do not copy-paste code without understanding it first.** If you encounter any difficulties in the future, do not hesitate to ask for help from the teaching assistants or peers. Keep up your spirits up and don't forget to enjoy every step of the process. Best of luck!

## Additional Reference

- [About pull request merges](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)
- [Resolving a merge conflict on GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)

## Contributors

- Muhammad Nabil Mu'afa
- Alden Luthfi
- Muhammad Oka (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
