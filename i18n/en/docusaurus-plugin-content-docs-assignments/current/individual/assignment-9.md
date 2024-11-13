---
sidebar_label: Assignment 9
sidebar_position: 9
Path: assignment/individual/assignment-9
---

# Assignment 9: Integrating Django Web Service with Flutter Application

Platform-Based Programming (CSGE602022) — organized by the Faculty of Computer Science, University of Indonesia, Odd Semester 2024/2025

---

## Assignment Description

In this assignment, you will integrate the Django services you have created in previous assignments with the Flutter application you created earlier.

The checklist for this assignment is as follows:

- [ ] Ensure the deployment of your Django project is running smoothly.
For issues related to PWS, which cannot yet be integrated with Flutter, the Teaching Assistant Team will provide further information later. In the meantime, you are allowed to perform integration on localhost only.
- [ ] Implement the registration feature in the Flutter project.
- [ ] Create a login page in the Flutter project.
- [ ] Integrate the Django authentication system with the Flutter project.
- [ ] Create a custom model according to your Django application project.
- [ ] Create a page containing a list of all items available at the `JSON` endpoint in Django that you have deployed.
    - [ ] Display the `name`, `price`, and `description` of each item on this page.
- [ ] Create a detail page for each item listed on the Product list page.
    - [ ] This page can be accessed by tapping on any item on the Product list page.
    - [ ] Display all attributes of your item model on this page.
    - [ ] Add a button to return to the item list page.
- [ ] Filter the item list page to display only items associated with the currently logged-in user.
- [ ] Answer the following questions in the `README.md` in the root folder (please modify the `README.md` you previously created; add subheadings for each assignment):
    - [ ] Explain why we need to create a model to retrieve or send JSON data. Will an error occur if we don't create a model first?
    - [ ] Explain the function of the http library that you implemented for this task.
    - [ ] Explain the function of `CookieRequest` and why it’s necessary to share the `CookieRequest` instance with all components in the Flutter app.
    - [ ] Explain the mechanism of data transmission, from input to display in Flutter.
    - [ ] Explain the authentication mechanism from login, register, to logout. Start from inputting account data in Flutter to Django’s completion of the authentication process and display of the menu in Flutter.
    - [ ] Explain how you implement the checklist above step by step! (not just following the tutorial).
- [ ] Perform `add`-`commit`-`push` to GitHub.

## Deadline

The deadline for Assignment 9 is **Wednesday, 20th November 2024, at 12:00 PM**.

The teaching assistants will check the last commit of the lab assignment repository, so you do not need to submit the repository link separately.
