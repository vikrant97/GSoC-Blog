---
layout: post
title: "Phase 1 Progress"
---

By the end of community bonding period we were done with all the **requirements elicitation** and **designing** process. In the community bonding period I also did the installation of the required tools : `apache-server`, `flask` and it's dependencies, `MySQL` and other `3rd party libraries` required.

This phase is directly headed towards the coding part of the project.

# [](#header-1)Decisions made post community bonding period
We decided to go with **MySQL** under the abstraction of _flask-SQLAlchemy ORM_.

## [](#header-2)Rationale for using MySQL

*   Not only it's very _popular_ and _easy to use_, but also
*   there's a great _support_ for it.
*   _Security_ wise also it's very reliable.
*   Also, switching from MySQL to Maria-DB is quite simple but the reverse is not true. So we can switch to Maria-DB in future if the need be.

# [](#header-1)Progress made so far
I am strictly following the timeline proposed in the project proposal and have been able to convey all the deliverables as per the timeline as of now. The Phase 1 coding tasks have been completed. Apropos of phase 1 deliverables, code has been pushed to the github repository [Rapid Annotator][repository-link].

## [](#header-2)Directory Structure / File Hierarchy
With _blueprints_, we can have possibly 2 different Directory Hierarchy choices namely : **functional** and **divisional**. By examining the pros and cons of both I decided to go with a _hybrid_ of the two.

*   As per _divisional approch_ We will divide Rapid Annotator into several smaller packages which will be related to specific tasks. For example **admin package** will manage all the control the admin has over all application.
*   Borrowing from _functional approach_ we will have code that can be shared across all the packages. For example : generic jinja-macros, jinja-filters, WTForms-validators, css and other reusable code can be used by any of the packages.   

Hence, the final Directory Structure is a below

![image](https://guptavaibhav18197.github.io/GSoC-Blog/assets/images/dirStructure.png)

## [](#header-2)Code Implemented
As explained above the entire code base is divided into many smaller packages using _flask_ **Blueprints**. Below is the list of packages of Rapid Annotator mentioning their functionality along with their names.

Packages of Rapid Annotator

| Functionality             | Name assigned         |
|:--------------------------|:----------------------|
| Login/Registration        | frontpage             |
| Home Page                 | home                  |
| Add New Experiment        | add_experiment        |
| View Experiment           | view_experiment       |
| Annotate “This Experiment”| annotate_experiment   |
| Admin Page                | admin                 |

Phase 1 deals with working on first 3 packages namely : `frontpage`, `home` , `add_experiment`. Broadly this phase aims at finishing the `frontpage` and `home` packages completely and start working on `add_experiment` package.

### Backend Implementation

*   Created **User** relation.
*   Created **Experiment** relation.
*   Created **ExperimentOwner** association table to make _many to many_ relation between User and Experiments.
*   Created **AnnotatorAssociation** association object to make _many to many_ relation between User and Experiments.

An _association object_ was needed since this relation had additional fields of _start_, _end_ and _current_ integer fields indicating the range of the files that specific User has to annotate and the current file number that specific User is annotating.

### Generic Code

*   Created generic macros for rendering similar structured information like forms.
*   Created a generic **base template** that will be common to all the tabs and pages via _Jinja template inheritance_.
*   Enhance UI of the basic structure of base template

### frontpage package

*   Created UI for Login Page.
*   Got _Flask-SQLAlchemy_ working and connected it to MySQL server.
*   Wrote **validators** for making sure username attribute follows a specific _regex_ pattern.
*   Created **Login Form** and **Registration Form** and fields using FlaskForm of _flask_WTF_ and fields of _WTForms_.
*   Linked it to database and finished user registration.

### home package

*   Displayed 2 tabs: **My Experiments** & **Experiments to Annotate**.
*   UI details and made a responsive front-end.
*   Created **filters** required to render specific stuff like datetime in specific format.

### add_experiment package

*   Added Owner dropdown displaying list to choose owner from.
*   Added Annotator dropdown displaying a list to choose annotator from.
*   Used Javascript's _jQuery_ library to make _ajax_ requests to add Owner and Annotators.

## Deviations from the proposal

### Changes in the database schema

*   In the _User model_: I have clubbed _first name_ and _second name_ : into `fullname`, since there is no need of an additional field for name.
*   In the _User model_: _Password Salt_ is not included in the model: because we are using _flask_bcrypt_ that recommends using the inbuilt salt value. So, I am now storing Password Hash under the field name _password_ itself.
*   In the _Experiment model_: **created_at** and **status**[complete/incomplete] attributes have been added for ease of access by the Owners and Annotators.  

[repository-link]: https://github.com/guptavaibhav18197/rapidannotator
