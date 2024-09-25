---
sidebar_label: Tutorial 4
sidebar_position: 6
Path: docs/tutorial-4
---

# Tutorial 4: Web Design Using HTML and CSS3 & Update and Delete Methods on Data

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understand the structure of HTML5 tags
- Know various types of HTML5 tags
- Understand CSS syntax
- Introduction to CSS frameworks, namely Bootstrap and Tailwind
- Understand the concept of static files in Django
- Understand the use of selectors in CSS
- Understand the implementation of update and delete in Django
- Style Django with Tailwind

## *Important Notes*
- Make sure your Django file structure is like this

![Django File Structure](/img/4-struktur-file-django.png)
```
Note: deploy.yml has been changed to push.yml
```
- Make sure the DEBUG variable in settings.py is like this
```python
...
PRODUCTION = os.getenv("PRODUCTION", False)
DEBUG = not PRODUCTION
...
```


## Introduction to HTML

HyperText Markup Language (HTML) is the standard markup language for documents to be displayed in a web browser. HTML defines the structure of the content of a website.

Please do independent exploration about HTML on the following [reference](https://www.w3schools.com/html/default.asp).

The difference between HTML and HTML5 can be read on the following [reference](https://www.geeksforgeeks.org/difference-between-html-and-html5/).

## Introduction to CSS

### What is CSS?

Cascading Style Sheets (CSS) is a language used to describe the appearance and format of a website written in a markup language (such as HTML). CSS is useful for making the appearance of websites more attractive.

To learn about the differences between CSS and CSS3, you can read the following [reference](https://www.geeksforgeeks.org/difference-between-css-and-css3/).

### How to Write CSS

In general, CSS can be written in the following form.

```css
selector {
  properties: value;
}
```

Please do independent exploration related to CSS on the following [reference](https://www.w3schools.com/css/).

There are three types of CSS writing:

1. **_Inline Styles_**
2. **_Internal Style Sheet_**
3. **_External Style Sheet_**

Please do independent exploration about these three types of CSS on the following [reference](https://www.geeksforgeeks.org/types-of-css-cascading-style-sheet/).

Note that if you create an External Style Sheet type, you need to add the `{% load static %}` tag to your HTML page. For example, like the code snippet below.

```html
{% load static %}
<html>
  <head>
    <title>Using External Style Sheet</title>
    <link rel="stylesheet" href="{% static 'style.css' %}" />
  </head>
  <body>
    <div>
      <h1>CSS is fun! :D</h1>
    </div>
    <div id="main">
      <div>
        <p>This is Tutorial 4</p>
        <h1><a href="">Great</a></h1>
        <p>An easy tutorial</p>
      </div>
    </div>
  </body>
</html>
```

This can happen because CSS is a static file in Django. Static files will be explained in the next section.

### Additional Notes

If there is more than one style defined for an element, then the style that will be applied is the one with the higher priority. Here's the order of priority, with number 1 having the highest priority.

1. _Inline style_
2. _External_ and internal _style sheets_
3. _Browser default_

## Static files in Django

In the Django framework, there are files called static files. Static files are HTML supporting files on a website. Examples of static files are CSS, JavaScript, and images.

The settings for static files are located in the **`settings.py`** file:

```html 
...
# Static files (CSS, JavaScript, Images)
# Documentation: https://docs.djangoproject.com/en/5.1/howto/static-files/
STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'static'
...
```
In `settings.py`, there are:

- `STATIC_ROOT` which determines the absolute path to the static files directory when running the `collectstatic` command on the project. This `STATIC_ROOT` will be useful for providing a path for static content in production access (`DEBUG=False` in `settings.py`)
- `STATIC_URL` which is the URL that can be publicly accessed to obtain these static files. For example: `http://localhost:8000/static/image/example-image.png`

The `collectstatic` command is a command to collect static files from all apps, making it easier to access for all apps.

A more detailed explanation about static files can be read in the following [reference](https://docs.djangoproject.com/en/5.1/ref/contrib/staticfiles/).

## Selectors in CSS

In this tutorial, we will introduce three types of selectors: **_Element Selector_**, **ID _Selector_**, dan **_Class Selector_**.

1. **Element Selector**

    Element Selector allows us to change properties for all elements that have the same HTML tag.
    
    Example of using Element Selector:
    ```html 
    <body>
      <div>
        <h1>This is h1</h1>
        <h2>This is h2, different from h1 :D</h2>
      </div>
      ...
    </body>
    ```
    We can use the element as a selector in the CSS file. Element selector uses the format *[id_name]* (without being preceded by a symbol)
    
    ```html 
    h1 {
      color: #5bc933;
      font-family: "Times New Roman";
      font-style: normal;
    }
    ```
1. **ID Selector**

    ID Selector uses the ID on the tag as its selector. ID is unique in one web page. ID can be added to the HTML template page.
    
    Example of using ID Selector on HTML template:
    
    ```html 
    <body>
      <div id="header">
        <h1>Playing with ID header</h1>
      </div>
      ...
    </body>
    ```
    
    Kemudian, kita dapat menggunakan ID tersebut sebagai _selector_ dalam **_file_ CSS**. ID _selector_ menggunakan format *#[id_name]* (selalu diawali #)
    Then, we can use that ID as a selector in the CSS file. ID selector uses the format #[id_name] (always preceded by #)
    ```html 
    #header {
      background-color: #a3b90e;
      margin-top: 0;
      padding: 20px 20px 20px 40px;
    }
    ```
    
3. **Class Selector**
    
    Class Selector allows us to group elements with the same characteristics.
    
    Example of using Class Selector on HTML template:
    
    ```html
    ...
    <div id="main">
        <div class="parent_content">
            <p class="date">September 9, 2024</p>
            <h2><a href="">Subject: The Fun of PBP</a></h2>
            <p id="content_1">PBP material is very exciting!</p>
        </div>
        <div class="parent_content">
            <p class="date">September 10, 2024</p>
            <h2><a href="">Subject: PBP Review</a></h2>
            <p id="content_2">To be more proficient, I review PBP material</p>
        </div>
        <div class="parent_content">
            <p class="date">September 11, 2024</p>
            <h2><a href="">Subject: Attending PBP Tutorial</a></h2>
            <p id="content_3">PBP tutorial is very exciting!</p>
        </div>
    </div>
    ...
    ```
    
    Then, we can use that Class as a selector in the CSS file. Class selector uses the format .[class_name] (preceded by .)
    
    ```html
    .content_section {
      background-color: #112a33;
      margin-bottom: 30px;
      color: #0F0F0F;
      font-family: cursive;
      padding: 20px 20px 20px 40px;
    }
    ```
    
To better understand CSS Selector Reference, you can read the following [reference](https://www.w3schools.com/cssref/css_selectors.php).

## CSS Tips & Tricks

### Understanding Combinators in CSS
Combinators in CSS connect two or more selectors to further specify the selected elements.

There are four combinators in CSS. Here's a summary of their usage:
    
| *Combinator* | Example | Explanation |
| -------- | -------- | -------- |
| Descendant selector (space) | `div p`     | Selects all `p` elements that are descendants of `div` elements |
| Child selector (>) | `div > p`     | Selects all `p` elements that are direct children of `div` elements |
| Adjacent sibling selector (+) | `div + p` | Selects the first `p` element that comes immediately after a `div` element (must have the same parent element) |
| General sibling selector (~) | `div ~ p` | Selects all `p` elements that are siblings of and come after `div` elements |

Please do independent exploration about combinators through the following [reference](https://www.w3schools.com/css/css_combinators.asp).

### Understanding Pseudo-classes in CSS
Pseudo-classes are used to define special states of an element. The syntax for using pseudo-classes is as follows:

```css
selector:pseudo-class {
  property: value;
}
```


Some pseudo-class examples:
| Pseudo-class | Styles are applied to ... |
| -------- | -------- |
| `:link` | unvisited links |
| `:visited` | visited links |
| `:hover` | when the user hovers over the element |
| `:active` | when the element is activated (usually when the user clicks the element) |
| `:focus` | when the element has focus (like when the user clicks an input field) |
| `:checked` | checked elements |
| `:disabled` | elements that have been made unresponsive (for example, buttons that can't be clicked) |

Please do independent exploration about pseudo-classes through this [reference](https://www.w3schools.com/css/css_pseudo_classes.asp).

### Understanding Box Model in CSS

![CSS Box Model](/img/4-box-model-css.png)

The box model in CSS is basically a box that wraps around every HTML element and consists of:

* *Content*: the content of the box (where text and images appear)
* *Padding*: clears an area around the content (transparent)
* *Border*: a border that goes around the padding and content
* *Margin*: clears an area outside the border (transparent)

Please do independent exploration about margin, border, and padding through the following [reference](https://w3schools.com/css/css_boxmodel.asp).

## Introduction to Bootstrap & Tailwind

In the field of web development, there are many CSS frameworks that are often used. The function of a framework is to make programmers' work easier when doing their jobs. The popular CSS frameworks today are Bootstrap and Tailwind. Both of these frameworks provide many advantages compared to the CSS we usually use. Here are the advantages of using frameworks compared to regular CSS:

1. Faster Development Process: Frameworks like Bootstrap provide ready-to-use components without having to write CSS code from scratch.
2. Responsive by Default: Frameworks like Bootstrap and Tailwind are designed to be responsive.
3. Easy Customization: Tailwind allows for deep customization. Meanwhile, Bootstrap also offers customization options but with a more limited approach.
4. Large Scalability: CSS frameworks provide a good structure for projects that grow over time.

Bootstrap and Tailwind, of course, as frameworks have significant differences from each other, namely:


| Tailwind | Bootstrap |
| -------- | --------- |
| Tailwind CSS builds appearances by combining pre-defined utility classes.     | Bootstrap uses pre-defined styles and components that have a ready-made appearance and can be used directly.      |
| Tailwind CSS has a slightly smaller CSS file compared to Bootstrap and will only load the utility classes that exist | Bootstrap has a larger CSS file compared to Tailwind CSS because it includes many pre-defined components. |
| Tailwind CSS provides high flexibility and adaptability to projects | Bootstrap often results in a more consistent appearance across projects because it uses pre-defined components. |
| Tailwind CSS has a steeper learning curve because it requires understanding of available utility classes and how to combine them to achieve the desired appearance. | Bootstrap has a faster learning curve for beginners because you can start with pre-defined components. |

## Responsive Web Design

Responsive web design is a web design system method that aims to produce a web display that looks good on all devices such as desktop, tablet, mobile, and so on. Responsive web design does not change the content of the website, but only changes the appearance and layout on each device to fit the screen width and capabilities of that device. In responsive web design, certain displays require CSS assistance (such as shrinking or enlarging) an element. 

One way to test whether a website uses responsive web design is by accessing the website and activating the `Toggle Device Mode` feature in the browser. This feature allows you to see how the website is displayed on various devices, such as computers, tablets, or smartphones, without having to change the size of the browser window.

Here's how to access this feature on **Google Chrome** browser.
* Windows/Linux : Press `CTRL + SHIFT + I` to open Dev Tools, then press `CTRL + SHIFT + M` to activate `Toggle Device Mode`
* Mac : `Command + Shift + M`
 
Another more practical way is to right-click on the browser and select Inspect Element/Inspect to open the useful Dev Tools.

To learn more about Responsive Web Design, you can open this [reference](https://web.dev/responsive-web-design-basics/).

## Tutorial: Adding Tailwind to the Application
In this tutorial, we will focus on using Tailwind in styling our Django application.

1. Open your Django project **(mental_health_tracker)**, then open the `base.html` file that was previously created in the templates folder located in your project root.

2. Inside `templates/base.html`, add the `<meta name="viewport">` tag so that your web page can adjust the size and behavior of mobile devices **(if not already)**.

    ```html
    <head>
        {% block meta %}
            <meta charset="UTF-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1">
        {% endblock meta %}
    </head>
    ```

3. To connect the Django template with Tailwind, we can use the CDN (Content Delivery Network) script from Tailwind to be placed in our Django html template. In `base.html`, you need to add the Tailwind cdn script in the head section.

    ```html
    <head>
    {% block meta %}
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1">
    {% endblock meta %}
    <script src="https://cdn.tailwindcss.com">
    </script>
    </head>
    ```

## Tutorial: Adding Bootstrap to the Application (Skip if Choosing Tailwind)
***Important***: If you choose Bootstrap, you must skip the Tailwind tutorial because CSS class conflicts can occur if combined with Bootstrap.

1. Open your Django project **(mental_health_tracker)**, then open the `base.html` file that was previously created in the templates folder located in your project root.

2. Inside `templates/base.html`, add the `<meta name="viewport">` tag so that your web page can adjust the size and behavior of mobile devices **(if not already)**.

    ```html
    <head>
        {% block meta %}
            <meta charset="UTF-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1">
        {% endblock meta %}
    </head>
    ```

3. Add Bootstrap CSS and JS.

    **CSS:**
    ```html
    <head>
        {% block meta %}
            ...
        {% endblock meta %}
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
    </head>
    ```

    **JS:**
    ```html
    <head>
        ...
        <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha384-KyZXEAg3QhqLMpG8r+J4jsl5c9zdLKaUk5Ae5f5b1bw6AUn5f5v8FZJoMxm6f5cH1" crossorigin="anonymous"></script>
    </head>
    ```


4. **(Optional)** If you want to use dropdowns, popovers, tooltips provided by the Bootstrap framework, you need to add these 2 lines of JS script below the JS script you have created previously.

    ```html
    <head>
        ...
        <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.min.js" integrity="sha384-BBtl+eGJRgqQAUMxJ7pMwbEyER4l1g+O15P+16Ep7Q9Q+zqX6gSbd85u4mG4QzX+" crossorigin="anonymous"></script>
    </head>
    ```

Reference: [Get Started with Bootstrap 5.3](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

## Tutorial: Adding *Edit Mood* Feature to the Application

Here are the things you need to do to add the feature to edit mood data:

1. Open `views.py` in the `main` subdirectory, and create a new function named `edit_mood` that takes `request` and `id` parameters as follows.

    ```python
    def edit_mood(request, id):
        # Get mood entry based on id
        mood = MoodEntry.objects.get(pk = id)

        # Set mood entry as an instance of the form
        form = MoodEntryForm(request.POST or None, instance=mood)

        if form.is_valid() and request.method == "POST":
            # Save form and return to home page
            form.save()
            return HttpResponseRedirect(reverse('main:show_main'))

        context = {'form': form}
        return render(request, "edit_mood.html", context)
    ```

2. Add imports to the `views.py` file (**Remember, only add imports!**)
   ```python
   from django.shortcuts import .., reverse
   from django.http import .., HttpResponseRedirect
   ```

3. Create a new HTML file named `edit_mood.html` in the `main/templates` subdirectory. Fill the file with the following template.

    ```html 
    {% extends 'base.html' %}

    {% load static %}

    {% block content %}

    <h1>Edit Mood</h1>

    <form method="POST">
        {% csrf_token %}
        <table>
            {{ form.as_table }}
            <tr>
                <td></td>
                <td>
                    <input type="submit" value="Edit Mood"/>
                </td>
            </tr>
        </table>
    </form>

    {% endblock %}
    ```

4. Open `urls.py` in the main directory and import the `edit_product` function you've just created.

    ```python
    from main.views import edit_mood
    ```

5. Add a URL path to `urlpatterns` to access the imported function.

    ```python 
    ...
    path('edit-mood/<uuid:id>', edit_mood, name='edit_mood'),
    ...
    ```
:::note
For the `id` data type, adjust it to match the data type of the id attribute in the MoodEntry model. If you're using an integer data type, change the data type to `<int:id>`
:::

7. Open `main.html` in the `main/templates` subdirectory. Add the following code snippet aligned with the last `<td>` element to display an *edit* button on each table row.

    ```html 
    ...
    <tr>
        ...
        <td>
            <a href="{% url 'main:edit_mood' mood_entry.pk %}">
                <button>
                    Edit
                </button>
            </a>
        </td>
    </tr>
    ...
    ```
**Code Explanation**
- `{% url 'main:edit_mood' mood_entry.pk %}` is used to build a URL by adding the primary key (pk) of the `mood_entry` object as a parameter. This parameter will be passed to the `edit_mood` view function, which needs the id value to know which entry to edit.

7. Run your Django project with the command `python manage.py runserver` and open [http://localhost:8000](http://localhost:8000) in your favorite browser. After logging in, try to click the `edit` button on a mood and change its data as you like. If the changes are saved and visible on the main page of the application without any *errors*, then congratulations, you have successfully added the *edit* feature!

## Tutorial: Adding *Delete Mood* Feature to the Application

Here are the things you need to do to add the feature to delete mood data:

1. Create a new function named `delete_mood` that takes `request` and `id` parameters in `views.py` in the `main` folder to delete mood data. You can use the following code.

    > Don't forget to try to understand the code 😅

    ```python
	def delete_mood(request, id):
	    # Get mood based on id
	    mood = MoodEntry.objects.get(pk = id)
	    # Delete mood
	    mood.delete()
	    # Return to home page
	    return HttpResponseRedirect(reverse('main:show_main'))
    ```

2. Open `urls.py` in the `main` folder and import the function you just created.

    ```python
    from main.views import delete_mood
    ```

3. Add a URL path to `urlpatterns` to access the imported function.

    ```python
    ...
    path('delete/<uuid:id>', delete_mood, name='delete_mood'), # adjust to the name of the function you created
    ...
    ```
:::note
For the `id` data type, adjust it to match the data type of the id attribute in the MoodEntry model. If you're using an integer data type, change the data type to `<int:id>`
:::

4. Open the `main.html` file in the `main/templates` folder and modify the existing code to be like this so that there's a delete button for each product.

    ```html 
    ...
    <tr>
        ...
        <td>
            <a href="{% url 'main:edit_mood' mood_entry.pk %}">
                <button>
                    Edit
                </button>
            </a>
        </td>
        <td>
            <a href="{% url 'main:delete_mood' mood_entry.pk %}">
                <button>
                    Delete
                </button>
            </a>
        </td>
    </tr>
    ...
    ```

5. Run your Django project with the command `python manage.py runserver` and open [http://localhost:8000](http://localhost:8000) in your favorite browser. After logging in, try to delete a mood data and refresh the page. If the mood disappears from the main page of your application without any errors, then congratulations, you have successfully added the delete feature!

## Tutorial: Adding Navigation Bar to the Application
A Navigation Bar (navbar) is an element typically used to navigate various pages or features in a web application. The navbar is usually placed at the top of the page and contains links or buttons that lead to other pages in the application.

- Create a new HTML file named `navbar.html` in the `templates/` folder in the root directory. You can fill the `navbar.html` with the following template.
```html
<nav class="bg-indigo-600 shadow-lg fixed top-0 left-0 z-40 w-screen">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <div class="flex items-center">
          <h1 class="text-2xl font-bold text-center text-white">Mental Health Tracker</h1>
        </div>
        <div class="hidden md:flex items-center">
          {% if user.is_authenticated %}
            <span class="text-gray-300 mr-4">Welcome, {{ user.username }}</span>
            <a href="{% url 'main:logout' %}" class="text-center bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded transition duration-300">
              Logout
            </a>
          {% else %}
            <a href="{% url 'main:login' %}" class="text-center bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition duration-300 mr-2">
              Login
            </a>
            <a href="{% url 'main:register' %}" class="text-center bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded transition duration-300">
              Register
            </a>
          {% endif %}
        </div>
        <div class="md:hidden flex items-center">
          <button class="mobile-menu-button">
            <svg class="w-6 h-6 text-white" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
              <path d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
    <!-- Mobile menu -->
    <div class="mobile-menu hidden md:hidden  px-4 w-full md:max-w-full">
      <div class="pt-2 pb-3 space-y-1 mx-auto">
        {% if user.is_authenticated %}
          <span class="block text-gray-300 px-3 py-2">Welcome, {{ user.username }}</span>
          <a href="{% url 'main:logout' %}" class="block text-center bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded transition duration-300">
            Logout
          </a>
        {% else %}
          <a href="{% url 'main:login' %}" class="block text-center bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition duration-300 mb-2">
            Login
          </a>
          <a href="{% url 'main:register' %}" class="block text-center bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded transition duration-300">
            Register
          </a>
        {% endif %}
      </div>
    </div>
    <script>
      const btn = document.querySelector("button.mobile-menu-button");
      const menu = document.querySelector(".mobile-menu");
    
      btn.addEventListener("click", () => {
        menu.classList.toggle("hidden");
      });
    </script>
  </nav>
```
:::note For this tutorial, you don't have to understand how `<script>` works. You will learn about the use of `<script>` in tutorial 5 next week.
:::

- Then, link the navbar to `main.html`, `create_mood_entry.html`, and `edit_mood.html` in the `main/templates/` subdirectory using the include `tags`:
    ```html
    {% extends 'base.html' %}
    {% block content %}
    {% include 'navbar.html' %}
    ...
    {% endblock content%}
    ```

:::note The `...` sign indicates other code in the file that doesn't need to be changed
:::

Here are some additional references on how to create a navigation bar that you can use:

- Using Tailwind: can be accessed through this [link](https://tailwindui.com/components/application-ui/navigation/navbars)
- Using Bootstrap: can be accessed through this [link](https://getbootstrap.com/docs/5.3/components/navbar/)
- Using manual CSS: can be accessed through this [link](https://www.w3schools.com/css/css_navbar.asp)

## Tutorial: Configuring Static Files in the Application

1. In `settings.py`, add the WhiteNoise middleware.
```python
...
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware', # Add it directly under SecurityMiddleware
    ...
]
...
```
By adding the WhiteNoise middleware to `settings.py`, Django can automatically manage static files in production mode (`DEBUG=False`) without needing complex configuration. This is useful so that static files can be accessed in your deployment because by default, if `DEBUG=False` then Django will not provide access to static files.

2. In `settings.py`, ensure that the `STATIC_ROOT`, `STATICFILES_DIRS`, and `STATIC_URL` variables are configured like this (if they don't exist, you can just add them):
```python
...
STATIC_URL = '/static/'
if DEBUG:
    STATICFILES_DIRS = [
        BASE_DIR / 'static' # refers to /static root project in development mode
    ]
else:
    STATIC_ROOT = BASE_DIR / 'static' # refers to /static root project in production mode
...
```

## Optional: Adding Styles to the Application with Tailwind and External CSS
:::note
This section is optional and you can skip it if you want to be creative in decorating the application yourself. If you want to try the teaching assistants' creation, you can follow the steps given in this section.
:::
### Add `global.css`
Create a `global.css` file in `/static/css` in the root directory like this:
![Global CSS Path](/img/4-global-css-path.png)
In this `global.css` file, you can add custom classes or CSS styles that you have defined yourself.

### Link `global.css` and Tailwind script to base.html
For the CSS styles added in `global.css` to be used in Django templates, you need to add that file to `base.html`.
Modify your `base.html` file as follows:
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    {% block meta %} {% endblock meta %}
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="{% static 'css/global.css' %}"/>
  </head>
  <body>
    {% block content %} {% endblock content %}
  </body>
</html>
```

### Adding custom styling to global.css
Modify the `global.css` file in `static/css/global.css` as follows:
```css 
.form-style form input, form textarea, form select {
    width: 100%;
    padding: 0.5rem;
    border: 2px solid #bcbcbc;
    border-radius: 0.375rem;
}
.form-style form input:focus, form textarea:focus, form select:focus {
    outline: none;
    border-color: #674ea7;
    box-shadow: 0 0 0 3px #674ea7;
}
@keyframes shine {
    0% { background-position: -200% 0; }
    100% { background-position: 200% 0; }
}
.animate-shine {
    background: linear-gradient(120deg, rgba(255, 255, 255, 0.3), rgba(255, 255, 255, 0.1) 50%, rgba(255, 255, 255, 0.3));
    background-size: 200% 100%;
    animation: shine 3s infinite;
}
```

### Styling the Login Page
Change the `login.html` file in the `main/templates/` subdirectory to be as follows:
``` html
{% extends 'base.html' %}

{% block meta %}
<title>Login</title>
{% endblock meta %}

{% block content %}
<div class="min-h-screen flex items-center justify-center w-screen bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
  <div class="max-w-md w-full space-y-8">
    <div>
      <h2 class="mt-6 text-center text-black text-3xl font-extrabold text-gray-900">
        Login to your account
      </h2>
    </div>
    <form class="mt-8 space-y-6" method="POST" action="">
      {% csrf_token %}
      <input type="hidden" name="remember" value="true">
      <div class="rounded-md shadow-sm -space-y-px">
        <div>
          <label for="username" class="sr-only">Username</label>
          <input id="username" name="username" type="text" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Username">
        </div>
        <div>
          <label for="password" class="sr-only">Password</label>
          <input id="password" name="password" type="password" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Password">
        </div>
      </div>

      <div>
        <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Sign in
        </button>
      </div>
    </form>

    {% if messages %}
    <div class="mt-4">
      {% for message in messages %}
      {% if message.tags == "success" %}
            <div class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% elif message.tags == "error" %}
            <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% else %}
            <div class="bg-blue-100 border border-blue-400 text-blue-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% endif %}
      {% endfor %}
    </div>
    {% endif %}

    <div class="text-center mt-4">
      <p class="text-sm text-black">
        Don't have an account yet?
        <a href="{% url 'main:register' %}" class="font-medium text-indigo-200 hover:text-indigo-300">
          Register Now
        </a>
      </p>
    </div>
  </div>
</div>
{% endblock content %}
```
![Example of Login Page](/img/4-contoh-tampilan-login-page.png)

### Styling the Register Page
Modify the `register.html` file in the `main/templates/` subdirectory as follows:
``` html
{% extends 'base.html' %}

{% block meta %}
<title>Register</title>
{% endblock meta %}

{% block content %}
<div class="min-h-screen flex items-center justify-center bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
  <div class="max-w-md w-full space-y-8 form-style">
    <div>
      <h2 class="mt-6 text-center text-3xl font-extrabold text-black">
        Create your account
      </h2>
    </div>
    <form class="mt-8 space-y-6" method="POST">
      {% csrf_token %}
      <input type="hidden" name="remember" value="true">
      <div class="rounded-md shadow-sm -space-y-px">
        {% for field in form %}
          <div class="{% if not forloop.first %}mt-4{% endif %}">
            <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-black">
              {{ field.label }}
            </label>
            <div class="relative">
              {{ field }}
              <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                {% if field.errors %}
                  <svg class="h-5 w-5 text-red-500" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
                  </svg>
                {% endif %}
              </div>
            </div>
            {% if field.errors %}
              {% for error in field.errors %}
                <p class="mt-1 text-sm text-red-600">{{ error }}</p>
              {% endfor %}
            {% endif %}
          </div>
        {% endfor %}
      </div>

      <div>
        <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Register
        </button>
      </div>
    </form>

    {% if messages %}
    <div class="mt-4">
      {% for message in messages %}
      <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
        <span class="block sm:inline">{{ message }}</span>
      </div>
      {% endfor %}
    </div>
    {% endif %}

    <div class="text-center mt-4">
      <p class="text-sm text-black">
        Already have an account?
        <a href="{% url 'main:login' %}" class="font-medium text-indigo-200 hover:text-indigo-300">
          Login here
        </a>
      </p>
    </div>
  </div>
</div>
{% endblock content %}
```
![Example Register Page](/img/4-contoh-tampilan-register-page.png)

### Styling the Home Page
1. Create a `card_info.html` file in the `main/templates` directory, then add the following HTML code:
```html
<div class="bg-indigo-700 rounded-xl overflow-hidden border-2 border-indigo-800">
    <div class="p-4 animate-shine">
      <h5 class="text-lg font-semibold text-gray-200">{{ title }}</h5>
      <p class="text-white">{{ value }}</p>
    </div>
</div>
```
![Example of Card Info](/img/4-contoh-tampilan-card-info.png)

> **Note:** This is an example display of the `card_info.html` element

2. Create a `card_mood.html` file in the `main/templates` directory, then add the following HTML code:
```html
<div class="relative break-inside-avoid">
  <div class="absolute top-2 z-10 left-1/2 -translate-x-1/2 flex items-center -space-x-2">
    <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
    <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
  </div>
  <div class="relative top-5 bg-indigo-100 shadow-md rounded-lg mb-6 break-inside-avoid flex flex-col border-2 border-indigo-300 transform rotate-1 hover:rotate-0 transition-transform duration-300">
    <div class="bg-indigo-200 text-gray-800 p-4 rounded-t-lg border-b-2 border-indigo-300">
      <h3 class="font-bold text-xl mb-2">{{mood_entry.mood}}</h3>
      <p class="text-gray-600">{{mood_entry.time}}</p>
    </div>
    <div class="p-4">
      <p class="font-semibold text-lg mb-2">My Feeling</p> 
      <p class="text-gray-700 mb-2">
        <span class="bg-[linear-gradient(to_bottom,transparent_0%,transparent_calc(100%_-_1px),#CDC1FF_calc(100%_-_1px))] bg-[length:100%_1.5rem] pb-1">{{mood_entry.feelings}}</span>
      </p>
      <div class="mt-4">
        <p class="text-gray-700 font-semibold mb-2">Intensity</p>
        <div class="relative pt-1">
          <div class="flex mb-2 items-center justify-between">
            <div>
              <span class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-indigo-600 bg-indigo-200">
                {% if mood_entry.mood_intensity > 10 %}10+{% else %}{{mood_entry.mood_intensity}}{% endif %}
              </span>
            </div>
          </div>
          <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
            <div style="width:{% if mood_entry.mood_intensity > 10 %}100%{% else %}{{ mood_entry.mood_intensity }}0%{% endif %}" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="absolute top-0 -right-4 flex space-x-1">
    <a href="{% url 'main:edit_mood' mood_entry.pk %}" class="bg-yellow-500 hover:bg-yellow-600 text-white rounded-full p-2 transition duration-300 shadow-md">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
        <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
      </svg>
    </a>
    <a href="{% url 'main:delete_mood' mood_entry.pk %}" class="bg-red-500 hover:bg-red-600 text-white rounded-full p-2 transition duration-300 shadow-md">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" />
      </svg>
    </a>
  </div>
</div>
```
![Example of Card Mood](/img/4-contoh-tampilan-card-mood.png)
> **Note:** This is an example display of the `card_mood.html` element
Next, we need a display if the mood_entry is still empty. Choose a sad photo or icon and name it `very-sad.png`. You are free to choose any photo. Add the `very-sad.png` photo to the `static/image` directory in the project root.
4. After everything is done, we need to use `card_info.html`, `card_mood.html`, and `very-sad.png` in the `main.html` template. In the `main/templates` directory, modify `main.html` like this:
```html 
{% extends 'base.html' %}
{% load static %}

{% block meta %}
<title>Mental Health Tracker</title>
{% endblock meta %}
{% block content %}
{% include 'navbar.html' %}
<div class="overflow-x-hidden px-4 md:px-8 pb-8 pt-24 min-h-screen bg-gray-100 flex flex-col">
  <div class="p-2 mb-6 relative">
    <div class="relative grid grid-cols-1 z-30 md:grid-cols-3 gap-8">
      {% include "card_info.html" with title='NPM' value=npm %}
      {% include "card_info.html" with title='Name' value=name %}
      {% include "card_info.html" with title='Class' value=class %}
    </div>
    <div class="w-full px-6  absolute top-[44px] left-0 z-20 hidden md:flex">
      <div class="w-full min-h-4 bg-indigo-700">
      </div>
    </div>
    <div class="h-full w-full py-6  absolute top-0 left-0 z-20 md:hidden flex ">
      <div class="h-full min-w-4 bg-indigo-700 mx-auto">
      </div>
    </div>
</div>
    <div class="px-3 mb-4">
      <div class="flex rounded-md items-center bg-indigo-600 py-2 px-4 w-fit">
        <h1 class="text-white text-center">Last Login: {{last_login}}</h1>
      </div>
    </div>
    <div class="flex justify-end mb-6">
        <a href="{% url 'main:create_mood_entry' %}" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105">
            Add New Mood Entry
        </a>
    </div>
    
    {% if not mood_entries %}
    <div class="flex flex-col items-center justify-center min-h-[24rem] p-6">
        <img src="{% static 'image/very-sad.png' %}" alt="Sad face" class="w-32 h-32 mb-4"/>
        <p class="text-center text-gray-600 mt-4">There is no mood data in mental health tracker.</p>
    </div>
    {% else %}
    <div class="columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6 w-full">
        {% for mood_entry in mood_entries %}
            {% include 'card_mood.html' with mood_entry=mood_entry %}
        {% endfor %}
    </div>
    {% endif %}
</div>
{% endblock content %}
```

The display of [http://localhost:8000](http://localhost:8000) will change to look like this:
![Example of Main Page when not in the mood](/img/4-contoh-tampilan-main-page-empty.png)

![Example of Main Page when in the mood](/img/4-contoh-tampilan-main-page.png)

### Styling the Create Mood Entry Page
6. Modify the `create_mood_entry.html` file in the `main/templates` subdirectory as follows:
```html
{% extends 'base.html' %}
{% load static %}
{% block meta %}
<title>Create Mood</title>
{% endblock meta %}

{% block content %}
{% include 'navbar.html' %}

<div class="flex flex-col min-h-screen bg-gray-100">
  <div class="container mx-auto px-4 py-8 mt-16 max-w-xl">
    <h1 class="text-3xl font-bold text-center mb-8 text-black">Create Mood Entry</h1>
  
    <div class="bg-white shadow-md rounded-lg p-6 form-style">
      <form method="POST" class="space-y-6">
        {% csrf_token %}
        {% for field in form %}
          <div class="flex flex-col">
            <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-gray-700">
              {{ field.label }}
            </label>
            <div class="w-full">
              {{ field }}
            </div>
            {% if field.help_text %}
              <p class="mt-1 text-sm text-gray-500">{{ field.help_text }}</p>
            {% endif %}
            {% for error in field.errors %}
              <p class="mt-1 text-sm text-red-600">{{ error }}</p>
            {% endfor %}
          </div>
        {% endfor %}
        <div class="flex justify-center mt-6">
          <button type="submit" class="bg-indigo-600 text-white font-semibold px-6 py-3 rounded-lg hover:bg-indigo-700 transition duration-300 ease-in-out w-full">
            Create Mood Entry
          </button>
        </div>
      </form>
    </div>
  </div>
</div>

{% endblock %}
```
![Example of Create Mood Entry Page](/img/4-contoh-tampilan-create-mood-entry-page.png)

### Styling the Edit Mood Page
7. Modify the `edit_mood.html` file in the `main/templates` subdirectory as follows:
```html
{% extends 'base.html' %}
{% load static %}
{% block meta %}
<title>Edit Mood</title>
{% endblock meta %}

{% block content %}
{% include 'navbar.html' %}
<div class="flex flex-col min-h-screen bg-gray-100">
  <div class="container mx-auto px-4 py-8 mt-16 max-w-xl">
    <h1 class="text-3xl font-bold text-center mb-8 text-black">Edit Mood Entry</h1>
  
    <div class="bg-white rounded-lg p-6 form-style">
      <form method="POST" class="space-y-6">
          {% csrf_token %}
          {% for field in form %}
              <div class="flex flex-col">
                  <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-gray-700">
                      {{ field.label }}
                  </label>
                  <div class="w-full">
                      {{ field }}
                  </div>
                  {% if field.help_text %}
                      <p class="mt-1 text-sm text-gray-500">{{ field.help_text }}</p>
                  {% endif %}
                  {% for error in field.errors %}
                      <p class="mt-1 text-sm text-red-600">{{ error }}</p>
                  {% endfor %}
              </div>
          {% endfor %}
          <div class="flex justify-center mt-6">
              <button type="submit" class="bg-indigo-600 text-white font-semibold px-6 py-3 rounded-lg hover:bg-indigo-700 transition duration-300 ease-in-out w-full">
                  Edit Mood Entry
              </button>
          </div>
      </form>
  </div>
  </div>
</div>
{% endblock %}
```
![Example of Edit Mood Entry Page](/img/4-contoh-tampilan-edit-mood-entry-page.png)

## Closing
- After following the tutorial above, you should have a local directory structure as follows.
 
   ```
   mental-health-tracker
   ├── .github\workflows
   │   └── push.yml
   ├── env    
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   ├── 0002_alter_moodentry_id.py
   │   │   └── 0003_moodentry_user.py   
   │   ├── templates
   │   │   ├── create_mood_entry.html
   │   │   ├── card_info.html
   │   │   ├── card_mood.html
   │   │   ├── edit_mood.html
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
   │   └── navbar.html
   ├── static
   │   └── css
   │       └── global.css
   │   └── image
   │       └── very-sad.png
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
   ```

## Contributor

- Isa Citra Buana
- Williams
- Ravie Hasan Abud
- Abbilhaidar Farras Zulfikar
- Alfredo Austin
- Juan Maxwell Tanaya
- Adrian Hakim Utomo (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
