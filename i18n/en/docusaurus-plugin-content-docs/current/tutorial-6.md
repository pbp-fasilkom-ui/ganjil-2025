---
sidebar_label: Tutorial 6
sidebar_position: 8
Path: docs/tutorial-6
---

# Tutorial 6: Introduction to Flutter

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Learning Objectives

After completing this tutorial, students will be able to:
- Understand the installation process of Flutter.
- Understand and be able to use the basic commands of Flutter that are necessary to develop an application.
- Understand the basics of creating and running an application in Flutter.
- Understand the basic elements of Flutter.

## Flutter

### Understanding Flutter

Flutter is an open source mobile application framework developed by Google in 2017. Framework is used to build applications for Android and iOS operating systems, as well as supporting the development of web, Windows, Linux, and MacOS based applications natively.

One of the main advantages of Flutter is its ability to produce applications for multiple platforms with a single codebase (cross-platform development). In addition, the Just-In-Time (JIT) feature allows developers to see changes made to the codebase directly without having to recompile from scratch.

Here are some other advantages that Flutter can provide as a framework that can be cross-platform:

- Fast and efficient performance: Flutter uses the Dart programming language and compiles into machine code. The host device understands the code, so it ensures fast and efficient performance.
- Fast, consistent, and scalable rendering: In contrast to specialized platform rendering tools, Flutter uses Skia, the open source graphics library developed by Google to render UI. This gives the user a consistent visual, regardless of the platform used to access the application.
- Developer-friendly tools: Google makes Flutter with ease of use in mind. With tools like hot reload, developers can see what changes to the code without losing status. Other tools like widget inspection make it easier to visualize and diagnose UI layout issues.

Flutter has two main components, the Flutter SDK and the framework UI.

- Flutter SDK (Software Development Kit) – is a collection of tools and software used to develop applications using Flutter. The SDK includes various components such as compiler, debugger, emulator, and a variety of libraries required to build Flutter applications.
- Framework UI – is a component used to render the user interface of the application. The framework provides various elements such as widgets, buttons, navigation, and other features that allow developers to create appealing and consistent user interfaces across different platforms.

## System Requirements
Before starting the installation and development using Flutter, ensure that the device that will be used meets the minimum requirements. Here are the hardware and software requirements that are recommended to ensure that the development process can run smoothly.

#### _Hardware Requirements_ (macOS)

| Requirement         | Minimum      | Recommended   |
|---------------------|---------------|----------------|
| CPU Cores           | 4             | 8              |
| Memory in GB        | 8             | 16             |
| Display Resolution  | WXGA (1366 x 768) | FHD (1920 x 1080) |
| Free Disk Space     | 44.0 GB       | 70.0 GB        |

#### _Hardware Requirements_ (Windows)

| Requirement        | Minimum      | Recommended    |
|---------------------|---------------|----------------|
| CPU Cores           | 4             | 8              |
| Memory in GB        | 8             | 16             |
| Display Resolution  | WXGA (1366 x 768) | FHD (1920 x 1080) |
| Free Disk Space     | 11.0 GB       | 60.0 GB        |

#### Software Requirements (Both macOS and Windows)

- **Operating System**:
  - macOS 11 (Big Sur) _or later_.
  - Windows 10 64-bit _or later_.

## Tutorial: Installing Flutter

Before developing applications with Flutter, the following steps are required to install it.

#### Windows
> For a more detailed tutorial, you can access the link [here](https://docs.flutter.dev/get-started/install/windows/mobile).
1. Download the Flutter SDK [here](https://docs.flutter.dev/get-started/install/windows/mobile#download-then-install-flutter) for Windows.
![image](https://hackmd.io/_uploads/ByeUnVWeye.png)
2. After the folder has been downloaded, move the zip folder to a permanent folder or destination and extract the downloaded zip folder. It is recommended to create the folder in the following location:
    - `%USERPROFILE%\dev\` Example: `C:\Users\{username}\dev\flutter`.
    - `%LOCALAPPDATA%` Example: `C:\Users\{username}\AppData\Local\flutter`.  
    :::warning
    Do not install Flutter in the directory or _path_ that meets one or both of the following conditions:
	    - Contains special characters or spaces (make sure that `{username}` does not contain spaces or special characters when placed anywhere else).
	    - Requires administrator privileges (example: `C:\Program Files`).
    :::

    ![image](https://hackmd.io/_uploads/S1texrWgke.png)
    :::info
    In this tutorial, we will be using the PATH `C:\Users\{username}\dev\flutter`
    :::
3. Add Flutter to the PATH variable
    - Open the Start menu and type "env" in the search field. Then, select `Edit the system environment variables` from the search results.
        ![image](https://hackmd.io/_uploads/HkI5lHZlyg.png)
    - In the `System Properties` window, click the `Environment Variables` button.
        ![image](https://hackmd.io/_uploads/B1KaeHWekx.png)
    - On the `User variables for {username}` section, search for the `Path` variable and double click to edit it.
        ![image](https://hackmd.io/_uploads/r1HKZrZeye.png)
    - In the folder that was extracted previously, search for the folder named `bin`.
Copy the full path from the folder.
        ![image](https://hackmd.io/_uploads/rkqfGSWx1g.png)
        ![image](https://hackmd.io/_uploads/HJlVMBZxyx.png)
    - In the `Edit Environment Variable` window that was previously open, click **New** or double click on an empty line, then add the copied path.
        ![image](https://hackmd.io/_uploads/ByeHMSWeJe.png)
4. After the path has been added, click `OK` to save the change, click `OK` on the `System Properties` window as well, then close all windows and reopen the terminal or PowerShell to apply the changes.
5. To ensure that Flutter has been added to the correct path, open the terminal or PowerShell and run the command `flutter --version`. If Flutter has been installed correctly, you will see the Flutter version information that was installed.
    ![image](https://hackmd.io/_uploads/rkd_YBblye.png)
6. Congratulations! 🐼 Installation of Flutter has been successfully completed and you can proceed with the Android Studio installation.

#### MacOS
> For a more detailed tutorial, you can access the link [here](https://docs.flutter.dev/get-started/install/macos/mobile-android).

Specifically for macOS users, you can install Flutter using the following command in the terminal.
```bash
brew install --cask flutter 
```

If you have not installed Homebrew on macOS, you can install it with the following command.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

By default, the downloaded file `--cask` through Homebrew will be saved in
- `/opt/homebrew/Caskroom` for **Apple Silicon**
- `/usr/local/Caskroom` for **Intel-based Mac**

To ensure that Flutter has been installed correctly, you can run the following command in the terminal.
```
brew info --cask flutter
```
If Flutter has been installed correctly, information will appear similar to the one below.
![Screen Shot 2024-10-19 at 9.28.17 PM](https://hackmd.io/_uploads/HJZfMrZgJe.png)

Congratulations! Installation of Flutter has been successfully completed. To check the version of Flutter, run the following command and proceed with the Android Studio installation.
```
flutter --version
```

#### Linux
Installation for Linux can be seen [here](https://docs.flutter.dev/get-started/install/linux/android).

## Tutorial: Installing Android Studio
1. To start, download Android Studio from the official website [here](https://developer.android.com/studio).
2. After the download is complete, open the installer for Android Studio and run it to install Android Studio.
3. After that, open Android Studio with the following steps to complete the installation:
    - Click `Next` on the welcome page to start the installation process. Then, select the `Standard` option in the Install Type section to automatically install all required components.
        ![image](https://hackmd.io/_uploads/r1no18-xJx.png)
    - Click the `Finish` button to continue the installation process.
        ![image](https://hackmd.io/_uploads/rJfRyUWxkl.png)
    - On the installation page, you will see the License Agreement as shown below. Select `Accept` to accept all licenses, then click `Finish` to continue the installation.
![image](https://hackmd.io/_uploads/ByTHeLZeJg.png)
    - After the installation is complete, ensure that the required SDK components are installed correctly. On the home page, select `More Actions` and then click `SDK Manager`.
    ![image](https://hackmd.io/_uploads/SknSzIWeyg.png)
    - Or, you can log in to the **Settings > Languages & Frameworks > Android SDK** menu to check and ensure that the required components are installed as shown below.
      ![image](https://hackmd.io/_uploads/B1PDXUWg1x.png)
    - Make sure that these components are selected (checked):
      - **Android SDK Command-line Tools**
      - **Android SDK Build-Tools**
      - **Android SDK Platform-Tools**
      - **Android Emulator**
      - **NDK (Side by Side)**
      - **CMake**
      - **Android Emulator hypervisor driver (installer)**
    - If the **Status** column shows Update available or Not installed for a specific component, select the component and click `Apply`.
    - After the installation process is complete, click `OK` to save the changes and close the window.
4. After the Flutter installation is complete, we need to ensure that all required components have been installed and configured correctly. For this, Flutter provides the `flutter doctor` command that helps check the installation status.
    - Open the terminal or PowerShell, then run the `flutter doctor` command. The result will show whether all the required components have been installed correctly. Example output:
        ```
        C:\Users\Ridho>flutter doctor
        Doctor summary (to see all details, run flutter doctor -v):
        [√] Flutter (Channel stable, 3.24.3, on Microsoft Windows [Version 10.0.22631.4317], locale en-ID)
        [√] Windows Version (Installed version of Windows is version 10 or higher)
        [!] Android toolchain - develop for Android devices (Android SDK version 32.1.0-rc1)
            ! Some Android licenses not accepted. To resolve this, run: flutter doctor --android-licenses
        [√] Chrome - develop for the web
        [X] Visual Studio - develop Windows apps
            X Visual Studio not installed; this is necessary to develop Windows apps.
              Download at https://visualstudio.microsoft.com/downloads/.
              Please install the "Desktop development with C++" workload, including all of its default components
        [√] Android Studio (version 2024.2)
        [√] VS Code, 64-bit edition (version 1.93.1)
        [√] Connected device (3 available)
        [√] Network resources

        ! Doctor found issues in 2 categories.
        ```
    - If `flutter doctor` finds an issue, such as in the Android toolchain with the message "Some Android licenses not accepted", you can resolve it by running the `flutter doctor --android-licenses` command.

        ```
        C:\Users\Ridho>flutter doctor --android-licenses
        5 of 7 SDK package licenses not accepted. 100% Computing updates...
        Review licenses that have not been accepted (y/N)? y
        ```
    - Follow the instructions displayed on the screen and type `y` to accept the licenses that have not been accepted. After that, the issue related to the Android license will be resolved. Run the `flutter doctor` again.
    
        ```
        C:\Users\Ridho>flutter doctor
        Doctor summary (to see all details, run flutter doctor -v):
        [√] Flutter (Channel stable, 3.24.3, on Microsoft Windows [Version 10.0.22631.4317], locale en-ID)
        [√] Windows Version (Installed version of Windows is version 10 or higher)
        [√] Android toolchain - develop for Android devices (Android SDK version 34.0.0)
        [√] Chrome - develop for the web
        [X] Visual Studio - develop Windows apps
            X Visual Studio not installed; this is necessary to develop Windows apps.
              Download at https://visualstudio.microsoft.com/downloads/.
              Please install the "Desktop development with C++" workload, including all of its default components
        [√] Android Studio (version 2024.2)
        [√] VS Code, 64-bit edition (version 1.93.1)
        [√] Connected device (3 available)
        [√] Network resources

        ! Doctor found issues in 1 category.
        ```
    - You do not need to install **Visual Studio** because the focus of development is on mobile applications, so **Visual Studio** is not required. However, if you are planning to develop a Desktop Windows application in the future, you can install **Visual Studio** with the "Desktop development with C++" component through the link [here](https://visualstudio.microsoft.com/downloads/).
5. Congratulations! 🐼 Installation of Flutter and Android Studio has been successfully completed! 🎉 You are ready to start developing Flutter applications.

## IDE Usage
You can choose the IDE that you will use to develop Flutter applications.  You are recommended to use Android Studio.
1. Android Studio
2. Visual Studio Code

If you are using VS Code for developing using Flutter, you will need to install two extensions, **Dart** and **Flutter**:
![Screen Shot 2024-10-19 at 9.40.25 PM](https://hackmd.io/_uploads/BJ88HHWlyx.png)
![Screen Shot 2024-10-19 at 9.41.28 PM](https://hackmd.io/_uploads/B1ldHSbx1l.png)

## Tutorial: *Getting Started with Flutter*

1. Open the Terminal or Command Prompt.
2. Create and enter the directory where you will be saving the Flutter project.
3. Generate a new Flutter project in the terminal with the name **mental_health_tracker**, then enter the project directory.
    ```
    flutter create <APP_NAME>
    cd <APP_NAME>
    ```
4. Run your project through the Terminal or Command Prompt.
    ```
    flutter run
    ```
    There are several options to run the Flutter application, but the easiest option is:
    - Using the [Android Studio emulator](https://docs.flutter.dev/get-started/install/macos#set-up-the-android-emulator)
    - Using Google Chrome
        - Run the following command to *enable web support* (only needs to be done once):
            ```
            flutter config --enable-web
            ```
        - Then, in the project directory, run the project using the Google Chrome application with the following command:
            ```
            flutter run -d chrome
            ```
    - Using run debug (F5) in VS Code.
5. The following display will be shown.
    - Using the Android Emulator on the device
    ![image](https://hackmd.io/_uploads/BJsB6IZgyg.png)
    
    - Using the Google Chrome browser
    ![image](https://hackmd.io/_uploads/HyRtTIWgJg.png)

6. Perform `git init` in the root folder and perform `add-commit-push` the project to a new GitHub repository. You can name the repository `mental-health-tracker-mobile`.


## Tutorial: Reorganizing the Project Structure

Before developing Flutter applications further, we will reorganize the project files first to make the project code easier to understand. This is a best practice in developing applications, such as [clean architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html).

1. Create a new file named `menu.dart` in the `mental_health_tracker/lib` directory. On the first line of the file, add the following code:

    ```dart
    import 'package:flutter/material.dart';
    ```

2. From the `main.dart` file, cut the lines from line 39 to the end that contains the two classes below:

    ```dart
    class MyHomePage ... {
        ...
    }
    
    class _MyHomePageState ... {
        ...
    }
    ```

    to the file `menu.dart` that you just created.

3. You will see that in the `main.dart` file, there will be an error on line 34, which contains the following code:

    ```dart
    home: const MyHomePage(title: 'Flutter Demo Home Page'),
    ```

    This happens because the `main.dart` file no longer understands the MyHomePage class because you have moved it to another file, `menu.dart`. To solve this issue, add the following code at the beginning of the file.

    ```dart
    import 'package:mental_health_tracker/menu.dart';
    ```

4. Run the project using the Terminal or Command Prompt to ensure that the application still runs correctly.

## Tutorial: Creating a Simple Widget in Flutter
In this tutorial, you will learn how to create a simple widget in Flutter. You will create the main page with mental_health_tracker as the header, followed by the user information on the top, and creating the card as the _button_ for features such as "View Mood", "Add Mood", and "Logout". When the button is pressed, a notification will pop up on the bottom of the screen.

### Step 1: Changing the Application Theme Color

1. Open the `main.dart` file.

2. Change the code in the `main.dart` file in the application theme that has the type `MaterialApp` as shown below.

   ```dart
    colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.deepPurple,
    ).copyWith(secondary: Colors.deepPurple[400]),
   ```

	:::note  
        You can also change the application theme as desired following the [Colors documentation](https://api.flutter.dev/flutter/material/Colors-class.html).
	:::


### Step 2: Changing the Widget Page Menu to Stateless

1. In the `main.dart` file, remove `const MyHomePage(title: 'Flutter Demo Home Page')` so it becomes:

   ```dart
   MyHomePage(),
   ```

    Do not forget to delete the `const`-keyword.

2. In the `menu.dart` file, you will change the page widget from stateful to stateless with:
    
    - Remove all contents from `class MyHomePage ...` such as `const MyHomePage({super.key, required this.title});`, variable `final String title;`, comments in the file, and `State<MyHomePage> createState() => _MyHomePageState();`
    - Change `... extends StatefulWidget` to `... extends StatelessWidget` in `class MyHomePage`.
    - Add `MyHomePage({super.key});` as a constructor of `MyHomePage`.
    - Remove the entirety of `class _MyHomePageState extends State<MyHomePage>`
    - Add the build Widget so that the code looks like the following.

    <br/>After completing the steps above, the `menu.dart` file should look like this.
	```dart
	class MyHomePage extends StatelessWidget {
	    MyHomePage({super.key});

	    @override
	    Widget build(BuildContext context) {
		return Scaffold(
		    ... // do not copy this!
		);
	    }
	}
	```

### Step 3: Creating a Card with NPM, Name, and Class
It is important to note that each UI created by Flutter is called a widget and is built on the `Widget build()` section.

1. Before creating the card, you can declare three variables of type string containing the NPM, name, and class in the `class MyHomePage` in the `menu.dart` file as shown below.

    ```dart
    class MyHomePage extends StatelessWidget {
        final String npm = '5000000000'; // NPM
        final String name = 'Gedagedi Gedagedago'; // Name
        final String className = 'PBP S'; // Class
        
        ...
    }

    ```
    :::note
    Do not forget to change NPM, Name, and Class according to your data!!
    :::

2. After declaring the three variables, you can create a new class named `InfoCard` in the `menu.dart` file to create a simple card that will display the NPM, name, and class information.
    ```dart
    ...
    class InfoCard extends StatelessWidget {
      // Card information that displays the title and content.

      final String title;  // Card title.
      final String content;  // Card content.

      const InfoCard({super.key, required this.title, required this.content});

      @override
      Widget build(BuildContext context) {
        return Card(
          // Create a card box with a shadow.
          elevation: 2.0,
          child: Container(
            // Set the size and spacing within the card.
            width: MediaQuery.of(context).size.width / 3.5, // Adjust with the width of the device used.
            padding: const EdgeInsets.all(16.0),
            // Place the title and content vertically.
            child: Column(
              children: [
                Text(
                  title,
                  style: const TextStyle(fontWeight: FontWeight.bold),
                ),
                const SizedBox(height: 8.0),
                Text(content),
              ],
            ),
          ),
        );
      }
    }

    ```


### Step 4: Creating a Button Card with Icon

1. Before creating a button for the card, you can create a new class named `ItemHomepage` that contains the attributes of the card that you will create (in this case, contains the name and icon). On the `menu.dart` file, put the code snippet given below outside of the `MyHomePage` and `InfoCard` class.

   ```dart
    ...
    class ItemHomepage {
        final String name;
        final IconData icon;

        ItemHomepage(this.name, this.icon);
    }
    ...
   ```
2. After that, you can create a list of `ItemHomepage` that contains the buttons you want to add to the `MyHomePage` class.

   ```dart
    class MyHomePage extends StatelessWidget {  
        ...
        final List<ItemHomepage> items = [
            ItemHomepage("View Mood", Icons.mood),
            ItemHomepage("Add Mood", Icons.add),
            ItemHomepage("Logout", Icons.logout),
        ];
        ...
    }
   ```

3. When you have added the buttons you want, you can create the `ItemCard` class to display the button. For now, the button that is pressed will only display the snackbar message "You have pressed the [**button name**] button.".
    ```dart
    ...
    class ItemCard extends StatelessWidget {
      // Display the card with an icon and name.

      final ItemHomepage item; 
      
      const ItemCard(this.item, {super.key}); 

      @override
      Widget build(BuildContext context) {
        return Material(
          // Specify the background color of the application theme.
          color: Theme.of(context).colorScheme.secondary,
          // Round the card border.
          borderRadius: BorderRadius.circular(12),
          
          child: InkWell(
            // Action when the card is pressed.
            onTap: () {
              // Display the SnackBar message when the card is pressed.
              ScaffoldMessenger.of(context)
                ..hideCurrentSnackBar()
                ..showSnackBar(
                  SnackBar(content: Text("You have pressed the ${item.name} button!"))
                );
            },
            // Container to store the Icon and Text
            child: Container(
              padding: const EdgeInsets.all(8),
              child: Center(
                child: Column(
                  // Place the Icon and Text in the center of the card.
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Icon(
                      item.icon,
                      color: Colors.white,
                      size: 30.0,
                    ),
                    const Padding(padding: EdgeInsets.all(3)),
                    Text(
                      item.name,
                      textAlign: TextAlign.center,
                      style: const TextStyle(color: Colors.white),
                    ),
                  ],
                ),
              ),
            ),
          ),
        );
      }
      
    }
    ...
    ```

### Step 5: Integrating InfoCard and ItemCard to Display on MyHomePage
Remember that all UI elements (Widget) in Flutter will be defined and built on the `Widget build()` section. To integrate and display all the cards you are enjoying on the `HomePage`, you can change the `Widget build()` section in the `MyHomePage` class.

```dart
...
class MyHomePage extends StatelessWidget {
  ...  

  @override
  Widget build(BuildContext context) {
    // Scaffold provides the basic structure of the page with the AppBar and body.
    return Scaffold(
      // AppBar is the top part of the page that displays the title.
      appBar: AppBar(
        // The title of the application "Mental Health Tracker" with white text and bold font.
        title: const Text(
          'Mental Health Tracker',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        // The background color of the AppBar is obtained from the application theme color scheme.
        backgroundColor: Theme.of(context).colorScheme.primary,
      ),
      // Body of the page with paddings around it.
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        // Place the widget vertically in a column.
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            // Row to display 3 InfoCard horizontally.
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),

            // Give a vertical space of 16 units.
            const SizedBox(height: 16.0),

            // Place the following widget in the center of the page.
            Center(
              child: Column(
                // Place the text and grid item vertically.

                children: [
                  // Display the welcome message with bold font and size 18.
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to Mental Health Tracker',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),

                  // Grid to display ItemCard in a 3 column grid.
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    // To ensure that the grid fits its height.
                    shrinkWrap: true,

                    // Display ItemCard for each item in the items list.
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
...
```

:::tip

As a best practice, run the `flutter analyze` command in the root folder of your project after your code has been written.

This is usually done to ensure that there are no issues in your code that can hinder performance or application functionality. If you follow the tutorial correctly, the result of the command should show that there are no issues detected in your project.

```bash
mental_health_tracker % flutter analyze
Analyzing mental_health_tracker...                                      
No issues found! (ran in 1.6s)
```

If there is an issue in your code (such as in the section below), try to resolve the issue according to the tutorial or review the code line where the issue occurred.

```bash
mental_health_tracker % flutter analyze
Analyzing mental_health_tracker...                                      

  error • The constructor being called isn't a const constructor • lib/main.dart:37:13 • const_with_non_const

1 issue found. (ran in 1.5s)
```

This step can also help with the building process that will be done in some of the tutorials that are coming.

:::

## Closing

Congratulations! You have successfully completed Tutorial 6! 🐼🎉

You can try running the Flutter application using the `flutter run` command, as shown in the tutorial.

Now, you have mastered the basics of Flutter, starting from installation to understanding the basic structure of the application.

1. Learn and remember the code that you wrote above correctly.
2. After completing all steps in the tutorial, the Flutter application should now be able to display the initial screen as shown below.
    ![image](https://hackmd.io/_uploads/Hy9dEd5gyx.png)

    :::note
    This screenshot is taken from the Indonesian tutorial. Some text content might differ with the English tutorial.
    :::
3. At the end of the tutorial, the local directory structure should look like this.
    ```
    mental_health_tracker
    ├── .dart_tool
    ├── .idea 
    ├── android
    ├── ios
    ├── lib
    │   ├── main.dart
    │   └── menu.dart
    ├── linux
    ├── macos
    ├── test
    ├── web
    ├── windows
    ├── .gitignore
    ├── .metadata
    ├── analysis_options.yaml
    ├── mental_health_tracker.iml
    ├── pubspec.lock
    ├── pubspec.yaml
    └── README.md
    ```
5. Make sure that the local directory structure is correct. Next, perform `add`, `commit`, and `push` to update the GitHub repository.
6. Run the following command to perform `add`, `commit`, and `push`

   ```shell
   git add .
   git commit -m "<pesan_commit>"
   git push -u origin <branch_utama>
   ```

   - Change `<commit_message>` according to your preference. Example: `git commit -m "tutorial 6 selesai"`.
   - Change `<main_branch>` according to the name of the main branch. Example: `git push -u origin main` or `git push -u origin master`.

## Additional References

- [Flutter Documentation](https://docs.flutter.dev/)
- [Write your first Flutter app, part 1](https://docs.flutter.dev/get-started/codelab)
- [An Introduction to Flutter: The Basics by FreeCodeCamp](https://www.freecodecamp.org/news/an-introduction-to-flutter-the-basics-9fe541fd39e2/)
- [Flutter Course for Beginners – 37-hour Cross Platform App Development Tutorial by FreeCodeCamp](https://www.youtube.com/watch?v=VPvVD8t02U8)
- [An Introduction to Flutter Clean Architecture](https://medium.com/ruangguru/an-introduction-to-flutter-clean-architecture-ae00154001b0)


## Contributors

- Restu Ahmad Ar Ridho
- Naufal Ichsan
- Vinka Alrezky As
- Fiona Ratu Maheswari
- Muhammad Oka (EN Translation)

## Credits

This tutorial was developed based on [PBP Odd 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) and [PBP Even 2024](https://github.com/pbp-fasilkom-ui/genap-2024) written by the 2024 Platform-Based Programming Teaching Team. All tutorials and instructions included in this repository are designed so that students who are taking Platform-Based Programming courses can complete the tutorials during lab sessions.
