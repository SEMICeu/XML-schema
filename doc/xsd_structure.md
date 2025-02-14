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

-   Business
-   CCCEV
-   Location
-   Person
-   Public Event
-   Public Organisation

The document at hand describes the structure of a number of XSD files
which can be used to validate the structure and vocabulary of the SEMIC

# XML Schema Files

They XML schema files were created for the core vocabularies listed
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
<dct:licence>Licensed under the CC BY 4.0</dct:licence>
<dct:rightsHolder>European Union</dct:rightsHolder>
<dct:rights>Copyright (C) European Union, 2024</dct:rights>
<dct:created>2024-10-15</dct:created>
</xs:appinfo>
</xs:annotation>
```
followed by the actual **schema definition**.

# Some Basic Rules for XML Schema Files

1.  XML schema element declaration MUST be:

```
 <?xml version="1.0" encoding="UTF-8"?>
```
 Note: "<?xml …" is called XML declaration. It is used for all kinds
 of XML files, not only for schemas.

2.  The XML document must be xs:schema. Note: Using "xs" as the
    namespace prefix is not mandatory. It depends on the namespace
    definition and could also be "xsd".

3.  The xs:schema must have a version attribute (see example above in
    Schema Structure).

4.  The xs:schema must have elementFormDefault=qualified and may have
    attributeFormDefault=unqualified.

5.  The xs:schema must have xs:appinfo to describe metadata of the Core
    Vocabularies. The xs:documentation element is used for human
    readable material and the xs:appinfo element is used to provide
    information for tools, style sheets and other applications.

 Just as schema construct documentation adds clarity to a schema,
 schema header documentation enables information — the purpose, use,
 and contents of a schema — to be concentrated in a single place within
 a schema. Schema header documentation should be included in all global
 elements.

 In order to facilitate processing information in the header by
 applications, the xs:appInfo element should be used for schema header
 documentation. Schema header documentation allows for discerning the
 purpose, use, and contents of the XML schema.

 XML schemas must include schema header documentation containing
 references to the created date, last modified date and contact point
 as mandatory and optionally a URL where the release notes of the
 schema are published.

6.  The UpperCamelCase (UCC) convention must be used for naming elements
    and types. The lowerCamerCase (LCC) convention must be used for
    attributes.

    Note: SEMIC often uses the lowerCamelCase (LCC) convention for
    elements. This allows for distinguishing between types and elements
    which might be more important than distinguishing between elements
    and attributes.

# Namespaces

The targetNamespace is the default namespace. XMLSchema and other
schemas imported must be qualified, i.e. the namespace declaration looks
as follows:
```
targetNamespace="http://data.europa.eu/m8g/xsd"
xmlns="http://data.europa.eu/m8g/xsd"
xmlns:xs="http://www.w3.org/2001/XMLSchema"
xmlns:dct="http://purl.org/dc/terms/"
xmlns:sawsdl=<http://www.w3.org/ns/sawsdl>
```
Namespaces imported from other projects have qualifiers of their own
(e.g. the dct namespace). "Supporting" schemas (e.g.
CoreVoc_CommonTypes.xsd) will take-on the targetNamespace of the main
schema.

# Elements vs. Types

Larger objects containing several items are declared as complexTypes,
e.g. the AgentType. It is always possible to create an element from the
type, if needed. With a type, other elements can reuse that type. Since
elements and types are in different symbol spaces, it would be feasible
to have an element and type with the same name, e.g.
```
<xs:complexType name="AgentType"  
sawsdl:modelReference="http://xmlns.com/foaf/0.1/Agent">
…
<xs:element name="AgentType" type="CodeType"/>.
```
# Global Approach

A component (element, complexType, or simpleType) is "global" if it is
an immediate child of <schema>, whereas it is "local" if it is not an
immediate child of <schema>, i.e., it is nested within another
component.

This global approach is also known as “Salami Slice.” All the elements
in the Salami Slice design are global. No nesting of element
declarations is required and the declarations can be reused throughout
the schema. All the elements must be defined within the global
namespace. Example:
```
<xs:element name="Person" type="PersonType"/>
<xs:complexType name="PersonType">
…
</xs:complexType>
```
# Extensibility

The XML schema creation project for Core Vocabularies is a community
project launched and promoted by the European Commission. The SEMIC
community stands for co-creation and sharing best practices. The Support
Center is also home to a community of adopters that share tooling,
standards and good practices to promote semantic interoperability.

Any kind of support, e.g. providing feedback via GitHub on the XML
schema files, would highly be appreciated.
