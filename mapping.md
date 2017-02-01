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
SCD: Options I see here could be to use (1) the publisher (static: "University of Konstanz") or (2) the first author, as found as the first creatorName in the in the DataCite metadata, or else (3) skip this one. The "A person or organization owning or managing rights over the resource", if we read it to be the current "owner" of the original data, to the degree relevant for data published in the public domain, is not explicitly recorded anywhere in the dataset. In some cases the first author would cease to be the "owner" if, say, they left the organization through which the data were collected.

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
SCD: Suggest we skip.
#### [collectionID](http://rs.tdwg.org/dwc/terms/index.htm#collectionID)

n/a

#### [datasetID](http://rs.tdwg.org/dwc/terms/index.htm#datasetID)

Resolvable DOI of the dataset, will be the same for all records in a dataset. Can be created by concatening `"http://doi.org/"` with `metadata.doi`:

    http://doi.org/10.5441/001/1.sj8t3r11

#### [institutionCode](http://rs.tdwg.org/dwc/terms/index.htm#institutionCode)

Recommended...
SCD: Suggest we skip for now.

#### [collectionCode](http://rs.tdwg.org/dwc/terms/index.htm#collectionCode)

n/a

#### [datasetName](http://rs.tdwg.org/dwc/terms/index.htm#datasetName)

Title of the dataset, will be the same for all records in a dataset. Can be retrieved from `metadata.title`:

    Data from: Olfaction and topography, but not magnetic cues, control navigation in a pelagic seabird: displacements with shearwaters in the Mediterranean Sea

#### [ownerInstitutionCode](http://rs.tdwg.org/dwc/terms/index.htm#ownerInstitutionCode)

Recommended...

#### [basisOfRecord](http://rs.tdwg.org/dwc/terms/index.htm#basisOfRecord)

Each record is recorded by a tracker, so use the **static value**:

    MachineObservation

#### [informationWithheld](http://rs.tdwg.org/dwc/terms/index.htm#informationWithheld)

Possibly...

#### [dataGeneralizations](http://rs.tdwg.org/dwc/terms/index.htm#dataGeneralizations)
#### [dynamicProperties](http://rs.tdwg.org/dwc/terms/index.htm#dynamicProperties)

Possibly...

### Occurrence

#### [occurrenceID](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceID)

Recommended...

#### [catalogNumber](http://rs.tdwg.org/dwc/terms/index.htm#catalogNumber)

n/a

#### [recordNumber](http://rs.tdwg.org/dwc/terms/index.htm#recordNumber)
#### [recordedBy](http://rs.tdwg.org/dwc/terms/index.htm#recordedBy)
#### [individualCount](http://rs.tdwg.org/dwc/terms/index.htm#individualCount)
#### [organismQuantity](http://rs.tdwg.org/dwc/terms/index.htm#organismQuantity)
#### [organismQuantityType](http://rs.tdwg.org/dwc/terms/index.htm#organismQuantityType)
#### [sex](http://rs.tdwg.org/dwc/terms/index.htm#sex)

Recommended...

#### [lifeStage](http://rs.tdwg.org/dwc/terms/index.htm#lifeStage)

Recommended...

#### [reproductiveCondition](http://rs.tdwg.org/dwc/terms/index.htm#reproductiveCondition)
#### [behavior](http://rs.tdwg.org/dwc/terms/index.htm#behavior)
#### [establishmentMeans](http://rs.tdwg.org/dwc/terms/index.htm#establishmentMeans)
#### [occurrenceStatus](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceStatus)
#### [preparations](http://rs.tdwg.org/dwc/terms/index.htm#preparations)

n/a

#### [disposition](http://rs.tdwg.org/dwc/terms/index.htm#disposition)

n/a

#### [associatedMedia](http://rs.tdwg.org/dwc/terms/index.htm#associatedMedia)
#### [associatedReferences](http://rs.tdwg.org/dwc/terms/index.htm#associatedReferences)
#### [associatedSequences](http://rs.tdwg.org/dwc/terms/index.htm#associatedSequences)
#### [associatedTaxa](http://rs.tdwg.org/dwc/terms/index.htm#associatedTaxa)
#### [otherCatalogNumbers](http://rs.tdwg.org/dwc/terms/index.htm#otherCatalogNumbers)

n/a

#### [occurrenceRemarks](http://rs.tdwg.org/dwc/terms/index.htm#occurrenceRemarks)

### Organism

#### [organismID](http://rs.tdwg.org/dwc/terms/index.htm#organismID)

Recommended...

#### [organismName](http://rs.tdwg.org/dwc/terms/index.htm#organismName)

Recommended...

#### [organismScope](http://rs.tdwg.org/dwc/terms/index.htm#organismScope)

n/a

#### [associatedOccurrences](http://rs.tdwg.org/dwc/terms/index.htm#associatedOccurrences)
#### [associatedOrganisms](http://rs.tdwg.org/dwc/terms/index.htm#associatedOrganisms)
#### [previousIdentifications](http://rs.tdwg.org/dwc/terms/index.htm#previousIdentifications)
#### [organismRemarks](http://rs.tdwg.org/dwc/terms/index.htm#organismRemarks)

### MaterialSample

n/a

### Event

#### [eventID](http://rs.tdwg.org/dwc/terms/index.htm#eventID)
#### [parentEventID](http://rs.tdwg.org/dwc/terms/index.htm#parentEventID)
#### [fieldNumber](http://rs.tdwg.org/dwc/terms/index.htm#fieldNumber)
#### [eventDate](http://rs.tdwg.org/dwc/terms/index.htm#eventDate)

Recommended...

#### [eventTime](http://rs.tdwg.org/dwc/terms/index.htm#eventTime)
#### [startDayOfYear](http://rs.tdwg.org/dwc/terms/index.htm#startDayOfYear)
#### [endDayOfYear](http://rs.tdwg.org/dwc/terms/index.htm#endDayOfYear)
#### [year](http://rs.tdwg.org/dwc/terms/index.htm#year)
#### [month](http://rs.tdwg.org/dwc/terms/index.htm#month)
#### [day](http://rs.tdwg.org/dwc/terms/index.htm#day)
#### [verbatimEventDate](http://rs.tdwg.org/dwc/terms/index.htm#verbatimEventDate)
#### [habitat](http://rs.tdwg.org/dwc/terms/index.htm#habitat)
#### [samplingProtocol](http://rs.tdwg.org/dwc/terms/index.htm#samplingProtocol)

Recommended...

#### [samplingEffort](http://rs.tdwg.org/dwc/terms/index.htm#samplingEffort)
#### [sampleSizeValue](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeValue)
#### [sampleSizeUnit](http://rs.tdwg.org/dwc/terms/index.htm#sampleSizeUnit)
#### [fieldNotes](http://rs.tdwg.org/dwc/terms/index.htm#fieldNotes)
#### [eventRemarks](http://rs.tdwg.org/dwc/terms/index.htm#eventRemarks)

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
