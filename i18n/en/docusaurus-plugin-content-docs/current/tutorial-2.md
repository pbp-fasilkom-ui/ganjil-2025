---
sidebar_label: Tutorial 2
sidebar_position: 3
Path: docs/tutorial-2
---

# Tutorial 2: Form and Data Delivery

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understand the purpose and how to implement the skeleton of a view
- Understand `XML` and `JSON` as one of the data delivery methods
- Understand how data submission is done using the `form` element in `HTML`
- Understand how to send data using the `XML` and `JSON` format
- Understand how to retrieve data based on a specific `ID`
- Understand the use of Postman as a data viewer

## Introduction to Data Delivery

In the development of a platform, sometimes we need to send data from one stack to another. Data that is sent can be of many different types. Some commonly used data formats between different applications are HTML, XML, and JSON. The implementation of data delivery in the form of HTML has already been covered in the previous tutorial. In this tutorial, we will cover data delivery in the form of XML and JSON.

## XML (Extensible Markup Language)

XML, or eXtensible Markup Language, is a format that is designed to be easy to read, because each element in XML describes itself. XML is commonly used in web and mobile applications for storage and transmission of data. An XML file only contains data in a specific tag, and to send, receive, store, or display information from the file, we need to create a program that can process it.


XML Format Example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<person>
    <name>Doddy Ferdiansyah</name>
    <age>25</age>
    <address>
        <street>Jl. Ganesa No.10</street>
        <city>Bandung</city>
        <province>Jawa Barat</province>
        <zip>40132</zip>
    </address>
</person>
```

The XML above is self-descriptive:

- There is information about name (`name`)
- There is information about age (`age`)
- There is information about address (`address`)
  - There is information about street (`street`)
  - There is information about city (`city`)
  - There is information about province (`province`)
  - There is information about zip code (`zip`)

An XML document is structured like a tree that starts from the root, then branches, and ends at the leaves. An XML document **must contain a root element** which is the parent of other elements. On the given example, `<person>` is the root element.

The line `<?xml version="1.0" encoding="UTF-8"?>` is usually called the **XML Prolog**. The XML Prolog is optional, but if there is, then it must be at the beginning of the XML document. On an XML document, **all elements must have closing tags**. **Tags** in XML are **case sensitive**, so the tag `<person>` is **different** from the tag `<Person>`.

## JSON (JavaScript Object Notation)

JSON, or JavaScript Object Notation, is a format that is designed to be easy to read, because each element in JSON is self-describing. JSON is commonly used in web and mobile applications for storage and transmission of data. Even though the syntax of JSON is based on JavaScript objects, JSON itself is a text format. Therefore, many programming languages have support for reading and creating JSON.

Example of JSON format:

```json
{
  "name": "Doddy Ferdiansyah",
  "age": 25,
  "address": {
    "street": "Jl. Ganesa No.10",
    "city": "Bandung",
    "province": "Jawa Barat",
    "zip": "40132"
  }
}
```
Data in JSON is stored in the form of key and value. In the example above, the key is `name`, `age`, and `address`. The value can be of primitive data type (string, number, boolean) or an object.

## Pre-Tutorial Notes

Before you start, and to ensure that you follow this tutorial correctly, we expect some results from tutorial 1:

- Local directory structure `mental-health-tracker` should look like this.

![Local Directory Structure](/img/2-struktur-direktori-lokal.png)

- Repository structure `mental-health-tracker` on GitHub should look like this.

![Repository Structure](/img/2-struktur-direktori-github.png)

## Tutorial: Implementing the Skeleton of a View

Before creating a registraton form, we need to create a skeleton that acts as a base for the views of our website. With the base view, we can ensure consistency in the design of our website and reduce the possibility of redundancy of code. In this tutorial, we will create a skeleton for the website that we will create in the next tutorial.

1. Create a directory `templates` in the main directory (**root folder**) and create a new HTML file named `base.html`. The `base.html` file acts as a base template that can be used as a generic view for other web pages within the project. Create the `base.html` file with the following code:

   ```html
   {% load static %}
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       {% block meta %} {% endblock meta %}
     </head>

     <body>
       {% block content %} {% endblock content %}
     </body>
   </html>
   ```

   The lines enclosed in `{% ... %}` are called template tags in Django. The lines in this example will function to dynamically load data from Django into the HTML.

   In the example above, the `{% block %}` tag in Django is used to define an area in the template that can be replaced by templates that inherit from the base template. The inherited template will extend the base template (in this case `base.html`) and replace the content in the block as needed.

3. Open the `settings.py` file in the project directory (`mental_health_tracker`) and find the line that contains the `TEMPLATES` variable. Adjust the code with the following code to make the `base.html` file detected as a template file.

   ```python
   ...
   TEMPLATES = [
       {
           'BACKEND': 'django.template.backends.django.DjangoTemplates',
           'DIRS': [BASE_DIR / 'templates'], # Add this line
           'APP_DIRS': True,
           ...
       }
   ]
   ...
   ```
   :::note
   In some cases, `APP_DIRS`'s value on your `TEMPLATES` configuration might be `False`. If it is, change it to `True`. `APP_DIRS`'s value must be `True`.

4. In the subdirectory `templates` in the `main` directory (`main/templates/`), change the `main.html` file created in the previous tutorial to the following.

   ```html
    {% extends 'base.html' %}
    {% block content %}
    <h1>Mental Health Tracker</h1>

    <h5>NPM: </h5>
    <p>{{ npm }}<p>

    <h5>Name:</h5>
    <p>{{ name }}</p>

    <h5>Class:</h5>
    <p>{{ class }}</p>
    {% endblock content %}
   ```

    Note that the code above is the same as the code in `main.html` in the previous tutorial. The difference is in the code above, we are using `base.html` as the main template.

## Tutorial: Changing the Primary Key From Integer to UUID

To apply best practices from an application security standpoint, there are some changes that you need to make to the `models.py` file on the `main/` subdirectory. By default, the ID of each model object you create uses an incremental integer starting from 1. This could become an "entrypoint" for a security vulnerability in your Django application, as enumeration of object IDs within the application could be performed.

If you are interested about this security vulnerability, you can read more here in [this article regarding IDOR](https://portswigger.net/web-security/access-control/idor). For now, we will focus on implementing the best practices to mitigate this vulnerability.

:::warning
If you have already created an object to your model, you must delete your database file (`db.sqlite3`) first so that the next steps will not produce errors.
:::

1. Add these lines to the `models.py` file on the `main/` subdirectory.

```python
import uuid  # add this line at the very top
...
class MoodEntry(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)  # add this line
    mood = models.CharField(max_length=255)
    time = models.DateField(auto_now_add=True)
    feelings = models.TextField()
    mood_intensity = models.IntegerField()
...
```

2. Do a model migration by running the commands below.

   Windows:
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

   Unix (Linux/macOS):
   ```
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

## Tutorial: Creating Form Input Data and Displaying Data Mood Entry on HTML

Until now, no data has been added and displayed in the application. Now, we will create a simple form to input a Mood Entry data in the application so that we can add new data to be displayed on the main page.

1. Create a new file in the `main` directory with the name `forms.py` to create the structure of the form that can receive new Mood Entry datas. Add the following code to the `forms.py` file.

   ```python
   from django.forms import ModelForm
   from main.models import MoodEntry

   class MoodEntryForm(ModelForm):
       class Meta:
           model = MoodEntry
           fields = ["mood", "feelings", "mood_intensity"]
   ```

   **Code Explanation:**

   - `model = MoodEntry` to indicate the model that will be used for the form. When data from the form is saved, the form's input will be saved as an object of `MoodEntry`.
   - `fields = ["mood", "feelings", "mood_intensity"]` to indicate the fields of the `MoodEntry` model that will be used for the form. The `time` field is not included in the `fields` list because it will be added automatically.

2. Open the `views.py` file in the `main` directory and add the following import at the top of the file.

   ```python
   from django.shortcuts import render, redirect   # Add import redirect at this line
   from main.forms import MoodEntryForm
   from main.models import MoodEntry
   ```

3. In the same file, create a new function with the name `create_mood_entry` that receives a parameter `request`. Add the following code below to produce a form that can automatically add a Mood Entry data automatically when data is submitted from the form.

   ```python
   def create_mood_entry(request):
       form = MoodEntryForm(request.POST or None)

       if form.is_valid() and request.method == "POST":
           form.save()
           return redirect('main:show_main')

       context = {'form': form}
       return render(request, "create_mood_entry.html", context)
   ```

   **Code Explanation:**

   - `form = MoodEntryForm(request.POST or None)` is used to create a new `MoodEntryForm` with the input from the user in `request.POST` entered into the QueryDict.
   - `form.is_valid()` is used to validate the input from the form.
   - `form.save()` is used to create and save the data from the form.
   - `return redirect('main:show_main')` is used to perform a redirect to the `show_main` function in the `main` application's views after the form data is successfully saved.

4. Change the `show_main` function that already exists in the `views.py` file to the following.

   ```python
   def show_main(request):
       mood_entries = MoodEntry.objects.all()

       context = {
           'name': 'Pak Bepe',
           'class': 'PBP KKI',
           'npm': '2306123456',
           'mood_entries': mood_entries
       }

       return render(request, "main.html", context)
   ```

   **Code Explanation:**

   The `MoodEntry.objects.all()` function is used to retrieve all objects of the `MoodEntry` objects stored in the database.

5. Open the `urls.py` file in the `main` directory and import the `create_mood_entry` function that you just created.

   ```python
   from main.views import show_main, create_mood_entry
   ```

6. Add the URL path to the `urlpatterns` variable in the `urls.py` file in the `main` directory to access the function that was imported in the previous point.

   ```python
   urlpatterns = [
      ...
      path('create-mood-entry', create_mood_entry, name='create_mood_entry'),
   ]
   ```

7. Create a new HTML file with the name `create_mood_entry.html` in the `main/templates` directory. Fill in the `create_mood_entry.html` file with the following code.

   ```html
   {% extends 'base.html' %} 
   {% block content %}
   <h1>Add New Mood Entry</h1>

   <form method="POST">
     {% csrf_token %}
     <table>
       {{ form.as_table }}
       <tr>
         <td></td>
         <td>
           <input type="submit" value="Add Mood Entry" />
         </td>
       </tr>
     </table>
   </form>

   {% endblock %}
   ```

   **Code Explanation:**

   - `<form method="POST">` is used to indicate the block for the form with the POST method.
   - `{% csrf_token %}` is a token that functions as a security system. The token is automatically generated by Django to prevent attacks.
   - `{{ form.as_table }}` is a template tag used to display the form fields created in the `forms.py` file as a table.
   - `<input type="submit" value="Add Mood Entry"/>` is used as a submit button to send the request to the `create_mood_entry(request)` view.

8. Open the `main.html` file and add the following code within the `{% block content %}` block to display the data in the form in the form of a table and the "Add New Mood Entry" button that will redirect to the form page.

   ```html
   ...
   {% if not mood_entries %}
   <p>There are no mood data in mental health tracker.</p>
   {% else %}
   <table>
     <tr>
       <th>Mood Name</th>
       <th>Time</th>
       <th>Feeling</th>
       <th>Mood Intensity</th>
     </tr>

     {% comment %} This is how to display mood data
     {% endcomment %} 
     {% for mood_entry in mood_entries %}
     <tr>
       <td>{{mood_entry.mood}}</td>
       <td>{{mood_entry.time}}</td>
       <td>{{mood_entry.feelings}}</td>
       <td>{{mood_entry.mood_intensity}}</td>
     </tr>
     {% endfor %}
   </table>
   {% endif %}

   <br />

   <a href="{% url 'main:create_mood_entry' %}">
     <button>Add New Mood Entry</button>
   </a>
   {% endblock content %}
   ```

9. Run the Django project with the `python manage.py runserver` command and go to [http://localhost:8000/](http://localhost:8000/) in your browser of choice. Try adding some new mood data and you should be able to see the added data on the main application page.

## Tutorial: Returning Data in XML Format

1. Open the `views.py` file in the `main` directory and add the `HttpResponse` and `Serializer` imports at the top of the file.

   ```python
   from django.http import HttpResponse
   from django.core import serializers
   ```

2. Create a new function that receives a parameter `request` with the name `show_xml` and create a variable in the function itself that stores the result of the query of all data in the `MoodEntry`.

   ```python
   def show_xml(request):
       data = MoodEntry.objects.all()
   ```

3. Add the return function as an `HttpResponse` that contains the serialised data result as XML and the `content_type="application/xml"`.

   ```python
   def show_xml(request):
       data = MoodEntry.objects.all()
       return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
   ```

   **Code Explanation:**

   `serializers` is used to translate object models into other formats such as in this case XML.

4. Open the `urls.py` file in the `main` directory and import the function that you just created.

   ```python
   from main.views import show_main, create_mood_entry, show_xml
   ```

5. Add the URL path to the `urlpatterns` variable in the `urls.py` file in the `main` directory to access the function that was imported in the previous point.

   ```python
   ...
   path('xml/', show_xml, name='show_xml'),
   ...
   ```

6. Run the Django project with the `python manage.py runserver` command and go to [http://localhost:8000/xml/](http://localhost:8000/xml/) in your browser of choice to see the result.

## Tutorial: Returning Data in JSON Format

1. Open the `views.py` file in the `main` directory and create a new function that receives a parameter `request` with the name `show_json` with a variable in the function itself that stores the result of the query of all data in the `MoodEntry`.

   ```python
   def show_json(request):
       data = MoodEntry.objects.all()
   ```

2. Add the return function as an `HttpResponse` that contains the serialised data result as JSON and the `content_type="application/json"`.

   ```python
   def show_json(request):
       data = MoodEntry.objects.all()
       return HttpResponse(serializers.serialize("json", data), content_type="application/json")
   ```

3. Open the `urls.py` file in the `main` directory and import the function that you just created.

   ```python
   from main.views import show_main, create_mood_entry, show_xml, show_json
   ```

4. Add the URL path to the `urlpatterns` variable in the `urls.py` file in the `main` directory to access the function that was imported in the previous point.

   ```python
   ...
   path('json/', show_json, name='show_json'),
   ...
   ```

5. Run the Django project with the `python manage.py runserver` command and go to [http://localhost:8000/json/](http://localhost:8000/json/) in your browser of choice to see the result.

## Tutorial: Returning Data Based on an ID in XML and JSON Format

1. Open the `views.py` file in the `main` directory and create two new functions that receive a parameter `request` and `id` with the names `show_xml_by_id` and `show_json_by_id`.

2. Create a variable in the function itself that stores the result of the query of data with the specific ID that exists in the `MoodEntry`.

   ```python
   data = MoodEntry.objects.filter(pk=id)
   ```

3. Add the return function as an `HttpResponse` that contains the serialised data result as JSON or XML and the `content_type` with the value `"application/xml"` (for XML) or `"application/json"` (for JSON).

   - XML

     ```python
     def show_xml_by_id(request, id):
         data = MoodEntry.objects.filter(pk=id)
         return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
     ```

   - JSON

     ```python
     def show_json_by_id(request, id):
         data = MoodEntry.objects.filter(pk=id)
         return HttpResponse(serializers.serialize("json", data), content_type="application/json")
     ```

4. Open the `urls.py` file in the `main` directory and import the function that you just created.

   ```python
   from main.views import show_main, create_mood_entry, show_xml, show_json, show_xml_by_id, show_json_by_id
   ```

5. Add the URL path to the `urlpatterns` variable in the `urls.py` file in the `main` directory to access the function that was imported in the previous point.

   ```python
   ...
   path('xml/<str:id>/', show_xml_by_id, name='show_xml_by_id'),
   path('json/<str:id>/', show_json_by_id, name='show_json_by_id'),
   ...
   ```

6. Run the Django project with the `python manage.py runserver` command and go to [http://localhost:8000/xml/[id]/](http://localhost:8000/xml/[id]/) or [http://localhost:8000/json/[id]/](http://localhost:8000/json/[id]/) in your browser of choice to see the result.

   > Note: Adjust the `[id]` in the URL above with the ID of the object that you want to see.

## Tutorial: Using Postman as a Data Viewer

1. Ensure that the server is running with the `python manage.py runserver` command.

2. Open Postman and create a new request with the method `GET` and url [http://localhost:8000/xml/](http://localhost:8000/xml/) or [http://localhost:8000/json/](http://localhost:8000/json/) to test whether the data is sent correctly.

   > Postman Installation Guide can be found on the [Postman official website](#additional-reference).

   Example:
    ![Postman Page](/img/2-tampilan-halaman-postman.png)

3. Click the `Send` button to send the request.

4. You will see the result of the response from the request in the bottom of Postman.

    ![Postman Response](/img/2-response-postman.png)

5. You can also change the url to [http://localhost:8000/xml/[id]](http://localhost:8000/xml/[id]) or [http://localhost:8000/json/[id]](http://localhost:8000/json/[id]) to test the retrieval of data based on an ID.

   ![Response Detail Postman](/img/2-response-detail-postman.png)

## Tutorial: Deploying to PWS Automatically With GitHub Actions

:::warning
As of right now, PWS is not yet stable. You can still follow the instructions on this step, but please do note that **the deployment in PWS can still fail.**
:::

On the previous tutorials, if you want to deploy to the PWS and push your changes to GitHub, you need to do two separate pushes, to GitHub (`git push origin main`) and to the PWS (`git push pws master`). On this tutorial, you will create a script that can help you deploy to the PWS and also push the changes to GitHub with only one push command. You only need to do the steps below carefully.

1. On the root directory of your Django project, create a subdirectory named `.github`. In that subdirectory, create another subdirectory named `workflows`. Enter that directory (`.github/workflows/`).

2. Create a file named `deploy.yml`. Fill the files with the code below.

   ```yml
   name: Push to PWS

   on:
     push:
       branches: [ main ]
       paths-ignore:
           - '**.md'
     pull_request:
       branches: [ main ]
       paths-ignore:
           - '**.md'

   jobs:
     build-and-push:
       runs-on: ubuntu-latest

       steps:
       - name: Checkout code
         uses: actions/checkout@v2
         with:
           fetch-depth: 0

       - name: Set up Git
         run: |
           git config --global user.name 'github-actions[bot]'
           git config --global user.email 'github-actions[bot]@users.noreply.github.com'

       - name: Check PWS remote, pull, merge, and push
         env:
           PWS_URL: ${{ secrets.PWS_URL }}
         run: |
             # Check if master branch exists locally
             if ! git show-ref --verify --quiet refs/heads/master; then
               echo "Creating master branch"
               git branch master
             fi
             
             # Switch to master branch
             git checkout master

             # Push to master branch and capture the output
             push_output=$(git push $PWS_URL main:master 2>&1)
             if [[ $? -ne 0 ]]; then
               echo "Push failed with output: $push_output"
               echo "Error: Unable to push changes. Please check the error message above and resolve any conflicts manually."
               exit 1
             fi
             echo "Push successful with output: $push_output"
   ```
   :::warning
   Do not push this code yet.
   :::

3. On your GitHub repository, go to Settings > Secrets and variables > Actions. You will be directed to a page with this interface.

   ![Screenshot of Action secrets and variables page](/img/2-secrets-and-variables.png)

   Press `New repository secret` to add a secret variable on your repository.

4. Fill in `Name` with `PWS_URL`. Then, fill the `Secret` with data using this format

   **https://`<sso.username>`:`<PWS project password>`@pbp.cs.ui.ac.id/`<sso.username>`/`<project name>`**

  For example, if your SSO username is `hanni.pham`, your project password is `abcd1234`, and your project name is `supernatural`, then you need to fill your `Secret` as shown here:
   ```
   https://hanni.pham:abcd1234@pbp.cs.ui.ac.id/hanni.pham/supernatural
   ```

   ![Example of secret values](/img/2-new-secret.png)

   If you are sure that the URL that you wrote is correct, press `Add Secret` to add the repository secret.

5. On the `settings.py` file on your project, add this line of code to the bottom-most of the file.

   ```python
   CSRF_TRUSTED_ORIGINS = ["http://localhost","http://127.0.0.1","http://<YOUR_PWS_URL>", "https://<YOUR_PWS_URL>"]
   ```

   Make sure to replace `<YOUR_PWS_URL>` to the deployment URL of your PWS project.

6. Do git add, commit, and push to GitHub. After that, open your repository page. Wait for a moment, and you should see a yellow indicator next to your commit message.

   ![Yellow indicator example](/img/2-yellow.png)

7. After the yellow indicator turns to a green checkmark, you can check your project page on PWS. There should be a new deployment that is building.

   :::tip
   If the indicator turns to a red cross, that could mean there are some steps that you did not do correctly. If you have checked your `deploy.yml` file is correct, you can try to re-add the repository secret on step 4.
   :::

After adding this script, you don't need to do `git push pws master` every time you want to deploy to the PWS. Now, every time you push to GitHub on the `main` branch, GitHub Actions will automatically push your project to PWS according to the last commit that you have pushed, therefore triggering a build process on your PWS project.

## Conclusion

1. After completing this tutorial, the web page you should see should look like this.

   ![Web Result](/img/2-web-result.png)

2. At the end of this tutorial, the local directory structure should look like this.

   ![Final Directory Structure](/img/2-final-struktur-direktori.png)

3. Before performing this step, **ensure that the local directory structure is correct**. Then, perform `add`, `commit`, and `push` to update the GitHub repository.

4. Run the following command to perform `add`, `commit`, and `push`.

   ```shell
   git add .
   git commit -m "<commit_message>"
   git push -u origin <main_branch>
   ```

   - Change `<commit_message>` according to your preference. Example: `git commit -m "finished tutorial 2"`.
   - Change `<main_branch>` according to the name of the main branch. Example: `git push -u origin main` or `git push -u origin master`.

## Additional Reference

- [Install and update Postman](https://learning.postman.com/docs/getting-started/installation/installation-and-updates)
- [Using a UUID as a primary key in Django models](https://stackoverflow.com/questions/3936182/using-a-uuid-as-a-primary-key-in-django-models-generic-relations-impact)

## Contributors

- Martin Marcelino Tarigan
- Sabrina Atha Shania
- Muhammad Daffa'I Rafi Prasetyo
- Resanda Dezca Asyam
- Muhammad Nabil Mu'afa
- Muhammad Oka (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
