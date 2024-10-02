---
sidebar_label: Tutorial 5
sidebar_position: 7
Path: docs/tutorial-5
---

# Tutorial 5: JavaScript and AJAX

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students are expected to be able to:

- Understand the usage of JavaScript in the context of front-end development
- Understand the basics of JavaScript
- Apply AJAX and Fetch API safely

## JavaScript

### Introduction to JavaScript

JavaScript is a high-level, multi-paradigm programming language. The multi-paradigm feature of JavaScript allows it to support object-oriented programming, imperative programming, and functional programming. JavaScript itself is an implementation of ECMAScript, that serves as a baseline for the JavaScript language. Other implementations of ECMAScript that is similar to JavaScript are JScript (Microsoft) and ActionScript (Adobe).

JavaScript, with HTML and CSS, is one of the three main technologies used in web development. The benefit of using JavaScript in web development is that dynamic page manipulation can be done and interaction between web pages and users can be increased. That is why most modern websites are using JavaScript on their web page to give the best experience to the user. Some things that we could do with JavaScript are to display information based on time, recognizing the type of device used, do validation on forms or data, creating cookies (not literally, but [HTTP cookies](https://en.wikipedia.org/wiki/HTTP_cookie)), change the CSS of an element dynamically, etc.

Usually, JavaScript is used on the client-side of a web (client-side JavaScript), but there are some types of JavaScript that are used on the server-side of a web (server-side JavaScript) like **node.js**. Client-side means that the JavaScript code will be executed on the user's system, not on the website's server. This means that the JavaScript code complexity will not affect the server's performance but will affect the user's system performance; where more complex JavaScript will force the browser to use more memory.

In the PBD course, we will only focus on the client-side JavaScript.

### JavaScript Execution by Browser

Take a look at the diagram below to understand how JavaScript execution is done by the browser.

![javascript-works](https://i.imgur.com/PvPYhB5.png)

After the browser downloads the HTML web page, the browser will look for the `<script></script>` tag, and the browser will see the tag script if the tag contains embedded JavaScript or external JavaScript. If the script tag refers to an external JavaScript code, the browser will download that file first.

### JavaScript Writing

JavaScript could be added as an **embedded JavaScript** or **external JavaScript**. JavaScript code could be defined or written as an *embedded* code in an HTML file or as a separate file. If written outside of the HTML, the file extension for the JavaScript file is `.js`. Below is an example of how to define a JavaScript code.

JavaScript could be placed in the head or body of an HTML file. In addition, the JavaScript code **must** be placed between the `<script>` and `</script>` tags. You can place more than one script tag containing JavaScript code in an HTML file.

#### Embedded JavaScript pada HTML

```html title="index.html"
<script type="text/JavaScript">
    alert("Hello World!");
</script>
```

#### External JavaScript pada HTML

```html title="index.html"
<script type="text/JavaScript" src="js/script.js"></script>
```

```javascript title="js/script.js"
alert("Hello World!");
```

On the external JavaScript file, the `<script>` tag is no longer needed.

Separating JavaScript from the external file can provide several benefits like the code can be used in other HTML files, JavaScript and HTML do not conflict, so the focus is on developing the application, and the page loading speed can be improved. `.js` files are usually cached by the browser so that if we open the page again and there is no changes on the `.js` file, then the browser will not request the file to the server again but it will use the cached file that has been stored.

### JavaScript Execution

After the JavaScript code has been loaded, then the browser will start executing the JavaScript code. If the code is not event-triggered, then it will be executed immediately. If the code is event-triggered, then it will only be executed if the defined event is triggered.

```javascript
// immediately executed
alert("Hello World");

// immediately executed
var obj = document.getElementById("object");
// immediately executed, adding an event handler for the onclick event to the object
obj.onclick = function () {
    // only executed if the 'object' element is clicked
    alert("You just clicked the object!");
};
```

### JavaScript Syntax

#### Variables

Defining variables in JavaScript is very easy. Here is an example.

```javascript
var example = 0; // var example is a number
var example = "example"; // var example is a string
var example = true; // var example is a boolean
```

JavaScript can hold many types of data; from strings, integers, even objects. Unlike Java, which uses data types, JavaScript has a loosely typed or dynamic language, meaning that you do not need to specify the type of data in the head variable (for example, if you want to create a variable with type data `int`, the syntax would be `int x = 9`), JavaScript will automatically read the type of data based on the standard (as shown in the example above).

There are some rules in choosing the identifiers or variable names in JavaScript. The first character **must** be an alphabet, underscore (`_`), or dollar sign (`$`). In addition, JavaScript identifiers are case sensitive.

#### String Concatenation

In JavaScript, we can also concatenate `string` with `string` like in Java.

```javascript
var str1 = "PBP" + " " + "Fun";
var str2 = "PBP";
var str3 = "Fun";
var str4 = str2 + " " + str3;
var str5 = "Fun";
var str6 = `PBP ${str5}`;  // Has the same result as "PBP" + " " + str5
```

### JavaScript Scopes

#### Local Variables

Variables defined **within** a function are scoped locally, so only the code within the function can access the variable.

```javascript
// code outside the thisFunction() function cannot access the courseName variable
function thisFunction() {
    var courseName = "PBP";
    // code within the thisFunction() function can access the courseName variable
}
```

#### Global Variables

Variables defined **outside** a function are global and can be accessed by other JavaScript code in the same file.

```javascript
var courseName = "PBP";
function thisFunction() {
    // code within the thisFunction() function can access the courseName variable
}
```

#### Auto Global Variables

Value assigned to a variable that has not been declared automatically becomes a global variable, even though the variable is within a function.

```javascript
thisFunction(); // thisFunction() function must be called first
console.log(courseName); // print "PBP" to the JavaScript console
function thisFunction() {
    courseName = "PBP";
}
```

#### Accessing Global Variables from HTML

You can access variables that are in JavaScript files in HTML files that load the JavaScript file.

```html
...
<input type="text" onclick="this.value=courseName" />
...
```

```javascript
...
var courseName = "PBP";
...
```

### Function and Event

Function is a group of code that can be called anywhere in the code program (similar to `method` in Java). This reduces redundancy of code (reducing code that can be repeated). Other than that, functions in JavaScript are useful to dynamically invoke elements. Functions can be called by another function or triggered by an event (which will be explained below). Below is an example of an `index.html` file.

```html title="index.html"
...
<input type="button" value="magicButton" id="magicButton" onclick="hooray();" />
...
```

Here is the code in `javascript.js`.

```javascript title="javascript.js"
...
function hooray() {
    alert("Yahoo!");
}
...
```

If `magicButton` is pressed, then the `onclick` function will run the `hooray()` function in `javascript.js`, then the *alert* will be displayed according to what was previously assigned.

The `onclick` code is an example of JavaScript's *event*. An *event* is JavaScript's ability to create a dynamic website. The meaning of `onclick` is to indicate what will happen to JavaScript if the element is pressed. Other than that, events are usually associated with a function that could be used as commands in JavaScript. There are also other examples of events such as `onchange`, `onmouseover`, `onmouseout`, and others, that you can read more [here](https://www.w3schools.com/js/js_events.asp).

### JavaScript DOM

#### HTML DOM

HTML DOM (Document Object Model) is a standard of how to change, take, and delete HTML elements. HTML DOM can be accessed through JavaScript or other programming languages. The details can be found [here](https://www.w3schools.com/js/js_htmldom.asp).

Here is an implementation example.

```html
...     
<div>
    <p onclick="myFunction()" id="demo">Example of HTML DOM</p>
</div>
...
```

```javascript
...
function myFunction() {
    document.getElementById("demo").innerHTML = "YOU CLICKED ME!";
}
...
```

#### CSS DOM

Similar to HTML DOM, CSS DOM can change CSS dynamically through JavaScript. The details can be found [here](https://www.w3schools.com/js/js_htmldom_css.asp).

Here is an implementation example.

```html title="index.html"
...
<p id="blueText" onclick="changeColor()">Click me v2</p>
...
```

```javascript title="javascript.js"
...
function changeColor(){
    document.getElementById("blueText").style.color="blue";
}
...
```

## AJAX

### Introduction to AJAX

AJAX is an abbreviation of ***A**synchronous **J**avaScript **A**nd **X**ML*.

AJAX is not a programming language, but a technology that provides the browser (to request data from the web server) with JavaScript and HTML DOM (to display data). AJAX can use XML to send data, but AJAX can also use text or JSON to send data. AJAX allows a web page to fetch data asynchronously by sending data to the server in the background. This means that we can update parts of a page without having to refresh the entire page.

Here is a diagram of how AJAX works.

![ajax-works](https://www.w3schools.com/js/pic_ajax.gif)

1. An event occurs on the web page (for example, the *submit data* button is pressed)
2. A `XMLHttpRequest` object is created by JavaScript
3. The `XMLHttpRequest` object sends the request to the server
4. The server processes the request
5. The server returns the response back to the web page
6. The response is read by JavaScript
7. The next action will be triggered by JavaScript according to the step that was made (for example, update the data on the page)

`XMLHttpRequest` was previously a standard way to make an AJAX request in JavaScript. However, XMLHttpRequest has some drawbacks, such as cumbersome handling when working with promises and callbacks, and limited support for modern code patterns.

Therefore, `fetch()` was introduced as a new API for making HTTP requests with a simpler syntax and direct support for promises. This allows developers to write code that is easier to read, manage, and better aligned with modern asynchronous paradigms like async/await. `fetch()` is also more flexible in handling other data formats such as JSON, and provides a better API for handling errors and HTTP responses. Further explanation of the differences between `fetch` and `XMLHttpRequest` can be found [here](https://www.tutorialspoint.com/ajax/fetch_api_vs_xmlhttprequest.htm).

On this course, you will be performing AJAX on a web browser using the `fetch()` function provided by JavaScript. In general, the use of `fetch()` for making AJAX calls can be seen [here](https://www.w3schools.com/jsref/api_fetch.asp).

### Fetch API

Fetch API is a new API that was introduced in ECMAScript 2020 as a new standard for making requests with `Promise`. Fetch API provides an interface for obtaining data sources (including all networks). It is a more flexible and powerful replacement of [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest). The Fetch API generally used to implement AJAX more easily than with `XMLHttpRequest`. Additionally, the Fetch API supports more HTTP methods and headers compared to traditional AJAX.

The `fetch()` function has several parameters, including:

- `url`: The URL of the data source that will be requested
- `method`: The HTTP method that will be used
- `headers`: The HTTP headers that will be sent
- `body`: The content of the request

The `fetch()` function returns an `Response` object. The `Response` object has several properties, including:

- `status`: The `status` code of the response
- `headers`: The HTTP headers of the response
- `body`: The content of the response

You can learn more about the Fetch API [here](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).

### Async and Await Functions

Before learning how to use the `fetch()` function, it's recommended that we first learn about the `async` and `await` functions which allow us to implement AJAX without the need to use an external library, such as [jQuery](https://jquery.com/).

The `async` and `await` functions are new functions introduced in ECMAScript 2017. The `async` function is used to indicate a function as an asynchronous function, while the `await` function is used to wait for the result of an `async` function.

You can learn more about the `async` and `await` functions at [this](https://www.w3schools.com/js/js_async.asp) link.

### Using Fetch API

The Fetch API provides a JavaScript interface to access and manipulate parts of the protocol, such as requests and responses. The API also provides the `fetch()` global method that provides an easy and reliable way to fetch data asynchronously across the entire network.

Unlike `XMLHttpRequest`, which is based on callbacks, Fetch API is based on `Promise` and provides an alternative that is easier and more reliable to use in *service worker*. This API also integrates advanced HTTP concepts such as CORS and other extensions to HTTP.

Here is an example of using Fetch API with the `async` and `await` functions to perform AJAX.

```javascript
async function fetchData() {
    const response = await fetch("https://hp-api.onrender.com/api/characters");
    const data = await response.json();
    return data;
}

const characters = await fetchData();
console.log(characters);
```

The code above will perform an AJAX request to request data from the Harry Potter characters API asynchronously. The AJAX request will store the result in the `characters` variable.

You can learn more about the Fetch API at [this link](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

## Tutorial: Adding Error Message to Login
To make the login process easier for your users, provide a conditional to the `login_user` view in your application as such.

```python title="main/views.py"
...
if form.is_valid():
    user = form.get_user()
    login(request, user)
    response = HttpResponseRedirect(reverse("main:show_main"))
    response.set_cookie('last_login', str(datetime.datetime.now()))
    return response
else:
    messages.error(request, "Invalid username or password. Please try again.")
...
```

**Code Explanation:**

- `messages.error(request, msg)` will "render" an error message to the `request` that is sending the login request, which will then be displayed in the `login.html` template.

## Tutorial: Creating Function to Add a Mood with AJAX

In this section, you will create a function in the views to add a new mood to the data base with AJAX.

1. Add the following two imports to the `views.py` file.
    ```python title="main/views.py"
    from django.views.decorators.csrf import csrf_exempt
    from django.views.decorators.http import require_POST
    ```

2. Create a new function in the `views.py` file with the name `add_mood_entry_ajax` that receives the `request` parameter as follows.

    ```python title="main/views.py"
    ...
    @csrf_exempt
    @require_POST
    def add_mood_entry_ajax(request):
        mood = request.POST.get("mood")
        feelings = request.POST.get("feelings")
        mood_intensity = request.POST.get("mood_intensity")
        user = request.user

        new_mood = MoodEntry(
            mood=mood, feelings=feelings,
            mood_intensity=mood_intensity,
            user=user
        )
        new_mood.save()

        return HttpResponse(b"CREATED", status=201)
        ...
    ```
    
    **Code Explanation**:
    - The `csrf_exempt` decorator tells Django to not check the `csrf_token` in the `POST` request that is sent to the function.
    - The `require_POST` decorator makes the function only accessible when the user sends a `POST` request to the function. If the user sends a request with a method other than that, then a `405 Method Not Allowed` error will be returned.
    - `mood = request.POST.get("mood")` and similarly used to retrieve data sent by the user through the `POST` request manually.
    - `new_mood = MoodEntry(...)` is an object `Mood` new that is created manually based on the datas sent from the `POST` request.

## Tutorial: Add Routing For `add_mood_entry_ajax`

1. Open `urls.py` on the `main` subdirectory and import the function that you have already made.
    ```python title="main/urls.py"
    from main.views import ..., add_mood_entry_ajax
    ```

2. Add the URL path inside of `urlpatterns` to allow access to the functions that has been imported.
    ```python title="main/urls.py"
    urlpatterns = [
        ...
        path('create-mood-entry-ajax', add_mood_entry_ajax, name='add_mood_entry_ajax'),
    ]
    ```

## Tutorial: Displaying Mood Entry Data with `fetch()` API

1. Open the `views.py` file and **remove the two lines** below.
    ```python title="main/views.py"
    mood_entries = MoodEntry.objects.filter(user=request.user)
    ```
    and
    ```python title="main/views.py"
    'mood_entries': mood_entries,
    ```
    In this tutorial, we will fetch the **Mood Entry** objects from the `/json` endpoint, therefore the code above is no longer required.

2. Open the `views.py` file and change the first line of the `show_json` and `show_xml` functions as follows.

    ```python title="main/views.py"
    data = MoodEntry.objects.filter(user=request.user)
    ```
3. Open the `main.html` file and remove the `mood_entries` block conditional to display the card_mood when empty. This is the code snippet that you have to remove.

    ```html title="main/templates/main.html"
    ...
        {% if not mood_entries %}
            <div class="flex flex-col items-center justify-center min-h-[24rem] p-6">
                <img src="{% static 'image/sedih-banget.png' %}" alt="Sad face" class="w-32 h-32 mb-4"/>
                <p class="text-center text-gray-600 mt-4">No mood data on the mental health tracker yet</p>
            </div>
        {% else %}
            <div class="columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6 w-full">
                {% for mood_entry in mood_entries %}
                    {% include 'card_mood.html' with mood_entry=mood_entry %}
                {% endfor %}
            </div>
        {% endif %}
    ...
    ```
    After removing the code snippet above, add this code snippet on the same place.

    ```html title="main/templates/main.html"
    <div id="mood_entry_cards"></div>
    ```

4. Create a `<script>` block below the file (before `{% endblock content %}`) and create a new function in the `<script>` block with the name `getMoodEntries`.

    ```html title="main/templates/main.html"
    <script>
      async function getMoodEntries(){
          return fetch("{% url 'main:show_json' %}").then((res) => res.json())
      }
    </script>
    ```
    **Code Explanation:**
    - This function uses the `fetch()` API to fetch the JSON data asynchronously.
    - After the data is fetched, the `then()` function is used to parse the JSON data into a JavaScript object.

5. Create a **new function** on the `<script>` block with the name `refreshMoodEntries` that is used to refresh moods data asynchronously.

    ```html title="main/templates/main.html"
    <script>
        ...
     async function refreshMoodEntries() {
        document.getElementById("mood_entry_cards").innerHTML = "";
        document.getElementById("mood_entry_cards").className = "";
        const moodEntries = await getMoodEntries();
        let htmlString = "";
        let classNameString = "";

        if (moodEntries.length === 0) {
            classNameString = "flex flex-col items-center justify-center min-h-[24rem] p-6";
            htmlString = `
                <div class="flex flex-col items-center justify-center min-h-[24rem] p-6">
                    <img src="{% static 'image/sedih-banget.png' %}" alt="Sad face" class="w-32 h-32 mb-4"/>
                    <p class="text-center text-gray-600 mt-4">No mood data on the mental health tracker yet.</p>
                </div>
            `;
        }
        else {
            classNameString = "columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6 w-full"
            moodEntries.forEach((item) => {
                htmlString += `
                <div class="relative break-inside-avoid">
                    <div class="absolute top-2 z-10 left-1/2 -translate-x-1/2 flex items-center -space-x-2">
                        <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
                        <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
                    </div>
                    <div class="relative top-5 bg-indigo-100 shadow-md rounded-lg mb-6 break-inside-avoid flex flex-col border-2 border-indigo-300 transform rotate-1 hover:rotate-0 transition-transform duration-300">
                        <div class="bg-indigo-200 text-gray-800 p-4 rounded-t-lg border-b-2 border-indigo-300">
                            <h3 class="font-bold text-xl mb-2">${item.fields.mood}</h3>
                            <p class="text-gray-600">${item.fields.time}</p>
                        </div>
                        <div class="p-4">
                            <p class="font-semibold text-lg mb-2">My Feeling</p>
                            <p class="text-gray-700 mb-2">
                                <span class="bg-[linear-gradient(to_bottom,transparent_0%,transparent_calc(100%_-_1px),#CDC1FF_calc(100%_-_1px))] bg-[length:100%_1.5rem] pb-1">${item.fields.feelings}</span>
                            </p>
                            <div class="mt-4">
                                <p class="text-gray-700 font-semibold mb-2">Intensity</p>
                                <div class="relative pt-1">
                                    <div class="flex mb-2 items-center justify-between">
                                        <div>
                                            <span class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-indigo-600 bg-indigo-200">
                                                ${item.fields.mood_intensity > 10 ? '10+' : item.fields.mood_intensity}
                                            </span>
                                        </div>
                                    </div>
                                    <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
                                        <div style="width: ${item.fields.mood_intensity > 10 ? 100 : item.fields.mood_intensity * 10}%;" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="absolute top-0 -right-4 flex space-x-1">
                        <a href="/edit-mood/${item.pk}" class="bg-yellow-500 hover:bg-yellow-600 text-white rounded-full p-2 transition duration-300 shadow-md">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
                                <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
                            </svg>
                        </a>
                        <a href="/delete/${item.pk}" class="bg-red-500 hover:bg-red-600 text-white rounded-full p-2 transition duration-300 shadow-md">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" />
                            </svg>
                        </a>
                    </div>
                </div>
                `;
            });
        }
        document.getElementById("mood_entry_cards").className = classNameString;
        document.getElementById("mood_entry_cards").innerHTML = htmlString;
    }
    refreshMoodEntries();
    </script>
    ```

    **Code Explanation:**
    - `document.getElementById("mood_entry_cards")` is used to get the element based on its ID. In this code, the element that is being targeted is the `<div>` tag with the ID `mood_entry_cards` that you have created previously.
    - `innerHTML` is used to fill in the child element of the element that is being targeted. If `innerHTML = ""`, then it will clear the contents of the child element of the element that is being targeted.
    - `className` is used to fill in the class name of the element that is being targeted.
    - `moodEntries.forEach((item))` is used to perform a *for each loop* on the data *moods* that is retrieved using the `getMoodEntries()` function. Then, `htmlString` will be concatenated with the data moods to display in the container with the *cards* like in the previous tutorial.
    - `refreshMoodEntries()` is used to call the function above when the page is loaded.

## Tutorial: Creating Modal as a Form to Add a Mood

1. Add the following code to implement the modal (Tailwind) on your application. You can place the following code below the `div` with the `id` `mood_entry_cards` that you have added previously.
   
    ```html title="main/templates/main.html"
    ...
    <div id="crudModal" tabindex="-1" aria-hidden="true" class="hidden fixed inset-0 z-50 w-full flex items-center justify-center bg-gray-800 bg-opacity-50 overflow-x-hidden overflow-y-auto transition-opacity duration-300 ease-out">
      <div id="crudModalContent" class="relative bg-white rounded-lg shadow-lg w-5/6 sm:w-3/4 md:w-1/2 lg:w-1/3 mx-4 sm:mx-0 transform scale-95 opacity-0 transition-transform transition-opacity duration-300 ease-out">
        <!-- Modal header -->
        <div class="flex items-center justify-between p-4 border-b rounded-t">
          <h3 class="text-xl font-semibold text-gray-900">
            Add New Mood Entry
          </h3>
          <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center" id="closeModalBtn">
            <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path>
            </svg>
            <span class="sr-only">Close modal</span>
          </button>
        </div>
        <!-- Modal body -->
        <div class="px-6 py-4 space-y-6 form-style">
          <form id="moodEntryForm">
            <div class="mb-4">
              <label for="mood" class="block text-sm font-medium text-gray-700">Mood</label>
              <input type="text" id="mood" name="mood" class="mt-1 block w-full border border-gray-300 rounded-md p-2 hover:border-indigo-700" placeholder="Enter your mood" required>
            </div>
            <div class="mb-4">
              <label for="feelings" class="block text-sm font-medium text-gray-700">Feelings</label>
              <textarea id="feelings" name="feelings" rows="3" class="mt-1 block w-full h-52 resize-none border border-gray-300 rounded-md p-2 hover:border-indigo-700" placeholder="Describe your feelings" required></textarea>
            </div>
            <div class="mb-4">
              <label for="moodIntensity" class="block text-sm font-medium text-gray-700">Mood Intensity (1-10)</label>
              <input type="number" id="moodIntensity" name="mood_intensity" min="1" max="10" class="mt-1 block w-full border border-gray-300 rounded-md p-2 hover:border-indigo-700" required>
            </div>
          </form>
        </div>
        <!-- Modal footer -->
        <div class="flex flex-col space-y-2 md:flex-row md:space-y-0 md:space-x-2 p-6 border-t border-gray-200 rounded-b justify-center md:justify-end">
          <button type="button" class="bg-gray-500 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded-lg" id="cancelButton">Cancel</button>
          <button type="submit" id="submitMoodEntry" form="moodEntryForm" class="bg-indigo-700 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-lg">Save</button>
        </div>
      </div>
    </div>
    ...
    ```
2. Because we are using vanilla Tailwind CSS, there is no built-in modal class. Therefore, to make the modal work, we need to add the following JavaScript functions.

    ```html title="main/templates/main.html"
    <script>
    ...
      const modal = document.getElementById('crudModal');
      const modalContent = document.getElementById('crudModalContent');

      function showModal() {
          const modal = document.getElementById('crudModal');
          const modalContent = document.getElementById('crudModalContent');

          modal.classList.remove('hidden'); 
          setTimeout(() => {
            modalContent.classList.remove('opacity-0', 'scale-95');
            modalContent.classList.add('opacity-100', 'scale-100');
          }, 50); 
      }

      function hideModal() {
          const modal = document.getElementById('crudModal');
          const modalContent = document.getElementById('crudModalContent');

          modalContent.classList.remove('opacity-100', 'scale-100');
          modalContent.classList.add('opacity-0', 'scale-95');

          setTimeout(() => {
            modal.classList.add('hidden');
          }, 150); 
      }

      document.getElementById("cancelButton").addEventListener("click", hideModal);
      document.getElementById("closeModalBtn").addEventListener("click", hideModal);
    ...
    </script>
    ```
    :::info
    The form and JavaScript functions in the modal that we have created are adapted to the model in the `mental_health_tracker` application. If you want to use other models with other fields, pay attention again to the values of the related HTML attributes.
    :::

3. Change the Add New Mood Entry button that you have added in the tutorial above and add a new button to perform the addition of data with AJAX.

    ```html title="main/templates/main.html"
    ...
        <a href="{% url 'main:create_mood_entry' %}" class="bg-indigo-400 hover:bg-indigo-400 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105 mx-4 ">
            Add New Mood Entry
        </a>
        <button data-modal-target="crudModal" data-modal-toggle="crudModal" class="btn bg-indigo-700 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105" onclick="showModal();">
          Add New Mood Entry by AJAX
        </button>
    ...
    ```

## Tutorial: Adding Data Mood with AJAX

The modal with the form that you have created previously cannot be used to add data mood. Therefore, you need to create a new JavaScript function to add data based on the input to the data base in an AJAX.

1. Create a new function in the block `<script>` with the name `addMoodEntry`.
    ```html title="main/templates/main.html"
    <script>
      function addMoodEntry() {
        fetch("{% url 'main:add_mood_entry_ajax' %}", {
          method: "POST",
          body: new FormData(document.querySelector('#moodEntryForm')),
        })
        .then(response => refreshMoodEntries())

        document.getElementById("moodEntryForm").reset(); 
        document.querySelector("[data-modal-toggle='crudModal']").click();

        return false;
      }
    ...
    </script>
    ```
    **Code Explanation:**
    - `new FormData(document.querySelector('#moodEntryForm'))` is used to create a new `FormData` object that contains the data from the form in the modal. The `FormData` object can be used to send the form data to the server.
    - `document.getElementById("moodEntryForm").reset()` is used to clear the contents of the field form modal after submitting.

2. Add an event listener to the form in the modal to run the `addMoodEntry()` function with the following code.
    ```html title="main/templates/main.html"
    <script>
    ...
     document.getElementById("moodEntryForm").addEventListener("submit", (e) => {
        e.preventDefault();
        addMoodEntry();
      })
    </script>
    ```

    **Code Explanation:**
    - `document.getElementById("moodEntryForm")`: Retrieves an element with the ID "moodEntryForm" from the DOM, which is the form element in the modal used for adding a mood entry using AJAX.
    - `.addEventListener("submit", ...)`: Adds an event listener to the form that was selected from the DOM in the previous step, then attaches a callback function that will be invoked when the form is submitted (i.e., when the input element with `type="submit"` is clicked).
    - `(e) => {...`: The callback function provided to the event listener, which will be executed when the form is submitted (the function is written using the arrow function notation introduced in the ES6 standard of JavaScript; you can explore this concept further at [about arrow functions](https://www.freecodecamp.org/news/javascript-arrow-functions-in-depth/)).
    - `e.preventDefault()`: By default, a form that experiences a submit event will attempt to send data to the URL specified in the `action` attribute of the `form` tag. However, since we are using a different AJAX method than what is typically done in Django, we want to disable this default behavior using the `preventDefault()` method.
    - `addMoodEntry()`: Calls the function to add a mood entry.

Congratulations! You have successfully created an application that can add data using AJAX. Go to [http://localhost:8000/](http://localhost:8000/) and try to add a new mood entry to the application. Now, the application should not need a reload every time a new mood entry has been added.

## Tutorial: Protecting the Application from Cross Site Scripting (XSS)

### Trying XSS

Did you notice that the code that you have just added actually opens a security hole in the application? To see the severity of the security hole, follow the steps below.

1. Add a new mood entry with the value of the `mood` field as follows. Other fields can be filled in according to your preference.
    ```html
    <img src=x onerror="alert('XSS!');">
    ```

2. Press the save button and if the storage is successful, you will get an alert with the value `XSS!` as shown in the figure below.
    
    ![Alert Box XSS](/img/5-alert-box-xss.png)

### Adding `strip_tags` to "Clean Up" New Data

From the input above, it can be seen that a hacker can add new data that can execute JavaScript in the user's browser application. The security hole is usually called Cross Site Scripting or XSS. More specifically, in this application, there is a Stored XSS, which is a payload for XSS that is stored in the application's data base. Of course, we do not want the application that we are creating to have a security hole. To close the security hole, you can follow the steps below.

1. Open the `views.py` and `forms.py` files and add the following imports.
    ```python title="main/views.py, main/forms.py"
    from django.utils.html import strip_tags
    ```

2. In the `add_mood_entry_ajax` function in the `views.py` file, use the `strip_tags` function on the `mood` and `feelings` data before the data is inserted into the `MoodEntry`.
    ```python title="main/views.py"
    ...
    @csrf_exempt
    @require_POST
    def add_mood_entry_ajax(request):
        # highlight-start
        mood = strip_tags(request.POST.get("mood")) # strip HTML tags!
        feelings = strip_tags(request.POST.get("feelings")) # strip HTML tags!
        # highlight-end
        ...
    ```
    **Code Explanation**:
    - The `strip_tags` function will remove all HTML tags that are present in the data sent by the user through the `POST` request, so that the data that is stored in the data base is clean. For example, `data = "<b>Programming</b> <button>Basic</button> Platform <span>Genap 2025</span>"`, `strip_tags(data)` will return `Programming Basic Platform Genap 2025`.
    - The `mood_intensity` field is not cleaned up with `strip_tags` because the field is an `IntegerField` and if it is not an `int`, Django will not store it in the data base.

3. On the `MoodEntryForm` class in the `forms.py` file, add the following two methods.
    ```python title="main/forms.py"
    ...
    class MoodEntryForm(ModelForm):
        class Meta:
            ...
        
        # highlight-start
        def clean_mood(self):
            mood = self.cleaned_data["mood"]
            return strip_tags(mood)
    
        def clean_feelings(self):
            feelings = self.cleaned_data["feelings"]
            return strip_tags(feelings)
        # highlight-end
    ...
    ```
    
    **Code Explanation**:
    - The `clean_mood` and `clean_feelings` methods will be called when `form.is_valid()` is called, so by adding the two methods, you have done validation for the `create_mood_entry` and `edit_mood` functions.

4. After adding `strip_tags`, remove the data that you have just added and try to add it again. If you get an error on the form that says the `mood` field cannot be empty, then congratulations, you have added a security hole against XSS! If you do not get an error, check again whether you have followed the steps above.

    ![Form Error](/img/5-form-error.png)

### Sanitizing Data with DOMPurify

The `strip_tags` function that you have added will "clean up" all new data, but old data must be cleaned up itself or we can use a JavaScript library called [DOMPurify](https://github.com/cure53/DOMPurify) for cleaning up on the frontend side. It is important to note that DOMPurify will only work if the data is retrieved to be displayed with HTML on the application's frontend. If there is an API `/json` or `/xml` used by the application, then the data that is obtained will still be "dirty".

1. Open the `main.html` file and add the following code to the `meta` block.
    ```html title="main/templates/main.html"
    {% block meta %}
    ...
    <script src="https://cdn.jsdelivr.net/npm/dompurify@3.1.7/dist/purify.min.js"></script>
    ...
    {% endblock meta %}
    ```

2. After that, add the following code to the `refreshMoodEntries` function that you have added previously.
    ```html title="main/templates/main.html"
    <script>
        ...
        async function refreshMoodEntries() {
            ...
            moodEntries.forEach((item) => {
                // highlight-start
                const mood = DOMPurify.sanitize(item.fields.mood);
                const feelings = DOMPurify.sanitize(item.fields.feelings);
                // highlight-end
                ...
            });
            ...
        }
        ...
    </script>
    ```
    
    :::note
    Don't forget to change all occurrences of `item.fields.mood` to `mood` and `item.fields.feelings` to `feelings`.
    :::

4. Refresh the main page and if you have previously had dirty data like the alert box that shows up, then the alert box should no longer appear on the browser.

## Closing

- After running the tutorial above, you should have the local directory structure as follows.
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
   │       └── sedih-banget.png
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
```

## Additional References

- [HackTricks Cross Site Scripting](https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting)
- [OWASP Cross Site Scripting](https://owasp.org/www-community/attacks/xss/)

## Contributors

- Juan Maxwell Tanaya
- Muhammad Faishal Adly Nelwan
- Muhammad Irfan Firmansyah
- Muhammad Oka (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
