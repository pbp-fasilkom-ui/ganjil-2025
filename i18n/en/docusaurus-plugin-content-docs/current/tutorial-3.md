---
sidebar_label: Tutorial 3
sidebar_position: 5
Path: docs/tutorial-3
---

# Tutorial 3: Authentication, Session, and Cookies

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understanding the basic concepts of authentication in web development.
- Understanding the role and function of cookies and sessions in web development.
- Understanding how cookies and sessions work in web development.
- Implementing cookies and sessions in a web project.

## Introduction to HTTP

HTTP (_HyperText Transfer Protocol_) is a protocol used for communication between a _client_ and a _server_. HTTP is _stateless_, meaning that each transaction/activity is considered a completely **new** transaction/activity. As such, no previous data is **stored** for the current transaction/activity.

Some basic concepts about HTTP:

1. **_Client/Server_**: The interaction occurs between a client and a server. The client is the party making the request, and the server is the party providing the response.

2. **_Stateless_**: Each activity (_request/response_) is independent, with no information retained from previous activities.

3. **_OSI Layer/Model_**: The _Open Systems Interconnection (OSI)_ model describes the 7 layers used by computer systems to communicate over a network. The 7-layer OSI model consists of the _Application Layer_, _Presentation Layer_, _Session Layer_, _Transport Layer_, _Network Layer_, _Data Link Layer_, and _Physical Layer_.

4. **_Application Layer_**: In the OSI model mentioned above, websites operate at the _application layer_. However, the _request/response_ process occurs at the _transport layer_, which generally uses the TCP protocol to determine how data is sent. The _application layer_ doesn't concern itself with what the _transport layer_ does (how data is sent, processed, etc) because it is solely focused on the _request_ and _response_.

:::note
The other OSI layers will be covered in Computer Networks/Data Communication Networks courses. Feel free to look them up if you're curious. 😉
:::

5. **_Client Actions Method_**: There are methods used by the client when making a request. Examples include: GET, POST, PUT, DELETE, etc. You can read more details [here](https://www.restapitutorial.com/lessons/httpmethods.html).

6. **_Server Status Code_**: These are status codes provided by the server in response to a request for a webpage. Examples include: 200 (OK), 404 (Page Not Found), 500 (Internal Server Error), etc. You can read more details [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

7. **_Headers_**: These are small pieces of information sent along with a request or response. This information is useful as additional data for processing the request/response. For example, in headers, there may be `content-type:json`, which means that the content being requested or sent is in `json` format. Headers also store _cookies_ data.

## Introduction to Cookies & Session

All communications between the client and server is carried out through the HTTP protocol, where HTTP is a _stateless protocol_. This means that each _state_ is independent and unrelated to the others. As a result, the client computer running the browser needs to create a TCP connection to the server **every time a request is made**.

Without a persistent connection between the client and server, software on either side (_endpoints_) cannot rely solely on the TCP connection for _holding state_ or _holding session state_.

### What is a _holding state_?

For example, if you want to access page A on a website that requires the user to be logged in. After logging into the website, you successfully access page A. If you then try to navigate to page B on the same website, without some form of _holding state_, **you would be asked to log in again**. This would happen every time you navigate to a different page, even though it’s the same website.

The process of telling the server "who" is logged in and storing this data is a form of client-server dialog and is the basis of a _session — a semi-permanent exchange of information_. Since HTTP is a _stateless protocol_, it is difficult to implement _holding state_, hence the need for techniques like _Cookies_ and _Sessions_ to solve this problem.

### How to implement a _holding state_?

One of the most common methods for _holding state_ is by using a _session ID_ stored as a _cookie_ on the client’s computer. A _session ID_ acts as a token (a string of characters) that identifies a unique session in a web application. Instead of storing all types of user information as cookies on the client, such as _username_, _name_, and _password_, only the _session ID_ is stored.

This _session ID_ can then be mapped to a data structure on the web server side, where you can store all the information you need. This approach is much safer for storing user information compared to storing it in cookies. In this way, the information cannot be tampered with by the client or an insecure connection.

Additionally, this approach is more "appropriate" if there is a large amount of data to be stored, since cookies can only store a maximum of 4 KB of data. Imagine you have logged into a website/application and received a _session ID_ (a _session identifier_). To achieve _holding state_ in HTTP, which is stateless, the browser typically sends the session ID to the server with each request. That way, with each request, the server can respond (roughly) "Oh, this is the right person!" Then, the server retrieves the state information from memory or a database based on the _session ID_ and returns the requested data.

The important distinction to remember is that _cookie_ data is stored on the client side, while session data is usually stored on the server side. For more details on _stateless_, _stateful_, _cookies_, and _sessions_, you can read [here](https://sethuramanmurali.wordpress.com/2013/07/07/stateful-stateless-cookie-and-session/).

Below is a summary table comparing _cookies_, _session_, and _local storage_.

|                        | **_Cookies_** | **_Local Storage_** | **_Sessions_**  |
| ---------------------- | ------------- | ------------------- | --------------- |
| **Capacity**           | 4 KB          | 5 MB                | 5 MB            |
| **Browser Technology** | HTML4/HTML5   | HTML5               | HTML5           |
| **Accessibility**      | All windows   | All windows         | Same tab        |
| **Expiration**         | Set manually  | Permanent           | When tab closes |

Some video links that can expand your knowledge on this topic:

- [Session & Cookies](https://www.youtube.com/watch?v=64veb6tKTm0&t=10s)
- [Cookies History](https://www.youtube.com/watch?v=I01XMRo2ESg)
- [Cookies vs. Local Storage vs. Session](https://www.youtube.com/watch?v=AwicscsvGLg)

## Pre-Tutorial Notes

Before you begin, and to help you follow Tutorial 3 effectively, we expect the following results from Tutorial 2:

- The directory structure of `mental-health-tracker` on your local machine should look like this:

```
   mental-health-tracker
   ├── .github\workflows
   │   └── deploy.yml
   ├── env
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   └── 0002_alter_moodentry_id.py
   │   ├── templates
   │   │   ├── create_mood_entry.html
   │   │   └── main.html
   │   ├── __init__.py
   │   ├── admin.py
   │   ├── apps.py
   │   ├── forms.py
   │   ├── models.py
   │   ├── tests.py
   │   ├── urls.py
   │   └── views.py
   ├── mental_health_tracker
   │   ├── __init__.py
   │   ├── asgi.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── templates
   │   └── base.html
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
```

- The `mental-health-tracker` repository structure on GitHub should look like this:

![GitHub Repository Structure](/img/3-file-before-github.png)

## Tutorial: Implementing Function and Registration Forms

In the previous tutorial, we created a form for adding mood entries. How was it? Pretty easy, right? In this tutorial, we’ll make the main page (`main`) restricted by creating user accounts. So, users who want to access the main page must first log in to gain access.

1. Firstly, activate the virtual environment in your terminal (Hint: Remember Tutorial 0!).

2. Open `views.py` in the `main` subdirectory of your project. Add `UserCreationForm` dan `messages` imports at the top.

   ```python
   from django.contrib.auth.forms import UserCreationForm
   from django.contrib import messages
   ```

   **Code Explanation:**

   `UserCreationForm` is a built-in form import that simplifies creating user registration forms in a web app. With this form, new users can easily register without needing to write custom code from scratch.

3. Add the following `register` function to `views.py`. This function automatically generates the registration form and creates a user account when the form data is submitted.

   ```python
   def register(request):
       form = UserCreationForm()

       if request.method == "POST":
           form = UserCreationForm(request.POST)
           if form.is_valid():
               form.save()
               messages.success(request, 'Your account has been successfully created!')
               return redirect('main:login')
       context = {'form':form}
       return render(request, 'register.html', context)
   ```

   **Code Explanation:**

   - `form = UserCreationForm(request.POST)` creates a new `UserCreationForm` from the import by passing in user input from `request.POST`.
   - `form.is_valid()` validates the form input.
   - `form.save()` creates and saves the form data.
   - `messages.success(request, 'Your account has been successfully created!')` displays a success message to the user after registration.
   - `return redirect('main:show_main')` redirects the user to the main page after saving the form data.

4. Create a new HTML file named `register.html` in the `main/templates` directory. You can use the following template:

   ```html
   {% extends 'base.html' %} {% block meta %}
   <title>Register</title>
   {% endblock meta %} {% block content %}

   <div class="login">
     <h1>Register</h1>

     <form method="POST">
       {% csrf_token %}
       <table>
         {{ form.as_table }}
         <tr>
           <td></td>
           <td><input type="submit" name="submit" value="Register" /></td>
         </tr>
       </table>
     </form>

     {% if messages %}
     <ul>
       {% for message in messages %}
       <li>{{ message }}</li>
       {% endfor %}
     </ul>
     {% endif %}
   </div>

   {% endblock content %}
   ```
   :::tip
   We are using the `{{ form.as_table }}` tag to ease us in making the form into an already made table. For more information, you can read about it [here](https://docs.djangoproject.com/en/5.1/topics/forms/#reusable-form-templates)
   :::


5. Open `urls.py` in the `main` subdirectory and import the `register` function.

   ```python
   from main.views import register
   ```

6. Add a URL path to `urlpatterns` to access the imported function.

   ```python
    urlpatterns = [
        ...
        path('register/', register, name='register'),
    ]
   ```

Now that we’ve added the registration form and created the `register` mechanism, in the next step, we'll create the _login_ form so users can authenticate their accounts.

## Tutorial: Implementing a Login Function

1. Reopen `views.py` in the `main` subdirectory and add the imports `authenticate`, `login` and `AuthenticationForm` at the top.

   ```python
   from django.contrib.auth.forms import UserCreationForm, AuthenticationForm
   from django.contrib.auth import authenticate, login
   ```

   **Code Explanation:**

   At a glance, the `authenticate` and `login` functions imported above are built-in Django functions used for authentication and login (if authentication is successful). For more details, refer to [here](https://docs.djangoproject.com/en/4.2/topics/auth/default/).

2. Add the `login_user` function below into `views.py`. This function is used to authenticate users trying to log in.

   ```python
   def login_user(request):
      if request.method == 'POST':
         form = AuthenticationForm(data=request.POST)

         if form.is_valid():
               user = form.get_user()
               login(request, user)
               return redirect('main:show_main')

      else:
         form = AuthenticationForm(request)
      context = {'form': form}
      return render(request, 'login.html', context)
   ```

   **Code Explanation:**

   - `login(request, user)` is used to log in the user. If the user is valid, this function creates a session for the logged-in user.

3. Create a new HTML file named `login.html` in the `main/templates` directory. Fill it with the following template:

   ```html
   {% extends 'base.html' %}

   {% block meta %}
   <title>Login</title>
   {% endblock meta %}

   {% block content %}
   <div class="login">
     <h1>Login</h1>

     <form method="POST" action="">
       {% csrf_token %}
       <table>
         {{ form.as_table }}
         <tr>
           <td></td>
           <td><input class="btn login_btn" type="submit" value="Login" /></td>
         </tr>
       </table>
     </form>

     {% if messages %}
     <ul>
       {% for message in messages %}
       <li>{{ message }}</li>
       {% endfor %}
     </ul>
     {% endif %} Don't have an account yet?
     <a href="{% url 'main:register' %}">Register Now</a>
   </div>

   {% endblock content %}
   ```

4. Open `urls.py` in the `main` subdirectory and import the function you just created.

   ```python
   from main.views import login_user
   ```

5. Add the URL path to `urlpatterns` to access the function.

   ```python
   urlpatterns = [
      ...
      path('login/', login_user, name='login'),
   ]
   ```

We have added the login form and created the `login` mechanism. Next, we will implement the `logout` mechanism and add a _logout_ button to the main page.

## Tutorial: Implementing a Logout Function

1. Reopen `views.py` in the `main` subdirectory and add the following `logout` import at the top.

   ```python
   from django.contrib.auth import logout
   ```

2. Add the following function to `views.py`. This function implements the logout mechanism.

   ```python
   def logout_user(request):
       logout(request)
       return redirect('main:login')
   ```

   **Code Explanation:**

   - `logout(request)` is used to delete the session of the currently logged-in user.
   - `return redirect('main:login')` redirects the user to the login page in the Django application.

3. Open `main.html` file in the `main/templates` directory and add the following code snippet after the hyperlink tag for "Add New Mood Entry."

   ```html
   ...
   <a href="{% url 'main:logout' %}">
     <button>Logout</button>
   </a>
   ...
   ```

   **Code Explanation:**

   - `{% url 'main:logout' %}` is used to dynamically link to the URL based on `app_name` and `name` defined in `urls.py`. In general, the syntax is `{% url 'app_name:view_name' %}`:
     - `app_name` refers to the name of the app defined in the `urls.py` file. If the app uses the `app_name` attribute in `urls.py`, it will be used to refer to the app. If `app_name` is not defined, the app's folder name will be used as the app name.
     - `view_name` is the name of the URL defined via the `name` parameter in the `path()` function in `urls.py`.
       [Code in urls.py](/img/3-tampilan-urls-py.png)

4. Open `urls.py` in the `main` subdirectory and import the `logout_user` function you created earlier.

   ```python
   from main.views import logout_user
   ```

5. Add the URL path to `urlpatterns` to access the function you imported earlier.

   ```python
   urlpatterns = [
      ...
      path('logout/', logout_user, name='logout'),
   ]
   ```

We have successfully implemented the `logout` mechanism and completed the authentication system in this project.

## Tutorial: Restricting Access to the Main Page

1. Reopen `views.py` in the `main` subdirectory and add the `login_required` import at the very top.

   ```python
   from django.contrib.auth.decorators import login_required
   ```

   **Code Explanation:**

   The line `from django.contrib.auth.decorators import login_required` imports a decorator that requires users to log in before accessing a particular webpage.

2. Add the code snippet `@login_required(login_url='/login')` above the `show_main` function so that the main page can only be accessed by authenticated (logged-in) users.

   ```python
   ...
   @login_required(login_url='/login')
   def show_main(request):
   ...
   ```

Once you've restricted access to the main page, run your Django project with the command `python manage.py runserver` and open [http://localhost:8000/](http://localhost:8000/) in your favorite browser to see the result. Instead of showing the list of mood entries on the main page, it should redirect you to the login page.

## Tutorial: Using Data from _Cookies_

Now, we will look at how to use cookies by adding `last login` data and displaying it on the main page.

1. Firstly, log out if you are currently running your Django application.

2. Reopen `views.py` in the `main` subdirectory. Add the imports for `HttpResponseRedirect`, `reverse`, and `datetime` at the very top.

   ```python
   import datetime
   from django.http import HttpResponseRedirect
   from django.urls import reverse
   ```

3. In the `login_user` function, we will add the functionality to set a cookie named `last_login` to track when the user last logged in. Do this by **replacing the code** in the `if form.is_valid()` block with the following snippet.

   ```python
   ...
   if form.is_valid():
       user = form.get_user()
       login(request, user)
       response = HttpResponseRedirect(reverse("main:show_main"))
       response.set_cookie('last_login', str(datetime.datetime.now()))
       return response
   ...
   ```

   **Code Explanation:**

   - `login(request, user)` handles logging the user in.
   - `response = HttpResponseRedirect(reverse("main:show_main"))` creates the response.
   - `response.set_cookie('last_login', str(datetime.datetime.now()))` creates a `last_login` cookie and adds it to the response.

:::note
Pay attention to your code's indentation to ensure no dead code appears in the function.
:::

4. In the `show_main` function, add the snippet `'last_login': request.COOKIES['last_login']` to the `context` variable. Here is an example of the updated code.

   ```python
   context = {
       'name': 'Pak Bepe',
       'class': 'PBP D',
       'npm': '2306123456',
       'mood_entries': mood_entries,
       'last_login': request.COOKIES['last_login'],
   }
   ```

   **Code Explanation:**

   `'last_login': request.COOKIES['last_login']` adds the `last_login` cookie information to the response, which will be displayed on the web page.

5. Modify the `logout_user` function to look like the following snippet.

   ```python
   def logout_user(request):
       logout(request)
       response = HttpResponseRedirect(reverse('main:login'))
       response.delete_cookie('last_login')
       return response
   ```

   **Code Explanation:**

   `response.delete_cookie('last_login')` deletes the `last_login` cookie when the user logs out.

6. Open the `main.html` file and add the following snippet after the _logout_ button to display the `last login` data.

   ```html
   ...
   <h5>Last login session: {{ last_login }}</h5>
   ...
   ```

7. Refresh the login page (or run your Django project using the command `python manage.py runserver` if you haven't already) and try logging in. Your `last login` data will appear on the main page.

8. If you're using Google Chrome, you can view the `last_login`, cookie data by using the inspect element feature and opening the _Application/Storage_ section. Click on the _Cookies_ section, and you will see available cookies. Apart from `last_login`, you can also see `sessionid` and `csrftoken`. Below is an example of the view.

   ![Main Page with Cookies Data](/img/3-tampilan-main-cookies.png)

:::info
For Safari users, you can view cookies in the browser using `Inspect element > Storage > Cookies`. If you can't find the inspect element option, enable it first via `Safari > Preferences > Advanced` and check the option `Show develop menu in menu bar`. Then, you can open the Inspect Element feature by right-clicking on the page and selecting Inspect Element, and navigate to `Storage > Cookies` to see cookies like `last_login`, `sessionid`, and `csrftoken`.
:::

9. If you log out and check the cookie history, the previously created cookie will be deleted and recreated when you log in again.

:::note
Before proceeding to the next tutorial, try **creating an account** on your website.
:::

## Tutorial: Connecting the `MoodEntry` model to the `User` model

:::danger
You must follow the tutorial sequentially from the beginning before proceeding with the following section. If you do not follow the tutorial in order, we are not responsible for any errors outside the scope of the tutorial that may arise.
:::

Lastly, we will link each `MoodEntry` object created to the user who made it so that an authorized user only sees the mood entries they have created. Follow these steps:

1. Open `models.py` in the `main` subdirectory and add the following code below the line that imports the model:

   ```python
   ...
   from django.contrib.auth.models import User
   ...
   ```

2. In the previously created `MoodEntry` model, add the following code:

   ```python
   class MoodEntry(models.Model):
       user = models.ForeignKey(User, on_delete=models.CASCADE)
       ...
   ```

   **Code Explanation:**

   The above code snippet connects a `MoodEntry` to a `User` through a relationship, where each `MoodEntry` is ensured to have an association with a user.

:::tip
You will learn more about `ForeignKey` in your Database course. More information on `ForeignKey` in Django can be found [here](https://docs.djangoproject.com/en/4.2/topics/db/examples/many_to_one/).
:::

3. Reopen `views.py` in the `main` subdirectory and modify the code in the `create_mood_entry` function as follows:

   ```python
   def create_mood_entry(request):
       form = MoodEntryForm(request.POST or None)

       if form.is_valid() and request.method == "POST":
           mood_entry = form.save(commit=False)
           mood_entry.user = request.user
           mood_entry.save()
           return redirect('main:show_main')

       context = {'form': form}
       return render(request, "create_mood_entry.html", context)
    ...
   ```

   **Code Explanation:**

   The parameter `commit=False` prevents Django from immediately saving the object created from the form to the database. This allows us to modify the object before saving it. In this case, we will fill the `user` field with the `User` object from the `request.user` return value, indicating that the object belongs to the logged-in user.

4. Change the value of `mood_entries` and `context` in the function `show_main` as follows.

   ```python
   def show_main(request):
       mood_entries = MoodEntry.objects.filter(user=request.user)

       context = {
            'name': request.user.username,
            ...
       }
   ...
   ```

   **Code Explanation:**

   - The above code displays the `Mood Entry` objects associated with the logged-in user. This is done by filtering all objects and only retrieving the `Mood Entry` where the `user` field is filled with the `User` object corresponding to the logged-in user.
   - The `request.user.username` code displays the logged-in user's username on the main page.

:::danger
Before running the code in the next step, make sure there is at least one user in the database. This is necessary because in the next step, you will be prompted to assign a default value to the `user` field for all existing rows. The model migration process will error if no user is previously recorded.
:::

5. Save all changes and run the model migration with `python manage.py makemigrations`.

6. You should encounter an error during the model migration. Select `1` to set a default value for the `user` field on all rows already created in the database.

   ![Migrations-1](/img/3-migration-pertama.png)

7. Type `1` again to assign the user with ID 1 (which we created earlier) to the existing model

   ![Migrations-2](/img/3-migration-kedua.png)

8. Run `python manage.py migrate` to apply the migration made in the previous step.
9. Lastly, we need to ensure our project is ready for a production environtment. To do that, add another import statement in `settings.py` in the `mental_health_tracker` subdirectory.

   ```python
   import os
   ```
   Then, change the variable `DEBUG` in `settings.py` into this.

   ```python
   PRODUCTION = os.getenv("PRODUCTION", False)
   DEBUG = not PRODUCTION
   ```

Run your Django project with the command `python manage.py runserver` and open [http://localhost:8000/](http://localhost:8000/) in your favorite browser to see the result. Try creating a new account and logging in with the newly created account. Observe the main page: the `Mood Entry` created with the previous account will not be displayed on the page of the new account. This means you have successfully linked the `Mood Entry` object to the `User` who created it.

## Conclusion

Congratulations! You've successfully completed Tutorial 3. 😄

After completing all the steps in this tutorial, you should now have a better understanding of using forms, authentication, sessions, and cookies in the Django framework.

1. After completing this tutorial, your web page should look like this:

   - Login page at [http://localhost:8000/login](http://localhost:8000/login)
     ![Login Page](/img/3-tampilan-halaman-login.png)
   - Main page at [http://localhost:8000/](http://localhost:8000/) after successfully logging in:
     ![Main Page](/img/3-tampilan-halaman-utama.png)

2. By the end of this tutorial, your `main` subdirectory structure should look like this:

   ```
   mental-health-tracker
   ├── .github\workflows
   │   └── deploy.yml
   ├── env
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   ├── 0002_alter_moodentry_id.py
   │   │   └── 0003_moodentry_user.py
   │   ├── templates
   │   │   ├── create_mood_entry.html
   │   │   ├── login.html
   │   │   ├── main.html
   │   │   └── register.html
   │   ├── __init__.py
   │   ├── admin.py
   │   ├── apps.py
   │   ├── forms.py
   │   ├── models.py
   │   ├── tests.py
   │   ├── urls.py
   │   └── views.py
   ├── mental_health_tracker
   │   ├── __init__.py
   │   ├── asgi.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── templates
   │   └── base.html
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
   ```

3. Before proceeding, **ensure your local directory structure is correct**. Next, run `add`, `commit`, and `push` to update the GitHub repository.

4. Run the following commands to `add`, `commit`, and `push`:

   ```shell
   git add .
   git commit -m "<commit_message>"
   git push -u origin <main_branch>
   ```

   - Replace `<commit_message>` with your preferred message. Example: `git commit -m "completed tutorial 3"`.
   - Replace `<main_branch>` with your main branch name. Example: `git push -u origin main` or `git push -u origin master`.

## Contributors

- Abbilhaidar Farras Zulfikar
- Clarence Grady
- Reyhan Zada Virgiwibowo
- Fernando Valentino Sitinjak
- Alden Luthfi
- Vincent Suryakim (EN Translation)

## Credits

This tutorial was developed based on [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
