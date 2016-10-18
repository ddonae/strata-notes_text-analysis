# NoSQL doesn't mean No Schema in MongoDB
@author: Steve Lott

## what is schema
- three schema concept: user or external views, logical model, physical implementation
- Erwin, column datatypes
- user's understanding may involve things that aren't written down, constraints, olicies
- derived data
- star scehma, normalized
- sql encdoded 4 times: DDL SQL, RDBMS, in the SQL code, and non-SQL code

## Schema in NoSQL
- user schema / logical schema are the same thing
- physical is storage mgmt system, for Mongo this is WiredTiger
- only encoded once, in the application

## representing a schema w/ code vs metadata
- representation mismatches: wrong query, wrong app program
    - if schemas don't match, change is expensive, hard to change
    - schema is limited to bare minimum
    - adding extra layers
- objective: defined schema, in the code, stated once
- schema representation: code or **metadata**
    - ad-hoc, pure coded-based: asserting column names using if statements
        - mapping using ORM-like layers (https://mongoengine.org)
    - schema as separate metadata, using JSON (https://json-schema.org/)
        - python-jsonschema
        - schema as code using dictionaries or in class definition
        - external files
        - in mongo schema collection

## use cases for schema definitions
- design and modeling: documenting assumptions
    - a spike is easiest
    - create scripts to mimic user stories, tweak until scripts work well, use for performance testing, formalize with swagger spec
- data validation: check the document before saving
    - try building some class, raise exception if it violates schema, otherwise insert into database
- schema migration: check the collection before making change and after

## python metaclass
using bson

## schema version mgmt and migration