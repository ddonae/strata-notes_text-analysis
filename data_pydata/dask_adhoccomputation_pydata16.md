# Dask for Parallelism and Distrbuted Computing
@author: Matthew Rocklin, Continuum Analytics

## Overview
- dask provides paralleize numpy and pandas, but also used for arbitrary computations  
- provides UI of scheduler to see how it runs and is splitting things up

recent talks: scipy july 2016, pygotham aug 2016

Key functions
- dask.array: distributed clustering, built on many numpy arrays, coordinates parallel algorithms  
- dask.dataframe: large dataframe composed of many pandas DFs

Breaks csv files into smaller bytes, turn bytes into pandas DF in memory  
- dask DF is coordinating the various pandas DFs  
- can run functions very quickly on dask DFs  

## Demo: Tips in NYC  
using filters and groupby  
what happens when problems don't fit into a big dataframe?
- dask core can be used to parallelizing python computations

## Example
- load a bunch of files, load sql table
- normalize data
- rolling computation and append to a list
- take random subset, compare them

## Ad-hoc computation functions
- use dask delayed to add lazy values to task
- can use dask to visualize the parallel computations
- dask distrbuted to compute
allows us to write parallel code in the way we would write normal code

## Comparisons and Use Cases
- Map / shuffle / reduce: Spark
- Pipelines, ETL: Luigi, Airflow, Celery
- Efficient TimeSeries
- Transpose of arrays and add themselves, matrix multiply
- modern SVD
- arbitrary graph execution
- dynamic task scheduler

## Task scheduling - How it works
decisions are done in small, done in constant time
which function to run first?
- the one that exposes most parallelism first
- one that is resource heavy first
where to run it? which machines?
- based on data locality
- minimize communication, move smaller bytes of data and move it to bigger
- balance computation and communication: move things based on expected run time on queue of workers
- move tasks to idle workers
intellgent scheduling requiers lots of measurement

other optimizations
- scale up or down based on load
- compress messages
- oversubscribe workers
- spill unused data to disk

