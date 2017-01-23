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

## UI
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

## Logic

### Login
- Post request with email and password in payload
- Check if email match the password on Postgres
- Create jwt cookie which contains the minimum information about the user. **Do we need an expiration time on the cookie?**
- If login error display the failed login message on the login page

### Forget Password

- User submit a post request with the email where the password needs to be reset for
- An email is sent to the email with a link /reset-password/{jwt-reset} where jwt-reset is a jwt valid only for a short period of time (5 minutes?). **Should we make the jwt-reset only be usable once or is the expiration time is enough?**

# Create new user

Only Safe Lives Admin can create a new user - except for a Service Manager who can also create only Service Worker user for their own service.

## UI

- Create html form to let admins enter information about new users
  - email, service dropdown (if applicable, some role are indepandent of services), role, dataset **which other data are required to create a new user?**
- Admin submit post request to create a new user
- Joi validation which verify that the email is not already used in the database, that a service has been selected **What are the other validations needed for this form?**

## Logic

- Admin create post rquest to create a new user
- If the data are valid an activation email is send to the new user. The email contains a jwt link activation valid for a short period of time (1 week?). Once this link is clicked the user is redirected to a page where the password is defined
- A user has the status "inactive" when created by an Admin but as soon as the password is defined by the user the account become "active"

# Create new service

Only a Safe Lives Admin can create a service. A Service Manager would then be able to edit her service only

- Create form to enter a new service
  - Name of the service, Location of the service, **What are the other fields needed to create a new service?**
  - Add Joi validation on these fields

# Create new role and dataset

a Safe Lives Admin and a Service Manager can create new type of role. Each new type must be linked to specific permissions.

