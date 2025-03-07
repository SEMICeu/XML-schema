# Introduction

W3C XML Schema Definition commonly referred to as ‘XSD’ is the means to
check the validity of the structure and the vocabulary of an XML
document. An XSD captures the object-oriented aspects of the modelling.
It establishes element/attribute declarations and simple/complex types
to express a set of rules to which XML documents must conform.

XSD Schemas are the main type of validation artefacts provided by
standardization organizations (e.g. W3C or Oasis). The schemas validate
that a particular XML document instance fulfils the structural and type
constraints defined by the standard.

The XML documents addressed by the XSD schemas are the SEMIC Core
Vocabularies:

 - [Person](https://semiceu.github.io/Core-Person-Vocabulary/releases/2.1.1/)
 - [Business](https://semiceu.github.io/Core-Business-Vocabulary/releases/2.2.0/)
 - [CCCEV](https://semiceu.github.io/CCCEV/releases/2.1.0/)
 - [Location](https://semiceu.github.io/Core-Location-Vocabulary/releases/2.1.0/)
 - [Public Event](https://semiceu.github.io/Core-Public-Event-Vocabulary/releases/1.1.0/)
 - [Public Organization](https://semiceu.github.io/CPOV/releases/2.1.1/)

The document at hand describes the structure of a number of XSD files
which can be used to validate the structure and vocabulary of the SEMIC

# XML Schema Files

The XML schema files were created for the core vocabularies listed
above :The XSD files are stored in the following folder structure:

-   CoreVoc_Aggregat
    -   CoreVoc_Aggregat.xsd
    -   dc.xsd
    -   dcmitype.xsd
    -   dcterms.xsd
-   CoreVoc_Business
    -   CoreVoc_Business.xsd
-   CoreVoc_CCCEV
    -   CoreVoc_CCCEV.xsd
-   CoreVoc_Common
    -   CoreVoc_CommonTypes.xsd
    -   xml.xsd
-   CoreVoc_Location
    -   CoreVoc_Location.xsd
-   CoreVoc_Person
    -   CoreVoc_Person.xsd
-   CoreVoc_PublicEvent
    -   CoreVoc_Public_Event.xsd
-   CoreVoc_PublicOrganisation
    -   CoreVoc_Public_Organization.xsd

Note: Components used in two or more vocabularies are stored in the
files:

-   CoreVoc_Aggregat.xsd contains complex types, e.g. the AddressType
-   CoreVoc_CommonTypes.xsd contains elementary types, e.g. a Generic
    Date Type

In addition, the supplementary schema files related to the Dublin Core
standard (dc.xsd, dcterm.xsd and dcmitype.xsd) or to the XML schema
(xml.xsd) have been downloaded and stored in the CoreVoc folder
structure in order to avoid a dependency on Internet availabilities.

# Internal Schema Structure

The internal structure of the XML schema files is as follows (the Person is used as an example here):

**the schema header with the Namespace definitions (see also below)**
```
<?xml version="1.0" encoding="UTF-8"?>
<!-- ===== Schema Header ================================= -->
<xs:schema
targetNamespace="http://data.europa.eu/m8g/xsd"
xmlns="http://data.europa.eu/m8g/xsd"
xmlns:xs="http://www.w3.org/2001/XMLSchema"
xmlns:dct="http://purl.org/dc/terms/"
xmlns:sawsdl="http://www.w3.org/ns/sawsdl"
elementFormDefault="qualified" attributeFormDefault="unqualified"
version="2.1.1">
```
**the import/include section**
```
<!-- ===== Includes/Imports ============================== -->
<xs:include
schemaLocation="../CoreVoc_Common/CoreVoc_CommonTypes.xsd"/>
<xs:include
schemaLocation="../CoreVoc_Aggregat/CoreVoc_Aggregat.xsd"/>
```
 
**the meta data (e.g. the title)**

```
<!-- ===== Meta Data==== ================================= -->
<xs:annotation>
<xs:documentation>Core Person Vocabulary</xs:documentation>
<xs:appinfo>
<dct:title>Core Person Vocabulary</dct:title>
<dct:description>This XML schema describes the Core Person  
vocabulary as part of SEMIC Core Vocabularies .</dct:description>
<dct:creator>Emidio Stani (PwC Belgium)</dct:creator>
<dct:creator>Ine Weyts (PwC Belgium)</dct:creator>
<dct:creator>Wolfgang Keber (DIaLOGIKa GmbH)</dct:creator>
<dct:contributor>Pavlina Fragkou (European
Commission)</dct:contributor>
<dct:contributor>Anastasia Sofou (Trasys
International)</dct:contributor>
<dct:contributor>Kristina Hector (DIaLOGIKa GmbH)</dct:contributor>
<dct:contributor>Patrick Plewka (DIaLOGIKa GmbH)</dct:contributor>
<dct:license>Licensed under the CC BY 4.0</dct:license>
<dct:rightsHolder>European Union</dct:rightsHolder>
<dct:rights>Copyright (C) European Union, 2024</dct:rights>
<dct:created>2024-10-15</dct:created>
</xs:appinfo>
</xs:annotation>
```
followed by the actual **schema definition**.

