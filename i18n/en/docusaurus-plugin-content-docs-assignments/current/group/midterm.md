---
sidebar_label: Midterm Project
sidebar_position: 1
Path: assignment/group/midterm
---

# Midterm Project

**Creating a Website using Django Framework (Group Project)**

---

## Specific Learning Objectives

1. Designing Web Pages
2. Implementing a website using the Django framework by fulfilling Models, Views, and Templates
3. Utilizing CSS frameworks to achieve Responsive Web Design
4. Implementing Unit Tests and deployment

## General Rules for Group Assignment

1. Each group consists of 5-6 people. Group divisions can be viewed on SCELE.
2. Each group creates one Git repository used by all group members to collaborate. Submit the Git repository link to SCELE.  
:::tip  
Each group is advised to use GitHub Organizations to facilitate collaboration between team members. Additionally, for the Final Project, each group will be asked to create a new repository, and GitHub Organizations can help in 'grouping' these repositories.  
:::  
3. Each group is allowed to come up with their own ideas about the application to be created. The application theme is **information about products in a city**. This theme is chosen because it's inspired by the new capital city, IKN (Nusantara Capital City). If we move to or visit a city for the first time and want to buy a product in that city, we might not know which store sells that product in that city, and we need an application that provides information about that product in that city.
4. For this PBP group assignment, each group is free to choose the city that becomes the location basis for the group's application, for example, Depok City.
5. Each group must determine the main product category that becomes the initial dataset of the group's application. The main product category must contain at least 100 types of products. Examples:
    - If the main product category is laptops & mobile phones, then the initial dataset must have at least 100 brands and types of laptops & mobile phones.
    - If the main product category is food & beverages, then the initial dataset must have at least 100 types of food & beverages.
    - If the main product category is books, then the initial dataset must have at least 100 book titles.
    - If the main product category is plants, then the initial dataset must have at least 100 types of plants.
6. Each group implements the initial dataset in the form of a Models class and stores data from the initial dataset into the Django database. Data sources for the initial dataset can come from anywhere, for example from Kaggle and Wikipedia.
7. Each group member works on a different module. Modules are determined by the group according to the application idea that has been discussed within the group.
8. The group assignment is deployed as a unified web application. Each group is expected to use PWS as a PaaS for TK project deployment, but each group is also given the freedom to deploy on other PaaS.

## Specific Rules per Group Member

1. Implement Models by creating, utilizing those provided by Django, or utilizing those already created by other group members (in other modules).
2. Implement Views to process requests and process data to produce responses using HTML templates or return JSON responses.
3. Implement HTML templates with a systematic and efficient framework, such as `base.html`, `header.html`, and `footer.html`.
4. Implement HTML templates using a responsive framework (such as [Bootstrap](https://getbootstrap.com/) or [Tailwind](https://tailwindcss.com/)).
5. Have a form page that can receive input from users which is then processed by Views. Examples of processing by Views are inserting data into Models, querying data from Models, and updating data in Models.
6. Implement JavaScript with AJAX calls.
7. Implement information filtering for logged-in users only. For example, address data, age, and mobile phone numbers can only be seen by logged-in users.
8. Implement filtering on the list of products from the initial dataset displayed. For example, displaying a list of products based on price.

## Group Assignment Stages

<table>
    <tr>
        <th>Stages and deliverables</th>
        <th>Deadlines and Notes</th>
    </tr>
    <tr>
        <td>
            <b>Stage I (40%)</b>
            <ul>
                <li>Creation of group GitHub</li>
                <li>README.md on GitHub containing:</li>
                    <ol>
                        <li>Names of group members</li>
                        <li>Application description (story of the proposed application and its usefulness)</li>
                        <li>List of modules to be implemented</li>
                        <li>Source of initial dataset for main product category</li>
                        <li>User roles and their descriptions (as there may be more than one type of user accessing the application)</li>
                        <li>Application deployment link</li>
                    </ol>
            </ul>
        </td>
        <td>
            <b>Deadline: Wednesday, October 9, 2024, at 23:55 WIB</b>
            <p><b>Submit to SCELE: GitHub Link</b> with the Django project code base prepared on GitHub.</p>
        </td>
    </tr>
    <tr>
        <td>
            <b>Stage II (60%)</b>
            <p>(Modules already well implemented)</p>
            <p>Checklist:</p>
            <ul>
                <li>Application modules from each group member</li>
                <li>URL Mapping for modules</li>
                <li>Models for modules</li>
                <li>Views for modules</li>
                <li>Integrated as a unified application</li>
                <li>Functionality according to design plan</li>
                <li>Unit Tests (passed) for all aspects, expected code coverage to reach at least 80%</li>
            </ul>
        </td>
        <td>
            <b>Deadline: Sunday, October 27, 2024, at 23.55 WIB</b>
            <p><b>Submission Criteria:</b> All modules worked on by each group member have appeared and can be accessed in the Django project.</p>
        </td>
    </tr>
</table>
