# Dynamics in Graphs, Adding Time as a Structure
@author: Benjamin Bengfort, District Data Labs

GH: https://github.com/districtdatalabs   
Library: GraphTool, NetworkX
- graphtool is faster and more scalable

Why use graphs?
- algorithm performance: optimization, iterations, lightweight embedding of sparse data, parallelism
- visual analytics: understanding networks and relationships, compact representations

## classes of graphs
- construction: given a set of paths is graph possible, everything connected or are there orphans
- optimization: shortest path
- enumeration
- existence

## property graphs: the data of graphs
structural elements with key-value pairs and unique ID
- graph of vertices and edges
    - can embed multi-domain models (multiple relational tables)
- vertex: object with incoming / outgoing edges
- edge: has source and target vertices

## how to model time in graphs?
in a relational context, we have entity tables and relationship tables
- if you put time with the relationship, then it is very static, only one time represented
- have to create event tables to capture series of discrete times
in a graph, time is a property
- ordinal, timestamps, durations, timers / elapsed
- can be edges, vertices, or the whole graph
- Example: time graph --> order of events (edges), predicted times (vertex), build time (edge), start finish duration (vertex)

## traversals
- starting node(s), traverse out along edges to other nodes until criteria is met, connecting information as you go
- add randomness to get stochastic
time modifies traversal
- can be bounded by time
- use centrality measures to weight time
- can use to model decay (how relationship changes over time)
- can use tentative or future edges
Example: email data model
- vertices as emails, timestamp as edge property
- calculate sent range: removes older emails
- calculate degree filter: can condense emails in the same thread are consolidated
- can use to view what's going on with your email for this month, what have I been working on?

## time aggregation
the granularity of time
- time as discrete time steps
- time as ordinal: before / after
- time as continuous, intervals between time steps
- hierarchy of time: years, months, days, hours, minutes, seconds,etc.
modeling time as an independent element
- time as vertices with properties
- time as a dynamic graph with multiple sub-graphs

## NLP graph analysis process
data ingestion
- baleen corpus ingestion: corpus of web text data
- minke corpus processing: extract noun keyphrases weighted by TFIDF
data modeling
- document graph as feeds, categories, phrases / text
- get subset, graph network too big
data wrangling
- filter out unique emails, only view commonalities
- take the log plot of magnitude of vertex types
visualize
- look at degree distribution: primarily there are phrases
- power log function: small worlds graphs

centrality of time
- extract week of year as granularity for time
- go through vertices (documents), extract publish date
- add week as vertex
- for every document, link to vertex of week

## centrality measures
determines important relationships
- degree
- betweeness: weeks ordered by importance and key phrases are sub-ordered by importance
- eigenvector
- katz

## keyphrase dynamics
what's going on over time?
- create a sequence of time ordered subgraphs
- detect when important keyphrases occur
animate the graph to see change over time (graphtool)
    - make sure to fix positions
    - transitions should be eased to see what' changing when
    - hold everything constant except for time
    - allow interactive control

## Visual elements of graphs (lane harrison)
how to eliminate the hairball
- layout: vertex and edge positioning
- vertices: shape, color, size, pie nodes
- edges: direction, tapering, size, color
visual analytics mantra
- overview first: sub analysis
- zoom and filter: centrality
- details on demand: visual elements, illiciting the properties








