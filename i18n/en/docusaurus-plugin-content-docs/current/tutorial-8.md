---
sidebar_label: Tutorial 8
sidebar_position: 10
Path: docs/tutorial-8
---

# Tutorial 8: Flutter Networking, Authentication, and Integration

Platform-Based Programming (CSGE602022) — organized by the Faculty of Computer Science, University of Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students are expected to:

- Understand the structure and creation of models in Flutter.
- Understand how to fetch, process, and display data from web services.
- Understand basic state management using Provider in Flutter.
- Able to authenticate with the Django web service with the Flutter application.

## Model in Flutter

In this tutorial, we will call a web service and display the results on the Flutter page we created. However, before making the web service call, we need to define the model we use for the web service call. In Flutter, models are defined using a class, similar to what has been learned in the OOP section of Programming Foundations 2.

:::tip
The code below is just an example. However, we highly recommend you to read it because the concepts will be used in the following sections.
:::

Here is an example of class in Flutter.

```dart
class Song {
    Song({
        this.id,
        this.title,
        this.artist,
        this.releaseDate,
    });

    int id;
    String title;
    String artist;
    DateTime releaseDate;
}
```

:::warning
If you encounter errors while creating the class, add the `required` keyword to each class parameter in the constructor section.
:::

So far, we have successfully created the class. Next, we will add some codes to form a `Song` model. This `Song` model represents the response from the web service call.

Import `dart:convert` at the top of the file.

```dart
import 'dart:convert';
...
```

In the `Song` class, add the following code.

```dart
factory Song.fromJson(Map<String, dynamic> json) => Song(
    id: json["id"],
    title: json["title"],
    artist: json["artist"],
    releaseDate: json["releaseDate"],
);

Map<String, dynamic> toJson() => {
    "id": id,
    "title": title,
    "artist": artist,
    "releaseDate": releaseDate,
};
```

Add the following code outside the `Song` class.

```dart
Song songFromJson(String str) => Song.fromJson(json.decode(str));
String songToJson(Song data) => json.encode(data.toJson());
```

The final code will look like this. It will display a single `Song` object from the web service.

```dart
import 'dart:convert';

Song songFromJson(String str) => Song.fromJson(json.decode(str));
String songToJson(Song data) => json.encode(data.toJson());

class Song {
    Song({
        this.id,
        this.title,
        this.artist,
        this.releaseDate,
    });

    int id;
    String title;
    String artist;
    String releaseDate;

    factory Song.fromJson(Map<String, dynamic> json) => Song(
        id: json["id"],
        title: json["title"],
        artist: json["artist"],
	releaseDate: json["releaseDate"],
    );

    Map<String, dynamic> toJson() => {
        "id": id,
        "title": title,
        "artist": artist,
        "releaseDate": releaseDate,
    };
}
```
### Explanation

There are additional codes such as the `toJson` and `fromJson` methods inside the `Song` class. This is because when we make a request to a web service with the **GET** method, we usually receive the result in the form of JSON. Therefore, we need to convert the data with the `fromJson` method so that Flutter recognizes this JSON as an object of the `Song` class. Additionally, there is also the `toJson` method, which will be used when sending data to the web service (such as **POST** or **PUT**).

Here is an example response from a web service with the **GET** method that can be converted into the `Song` model.

```json
{
    "id": 1,
    "title": "APT.",
    "artist": "Rosé & Bruno Mars",
    "releaseDate": "2024-10-18T00:00:00+0000"
}
```

Now, what if the response from the web service consists of a collection of JSON objects? It is actually the same as the code above, but with some modifications to the `songFromJson` and `songToJson` methods.

The code is as follows.

```dart
List<Song> songsFromJson(String str) => List<Song>.from(json.decode(str).map((song) => Song.fromJson(song)));

String songsToJson(List<Song> data) => json.encode(List<dynamic>.from(data.map((song) => song.toJson())));
```

Here is an example response from a web service with the **GET** method that can be converted into the `Song` model.

```json
[
    {
        "id": 1,
        "title": "APT.",
        "artist": "Rosé & Bruno Mars",
        "releaseDate": "2024-10-18T21:39:14+0200"
    },
    {
        "id": 2,
        "title": "Espresso",
        "artist": "Sabrina Carpenter",
        "releaseDate": "2024-10-18T00:00:00+0000"
    }
    {
        "id": 3,
        "title": "Supernatural",
        "artist": "NewJeans",
        "releaseDate": "2024-10-18T00:00:00+0000"
    }
]
```

## Fetching Data from Web Service in Flutter

During application development, there are times when we need to fetch external data from outside our application (the Internet) to display in our application. This tutorial aims to understand how to fetch data from a web service in Flutter.

In general, there are several steps when you want to display data from another web service to a Flutter application, namely:

1. Add the `http` dependency to the project; this dependency is used for exchanging HTTP requests.

2. Create a model according to the response from the data originating from that web service.

3. Make an HTTP request to the web service using the `http` dependency.

4. Convert the object obtained from the web service to the model we created in step two.

5. Display the converted data to the application using `FutureBuilder`.

For further explanation, you can read the details [here](http://docs.flutter.dev/cookbook/networking/fetch-data#5-display-the-data).

## Basic State Management using Provider

`Provider` is a wrapper around `InheritedWidget` to make `InheritedWidget` easier to use and more reusable. `InheritedWidget` itself is the basic class for Flutter widgets that efficiently spread information to other widgets in one tree.

The benefits of using `provider` are as follows:

- Allocating resources becomes simpler.
- Lazy-loading.
- Reducing boilerplate every time a new class is created.
- Supported by Flutter Devtools so that `provider` can be tracked from Devtool.
- Scalability improvement for classes that utilize complex built-in listening mechanisms.

For more information about `provider`, please visit the [Provider package page](http://pub.dev/packages/provider).

## Tutorial: Django-Flutter Authentication Integration

### NOTES

For now, if you follow the steps to completion, integration between Flutter and PWS cannot be achieved yet. This is due to PWS still being insecure (using `http://`, not `https://`). Therefore, for this tutorial, you are welcome to experiment using only localhost or another deployment platform that is already secure.

### Set Up Authentication in Django for Flutter

Follow the steps below to integrate the authentication system in **Django**.

1. Create a `django-app` named `authentication` in your Django project you created earlier.

2. Add `authentication` to `INSTALLED_APPS` in the main project `settings.py` file of your Django application.

    :::tip  
    If you forgot how to perform steps 1 and 2, you can read Tutorial 1 again.
    :::  

3. Run the command `pip install django-cors-headers` to install the required library. Don't forget to **enable the Python virtual environment** prior. **Don't forget to add `django-cors-headers` to `requirements.txt` as well.**

4. Add `corsheaders` to `INSTALLED_APPS` in the main project `settings.py` file of your Django application.

5. Add `corsheaders.middleware.CorsMiddleware` to `MIDDLEWARE` in the main project `settings.py` file of your Django application.

6. Add the following variables to the main project `settings.py` file of your Django application.

    ```python
    CORS_ALLOW_ALL_ORIGINS = True
    CORS_ALLOW_CREDENTIALS = True
    CSRF_COOKIE_SECURE = True
    SESSION_COOKIE_SECURE = True
    CSRF_COOKIE_SAMESITE = 'None'
    SESSION_COOKIE_SAMESITE = 'None'
    ```
    
7. Create a view method for login in `authentication/views.py`.

    ```python
	from django.contrib.auth import authenticate, login as auth_login
	from django.http import JsonResponse
	from django.views.decorators.csrf import csrf_exempt
	
	@csrf_exempt
    def login(request):
        username = request.POST['username']
        password = request.POST['password']
        user = authenticate(username=username, password=password)
        if user is not None:
            if user.is_active:
                auth_login(request, user)
                # Successful login status.
                return JsonResponse({
                    "username": user.username,
                    "status": True,
                    "message": "Login successful!"
                    # Add other data if you want to send data to Flutter.
                }, status=200)
            else:
                return JsonResponse({
                    "status": False,
                    "message": "Login failed, account disabled."
                }, status=401)

        else:
            return JsonResponse({
                "status": False,
                "message": "Login failed, check email or password again."
            }, status=401)
	```

8. Create a `urls.py` file in the `authentication` folder and add URL routing to the function created with the `login/` endpoint.

    ```python
	from django.urls import path
	from authentication.views import login
	
	app_name = 'authentication'
	
	urlpatterns = [
	    path('login/', login, name='login'),
	]
    ```
    
9. Finally, add `path('auth/', include('authentication.urls'))`, to the `shopping_list/urls.py` file.

### Integrate Authentication System in Flutter

To facilitate the creation of the authentication system, the teaching assistant team has created a Flutter package that can be used to contact the Django web service (including `GET` and `POST` operations).

The package can be accessed via the following link: [pbp_django_auth](http://pub.dev/packages/pbp_django_auth)

Follow the steps below to integrate the authentication system into **Flutter**.

1. Install the package provided by the teaching assistant team by running the following commands in the Terminal.

    ```bash
	flutter pub add provider
	flutter pub add pbp_django_auth
	```
    
2. To use the package, you need to modify the root widget to provide the `CookieRequest` library to all child widgets using `Provider`.

    For example, if your application was like this before:
    
    ```dart
	class MyApp extends StatelessWidget {
	  const MyApp({Key? key}) : super(key: key);

	@override
	  Widget build(BuildContext context) {
	    return MaterialApp(
	      title: 'Mental Health Tracker',
	      theme: ThemeData(
	    useMaterial3: true,
		colorScheme: ColorScheme.fromSwatch(
	      primarySwatch: Colors.deepPurple,
	    ).copyWith(secondary: Colors.deepPurple[400]),
	      ),
	      home: MyHomePage(),
	    );
	  }
	}
    ```
    
    Change it to:
    
    ```dart
    class MyApp extends StatelessWidget {
      const MyApp({super.key});

      @override
      Widget build(BuildContext context) {
        return Provider(
          create: (_) {
            CookieRequest request = CookieRequest();
            return request;
          },
          child: MaterialApp(
            title: 'Mental Health Tracker',
            theme: ThemeData(
              useMaterial3: true,
              colorScheme: ColorScheme.fromSwatch(
                primarySwatch: Colors.deepPurple,
              ).copyWith(secondary: Colors.deepPurple[400]),
            ),
            home: MyHomePage(),
          ),
        );
      }
    }
    ```

    This will create a new `Provider` object that will share an instance of `CookieRequest` with all components in the application.

    :::note  
    Don't forget to add `import 'package:pbp_django_auth/pbp_django_auth.dart';` to the top of the file.
    :::  
    `
3. Create a new file in the `screens` folder named `login.dart`.

4. Fill the `login.dart` file with the following code.

    ```dart
    import 'package:mental_health_tracker/screens/menu.dart';
    import 'package:flutter/material.dart';
    import 'package:pbp_django_auth/pbp_django_auth.dart';
    import 'package:provider/provider.dart';
    // TODO: Import RegisterPage later

    void main() {
      runApp(const LoginApp());
    }

    class LoginApp extends StatelessWidget {
      const LoginApp({super.key});

      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Login',
          theme: ThemeData(
            useMaterial3: true,
            colorScheme: ColorScheme.fromSwatch(
              primarySwatch: Colors.deepPurple,
            ).copyWith(secondary: Colors.deepPurple[400]),
          ),
          home: const LoginPage(),
        );
      }
    }

    class LoginPage extends StatefulWidget {
      const LoginPage({super.key});

      @override
      State<LoginPage> createState() => _LoginPageState();
    }

    class _LoginPageState extends State<LoginPage> {
      final TextEditingController _usernameController = TextEditingController();
      final TextEditingController _passwordController = TextEditingController();

      @override
      Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();

        return Scaffold(
          appBar: AppBar(
            title: const Text('Login'),
          ),
          body: Center(
            child: SingleChildScrollView(
              padding: const EdgeInsets.all(16.0),
              child: Card(
                elevation: 8,
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(12.0),
                ),
                child: Padding(
                  padding: const EdgeInsets.all(20.0),
                  child: Column(
                    mainAxisSize: MainAxisSize.min,
                    children: [
                      const Text(
                        'Login',
                        style: TextStyle(
                          fontSize: 24.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      const SizedBox(height: 30.0),
                      TextField(
                        controller: _usernameController,
                        decoration: const InputDecoration(
                          labelText: 'Username',
                          hintText: 'Enter your username',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.all(Radius.circular(12.0)),
                          ),
                          contentPadding:
                              EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                        ),
                      ),
                      const SizedBox(height: 12.0),
                      TextField(
                        controller: _passwordController,
                        decoration: const InputDecoration(
                          labelText: 'Password',
                          hintText: 'Enter your password',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.all(Radius.circular(12.0)),
                          ),
                          contentPadding:
                              EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                        ),
                        obscureText: true,
                      ),
                      const SizedBox(height: 24.0),
                      ElevatedButton(
                        onPressed: () async {
                          String username = _usernameController.text;
                          String password = _passwordController.text;

			  // Check credentials
			  // TODO: Change the URL and don't forget to add a trailing slash (/) at the end of the URL!
			  // To connect the Android emulator to Django on localhost,
			  // use the URL http://10.0.2.2/
                          final response = await request
                              .login("http://[YOUR_APP_URL]/auth/login/", {
                            'username': username,
                            'password': password,
                          });

                          if (request.loggedIn) {
                            String message = response['message'];
                            String uname = response['username'];
                            if (context.mounted) {
                              Navigator.pushReplacement(
                                context,
                                MaterialPageRoute(
                                    builder: (context) => MyHomePage()),
                              );
                              ScaffoldMessenger.of(context)
                                ..hideCurrentSnackBar()
                                ..showSnackBar(
                                  SnackBar(
                                      content:
                                          Text("$message Welcome, $uname.")),
                                );
                            }
                          } else {
                            if (context.mounted) {
                              showDialog(
                                context: context,
                                builder: (context) => AlertDialog(
                                  title: const Text('Login Failed'),
                                  content: Text(response['message']),
                                  actions: [
                                    TextButton(
                                      child: const Text('OK'),
                                      onPressed: () {
                                        Navigator.pop(context);
                                      },
                                    ),
                                  ],
                                ),
                              );
                            }
                          }
                        },
                        style: ElevatedButton.styleFrom(
                          foregroundColor: Colors.white,
                          minimumSize: Size(double.infinity, 50),
                          backgroundColor: Theme.of(context).colorScheme.primary,
                          padding: const EdgeInsets.symmetric(vertical: 16.0),
                        ),
                        child: const Text('Login'),
                      ),
                      const SizedBox(height: 36.0),
                      GestureDetector(
                        onTap: () {
                          Navigator.push(
                            context,
                            MaterialPageRoute(
                                builder: (context) => const RegisterPage()),
                          );
                        },
                        child: Text(
                          'Don\'t have an account? Register',
                          style: TextStyle(
                            color: Theme.of(context).colorScheme.primary,
                            fontSize: 16.0,
                          ),
                        ),
                      ),
                    ],
                  ),
                ),
              ),
            ),
          ),
        );
      }
    }
    ```
    
5. In the `main.dart` file, in the `MaterialApp(...)` widget, change `home: MyHomePage()` to `home: LoginPage()`.

6. In this step, you will implement a register function in your project. Before that, modify the `authentication` module on your Django project that you have made. Add another method in your views in `authentication/views.py` that you have already made.

```python
from django.contrib.auth.models import User
import json

...

@csrf_exempt
def register(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        username = data['username']
        password1 = data['password1']
        password2 = data['password2']

        # Check if the passwords match
        if password1 != password2:
            return JsonResponse({
                "status": False,
                "message": "Passwords do not match."
            }, status=400)

        # Check if the username is already taken
        if User.objects.filter(username=username).exists():
            return JsonResponse({
                "status": False,
                "message": "Username already exists."
            }, status=400)

        # Create the new user
        user = User.objects.create_user(username=username, password=password1)
        user.save()

        return JsonResponse({
            "username": user.username,
            "status": 'success',
            "message": "User created successfully!"
        }, status=200)

    else:
        return JsonResponse({
            "status": False,
            "message": "Invalid request method."
        }, status=400)

```

7. Add another _path_ in `authentication/urls.py`, modify it as follows

```python
from authentication.views import login, register  # add "register" to this line
...
path('register/', register, name='register'),
```

8. In your Flutter project, create another file in `screens` folder with the name `register.dart`.

9. Fill the file `register.dart` as follows.

    ```dart
    import 'dart:convert';
    import 'package:flutter/material.dart';
    import 'package:mental_health_tracker/screens/login.dart';
    import 'package:pbp_django_auth/pbp_django_auth.dart';
    import 'package:provider/provider.dart';

    class RegisterPage extends StatefulWidget {
      const RegisterPage({super.key});

      @override
      State<RegisterPage> createState() => _RegisterPageState();
    }

    class _RegisterPageState extends State<RegisterPage> {
      final _usernameController = TextEditingController();
      final _passwordController = TextEditingController();
      final _confirmPasswordController = TextEditingController();

      @override
      Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();
        return Scaffold(
          appBar: AppBar(
            title: const Text('Register'),
            leading: IconButton(
              icon: const Icon(Icons.arrow_back),
              onPressed: () {
                Navigator.pop(context);
              },
            ),
          ),
          body: Center(
            child: SingleChildScrollView(
              padding: const EdgeInsets.all(16.0),
              child: Card(
                elevation: 8,
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(12.0),
                ),
                child: Padding(
                  padding: const EdgeInsets.all(20.0),
                  child: Column(
                    mainAxisSize: MainAxisSize.min,
                    children: <Widget>[
                      const Text(
                        'Register',
                        style: TextStyle(
                          fontSize: 24.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      const SizedBox(height: 30.0),
                      TextFormField(
                        controller: _usernameController,
                        decoration: const InputDecoration(
                          labelText: 'Username',
                          hintText: 'Enter your username',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.all(Radius.circular(12.0)),
                          ),
                          contentPadding:
                              EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                        ),
                        validator: (value) {
                          if (value == null || value.isEmpty) {
                            return 'Please enter your username';
                          }
                          return null;
                        },
                      ),
                      const SizedBox(height: 12.0),
                      TextFormField(
                        controller: _passwordController,
                        decoration: const InputDecoration(
                          labelText: 'Password',
                          hintText: 'Enter your password',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.all(Radius.circular(12.0)),
                          ),
                          contentPadding:
                              EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                        ),
                        obscureText: true,
                        validator: (value) {
                          if (value == null || value.isEmpty) {
                            return 'Please enter your password';
                          }
                          return null;
                        },
                      ),
                      const SizedBox(height: 12.0),
                      TextFormField(
                        controller: _confirmPasswordController,
                        decoration: const InputDecoration(
                          labelText: 'Confirm Password',
                          hintText: 'Confirm your password',
                          border: OutlineInputBorder(
                            borderRadius: BorderRadius.all(Radius.circular(12.0)),
                          ),
                          contentPadding:
                              EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                        ),
                        obscureText: true,
                        validator: (value) {
                          if (value == null || value.isEmpty) {
                            return 'Please confirm your password';
                          }
                          return null;
                        },
                      ),
                      const SizedBox(height: 24.0),
                      ElevatedButton(
                        onPressed: () async {
                          String username = _usernameController.text;
                          String password1 = _passwordController.text;
                          String password2 = _confirmPasswordController.text;

                          // Check credentials
                          // TODO: Change the url, don't forget to add a slash (/) inthe end of the URL!
                          // To connect Android emulator with Django on localhost,
                          // use the URL http://10.0.2.2/
                          final response = await request.postJson(
                              "http://[YOUR_APP_URL]/auth/register/",
                              jsonEncode({
                                "username": username,
                                "password1": password1,
                                "password2": password2,
                              }));
                          if (context.mounted) {
                            if (response['status'] == 'success') {
                              ScaffoldMessenger.of(context).showSnackBar(
                                const SnackBar(
                                  content: Text('Successfully registered!'),
                                ),
                              );
                              Navigator.pushReplacement(
                                context,
                                MaterialPageRoute(
                                    builder: (context) => const LoginPage()),
                              );
                            } else {
                              ScaffoldMessenger.of(context).showSnackBar(
                                const SnackBar(
                                  content: Text('Failed to register!'),
                                ),
                              );
                            }
                          }
                        },
                        style: ElevatedButton.styleFrom(
                          foregroundColor: Colors.white,
                          minimumSize: Size(double.infinity, 50),
                          backgroundColor: Theme.of(context).colorScheme.primary,
                          padding: const EdgeInsets.symmetric(vertical: 16.0),
                        ),
                        child: const Text('Register'),
                      ),
                    ],
                  ),
                ),
              ),
            ),
          ),
        );
      }
    }
    ```

8. Run your Flutter application and try to login.

## Custom Model Creation

In creating a model that adapts to JSON data, we can use the [Quicktype](http://app.quicktype.io/) website with the following steps.

1. Open the `JSON` endpoint you created earlier in tutorial 2.

2. Copy the `JSON` data and open the [Quicktype](http://app.quicktype.io/) website.

3. On the Quicktype website, change the _setup name_ to `MoodEntry`, _source type_ to `JSON`, and _language_ to `Dart`.

4. Paste the previously copied `JSON` data into the textbox _textbox_ provided on Quicktype.

5. Click the `Copy Code` on Quicktype.

    Here is an example result.

    ![Contoh Quicktype](/img/8-quicktype-example.png)

After obtaining the model code through Quicktype, open the Flutter project again, create a new file under the `models/` folder in the subdirectory `lib/` with the name `mood_entry.dart`, and paste the copied code from Quicktype.

## Fetch Data from Django and Show Data in the Flutter App

### Add HTTP Dependency

To create HTTP requests, we need the [http](http://pub.dev/packages/http) package.

1. Run `flutter pub add http` in your Flutter project terminal to add the `http` package.

2. In the file `android/app/src/main/AndroidManifest.xml`, add this code to allow your Flutter app to access the internet.

    ```xml
    ...
        <application>
        ...
        </application>
        <!-- Required to fetch data from the Internet. -->
        <uses-permission android:name="android.permission.INTERNET" />
    ...
    ```

### Fetch Data from Django

1. Create a new file in the `lib/screens` directory with name `list_moodentry.dart`.

2. In the file `list_moodentry.dart`, import the necessary libraries. Change the [APP_NAME] to your Flutter project app name.

    ```dart
    import 'package:flutter/material.dart';
    import 'package:[APP_NAME]/models/moodentry.dart';
    ...
    ```

3. Copy and paste these lines of code `list_moodentry.dart`. Do not forget to import the necessary files.

    ```dart
    ...
    import 'package:[APP_NAME]/widgets/left_drawer.dart';

    class MoodEntryPage extends StatefulWidget {
      const MoodEntryPage({super.key});

      @override
      State<MoodEntryPage> createState() => _MoodEntryPageState();
    }

    class _MoodEntryPageState extends State<MoodEntryPage> {
      Future<List<MoodEntry>> fetchMood(CookieRequest request) async {
        // TODO: Don't forget to add the trailing slash (/) at the end of the URL!
        final response = await request.get('http://[YOUR_APP_URL]/json/');

        // Decoding the response into JSON
        var data = response;

        // Convert json data to a MoodEntry object
        List<MoodEntry> listMood = [];
        for (var d in data) {
          if (d != null) {
            listMood.add(MoodEntry.fromJson(d));
          }
        }
        return listMood;
        }
      }

      @override
      Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();
        return Scaffold(
          appBar: AppBar(
            title: const Text('Mood Entry List'),
          ),
          drawer: const LeftDrawer(),
          body: FutureBuilder(
            future: fetchMood(request),
            builder: (context, AsyncSnapshot snapshot) {
              if (snapshot.data == null) {
                return const Center(child: CircularProgressIndicator());
              } else {
                if (!snapshot.hasData) {
                  return const Column(
                    children: [
                      Text(
                        'There is no mood data in mental health tracker.',
                        style: TextStyle(fontSize: 20, color: Color(0xff59A5D8)),
                      ),
                      SizedBox(height: 8),
                    ],
                  );
                } else {
                  return ListView.builder(
                    itemCount: snapshot.data!.length,
                    itemBuilder: (_, index) => Container(
                      margin:
                          const EdgeInsets.symmetric(horizontal: 16, vertical: 12),
                      padding: const EdgeInsets.all(20.0),
                      child: Column(
                        mainAxisAlignment: MainAxisAlignment.start,
                        crossAxisAlignment: CrossAxisAlignment.start,
                        children: [
                          Text(
                            "${snapshot.data![index].fields.mood}",
                            style: const TextStyle(
                              fontSize: 18.0,
                              fontWeight: FontWeight.bold,
                            ),
                          ),
                          const SizedBox(height: 10),
                          Text("${snapshot.data![index].fields.feelings}"),
                          const SizedBox(height: 10),
                          Text("${snapshot.data![index].fields.moodIntensity}"),
                          const SizedBox(height: 10),
                          Text("${snapshot.data![index].fields.time}")
                        ],
                      ),
                    ),
                  );
                }
              }
            },
          ),
        );
      }
    }
    ```

4. Add the page `list_moodentry.dart` to `widgets/left_drawer.dart` with this code.

    ```dart
    // ListTile Menu code
    ...
    ListTile(
        leading: const Icon(Icons.add_reaction_rounded),
        title: const Text('Mood List'),
        onTap: () {
            // Route to the mood page
            Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const MoodEntryPage()),
            );
        },
    ),
    ...
    ```

5. Change the function of the `Lihat Mood` button in the main page to redirect the page to `MoodPage`. You can add the redirection by adding `else if` after the `if(...){...}` code at the end of the `onTap: () { }` code in the `widgets/mood_card.dart` file.

    ```dart
    ...
    else if (item.name == "View Mood") {
        Navigator.push(context,
            MaterialPageRoute(
                builder: (context) => const MoodEntryPage()
            ),
        );
    }
    ...
    ```

6. Import the necessary files while adding the `MoodEntryPage` to the `left_drawer.dart` and `tracker_card.dart`.

7. Run the app and try to add some `MoodEntry` in your website. Check the result in the new `Daftar Mood` page in Flutter.

## Integrate Flutter Form with the Django Service

Do these steps in your **Django** project.

1. Create a new views function in the `main/views.py` in your Django project with this code. Don;t forget to add the necessary imports.

    ```python
    from django.views.decorators.csrf import csrf_exempt
    import json
    from django.http import JsonResponse
    ...
    @csrf_exempt
    def create_mood_flutter(request):
        if request.method == 'POST':

            data = json.loads(request.body)
            new_mood = MoodEntry.objects.create(
                user=request.user,
                mood=data["mood"],
                mood_intensity=int(data["mood_intensity"]),
                feelings=data["feelings"]
            )

            new_mood.save()

            return JsonResponse({"status": "success"}, status=200)
        else:
            return JsonResponse({"status": "error"}, status=401)
    ```

2. Add new path in the `main/urls.py` file with this code.

    ```python
    path('create-flutter/', create_mood_flutter, name='create_mood_flutter'),
    ```

3. Rerun (and redeploy) your app. If you have deployed your app before, any data and transactions will be lost after the redeployment.

Do these steps in your **Flutter** project.

1. Connect the page `moodentry_form.dart` to `CookieRequest` by adding this code.

    ```dart
    ...
    @override
    Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();

        return Scaffold(
        ...
    ```

2. change the `onPressed: ()` _button_  instructions as follows.

    ```dart
    ...
    onPressed: () async {
        if (_formKey.currentState!.validate()) {
            // Send request to Django and wait for the response
            // TODO: Change the URL to your Django app's URL. Don't forget to add the trailing slash (/) if needed.
            final response = await request.postJson(
                "http://[YOUR_APP_URL]/create-flutter/",
                jsonEncode(<String, String>{
                    'mood': _mood,
                    'mood_intensity': _moodIntensity.toString(),
                    'feelings': _feelings,
                // TODO: Adjust the fields with your project
                }),
            );
            if (context.mounted) {
                if (response['status'] == 'success') {
                    ScaffoldMessenger.of(context)
                        .showSnackBar(const SnackBar(
                    content: Text("New mood has saved successfully!"),
                    ));
                    Navigator.pushReplacement(
                        context,
                        MaterialPageRoute(builder: (context) => MyHomePage()),
                    );
                } else {
                    ScaffoldMessenger.of(context)
                        .showSnackBar(const SnackBar(
                        content:
                            Text("Something went wrong, please try again."),
                    ));
                }
            }
        }
    },
    ...
    ```

3. Do some quick fixes by importing the necessary files.

4. Rerun your app and try add new transactions from your Flutter app.

## Logout Feature Implementation

Do these steps in your **Django** project.

1. Add a new views method for logout in the `authentication/views.py`.

    ```python
    from django.contrib.auth import logout as auth_logout
    ...
    @csrf_exempt
    def logout(request):
        username = request.user.username

        try:
            auth_logout(request)
            return JsonResponse({
                "username": username,
                "status": True,
                "message": "Logged out successfully!"
            }, status=200)
        except:
            return JsonResponse({
            "status": False,
            "message": "Logout failed."
            }, status=401)
    ```

2. Add a new path in the `authentication/urls.py` file.

    ```python
    from authentication.views import logout
    ...
    path('logout/', logout, name='logout'),
    ```

Do these steps in the **Flutter** project.

1. Add this code to the `lib/widgets/mood_card.dart` file. Do not forget to resolve the import issues. after you add the follong lines of code.

    ```dart
    ...
    @override
    Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();
        return Material(
            ...
    ```

2. Change the `onTap: () {...}` for the widget `Inkwell` to `onTap: () async {...}` This allows the widget `Inkwell` do the logout process asynchronously.

3. Add the following code into the `async {...}` in the last part:

    ```dart
    ...
    // previous if statement
    // add the else if statement below
    else if (item.name == "Logout") {
        final response = await request.logout(
            // TODO: Change the URL to your Django app's URL. Don't forget to add the trailing slash (/) if needed.
            "http://[YOUR_APP_URL]/auth/logout/");
        String message = response["message"];
        if (context.mounted) {
            if (response['status']) {
                String uname = response["username"];
                ScaffoldMessenger.of(context).showSnackBar(SnackBar(
                    content: Text("$message Goodbye, $uname."),
                ));
                Navigator.pushReplacement(
                    context,
                    MaterialPageRoute(builder: (context) => const LoginPage()),
                );
            } else {
                ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(
                        content: Text(message),
                    ),
                );
            }
        }
    }
    ...
    ```

4. Rerun the app and try to logout.

## Closing

Congratulations! You have completed the Tutorial 8! Hopefully with this tutorial, you can understand more about models, data fetching, basic state management, and Django-Flutter integration.😄

1. Read and understand the codes we listed above again. **Don't forget to complete the TODO!**

:::tip  
Don't forget to run `flutter analyze` to see if there are any optimizations that can be done.  
:::  

2. Run the following commands to `add`, `commit`, and `push`:

	```shell
	git add .
	git commit -m "<commit_message>"
	git push -u origin <main_branch>
	```

	- Replace `<commit_message>` with your desired message. For example: `git commit -m "tutorial 8 selesai"`.
	- Replace `<main_branch>` with your main branch name. For example: `git push -u origin main` or `git push -u origin master`.

## Additional References

- [Fetch Data From the Internet](http://docs.flutter.dev/cookbook/networking/fetch-data)
- [How to create models in Flutter Dart](http://thegrowingdeveloper.org/coding-blog/how-to-create-models-in-flutter-dart)
- [Simple app state management | Flutter](http://docs.flutter.dev/development/data-and-backend/state-mgmt/simple)
- [Flutter State Management with Provider](http://blog.devgenius.io/flutter-state-management-with-provider-5a57eca108f1)
- [Pengenalan State Management Flutter dan Jenis-jenisnya](http://caraguna.com/pengenalan-state-management-flutter/)

## Contributors

- Abbilhaidar Farras Zulfikar
- Clarence Grady
- Fernando Valentino Sitinjak
- Reyhan Zada Virgiwibowo
- Muhammad Nabil Mu'afa & Alden Luthfi (EN Translation)

## Credits

This tutorial was developed based on [PBP Genap 2024](http://github.com/pbp-fasilkom-ui/genap-2024) written by the 2023 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
