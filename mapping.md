# Mapping between Darwin Core and Movebank data model

For Darwin Core term definitions, see http://rs.tdwg.org/dwc/terms/index.htm

## Occurrence

### Record-level terms

#### [type](http://rs.tdwg.org/dwc/terms/index.htm#type)

Each record is an event, so use the **static value**:

    Event

#### [modified](http://rs.tdwg.org/dwc/terms/index.htm#modified)

Possibly...
SCD: Here would we use the publication date for the dataset?

#### [language](http://rs.tdwg.org/dwc/terms/index.htm#language)

We assume all data to be in English, so use the **static value**:

    en

#### [license](http://rs.tdwg.org/dwc/terms/index.htm#license)

All data in the Movebank Data Repository are published under CC0. That information could be retrieved from `metadata.rightsURI`, but it's easier to use the **static value** (with the exact same content):

    http://creativecommons.org/publicdomain/zero/1.0/

#### [rightsHolder](http://rs.tdwg.org/dwc/terms/index.htm#rightsHolder)

Recommended...
SCD: The definition is "A person or organization owning or managing rights over the resource". If we consider that these are public domain data and think of the analogy of a museum that has specimens originally collected by different groups or individuals, and the museum is the RightsHolder, then here we should use the use the **static value** `University of Konstanz`. If it should rather represent who/what should be cited for the use of the data, the other option would be to concatenate author names as stored in `creator`. Or we could skip. We don't collect information about the institutional "owner" for datasets (often there would be multiple affiliations that might or might not change with authors change jobs, so it would get complicated).

#### [accessRights](http://rs.tdwg.org/dwc/terms/index.htm#accessRights)

SCD: Use **static value**, either the "Terms of Use" included in the readme file of every published data file (first example below) or the second, shorter, example.

    This data file is licensed by the Creative Commons Zero (CC0 1.0) license. The intent of this license is to facilitate the re-use of works. The Creative Commons Zero license is a "no rights reserved" license that allows copyright holders to opt out of copyright protections automatically extended by copyright and other laws, thus placing works in the public domain with as little legal restriction as possible. However, works published with this license must still be appropriately cited following professional and ethical standards for academic citation. We highly recommend that you contact the data creator if possible if you will be re-using or re-analyzing data in this file. Researchers will likely be interested in learning about new uses of their data, might also have important insights about how to properly analyze and interpret their data, and/or might have additional data they would be willing to contribute to your project. Feel free to contact us at support@movebank.org if you need assistance contacting data owners.
    
    CC0 1.0 license. Cite use and contact data creator as possible for input if data will be reanalyzed.

#### [bibliographicCitation](http://rs.tdwg.org/dwc/terms/index.htm#bibliographicCitation)

Possibly...
SCD: Would be nice to include this if possible. The citation for the data package can be built from the DataCite metadata using the general format `metadata.creator/creatorName`[, repeat as needed for multiple creators] (`metadata.publicationYear`) `metadata.title`. Movebank Data Repository. doi:`metadata.identifier`

    Hernandez-Pliego J, Rodriguez C, Bustamante J (2015) Data from: Why do kestrels soar? Movebank Data Repository. doi:10.5441/001/1.sj8t3r11
    
#### [references](http://rs.tdwg.org/dwc/terms/index.htm#references)

Use the value from `metadata.description descriptionType="Other"` in the DataCite metadata (this is always the full citation for the primary paper associated with the dataset).
    
    Hernandez-Pliego J, Rodriguez C, Bustamante J (2015) Why do kestrels soar? PLOS ONE. 10(12): e0145402. doi:10.1371/journal.pone.0145402

#### [institutionID](http://rs.tdwg.org/dwc/terms/index.htm#institutionID)

SCD: Suggest we skip. See notes under [rightsHolder]. We don't collect information about the institutional "owner" for datasets, so the only option would be to use the **static value** `University of Konstanz`.

#### [collectionID](http://rs.tdwg.org/dwc/terms/index.htm#collectionID)
n/a

#### [datasetID](http://rs.tdwg.org/dwc/terms/index.htm#datasetID)

Resolvable DOI of the dataset, will be the same for all records in a dataset. Can be created by concatening `"http://doi.org/"` with `metadata.doi`:

    http://doi.org/10.5441/001/1.sj8t3r11

#### [institutionCode](http://rs.tdwg.org/dwc/terms/index.htm#institutionCode)

Recommended...
SCD: Suggest we skip or use the **static value** `University of Konstanz`. See notes under [rightsHolder].

#### [collectionCode](http://rs.tdwg.org/dwc/terms/index.htm#collectionCode)
n/a

#### [datasetName](http://rs.tdwg.org/dwc/terms/index.htm#datasetName)

Title of the dataset, will be the same for all records in a dataset. Can be retrieved from `metadata.title`:

    Data from: Olfaction and topography, but not magnetic cues, control navigation in a pelagic seabird: displacements with shearwaters in the Mediterranean Sea

#### [ownerInstitutionCode](http://rs.tdwg.org/dwc/terms/index.htm#ownerInstitutionCode)

Recommended...
SCD: Suggest we skip or use the **static value** `University of Konstanz`. See notes about [rightsHolder].

#### [basisOfRecord](http://rs.tdwg.org/dwc/terms/index.htm#basisOfRecord)

Each record is recorded by a tracker, so use the **static value**:
SCD: Note there are 1-2 exceptions, in which the locations were noted by a human observer. In these cases the `sensor-type` in the data file will be `natural-mark` and we could use HumanObservation.

    MachineObservation

#### [informationWithheld](http://rs.tdwg.org/dwc/terms/index.htm#informationWithheld)

Possibly...
Assuming we will not map every variable from published datasets to DC, here we can refer to the DOI of the dataset, will be the same for all records in a dataset. Concatene `"see doi"` with `metadata.doi`:

    see doi 10.5441/001/1.sj8t3r11

#### [dataGeneralizations](http://rs.tdwg.org/dwc/terms/index.htm#dataGeneralizations)
n/a

#### [dynamicProperties](http://rs.tdwg.org/dwc/terms/index.htm#dynamicProperties)

Possibly...
SCD: ?? Might use this to concatenate values from miscellaneous data and reference data attributes from the files?

### Occurrence

#### [occurrenceID](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceID)

Recommended...
SCD: I think this is better put under [eventID], or can/should it go both places? The event-id is a unique ID for each dataset-record and can be retrieved from the data file `event-id` (this variable is always included). Note that when the same record is published in multiple datasets, the event-id will not be the same. Alternative might be to have this automatically created as a sequential unique number.

    275195086

#### [catalogNumber](http://rs.tdwg.org/dwc/terms/index.htm#catalogNumber)
n/a
#### [recordNumber](http://rs.tdwg.org/dwc/terms/index.htm#recordNumber)
n/a
#### [recordedBy](http://rs.tdwg.org/dwc/terms/index.htm#recordedBy)
n/a

#### [individualCount](http://rs.tdwg.org/dwc/terms/index.htm#individualCount)

Records always represent 1 animal so use the **static value**

    1
    
#### [organismQuantity](http://rs.tdwg.org/dwc/terms/index.htm#organismQuantity)
n/a
#### [organismQuantityType](http://rs.tdwg.org/dwc/terms/index.htm#organismQuantityType)
n/a

#### [sex](http://rs.tdwg.org/dwc/terms/index.htm#sex)

Recommended...
Stored in the reference data file as `animal-sex` (optional, often used), linked to records in the data file by matching the reference data `animal-id` with the data file `individual-local-identifier`. Always m, f, or blank.

    f
    
#### [lifeStage](http://rs.tdwg.org/dwc/terms/index.htm#lifeStage)

Recommended...
Stored in the reference data file as `animal-life-stage` (optional, often used), linked to records in the data file by the same `animal-id`= `individual-local-identifier` and the same `tag-id` = `tag-local-identifier`. The value represents the age at the beginning of the deployment, so if there are multiple deployments there could be multiple life stage values for the same animal in the dataset.

    adult (> 1 year)

#### [reproductiveCondition](http://rs.tdwg.org/dwc/terms/index.htm#reproductiveCondition)

Stored in the reference data file as `animal-reproductive-condition` (optional, sometimes used), linked to records in the data file by the same `animal-id`= `individual-local-identifier` and the same `tag-id` = `tag-local-identifier`. The value represents the condition at the beginning of the deployment, so if there are multiple deployments there could be multiple reproductive condition values for the same animal in the dataset.

    breeding

#### [behavior](http://rs.tdwg.org/dwc/terms/index.htm#behavior)

SCD: Behavior information can be stored in several non-required data file attributes, but few datasets include them, including the example. Attributes that could be stored here include `behavioural-classification`, `migration-stage`, `migration-stage-standard`, possible others very rarely used.

#### [establishmentMeans](http://rs.tdwg.org/dwc/terms/index.htm#establishmentMeans)
n/a

#### [occurrenceStatus](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceStatus)

We don't record absent values so use the **static value**
    
    present
    
#### [preparations](http://rs.tdwg.org/dwc/terms/index.htm#preparations)
n/a
#### [disposition](http://rs.tdwg.org/dwc/terms/index.htm#disposition)
n/a
#### [associatedMedia](http://rs.tdwg.org/dwc/terms/index.htm#associatedMedia)
n/a

#### [associatedReferences](http://rs.tdwg.org/dwc/terms/index.htm#associatedReferences)

Here we could concatenate the DOIs stored in the metadata as `relatedIdentifier relatedIdentifierType="DOI" relationType="IsSupplementTo"` and `relatedIdentifier relatedIdentifierType="DOI" relationType="IsDocumentedBy"`, separated by ` | `. `IsSupplementTo` is the DOI for the reference included in [references] and `IsDocumentedBy` (sometimes used) is the DOI/s for additional papers published using the same dataset.

    10.1371/journal.pone.0145402

#### [associatedSequences](http://rs.tdwg.org/dwc/terms/index.htm#associatedSequences)
n/a

#### [associatedTaxa](http://rs.tdwg.org/dwc/terms/index.htm#associatedTaxa)

SCD: Stored in the data file as `individual-taxon-canonical-name` (this variable is always included). Store as [scientificName] instead?

    Falco naumanni
    
#### [otherCatalogNumbers](http://rs.tdwg.org/dwc/terms/index.htm#otherCatalogNumbers)
n/a
#### [occurrenceRemarks](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceRemarks)
n/a

### Organism

#### [organismID](http://rs.tdwg.org/dwc/terms/index.htm#organismID)
Recommended...
n/a

#### [organismName](http://rs.tdwg.org/dwc/terms/index.htm#organismName)

Recommended...
Stored in the data file as `individual-local-identifier` (this variable is always included).

    B[5.H]

#### [organismScope](http://rs.tdwg.org/dwc/terms/index.htm#organismScope)
n/a
#### [associatedOccurrences](http://rs.tdwg.org/dwc/terms/index.htm#associatedOccurrences)
n/a
#### [associatedOrganisms](http://rs.tdwg.org/dwc/terms/index.htm#associatedOrganisms)
n/a
#### [previousIdentifications](http://rs.tdwg.org/dwc/terms/index.htm#previousIdentifications)
n/a

#### [organismRemarks](http://rs.tdwg.org/dwc/terms/index.htm#organismRemarks)

Stored in the reference data file as `animal-comments` (optional, sometimes used), linked to records in the data file by the same `animal-id`= `individual-local-identifier`. Not included in the example dataset.

### MaterialSample
n/a

### Event

#### [eventID](http://rs.tdwg.org/dwc/terms/index.htm#eventID)

The event-id is a unique ID for each dataset-record and can be retrieved from the data file `event-id` (this variable is always included). Note that when the same record is published in multiple datasets, the event-id will not be the same. Also see [occurrenceID].

    275195086
    
#### [parentEventID](http://rs.tdwg.org/dwc/terms/index.htm#parentEventID)
n/a
#### [fieldNumber](http://rs.tdwg.org/dwc/terms/index.htm#fieldNumber)
n/a
#### [eventDate](http://rs.tdwg.org/dwc/terms/index.htm#eventDate)

Recommended...
SCD: Stored in the data file as `timestamp` (this variable is always included), always in format yyyy-MM-dd HH:mm:ss.SSS (UTC). Do we need to convert these values to make the time zone unambiguous or use a standard encoding scheme?
    
    2012-06-06 14:20:07.000

#### [eventTime](http://rs.tdwg.org/dwc/terms/index.htm#eventTime)
n/a
#### [startDayOfYear](http://rs.tdwg.org/dwc/terms/index.htm#startDayOfYear)
n/a
#### [endDayOfYear](http://rs.tdwg.org/dwc/terms/index.htm#endDayOfYear)
n/a
#### [year](http://rs.tdwg.org/dwc/terms/index.htm#year)
n/a
#### [month](http://rs.tdwg.org/dwc/terms/index.htm#month)
n/a
#### [day](http://rs.tdwg.org/dwc/terms/index.htm#day)
n/a
#### [verbatimEventDate](http://rs.tdwg.org/dwc/terms/index.htm#verbatimEventDate)

SCD: Could use this instead of eventDate to avoid needing to convert? Stored in the data file as `timestamp` (this variable is always included), always in format yyyy-MM-dd HH:mm:ss.SSS (UTC).
    
    2012-06-06 14:20:07.000

#### [habitat](http://rs.tdwg.org/dwc/terms/index.htm#habitat)

Stored in the data file as `habitat` (optional, rarely used). Not used in the example dataset.
    
#### [samplingProtocol](http://rs.tdwg.org/dwc/terms/index.htm#samplingProtocol)

Recommended...
SCD: Also see [locationAccordingTo]. Can store the sensor type (i.e. tracking method) here, stored in the data file as `sensor-type` (this variable is always included). Here or elsewhere we should at mimimum record the `tag-manufacturer-name` and possibly other methods information stored in the reference data file. A complete example could concatenate `sensor-type` + `": "` + `tag-manufacturer-name` + `" "` + `tag-model` + `"; tag readout method: "` `tag-readout-method`. The latter four reference data attributes can be linked to records in the data file by the same `animal-id`= `individual-local-identifier` and the same `tag-id` = `tag-local-identifier`. If there are multiple deployments there could tag information for the same animal in the dataset.

    gps: Technosmart GiPSy-2; tag readout method: tag-retrieval

#### [samplingEffort](http://rs.tdwg.org/dwc/terms/index.htm#samplingEffort)
n/a
#### [sampleSizeValue](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeValue)
n/a
#### [sampleSizeUnit](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeUnit)
n/a
#### [fieldNotes](http://rs.tdwg.org/dwc/terms/index.htm#fieldNotes)
n/a
#### [eventRemarks](http://rs.tdwg.org/dwc/terms/index.htm#eventRemarks)

Stored in the data file as `comments` (optional, sometimes used). Not included in most datasets including the example. In some cases the readme file must be consulted for explanation.

### Location

#### [locationID](http://rs.tdwg.org/dwc/terms/index.htm#locationID)
n/a
#### [higherGeographyID](http://rs.tdwg.org/dwc/terms/index.htm#higherGeographyID)
n/a
#### [higherGeography](http://rs.tdwg.org/dwc/terms/index.htm#higherGeography)
n/a
#### [continent](http://rs.tdwg.org/dwc/terms/index.htm#continent)
n/a
#### [waterBody](http://rs.tdwg.org/dwc/terms/index.htm#waterBody)
n/a
#### [islandGroup](http://rs.tdwg.org/dwc/terms/index.htm#islandGroup)
n/a
#### [island](http://rs.tdwg.org/dwc/terms/index.htm#island)
n/a
#### [country](http://rs.tdwg.org/dwc/terms/index.htm#country)
n/a
#### [countryCode](http://rs.tdwg.org/dwc/terms/index.htm#countryCode)
n/a
#### [stateProvince](http://rs.tdwg.org/dwc/terms/index.htm#stateProvince)
n/a
#### [county](http://rs.tdwg.org/dwc/terms/index.htm#county)
n/a
#### [municipality](http://rs.tdwg.org/dwc/terms/index.htm#municipality)
n/a
#### [locality](http://rs.tdwg.org/dwc/terms/index.htm#locality)
n/a
#### [verbatimLocality](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLocality)
n/a
#### [minimumElevationInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumElevationInMeters)
Recommended...
n/a
#### [maximumElevationInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumElevationInMeters)
n/a
#### [verbatimElevation](http://rs.tdwg.org/dwc/terms/index.htm#verbatimElevation)

SCD: Stored in the data file as `height-above-ellipsoid`, `height-above-msl`, or `height-raw` (optional, sometimes used, the first two are always in m, units are undefined for height-raw). Not used in the example dataset. Could also use the ElevationInMeters or DistanceAboveSurface terms, but this might be more straightforward.

#### [minimumDepthInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumDepthInMeters)
n/a
#### [maximumDepthInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumDepthInMeters)
n/a
#### [verbatimDepth](http://rs.tdwg.org/dwc/terms/index.htm#verbatimDepth)
n/a
#### [minimumDistanceAboveSurfaceInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumDistanceAboveSurfaceInMeters)
Recommended...
n/a
#### [maximumDistanceAboveSurfaceInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumDistanceAboveSurfaceInMeters)
n/a

#### [locationAccordingTo](http://rs.tdwg.org/dwc/terms/index.htm#locationAccordingTo)

SCD: Could store the sensor type (i.e. tracking method) here, stored in the data file as `sensor-type` (this variable is always included). Also see [samplingProtocol].

    gps
    
#### [locationRemarks](http://rs.tdwg.org/dwc/terms/index.htm#locationRemarks)
n/a

#### [decimalLatitude](http://rs.tdwg.org/dwc/terms/index.htm#decimalLatitude)

Recommended...
SCD: Stored in the data file as `location-lat`. This is technically optional and sometimes blank for individual data records where a fix was not obtained, and absent for a few datasets in which only raw light level values measured by geolocators are archived.

    37.391942

#### [decimalLongitude](http://rs.tdwg.org/dwc/terms/index.htm#decimalLongitude)

Recommended...
SCD: Stored in the data file as `location-long`. This is technically optional and sometimes blank for individual data records where a fix was not obtained, and absent for a few datasets in which only raw light level values measured by geolocators are archived.

    -6.557898
    
#### [geodeticDatum](http://rs.tdwg.org/dwc/terms/index.htm#geodeticDatum)

Recommended...
All locations stored in WGS84 coordinate system, so use the **static value**:

    WGS84

#### [coordinateUncertaintyInMeters](http://rs.tdwg.org/dwc/terms/index.htm#coordinateUncertaintyInMeters)

Recommended...
Stored in the data file as `location-error-numerical` (optional, rarely used, in m). Not used in the example dataset.

#### [coordinatePrecision](http://rs.tdwg.org/dwc/terms/index.htm#coordinatePrecision)
n/a
#### [pointRadiusSpatialFit](http://rs.tdwg.org/dwc/terms/index.htm#pointRadiusSpatialFit)
n/a
#### [verbatimCoordinates](http://rs.tdwg.org/dwc/terms/index.htm#verbatimCoordinates)
n/a
#### [verbatimLatitude](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLatitude)
n/a
#### [verbatimLongitude](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLongitude)
n/a
#### [verbatimCoordinateSystem](http://rs.tdwg.org/dwc/terms/index.htm#verbatimCoordinateSystem)
n/a
#### [verbatimSRS](http://rs.tdwg.org/dwc/terms/index.htm#verbatimSRS)
n/a
#### [footprintWKT](http://rs.tdwg.org/dwc/terms/index.htm#footprintWKT)
n/a
#### [footprintSRS](http://rs.tdwg.org/dwc/terms/index.htm#footprintSRS)
n/a
#### [footprintSpatialFit](http://rs.tdwg.org/dwc/terms/index.htm#footprintSpatialFit)
n/a
#### [georeferencedBy](http://rs.tdwg.org/dwc/terms/index.htm#georeferencedBy)
n/a
#### [georeferencedDate](http://rs.tdwg.org/dwc/terms/index.htm#georeferencedDate)

Possibly...
SCD: See [eventDate]. Should the values be duplicated here?

#### [georeferenceProtocol](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceProtocol)
Possibly...
n/a

#### [georeferenceSources](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceSources)

Possibly...
SCD: n/a, see [locationAccordingTo] and [samplingProtocol]

#### [georeferenceVerificationStatus](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceVerificationStatus)
Possibly...
n/a
#### [georeferenceRemarks](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceRemarks)
n/a
### GeologicalContext
n/a

### Taxon

#### [taxonID](http://rs.tdwg.org/dwc/terms/index.htm#taxonID)
n/a
#### [scientificNameID](http://rs.tdwg.org/dwc/terms/index.htm#scientificNameID)
n/a
#### [acceptedNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#acceptedNameUsageID)
n/a
#### [parentNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#parentNameUsageID)
n/a
#### [originalNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#originalNameUsageID)
n/a
#### [nameAccordingToID](http://rs.tdwg.org/dwc/terms/index.htm#nameAccordingToID)
n/a
#### [namePublishedInID](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedInID)
n/a
#### [taxonConceptID](http://rs.tdwg.org/dwc/terms/index.htm#taxonConceptID)
n/a
#### [scientificName](http://rs.tdwg.org/dwc/terms/index.htm#scientificName)

Recommended...
SCD: Stored in the data file as `individual-taxon-canonical-name` (this variable is always included). Store here instead of in [associatedTaxa]?

    Falco naumanni

#### [acceptedNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#acceptedNameUsage)
n/a
#### [parentNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#parentNameUsage)
n/a
#### [originalNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#originalNameUsage)
n/a
#### [nameAccordingTo](http://rs.tdwg.org/dwc/terms/index.htm#nameAccordingTo)
n/a
#### [namePublishedIn](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedIn)
n/a
#### [namePublishedInYear](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedInYear)
n/a
#### [higherClassification](http://rs.tdwg.org/dwc/terms/index.htm#higherClassification)
n/a
#### [kingdom](http://rs.tdwg.org/dwc/terms/index.htm#kingdom)

Recommended...
It should be safe to use the **static value**

    Animalia

#### [phylum](http://rs.tdwg.org/dwc/terms/index.htm#phylum)

Possibly...
SCD: Unless you know a fancy way to pull in the ITIS taxonomy by API we should skip these others. We have a published study of genus Bombus (Phylum Arthropoda) so can't statically enter anything more than Animalia.

#### [class](http://rs.tdwg.org/dwc/terms/index.htm#class)
Possibly...
n/a
#### [order](http://rs.tdwg.org/dwc/terms/index.htm#order)
Possibly...
n/a
#### [family](http://rs.tdwg.org/dwc/terms/index.htm#family)
Possibly...
n/a
#### [genus](http://rs.tdwg.org/dwc/terms/index.htm#genus)
Possibly...
n/a
#### [subgenus](http://rs.tdwg.org/dwc/terms/index.htm#subgenus)
Possibly...
n/a
#### [specificEpithet](http://rs.tdwg.org/dwc/terms/index.htm#specificEpithet)
n/a
#### [infraspecificEpithet](http://rs.tdwg.org/dwc/terms/index.htm#infraspecificEpithet)
n/a
#### [taxonRank](http://rs.tdwg.org/dwc/terms/index.htm#taxonRank)
Possibly...
n/a
#### [verbatimTaxonRank](http://rs.tdwg.org/dwc/terms/index.htm#verbatimTaxonRank)
n/a
#### [scientificNameAuthorship](http://rs.tdwg.org/dwc/terms/index.htm#scientificNameAuthorship)
Possibly...
n/a
#### [vernacularName](http://rs.tdwg.org/dwc/terms/index.htm#vernacularName)
Possibly...
n/a

#### [nomenclaturalCode](http://rs.tdwg.org/dwc/terms/index.htm#nomenclaturalCode)

Possibly...
All taxonomic names are valid names as defined by the Integrated Taxonomic Information System (ITIS, www.itis.gov) as of the time of publication, so use the **static value**:

    ITIS

#### [taxonomicStatus](http://rs.tdwg.org/dwc/terms/index.htm#taxonomicStatus)
n/a
#### [nomenclaturalStatus](http://rs.tdwg.org/dwc/terms/index.htm#nomenclaturalStatus)
n/a
#### [taxonRemarks](http://rs.tdwg.org/dwc/terms/index.htm#taxonRemarks)

SCD: We allow owners to store taxonomic information not valid in ITIS in the reference data file as `animal-taxon-detail` (optional, sometimes used), linked to records in the data file by the same `animal-id`= `individual-local-identifier`. Could concatonate `taxonomic detail not valid in ITIS: ` + value in `animal-taxon-detail` when present. Not included in the example dataset.

### MeasurementOrFact

SCD: Possible we'll want to use terms from this class....
