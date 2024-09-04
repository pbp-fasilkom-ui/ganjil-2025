---
sidebar_label: Tutorial 1
sidebar_position: 3
Path: docs/tutorial-1
---

# Tutorial 1: Introduction to Django Application and Model-View-Template in Django

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understand the concept of MVT on a Django application
- Understand the flow Django uses to display a HTML page
- Understand routing configurations on `urls.py`
- Understand the relationship between models, views and templates in Django
- Understand unit test creation on the Django framework

## Summary of Tutorial 0

To help you complete this tutorial, we expect the results of your Tutorial 0 is as follows.

1. On your local computer, there is a root directory `mental-health-tracker` that is initialized as a local repository.
2. On the `mental-health-tracker` directory, there are these files and subdirectories.

    - `.env` subdirectory
    - `mental_health_tracker` subdirectory. This is different from the root directory, where this subdirectory is created after running the command

        ```bash
        django-admin startproject mental_health_tracker .
        ```
        
    - `.gitignore` file
    - `manage.py` file
    - `requirements.txt` file
    - (Optional) `db.sqlite3` file

    The structure of the root directory `mental-health-tracker` is as follows.

    ```
    mental-health-tracker
    ├── mental_health_tracker
    │   ├── __init__.py
    │   ├── asgi.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── manage.py
    ├── .gitignore
    └── requirements.txt
    ```

3. On the GitHub repository, make sure that the repository `mental-health-tracker` has the following directories and files.

    - The project directory `mental_health_tracker`. This directory is a result of running the command

        ```bash
        django-admin startproject mental_health_tracker .
        ```

    - `.gitignore` file
    - `manage.py` file
    - `requirements.txt` file

    The structure of the `mental-health-tracker` repository on GitHub is as follows

    ![GitHub Repository Structure](/img/1-filebefore-github.png)
    
## Introduction to the MVT concept

In the realms of web development, there are some concepts and architectures that assist in designing and developing an application. One of the concepts that is commonly used is MVT (Model-View-Template).

### What is MVT?

![MVT Diagram](https://miro.medium.com/v2/resize:fit:1400/1*m2_0pEyl1cfnfWYgCSlAZA.png)

**MVT** stands for **Model-View-Template**. MVT is an architecture that is used on web development to separate the main components of an application. This concept allows developers to organize and manage code in a structured way.

### What is a Model?

**Model** is a component in an MVT that is in charge of organizing and managing the data of an application. The model represents the data structure and application logic behind the interface. The model connects the application with the database and manages interaction with the data.

### What is a View?

**View** is a component that handles the presentation logic in the MVT architecture. View is in control of how the data that is organized by the model will be displayed to the user. In the context of MVT, view acts as an interface controller and retrieves data from the model to be displayed by the user.

### What is a Template?

**Template** is a component that is used to organize the user interface. Template separates the HTML code from the application logic. In MVT, template is used to design the interface that would be populated by data from the model through the view.

### Relationship between MVT components

In a nutshell, the MVT concepts operates within the following framework:

- **Model**: Stores data and application logic.
- **View**: Displays data from the model and linking it to the template
- **Template**: Defining the user interface.

### Benefits of MVT

- **Separation of Concerns**

    MVT separates tasks between the application logic, interface, and data, allowing developers to work on each components independently.

- **Easily Manageable Code**
    
    With clear separation of concerns, the code will be more organized and easier to manage.

- **Reusability**

    The code can be reused in other parts of the application.

- **Scalability**

    The structure of MVT supports scalability by allowing parallel development for every component.

**Notes:**

- The concept of MVT is closely related to the Django framework in web development using the Python programming language.
- In practice, a good understanding of the MVT concept will help you on developing a more structured and more organized web application.

## Tutorial: Creating a Django Application and Configuring the Model

In this tutorial, the concepts of applications and projects in Django will be explained

**What is a Project and Application in Django?**

- **Project** is the whole web project that you've built with Django. **This project contains multiple applications** that works together to create a complete website or web application.

- **Application** is a modular unit that does a specific task in a Django project. Each application can have its own models, views, templates, and URLs. Applications allow you to break down functionalities into separate and manageable components that can be handled independently.

Before starting, you need to remember that the root directory is the **outer** directory (`mental-health-tracker`), while the project directory is the directory **inside** the root directory (`mental_health_tracker`).

### Step 1: Preparation

1. Open the `mental-health-tracker` root directory.

    - Before starting, make sure you are on the `mental-health-tracker` **root** directory that has been made in Tutorial 0.
    - The development of your Django project will be done in this directory 😎. 

2. Open a terminal or command prompt and make sure that you are already on the `mental-health-tracker` root directory.

:::tip

- Use the `cd [directory]` command to move between directories. This command is very important to remember since proficiency of using the terminal is very helpful, not only in this course but also on other courses in the future.

:::

3. Activate the virtual environment that has been created previously by running the following command. **(Please take note of the operating system that you are using)**.

   - **Windows:**

     ```bash
     env\Scripts\activate
     ```

   - **Unix (Linux & Mac OS):**

     ```bash
     source env/bin/activate
     ```
:::tip
- For Windows users, if you receive an error saying "The execution of scripts is disabled on this system...", 
    - Open PowerShell as an **administrator** and run the following command
        ```bash
        Set-ExecutionPolicy Unrestricted -Force
        ```
    - Pick option `A` and press `Enter`.
- For Unix (Linux & macOS) users, if you receive an error saying "... Permission Denied",
    - Run the following command
        ```bash
        chmod +x env/bin/activate
        ```
:::

### Step 2: Creating the `main` Application Inside the `mental-health-tracker` Project

You will create a new application called `main` inside the `mental-health-tracker` project.

1. Run the following command to create a new application with the name **main**.

     ```shell
     python manage.py startapp main
     ```

    After running the command above, a new directory with the name `main` will be created. The `main` directory will contain the starting structure for your Django application.

:::note
If you are still confused about terms such as **root directory**, **project directory**, **application directory**, that's okay! You will get used to it as time goes by. Keep going!
:::

2. Registering the `main` application on the project.

    - Open the `settings.py` file inside the `mental_health_tracker` project directoryr.
    - Add `'main'` to the `INSTALLED_APPS` variable as shown below.

     ```python
     INSTALLED_APPS = [
         ...,
         'main'
     ]
     ```
     
By following those steps, you have successfully registered the `main` application to your mental health tracker project.

## Tutorial: Implementing Basic Templates

At this stage, you will create a template located in the `templates` directory within `main`. This template is used to display data from your mental health program.

:::note
Currently, the mental health tracker application does not display any data. Data will be displayed in tutorial 2. Keep going!
:::

### Step 1: Creating and Filling the `main.html` File

Let's get acquainted with HTML first. HTML (Hypertext Markup Language) is a markup language used on web pages to interpret and write text, images, and other materials visually and audibly.

:::note
Hint: You will learn more about HTML in tutorial 4.
:::

1. **Create a new directory** named `templates` inside the `main` application directory.

2. Inside the `templates` directory, **create a new file** named `main.html` and fill the `main.html` file with the following code. **Change the name and class according to your personal data!**

     ```html
     <h1>Mental Health Tracker</h1>

     <h5>NPM: </h5>
     <p>2306123456</p> <!-- Change according to your npm -->
     <h5>Name: </h5>
     <p>Pak Bepe</p> <!-- Change according to your name -->
     <h5>Class: </h5>
     <p>PBP E</p> <!-- Change according to your class -->
     ```

3. Open the HTML file in a web browser.

   - Before connecting it to the application, try opening the `main.html` file in your web browser.
   - Note that at this stage it is **only to check** the basic HTML display and **is not yet connected to Django.**
   - Here's an example of the expected HTML display.
     ![main.html](/img/1-html-template.jpeg)

## Tutorial: Implementing Basic Models

### Step 1: Modifying the `models.py` File in the `main` Application

In this step, you will modify the `models.py` file located in the `main` application directory to define a new model.

1. Open the `models.py` file in the `main` application directory.

2. Fill the `models.py` file with the following code.

    ```python
    from django.db import models

    class MoodEntry(models.Model):
        mood = models.CharField(max_length=255)
        time = models.DateField(auto_now_add=True)
        feelings = models.TextField()
        mood_intensity = models.IntegerField()

        @property
        def is_mood_strong(self):
            return self.mood_intensity > 5
    ```

    **Code Explanation:**

    - `models.Model` is the base class used to define models in Django.
    - `MoodEntry` is the name of the model you define.
    - *`mood`*, *`time`*, *`feelings`*, and *`mood_intensity`* are attributes or fields in the model. Each field has an appropriate data type such as `CharField`, `DateField`, `IntegerField`, and `TextField`.
    - The `@property` decorator is used to add read-only attributes that are not stored in the database but are calculated/derived from other attributes. In this case, *`is_mood_strong()`* with the `@property` decorator measures whether the user's mood is considered "strong" at that time based on *`mood_intensity`*.
    
    :::tip
    You will learn more about "derived attributes" in Databases course. In the meantime, if you would like to know more about the `@property` decorator, you can read [Python's documentation on property](https://docs.python.org/3/library/functions.html#property).
    :::

### Step 2: Creating and Applying Model Migrations

**What are model migrations?**

- Model migrations are Django's way of tracking changes to your database models.
- These migrations are instructions to change the database table structure according to the changes in the model defined in your latest code.

**How to perform model migrations?**

1. Run the following command to create model migrations.

    ```shell
    python manage.py makemigrations
    ```

    :::tip
    `makemigrations` creates migration files that contain model changes that have **not yet** been applied to the database.
    :::

2. Run the following command to apply migrations to the local database.

    ```shell
    python manage.py migrate
    ```

    :::tip
    `migrate` applies the model changes listed in the migration files to the database by running the previous command.
    :::

**Every time you make changes to the *model***, such as adding or changing attributes, **you MUST perform migrations** to reflect these changes.

## Tutorial: Connecting Views with Templates

At this stage, you will connect the view component with the template component using Django.

### Step 1: Integrating MVT Components

You will import the necessary modules and create the `show_main` view function.

1. Open the `views.py` file located in the `main` application file.

2. If the file is empty, add the following import lines at the very top of the file.

    ```python
    from django.shortcuts import render
    ```

    **Code Explanation:**

    - `from django.shortcuts import render` is useful for importing the *render* function from the `django.shortcuts` module.
    - The *render* function will be used to *render* HTML views using the given data.

3. Add the `show_main` function below the imports:

    ```python
    def show_main(request):
        context = {
            'npm' : '2306123456',
            'name': 'Pak Bepe',
            'class': 'PBP E'
        }

        return render(request, "main.html", context)
    ```

    **Code Explanation:**

    - The code snippet above declares the `show_main` function, which accepts a `request` parameter. This function will handle HTTP requests and return the appropriate view.
    - `context` is a *dictionary* containing data to be sent to the view. At this time, there are three pieces of data included, namely:

       - `npm`: Your npm data.
       - `name`: Your name data.
       - `class`: Your class data.

    - `return render(request, "main.html", context)` is useful for rendering the `main.html` view using the `render` function. The `render` function takes three arguments:

       - `request`: This is the HTTP request object sent by the user.
       - `main.html`: This is the name of the *template* file that will be used to render the view.
       - `context`: This is the *dictionary* containing data that will be passed to the view for dynamic display.

## Step 2: Template Modification

At this stage, you will modify the `main.html` template to display data that has been retrieved from the model.

1. Open the `main.html` file that was previously created in the `templates` directory in the `main` directory.

2. Change the name and class to the appropriate Django code structure to display the data.

    ```html
    ...
    <h5>NPM: </h5>
    <p>{{ npm }}<p>
    <h5>Name: </h5>
    <p>{{ name }}<p>
    <h5>Class: </h5>
    <p>{{ class }}<p>
    ...
    ```

    **Code Explanation:**

    The Django syntax `{{ npm }}`, `{{ name }}`, and `{{ class }}`, usually called template variables, is used to display the values of variables that have been defined in the `context`.

## Tutorial: Configuring URL *Routing*

In this part of the tutorial, you will configure the URL routing to make your `main` application accessible from a web browser.

### Step 1: Configuring the URL *Routing* for the `main` application

1. Create a `urls.py` file in the `main` directory.
2. Paste the following content inside `urls.py`:

    ```python
    from django.urls import path
    from main.views import show_main

    app_name = 'main'

    urlpatterns = [
        path('', show_main, name='show_main'),
    ]
    ```

   **Code Explanation for the `urls.py` file of the `main` application:**

   - The `urls.py` is responsible for managing the URL routing related to the `main` application.
   - Import the `path` function from `django.urls` to define the URL pattern.
   - Use the `show_main` function from the `main.views` module as the view that will be displayed when the corresponding URL is accessed.
   - The `app_name` variable is set to give a unique namespace to the URL patterns within the application.

### Step 2: Configuring the project URL *Routing*

You will add a URL route in the project's `urls.py` to connect it to the `main` view.

1. Open the `urls.py` file inside of the `mental_health_tracker` project directory, not the one inside the `main` a directory.
2. Import the `include` function from `django.urls`.

    ```python
    ...
    from django.urls import path, include
    ...
    ```
    
3. Add the following URL route to direct to the `main` view within the `urlpatterns` variable.

    ```python
    urlpatterns = [
        ...
        path('', include('main.urls')),
        ...
    ]
    ```

   **Explanation:**

   - The `urls.py` file in the project is responsible for setting up project-level URL routes.
   - The `include` function is used to import URL routes from other apps (in this case, from the `main` app) into the project's `urls.py` file.
   - The URL path `'main/'` will direct requests to the routes defined in the `urls.py` file of the `main` app. The URL path is an empty string since we want access the main page directly.

   :::tip 
   As an illustration, if you set te URL path as `'main'` on the example above, then you need to access `http://localhost:8000/main/` to view the main page. Since the URL path is empty, you can access the main page directly with `http://localhost:8000/`.
   :::

4. Run the Django project with the command `python manage.py runserver`.

5. Open [http://localhost:8000/](http://localhost:8000/) in your favorite web browser to view the page you have created.

With the above steps, you have successfully implemented a basic view in the `main` app and connected it with the project's URL route. Make sure you understand each step and the information provided to enable the view in your Django project.

### What is the difference between `urls.py` in an app and `urls.py` in a project?

- The `urls.py` file in an app sets up specific URL routes for the features within that app.
- The `urls.py` file in a project directs project-level URL routes and can import URL routes from the `urls.py` files of apps, allowing the apps in a Django project to be modular and separate.

## Tutorial: Introduction to Django *Unit Testing*

*Unit testing* can be used to check if the code you have written works as intended. It is also helpful when you make changes to the code. By using tests, you can verify whether the changes made cause any unwanted behavior in the application.

### Step 1: Creating a Unit *Test*

1. Open the `tests.py` file in the `main` app directory.
2. Populate `tests.py` with the following code.

    ```python
    from django.test import TestCase, Client
    from django.utils import timezone
    from .models import MoodEntry

    class MainTest(TestCase):
        def test_main_url_is_exist(self):
            response = Client().get('')
            self.assertEqual(response.status_code, 200)

        def test_main_using_main_template(self):
            response = Client().get('')
            self.assertTemplateUsed(response, 'main.html')

        def test_nonexistent_page(self):
            response = Client().get('/skibidi/')
            self.assertEqual(response.status_code, 404)

        def test_strong_mood_user(self):
            now = timezone.now()
            mood = MoodEntry.objects.create(
              mood="Happy",
              time = now,
              feelings = "I'm happy, even though my clothes are soaked from the rain :(",
              mood_intensity = 8,
            )
            self.assertTrue(mood.is_mood_strong)
    ```

    **Explanation:**
    - `test_main_url_is_exist` is a test to check whether the main URL path (`''`) is accessible.
    - `test_main_using_main_template` is a test to verify if the main page is rendered using the `main.html` template.
    - `test_nonexistent_page` is a test to verify that a page that doesn't exist in your Django project really doesn't exist and will return 404 response code (Not Found)
    - `test_strong_mood_user` is a test to verify the code logic, especially when deciding whether the user's mood can be considered strong with some `mood_intensity` value stored.

When performing unit testing, make sure to always check all possible cases. For example, when testing the `is_mood_strong` property, there should be two cases that result in the function output being either `True` or `False`.

### Step 2: Running the *Tests*

1. Run the tests using the following command:

    ```shell
    python manage.py test
    ```

2. If the tests pass, you will see the following output:

    ```text
    Found 4 test(s).
    Creating test database for alias 'default'...
    System check identified no issues (0 silenced).
    ..
    ----------------------------------------------------------------------
    Ran 4 tests in 0.016s

    OK
    Destroying test database for alias 'default'...
    ```

**Congratulations!** You have successfully written and run Django tests.

## Conclusion

1. At the end of this tutorial, your local directory should look like this:
   ```
   mental-health-tracker
   ├── main
   │   ├── __init__.py
   │   ├── admin.py
   │   ├── apps.py
   │   ├── migrations
   │   │   ├── 0001_initial.py
   │   │   └── __init__.py
   │   ├── models.py
   │   ├── templates
   │   │   └── main.html
   │   ├── tests.py
   │   ├── urls.py
   │   └── views.py
   ├── mental_health_tracker
   │   ├── __init__.py
   │   ├── asgi.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── manage.py
   ├── .gitignore
   └── requirements.txt
   ```

2. Before proceeding with this step, **ensure your local directory structure is correct**. Next, perform `add`, `commit` and `push` to update your GitHub repository.
3. Run the following commands to perform `add`, `commit`, and `push`.

    ```shell
    git add .
    git commit -m "<commit_message>"
    git push -u origin <main_branch>
    ```

    - Replace `<commit_message>` with your desired message. Example: `git commit -m "Finished tutorial 1"`.
    - Replace `<main_branch>` with the name of your main branch. Example: `git push -u origin main` or `git push -u origin master`.

4. Below is the structure of your GitHub directory after completing this tutorial.

    ![GitHub Repository Structure](/img/1-fileafter-github.png)

## Additional References

- [Django Unit Testing](https://docs.djangoproject.com/en/4.2/topics/testing/)
- [Django Model Unit Testing](https://stackoverflow.com/questions/64574713/django-models-unit-tests-help-for-a-newbie)

## Contributor

- Alden Luthfi
- Juan Dharmananda Khusuma
- Puti Raissa
- Tsabit Coda R
- Muhammad Oka (EN Translation)
- Vincent Suryakim (EN Translation)
- Adrian Hakim Utomo (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
