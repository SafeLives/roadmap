# Case Worker - 5 days

This part of the application is directly linked to the "form management system". Once a specific form is defined, the structure of the form is saved in Postgres. Each time a case worker insert data for a specific form, the structure of the form is loaded from Postgres and automatically converted to HTML. Then the Case worker only has to save and submit the data which will be saved in Postgres.

see how to work with encryption (https://www.postgresql.org/docs/8.1/static/encryption-options.html) to keep the data linked to clients secure

## Landing page

As a case worker:

- I can search for a client by her Id

- I can access the page to create a new client
- I can see my main stats:
  - number and links of unfinished cases
  - main analysis extracted from my cases and my service

## Save and Edit Client

- search for existing client
- save data for new client
- edit data for a specific client

## Save and Edit forms

- Select the client
- Select the type of form
- Save data for each step of the form
- Edit data of a form
- Submit the completed form
