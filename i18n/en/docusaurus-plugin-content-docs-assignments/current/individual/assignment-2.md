---
sidebar_label: Tugas 2
sidebar_position: 1
Path: docs/tugas-2
---

# Tugas 2: Implementasi *Model-View-Template* (MVT) pada Django

Platform-Based Programming (CSGE602022) — Organized by the Faculty of Computer Science Universitas Indonesia, Odd Semester 2024/2025

---

## Assignment Description

On this assignment, you will implement the *Model-View-Template* concept and some concepts you have learned in class and tutorials. Please note that the project you create for the assignment **is different** from the project used in the tutorial.

## Application Theme

The main application theme for the PBP assignment is an *E-Commerce* application. You are given a choice of name and a small application theme. Create the assignment in your own way if you want.

:::danger
Make sure the name and content of the assignment **DO NOT** contain **NSFW** and do not violate SARA (Ethnicity, Religion, Race, and Inter-group Relations). If you violate this rule, there might be consequences that potentially affect other courses you are currently taking. For example, your GitHub account could get suspended.
:::

Your application from the assignment must have the following attributes in the model.

- `name` as the name of the item with type `CharField`.
- `price` as the price of the item with type `IntegerField`.
- `description` as the description of the item with type `TextField`.

You are allowed to add other attributes if you want, such as `stock`, `category`, `image`, and others. However, the application you create must have the three mandatory attributes above (`name`, `price`, `description`). The name of the mandatory attributes can be changed according to your application needs.

Some ideas for application management that you can make are as follows.

- e-shop: `nama`, `harga`, `description`, `rating`, `date`.
- Coquette Shop: `name`, `price`, `description`, `coquette-ness`.
- Toko Ijo: `name`, `price`, `description`, `quantity`.

## Assignment Checklist

These are the *checklist* for the assignment.

- [ ] Create a new Django project.
- [ ] Create an application with the name `main` in the project.
- [ ] Perform *routing* in the project so that the application `main` can run.
- [ ] Create a model in the application `main` with the name `Product` and have the mandatory attributes as follows.
    - `name`
    - `price`
    - `description`
- [ ] Create a function in `views.py` to return to an HTML *template* that displays the name of the application and your name and class.
- [ ] Create a *routing* in `urls.py` for the application `main` to map the function created in `views.py`.
- [ ] Perform *deployment* to PWS for the application that has been created so that it can be accessed by others via the Internet.
- [ ] Create a `README.md` that contains a link to the PWS application that has been *deployed*, as well as answers to the following questions.
    - Explain how you implemented the checklist above step-by-step (not just following the tutorial).
    - Create a diagram that contains the *request client* to a Django-based web application and the response it gives, and explain the relationship between `urls.py`, `views.py`, `models.py`, and the `html` file.
    - Explain the use of `git` in software development!
    - In your opinion, out of all the frameworks available, why is Django used as the starting point for learning software development?
    - Why is the Django model called an *ORM*?

Keep in mind that you must complete this assignment using a **different** repository than the tutorial.

## Deadline

The deaadline for Assignment 2 is **Wednesday, September 11th 12.00 PM**.

Please submit the link to the repository you used in the submission slot provided by SCELE.
