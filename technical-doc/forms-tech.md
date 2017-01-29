# Forms - 4 sprints

Most of the work on this part is to create a postgres representation of a form which is abstract enough to be able to be dynamically modify. Once th structure is defined we need to be sur that the UI which will be automatically rendered from the form strucutre is correctly displayed

## How to represent a form:

A from can be represented by the following three main types:

- Form = list of sections
- Section = list of questions
- Question = label + predefine type of answer (text, boolean, integer, ...)

The "Question" type conatins the "anwser" type which must be predefine (most of the anwser of the form are checkbox, so can be represented by a boolean) and easyly represented with HTML.

So when a user create a new type of form she will create new entries in these main tables (form, section, question, answer) in Postgres.

**To keep the order of the section and questions each item of the forms must have an "order" property.**

## Creating a form

- create form - define the name of the form - link the section to the form
- create section - define the name of the section - link the questions to the section
- create question - define the name and the question itself - link the type of anwser

- anwsers - this table will contain all the answer submitted by the case workder for each cases

## Editing a form

To keep the integrity of the forms already submitted, editing a form is creating a new version of a specific form. This will allow us to keep track of all the modification and to avoid conflict with the data already saved if a form is changed



## Define action on specific response

Some type of answers can have an effect on other questions (disable some questions depending of the result of previous anwser). To create this link between questions, we can specify some basic trigger actions than can be automatically executed. These triggers allow the case workers to submit data rapidly.