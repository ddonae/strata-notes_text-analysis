Twitter Real Time Stack
Event Processing with Distributed Log and Heron
@ Karthik Ramasamy, @karthikz

maturity scale --> levels of time and data processing
- real-time, seconds / near real time, minutes
- batch = hours days months 

batch = ad-hoc queries
near real time = impressions, hashtag trends
OLTP = deterministic workflows, fanout tweets, search for tweets
real time = financial trading

twitter is all about real time
- trends = hashtags
- conversations = sports, moments
- recommendations = product recs, promoted feeds
- search = tweet indexing

academies of real time
streaming: data in motion
interactive: data at rest, store & query

use cases
online services = transactional log, queues
near real time = change propagation, streaming
batch analytics = log aggregation, client events

**real time stack**
scribe: point of data collection, at origin
- open source log aggregation
- throughput and scale tight SLAs
- runs on every machine
event bus: web services
- publisher / subscriber system
- publisher partitions log stream of metadata
- metadata governs partition of data to event stream, caches and pushes to dlog
- subscriber consumes data via push / listening for new data
dlog: building block for systems
- distributed log for event streams
- write proxy - protocol guarantees durability
- read proxy - informed that record is committed and ready to consume
- manhattan key value store
- durable deferred RPC
- real time search indexing
- pub sub system
- globally replicated log
heron: streaming engine (similar to storm)
- container based architecture
- separate monitoring and scheduling (uses YARN, Mesos, etc)
- simplified execution model: process based (instead of thread based)
- better performance
- API compatible with Storm
- task isolation for debugging and profiling
- mainstream languages like C++, Java, and Python
- support for back pressure for self adjusting topologies
- batching of tuples
- efficient resource consumption

old stack of twitter messaging - kestrel, book keeper, my SQL, scribe > kafka > hdfs
- kestrel (home-grown) challenges: durability is hard, expensive to subscribe, degrades performance, scales poorly, cross DC replication, file system cache

rethinking messaging - ideal world
- unified stack
- multi tenancy
- durable write, intra cluster, geo-replication
- scales resources independently
- easy to manage

heron topology: spouts and bolts
stream groupings: shuffle, fields, all grouping, global grouping

heron architecture
- submit job to scheduler
- container 0 as topology master
- scales data containers for running jobs
- stream manager: routes data across containers
    - spout backpressure
    - above threshold, clamps spouts
    - data drains from buffers, then spout reopens
- metrics manager: 
- zookeeper cluster: blueprint for data, physical plan for processing

heron performance settings
- spout parallelism vs tuples/min and # cores used
- throughput increased by 5x from heron paper to master
- CPU usage increased

lambda architecture
- combining batch (hadoop) and real time (storm)
- scribe collection pipeline > event bus > heron analytics pipeline > results
- allows separate pipelines for collecting data real-time and processing / analyzing data via batch
- summingbird: aggregates between cache and key values

resources
- check out published papers
- heronstreaming.io
- github.com/twitter/heron





