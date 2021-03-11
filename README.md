# aem-rrd-visualizer
Visualize the AEM "metrics.rrd"-file using Graphite and Grafana (and convert the "metrics.rrd" to the real rrd-format).

## Abstract
Starting with AEM 6.4 there will be a metrics reporter enabled that periodically collects metrics and stores them in a time-series data base using RRD4J. The primary purpose of this reporter is to collect metrics data for diagnostics, e.g. to analyze why performance was bad as reported by a customer. The data base contains metrics data with four different granularity levels and with different retention time:

* Per minute averages are kept for the last six hours
* Per five minute averages are kept for the last two days
* Per hour averages are kept for one month
* Per day averages are kept for one year

These are similar to Jackrabbit TimeSeries data already available in AEM with the difference that metrics are stored to the local filesystem and survive restarts.

This tool used DOCKER to build an environment which can:

* convert the RRD4J format to the normal RRD format 
* install Graphite to read the RRD-output
* install Grafana to display a dashboads with charts, reading the information from Graphana and outputs it using the browser on " http://localhost " (port: 80).

## Required Applications
* [Docker for OSx (native)](https://docs.docker.com/engine/installation/mac/)
* [Docker for Windows (uses HyperV - VMware and VirtualBox will not work anymore)](https://docs.docker.com/engine/installation/windows/)

## Build AEM Images
Execute within the _repository-root_ folder:
```
docker-compose build
```
## Start environment
Execute within the project root folder
```
docker-compose up 
```
or for e.g. only the RRD converter "openjdk-rdd-converter"
```
docker-compose up  openjdk-rdd-converter
```

## Screenshots

![localhost AEM Dashboard](/resources/AEM_Metrics-Dashbaord.png)