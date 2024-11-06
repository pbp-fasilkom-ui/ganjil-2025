---
sidebar_label: Assignment 8
sidebar_position: 8
Path: assignment/individual/assignment-8
---

# Assignment 8: Flutter Navigation, Layouts, Forms, and Input Elements

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science, Universitas Indonesia, Odd Semester 2024/2025

---

## Assignment Description

In this assignment, you will implement navigation, layout, form, and form input elements in the Flutter application you developed in the previous assignment.

The checklist for this assignment is as follows:

- [ ] Create at least one new page in the application, specifically a form page to add a new item with the following requirements:
	- [ ] Use at least three input elements: `name`, `amount`, and `description`. Add input elements according to the model in your previous Django project.
    - [ ] Include a `Save` button.
    - [ ] Each input element in the form must also be validated with the following criteria:
        - [ ] No input field should be left empty.
        - [ ] Each input field must contain data in the model's data type.
        ::::warning
        Pay attention to cases such as negative numbers, minimum string length (if applicable), maximum string length (if applicable), and so on. It's not just about data types!
        ::::
- [ ] Redirect the user to the new item addition form when they press the `Add Item` button on the main page.
- [ ] Display the data from the form in a `pop-up` after pressing the `Save` button on the new item addition form page.
- [ ] Create a drawer in the application with the following requirements:
    - [ ] The drawer should contain at least two options: `Home` and `Add Item`.
    - [ ] When selecting the `Home` option, the application should redirect the user to the main page.
    - [ ] When selecting the `Add Item` option, the application should redirect the user to the new item addition form page.
- [ ] Answer the following questions in `README.md` in the root folder (please modify the `README.md` you created earlier; add subtitles for each assignment).
    - [ ] What is the purpose of `const` in Flutter? Explain the advantages of using `const` in Flutter code. When should we use `const`, and when should it not be used?
    - [ ] Explain and compare the usage of Column and Row in Flutter. Provide example implementations of each layout widget!
    - [ ] List the input elements you used on the form page in this assignment. Are there other Flutter input elements you didn’t use in this assignment? Explain!
    - [ ] How do you set the theme within a Flutter application to ensure consistency? Did you implement a theme in your application?
    - [ ] How do you manage navigation in a multi-page Flutter application?
- [ ] Perform `add`-`commit`-`push` to GitHub.

## Submission Deadline

The deadline for Assignment 8 is Wednesday, November 13, 2024, at 12:00 pm.

Teaching assistants will check the last commit from your task repository, so there is no need to submit the repository link in the submission slot.