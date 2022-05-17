# Movebank2GBIF

A proof of concept to make public Movebank data available on GBIF.

## Note

This repository is now archived. Many of the ideas decribed in this repository and issues were implemented as part of the NLBIF-funded project [**MOVE2GBIF**](https://www.inbo.be/inbo/en-GB/projects/move2gbif-mobilizing-animal-gps-tracking-data-to-movebank-and-gbif-evinbo) in 2021-2022. The aim of that project was not to publish _all_ available Movebank datasets to GBIF, but rather to provide **guidelines and tools** to do so (see R package [movepub](https://github.com/inbo/movepub)) and to test this on a number of [INBO and Sovon datasets](https://github.com/inbo/bird-tracking).

## Rationale

The animal tracking research community uses [Movebank](https://www.movebank.org/) as the central hub and repository for their data. Tracking data supporting a study can be deposited in the [Movebank data repository](https://www.movebank.org/node/15294): these data are public (under a CC0 license), formatted using a common data model, documented with metadata, and referencable via a DOI (via DataCite). In this repository, we want to create a proof of concept in which these data and metadata are reformatted as Darwin Core Archives and registered with GBIF, making these datasets available through the GBIF [website](http://www.gbif.org) and [services](http://www.gbif.org/developer/summary).

## Contributors

* [Peter Desmet](https://github.com/peterdesmet)
* [Sarah Davidson](https://github.com/sarahcd)
