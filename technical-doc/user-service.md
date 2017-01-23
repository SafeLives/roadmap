# Users and Services - 10 days

We have recently created this kind of user and services (organisation) management system with EMF. All this system is extracted in an Hapi plugin, [pg-people](https://www.npmjs.com/package/pg-people) and can be easily reused.

[Abase](https://github.com/dwyl/abase) might also be userfull for these features.

I don't see any difficulties and the logic of this kind of system is relatively simple.

Main steps:

- create Postgress tables user and service
- create handler to add and edit users
- create handler to add and edit services
- create handler to add and edit role/type of users
- create handler to add and edit a dataset
- create handler to attached a role/type of users to a Dataset
- display list of users
- display list of services
- apply right permissions to each routes
- send validation email to new created user
- Create UI, html, css

# Login

- Create UI for login page
  - email and password fields with submit button
  - Add Joi validation on the payload submitted
    - email field contain a email?
    - password field contains minimum length?
  - add error html placeholder (span with specific css class)
    - **The error message shouldn't give any information on what went wrong during the login process**: "The email doesn't exists", "The password is not the right one for bob@gmail.com"...
    - Instead just say the login didn't work: "Sorry the email or passwor is incorrect"
  - Add "forge password?" link


- Create UI for "forget password" page
  - email field
  - Joi validation on email field
