# Creating PostgreSQL Databases

## Structure of PostgreSQL Database

### Creating a database

CREATE DATABSE db_name;

### Creating tables

#### Syntax

CREATE TABLE table_name(

    column1_name column1_datatype [col1_constraints}

);

##### Example

CREATE TABLE school (

    id serial PRIMARY KEY,

    name TEXT NOT NULL

    mascot_name TEXT

);

### Creating schemas

Providing database users with separate environments

**Schema Uses**

- organizing database objects into related groups

**The default schema**

- The public schema is the default schema in PostgreSQL

#### Example

CREATE TABLE school (

    id serial PRIMARY KEY,

    name TEXT NOT NULL

    mascot_name TEXT

);

name of schema: public.school 

**Create SCHEMA command**

#### Syntax

CREATE SCHEMA schema_name;

##### Example

CREATE SCHEMA division1;

CREATE TABLE division1.school (

    id serial PRIMARY KEY,

    name TEXT NOT NULL

    mascot_name TEXT,

    num_scholarships INTEGER DEFAULT 0 --IF NO VALUE IS EXPLICITLY STATED

);
