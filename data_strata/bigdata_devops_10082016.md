# Big Data DevOps for Data Science
@author: Marck Vaisman

## What is DevOps?
agilerelationship between development and IT operations
change and improve relationship with better communications and collaboration
allows data practitioners to set up their environments to do what they need to do; get the right tools to do the right job

## What is the ideal Big Data environment?
- Hadoop, YARN, Spark, Hive, Sqoop
- Anaconda Python, Python IDEs, Jupyter
- Sublime Text and packages
- R and RStudio
- Pyspark, sparkR
- Git, GitHub
- Codecs(zip,gzip, lzop)
- Curl, wget
- Access to data on HDFS

## Use Cases
- small teams with limited engineering support
- transient infrasctructure
- sharing environment with multiple users
- for R&D, exploratory analysis, learning the tools
- NOT for production system, use commercial products for this

## Ways to set up
- cloud, managed cluster
- DRY: Don't Repeat Yourself
- use shellscript, bootstrap actions
- **Use Ansible**

## What is Ansible
- similar to Chef, Puppet
- written in python
- use and configure remote systems
- only need SSH, agentless
- human readable, uses YAML
- connects to your machine, issues commands using python
- modules: identity mgmt, clustering, database

## What do you need it to do
- hosts file, logins into machine, installs the items you neeed
- setups up tables
- setting up ports and env vars
- put path on every node
- HDFS permissions for sharing
- set up Git for version control





