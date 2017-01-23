# Analysis tables

![analysis](../../img/analysis.png)

An analysis table is a collection of answers from a specific question of a form.
The answers are aggregated or analysed (average, median, sum...) then represented by specific graphs.

The main goal of the analysis table feature is to allow an Safe Lives Admin to extract and create quickly the representation of the anwsers.

The current way of creating the analysis table (with Snap) is to export in csv. Then Excel is used to filter and process the results. The goal of the new analysis tables process is to simplify and include the data processing into the application without having to export the data in csv.

## Features

As a Safe Lives Admin:

### Browse existing analysis tables

- I can see the list of the graph representation of the existing analysis tables
- I can filter run the analysis table on a specific timeline
- I can filter the analysis table

### Create new analysis tables

![new analysis table](../../img/analysis-create.png)

- I can edit an existing analysis table By searching by categories/tags linked to the analysis table
- I can create a new analysis table:

#### Main strucutre of a table

- the aggregate value for each answer of the question (ex: location)
or
- caluculated value (sum, median, average,...) from the answer (ex: age)
- the numerical value
- the percentage for a specific service
- comparaison to the previous year

The structure of the table can be extended by adding different type of column

- compare by role
- compare by services
- ...

![analysis table type](../../img/analysis-table-type.png)

#### Filter data of a table

The forms where the data of the tables are extracted from can be first filtred:
- by services
- by roles
- by dataset (set of specific roles)
- by type of anwser on specific question (ex: only take children forms)

#### Table based on calculated value (instead of specific answer)

It is possible to create a specific table based on a calculated values, the average time of the cases length for a specific service. The length of a case is calculated from the time of creation and exit of a form.

## Flexibility of the analysis table

The analysis table are build on a main structure (value, percentage, compare by year) however this structure needs to be easily extended and more complicated analysis need to be added to the tables. Currrently the wireframes descibed the basic structure of a table but managing all the complexity and cases of the analysis tables will be difficult inside the application. Building a whole analysis system could be time consuming (months of development) and not very effecient. For that we recommend to use some specific tools (https://redash.io/get-started/ or https://www.elastic.co/products/kibana, see also a this list of tools https://blog.blendo.co/the-ultimate-list-of-custom-dashboards-and-bi-tools-to-track-your-metrics-and-gather-insights/) which can be easily integrated with the new database.

![analysis table type](../../img/redash-preview.png)

The application can however provide some predefine graphs and analysis tables. This can be some relatively easy queries that are used often by Safe lives and the other services (http://www.chartjs.org/, https://d3js.org/).