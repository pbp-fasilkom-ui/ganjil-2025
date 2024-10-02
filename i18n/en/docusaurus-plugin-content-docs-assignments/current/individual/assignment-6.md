---
sidebar_label: Assignment 6
sidebar_position: 6
Path: assignment/individual/assignment-6
---

# Assignment 6: JavaScript and Asynchronous JavaScript

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Assignment Description

In this assignment, you have to implement AJAX in the application that you created in the previous assignment.

Checklist for this assignment is as follows:

- [ ] Modify the previously created assignment 5 to use AJAX.
  - [ ] AJAX GET
    - [ ] Modify the codes in data cards to able to use AJAX GET.
    - [ ] Retrieve data using AJAX GET. Make sure that the datas retrieved are only the datas belonging to the logged in user.
  - [ ] AJAX POST
    - [ ] Create a button that opens a modal with a form for adding a mood entry.

        :::note  
        The modal is triggered by clicking a button on the main page. When adding a mood entry successfully, the modal should be closed, and the form input should be cleared from the data entered before. If adding the mood entry fails, show an error message. 
        :::

    - [ ] Create a new view function to add a new mood entry to the database.
    - [ ] Create a `/create-ajax/` path that routes to the new view function you created.
    - [ ] Connect the form you created inside the modal to the `/create-ajax/` path.
    - [ ] Perform asynchronous refresh on the main page to display the latest item list without reloading the entire main page.
    :::warning
    Make sure the AJAX `GET` and `POST` can be done securely.
    :::
- [ ] Answer the following questions in `README.md` in the root folder (please modify the `README.md` you have created; add subheadings for each task).
    - [ ] Explain the benefits of using JavaScript in developing web applications!
    - [ ] Explain why we need to use `await` when we call `fetch()`! What would happen if we don't use `await`?
    - [ ] Why do we need to use the `csrf_exempt` decorator on the view used for AJAX `POST`?
    - [ ] On this week's tutorial, the user input sanitization is done in the back-end as well. Why can't the sanitization be done just in the front-end? 
    - [ ] Explain how you implemented the checklist above step-by-step (not just following the tutorial)!

- [ ] Perform `add`-`commit`-`push` to GitHub.

## Deadline

The deadline for Assignment 6 is **Wednesday, 9th October 2024, at 12:00 p.m.**

The teaching assistants will check the last commit of the lab assignment repository, so you do not need to submit the repository link separately.
