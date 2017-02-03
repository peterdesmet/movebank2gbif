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
SCD: Options I see here could be to use (1) the publisher (static: `University of Konstanz`) or (2) the first author, as found as the first creatorName in the in the DataCite metadata, or else (3) skip this one. The "A person or organization owning or managing rights over the resource", if we read it to be the current "owner" of the original data, to the degree relevant for data published in the public domain, is not explicitly recorded anywhere in the dataset. In some cases the first author would cease to be the "owner" if, say, they left the organization through which the data were collected.

#### [accessRights](http://rs.tdwg.org/dwc/terms/index.htm#accessRights)

SCD: Is this value too long? It is the "Terms of Use" included in the readme file of every published data file. I could shorten this to 1 phrase instead. **static value**:

    This data file is licensed by the Creative Commons Zero (CC0 1.0) license. The intent of this license is to facilitate the re-use of works. The Creative Commons Zero license is a "no rights reserved" license that allows copyright holders to opt out of copyright protections automatically extended by copyright and other laws, thus placing works in the public domain with as little legal restriction as possible. However, works published with this license must still be appropriately cited following professional and ethical standards for academic citation. We highly recommend that you contact the data creator if possible if you will be re-using or re-analyzing data in this file. Researchers will likely be interested in learning about new uses of their data, might also have important insights about how to properly analyze and interpret their data, and/or might have additional data they would be willing to contribute to your project. Feel free to contact us at support@movebank.org if you need assistance contacting data owners.

#### [bibliographicCitation](http://rs.tdwg.org/dwc/terms/index.htm#bibliographicCitation)

Possibly...SCD: Would be nice to include this if possible. The citation for the data package can be built from the DataCite metadata using the general format `metadata.creator/creatorName` (`metadata.publicationYear`) Data from: `metadata.title/titles` [but ignore/remove "Data from: "]. Movebank Data Repository. doi:`metadata.identifier`
It should be possible to find script to do this somewhere in our or Dryad's implementation of DataCite.

    Hernandez-Pliego J, Rodriguez C, Bustamante J (2015) Data from: Why do kestrels soar? Movebank Data Repository. doi:10.5441/001/1.sj8t3r11
    
#### [references](http://rs.tdwg.org/dwc/terms/index.htm#references)

SCD: We could (1) take the value from `metadata.description descriptionType="Other"` in the DataCite metadata (this is always the full citation for the primary paper associated with the dataset) or (2) take the value/s from `metadata.relatedIdentifier relatedIdentifierType="DOI" relationType="IsSupplementTo"` (these are the DOIs only for papers associated with the dataset—always 1 that corresponds with the full citation in (1) and can also include DOIs for additional papers that use the dataset. (1) is probably the best option.
    
    Hernandez-Pliego J, Rodriguez C, Bustamante J (2015) Why do kestrels soar? PLOS ONE. 10(12): e0145402. doi:10.1371/journal.pone.0145402

#### [institutionID](http://rs.tdwg.org/dwc/terms/index.htm#institutionID)

SCD: Suggest we skip. See notes about [rightsHolder].

#### [collectionID](http://rs.tdwg.org/dwc/terms/index.htm#collectionID)
n/a

#### [datasetID](http://rs.tdwg.org/dwc/terms/index.htm#datasetID)

Resolvable DOI of the dataset, will be the same for all records in a dataset. Can be created by concatening `"http://doi.org/"` with `metadata.doi`:

    http://doi.org/10.5441/001/1.sj8t3r11

#### [institutionCode](http://rs.tdwg.org/dwc/terms/index.htm#institutionCode)

Recommended...
SCD: Suggest we skip for now. See notes about [rightsHolder]. This term has the same definition as the same as ownerInstitutionCode?

#### [collectionCode](http://rs.tdwg.org/dwc/terms/index.htm#collectionCode)
n/a

#### [datasetName](http://rs.tdwg.org/dwc/terms/index.htm#datasetName)

Title of the dataset, will be the same for all records in a dataset. Can be retrieved from `metadata.title`:

    Data from: Olfaction and topography, but not magnetic cues, control navigation in a pelagic seabird: displacements with shearwaters in the Mediterranean Sea

#### [ownerInstitutionCode](http://rs.tdwg.org/dwc/terms/index.htm#ownerInstitutionCode)

Recommended...
SCD: Suggest we skip for now. See notes about [rightsHolder]. This term has the same definition as the same as InstitutionCode?

#### [basisOfRecord](http://rs.tdwg.org/dwc/terms/index.htm#basisOfRecord)

Each record is recorded by a tracker, so use the **static value**:
SCD: Note there are 1-2 exceptions, in which the locations were noted by a human observer. In these cases the `sensor-type` in the data file will be `natural-mark` and we could use HumanObservation.

    MachineObservation

#### [informationWithheld](http://rs.tdwg.org/dwc/terms/index.htm#informationWithheld)

Possibly...

#### [dataGeneralizations](http://rs.tdwg.org/dwc/terms/index.htm#dataGeneralizations)
n/a

#### [dynamicProperties](http://rs.tdwg.org/dwc/terms/index.htm#dynamicProperties)

Possibly...
SCD: ?? Might use this to concatenate values from miscellaneous data and reference data attributes from the files?

### Occurrence

#### [occurrenceID](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceID)

Recommended...
SCD: I think this is better put under Event > eventID? Or can it go both places? The event-id is a unique ID for each dataset-record and can be retrieved from the data file `event-id` (this variable is always included). Note that when the same record is published in multiple datasets, the event-id will not be the same, so if this is a problem we can skip this one.

    275195086

#### [catalogNumber](http://rs.tdwg.org/dwc/terms/index.htm#catalogNumber)

n/a
SCD: Could use this instead of occurrenceID as described above.

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
Stored in the reference data file as `animal-life-stage` (optional, often used), linked to records in the data file by the same `animal-id`= `individual-local-identifier` + `tag-id` = `tag-local-identifier`. The value represents the age at the beginning of the deployment, so if there are multiple deployments there could be multiple life stage values for the same animal in the dataset.

    adult (> 1 year)

#### [reproductiveCondition](http://rs.tdwg.org/dwc/terms/index.htm#reproductiveCondition)

Stored in the reference data file as `animal-reproductive-condition` (optional, sometimes used), linked to records in the data file by the same `animal-id`= `individual-local-identifier` + `tag-id` = `tag-local-identifier`. The value represents the condition at the beginning of the deployment, so if there are multiple deployments there could be multiple reproductive condition values for the same animal in the dataset.

    breeding

#### [behavior](http://rs.tdwg.org/dwc/terms/index.htm#behavior)

SCD: Behavior information can be stored in several non-required data file attributes, but few datasets include them, including the example. Attributes that could be stored here include `behavioural-classfication`, `migration-stage`, `migration-stage-standard`, possible others very rarely used.

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

SCD: Is this covered by [references]?

#### [associatedSequences](http://rs.tdwg.org/dwc/terms/index.htm#associatedSequences)
n/a

#### [associatedTaxa](http://rs.tdwg.org/dwc/terms/index.htm#associatedTaxa)

Stored in the data file as `individual-taxon-canonical-name` (this variable is always included).

    Falco naumanni
    
#### [otherCatalogNumbers](http://rs.tdwg.org/dwc/terms/index.htm#otherCatalogNumbers)
n/a

#### [occurrenceRemarks](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceRemarks)

SCD: n/a? See eventRemarks.

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

Stored in the reference data file as `animal-comments` (optional, sometimes used), linked to records in the data file by the same `animal-id`= `individual-local-identifier` + `tag-id` = `tag-local-identifier`. Not included in the example dataset.

### MaterialSample
n/a
### Event

#### [eventID](http://rs.tdwg.org/dwc/terms/index.htm#eventID)

The event-id is a unique ID for each dataset-record and can be retrieved from the data file `event-id` (this variable is always included). Note that when the same record is published in multiple datasets, the event-id will not be the same, so if this is a problem we can skip this one.

    275195086
    
#### [parentEventID](http://rs.tdwg.org/dwc/terms/index.htm#parentEventID)
n/a?
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

SCD: Could use this instead of eventDate to avoid needing to convert?

#### [habitat](http://rs.tdwg.org/dwc/terms/index.htm#habitat)

Stored in the data file as `habitat` (optional, rarely used). Not used in the example dataset.
    
#### [samplingProtocol](http://rs.tdwg.org/dwc/terms/index.htm#samplingProtocol)

Recommended...
SCD: Could store the sensor type (i.e. tracking method) here, stored in the data file as `sensor-type` (this variable is always included).

    gps

#### [samplingEffort](http://rs.tdwg.org/dwc/terms/index.htm#samplingEffort)
n/a
#### [sampleSizeValue](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeValue)
n/a
#### [sampleSizeUnit](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeUnit)
n/a
#### [fieldNotes](http://rs.tdwg.org/dwc/terms/index.htm#fieldNotes)
n/a
#### [eventRemarks](http://rs.tdwg.org/dwc/terms/index.htm#eventRemarks)

SCD: Better here than occurrenceRemarks? Stored in the data file as `comments` (optional, sometimes used). Not included in most datasets including the example.

### Location

#### [locationID](http://rs.tdwg.org/dwc/terms/index.htm#locationID)
#### [higherGeographyID](http://rs.tdwg.org/dwc/terms/index.htm#higherGeographyID)
#### [higherGeography](http://rs.tdwg.org/dwc/terms/index.htm#higherGeography)
#### [continent](http://rs.tdwg.org/dwc/terms/index.htm#continent)
#### [waterBody](http://rs.tdwg.org/dwc/terms/index.htm#waterBody)
#### [islandGroup](http://rs.tdwg.org/dwc/terms/index.htm#islandGroup)
#### [island](http://rs.tdwg.org/dwc/terms/index.htm#island)
#### [country](http://rs.tdwg.org/dwc/terms/index.htm#country)
#### [countryCode](http://rs.tdwg.org/dwc/terms/index.htm#countryCode)
#### [stateProvince](http://rs.tdwg.org/dwc/terms/index.htm#stateProvince)
#### [county](http://rs.tdwg.org/dwc/terms/index.htm#county)
#### [municipality](http://rs.tdwg.org/dwc/terms/index.htm#municipality)
#### [locality](http://rs.tdwg.org/dwc/terms/index.htm#locality)
#### [verbatimLocality](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLocality)
#### [minimumElevationInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumElevationInMeters)

Recommended...

#### [maximumElevationInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumElevationInMeters)
#### [verbatimElevation](http://rs.tdwg.org/dwc/terms/index.htm#verbatimElevation)
#### [minimumDepthInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumDepthInMeters)
#### [maximumDepthInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumDepthInMeters)
#### [verbatimDepth](http://rs.tdwg.org/dwc/terms/index.htm#verbatimDepth)
#### [minimumDistanceAboveSurfaceInMeters](http://rs.tdwg.org/dwc/terms/index.htm#minimumDistanceAboveSurfaceInMeters)

Recommended...

#### [maximumDistanceAboveSurfaceInMeters](http://rs.tdwg.org/dwc/terms/index.htm#maximumDistanceAboveSurfaceInMeters)
#### [locationAccordingTo](http://rs.tdwg.org/dwc/terms/index.htm#locationAccordingTo)
#### [locationRemarks](http://rs.tdwg.org/dwc/terms/index.htm#locationRemarks)
#### [decimalLatitude](http://rs.tdwg.org/dwc/terms/index.htm#decimalLatitude)

Recommended...

#### [decimalLongitude](http://rs.tdwg.org/dwc/terms/index.htm#decimalLongitude)

Recommended...

#### [geodeticDatum](http://rs.tdwg.org/dwc/terms/index.htm#geodeticDatum)

Recommended...

#### [coordinateUncertaintyInMeters](http://rs.tdwg.org/dwc/terms/index.htm#coordinateUncertaintyInMeters)

Recommended...

#### [coordinatePrecision](http://rs.tdwg.org/dwc/terms/index.htm#coordinatePrecision)
#### [pointRadiusSpatialFit](http://rs.tdwg.org/dwc/terms/index.htm#pointRadiusSpatialFit)
#### [verbatimCoordinates](http://rs.tdwg.org/dwc/terms/index.htm#verbatimCoordinates)
#### [verbatimLatitude](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLatitude)
#### [verbatimLongitude](http://rs.tdwg.org/dwc/terms/index.htm#verbatimLongitude)
#### [verbatimCoordinateSystem](http://rs.tdwg.org/dwc/terms/index.htm#verbatimCoordinateSystem)
#### [verbatimSRS](http://rs.tdwg.org/dwc/terms/index.htm#verbatimSRS)
#### [footprintWKT](http://rs.tdwg.org/dwc/terms/index.htm#footprintWKT)
#### [footprintSRS](http://rs.tdwg.org/dwc/terms/index.htm#footprintSRS)
#### [footprintSpatialFit](http://rs.tdwg.org/dwc/terms/index.htm#footprintSpatialFit)
#### [georeferencedBy](http://rs.tdwg.org/dwc/terms/index.htm#georeferencedBy)
#### [georeferencedDate](http://rs.tdwg.org/dwc/terms/index.htm#georeferencedDate)

Possibly...

#### [georeferenceProtocol](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceProtocol)

Possibly...

#### [georeferenceSources](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceSources)

Possibly...

#### [georeferenceVerificationStatus](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceVerificationStatus)

Possibly...

#### [georeferenceRemarks](http://rs.tdwg.org/dwc/terms/index.htm#georeferenceRemarks)

### GeologicalContext

n/a

### Taxon

#### [taxonID](http://rs.tdwg.org/dwc/terms/index.htm#taxonID)
#### [scientificNameID](http://rs.tdwg.org/dwc/terms/index.htm#scientificNameID)
#### [acceptedNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#acceptedNameUsageID)
#### [parentNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#parentNameUsageID)
#### [originalNameUsageID](http://rs.tdwg.org/dwc/terms/index.htm#originalNameUsageID)
#### [nameAccordingToID](http://rs.tdwg.org/dwc/terms/index.htm#nameAccordingToID)
#### [namePublishedInID](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedInID)
#### [taxonConceptID](http://rs.tdwg.org/dwc/terms/index.htm#taxonConceptID)
#### [scientificName](http://rs.tdwg.org/dwc/terms/index.htm#scientificName)

Recommended...

#### [acceptedNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#acceptedNameUsage)
#### [parentNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#parentNameUsage)
#### [originalNameUsage](http://rs.tdwg.org/dwc/terms/index.htm#originalNameUsage)
#### [nameAccordingTo](http://rs.tdwg.org/dwc/terms/index.htm#nameAccordingTo)
#### [namePublishedIn](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedIn)
#### [namePublishedInYear](http://rs.tdwg.org/dwc/terms/index.htm#namePublishedInYear)
#### [higherClassification](http://rs.tdwg.org/dwc/terms/index.htm#higherClassification)
#### [kingdom](http://rs.tdwg.org/dwc/terms/index.htm#kingdom)

Recommended...

#### [phylum](http://rs.tdwg.org/dwc/terms/index.htm#phylum)

Possibly...

#### [class](http://rs.tdwg.org/dwc/terms/index.htm#class)

Possibly...

#### [order](http://rs.tdwg.org/dwc/terms/index.htm#order)

Possibly...

#### [family](http://rs.tdwg.org/dwc/terms/index.htm#family)

Possibly...

#### [genus](http://rs.tdwg.org/dwc/terms/index.htm#genus)

Possibly...

#### [subgenus](http://rs.tdwg.org/dwc/terms/index.htm#subgenus)

Possibly...

#### [specificEpithet](http://rs.tdwg.org/dwc/terms/index.htm#specificEpithet)
#### [infraspecificEpithet](http://rs.tdwg.org/dwc/terms/index.htm#infraspecificEpithet)
#### [taxonRank](http://rs.tdwg.org/dwc/terms/index.htm#taxonRank)

Possibly...

#### [verbatimTaxonRank](http://rs.tdwg.org/dwc/terms/index.htm#verbatimTaxonRank)
#### [scientificNameAuthorship](http://rs.tdwg.org/dwc/terms/index.htm#scientificNameAuthorship)

Possibly...

#### [vernacularName](http://rs.tdwg.org/dwc/terms/index.htm#vernacularName)

Possibly...

#### [nomenclaturalCode](http://rs.tdwg.org/dwc/terms/index.htm#nomenclaturalCode)

Possibly...

#### [taxonomicStatus](http://rs.tdwg.org/dwc/terms/index.htm#taxonomicStatus)
#### [nomenclaturalStatus](http://rs.tdwg.org/dwc/terms/index.htm#nomenclaturalStatus)
#### [taxonRemarks](http://rs.tdwg.org/dwc/terms/index.htm#taxonRemarks)
