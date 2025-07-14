# Rules

This page illustrates the rules followed by the XML schema.

# Non-automated rules

## Alphabetical Order

Properties/relations belonging to a class should be listed in alphabetical order. 
This rule allows the inspection of missing properties/relations while looking at the respective specification, where they are described in alphabetical order

## Schema Attributes

The xs:schema must have elementFormDefault=qualified and may have attributeFormDefault=unqualified.

## Schema header documentation 

Just as schema construct documentation adds clarity to a schema, schema header documentation enables information — the purpose, use,  and contents of a schema — to be concentrated in a single place within  a schema. Schema header documentation should be included in all global  elements. It must also contain references to the created date, last modified date and contact point as mandatory and optionally a URL where the release notes of the schema are published.

## Namespaces

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

## Elements vs. Types

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

## Global Approach

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

## Extensibility

The XML schema creation project for Core Vocabularies is a community
project launched and promoted by the European Commission. The SEMIC
community stands for co-creation and sharing best practices. The Support
Center is also home to a community of adopters that share tooling,
standards and good practices to promote semantic interoperability.

Any kind of support, e.g. providing feedback via GitHub on the XML
schema files, would highly be appreciated.

# Schematron Rules

The below table shows the list the schematron rules that can be applied to structure the XML schema automatically:

| Rule  | Rationale | Link |
| ------------- | ------------- | ------------- |
| Simple type definition is top-level  | This rule ensures that simple types are defined globals, therefore they can be reused. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L23) |
| Simple type has data definition  | This rule ensures that simple types have documentation. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L29)  |
| Simple type has semantic annotation | This rules ensures that mappings with the original vocabulary is in place. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L35)  |
| Complex type definition is top-level | This rule ensures that complex types are defined globals, therefore they can be reused. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L41)  |
| Complex type has data definition |  This rule ensures that complex types have documentation. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L47)  |
| Complex type and its elements have semantic annotation | This rules ensures that mappings with the original vocabulary is in place. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L53)  |
| Element declaration is top-level | This rule ensures that elements are defined globals, therefore they can be reused. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L67)  |
| Schema has data definition | This rule ensures that elements have documentation. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L73)  |
| Schema has app info | This rule ensures that the XML schema has metadata defined. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L79)  |
| Schema document defines target namespace  | This rule ensures that the target namespace is present, so all the elements/types belong to it. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L85)  |
| Schema has version  | This rule ensures that the XML schema has a version.  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L91)  |
| Schema version follows dot-notation  | This rule ensures that the version follows dot-notation, in practice the same used by the respective vocabulary. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L97)  |
| xs:import must have namespace  | This rule ensures that namespaces imported must be named. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L103)  |
| Schema component names have only specific characters  | This rule ensures that certain characters do not appear in the name.  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L109)  |
| Attribute name begins with lower case letter  | This rule ensures that all attributes start with lower letters. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L115)  |
| Name of schema component other than attribute and proxy type begins with upper case letter  | This rule ensures that all other types start with capital letters. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L122)  |
| Name of type ends in "Type"  | This rule ensures that all types names ends with "Type" .  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L134)  |
| Warning for the use of anyType | This rule ensures in general anyType should not be used but, considering the semantic context, it is allowed with exceptions. | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L143) |
| The xs:schema must have xs:appinfo to describe metadata of the Core Vocabularies. | The xs:documentation element is used for human readable material and the xs:appinfo element is used to provide information for tools, style sheets and other applications. |[link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L79) |
| XML schema element declaration MUST be: ... &lt;?xml version="1.0" encoding="UTF-8"?&gt;...| "<?xml …" is called XML declaration. It is used for all kinds  of XML files, not only for schemas.| [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L67)  |
| The XML document must be xs:schema. | Note: Using "xs" as the namespace prefix is not mandatory. It depends on the namespace definition and could also be "xsd". |[link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L85) |
| lowerCamelCase convention | The lowerCamerCase (LCC) convention must be used for attributes. |[link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L115) | 
| UpperCamelCase convention | The UpperCamelCase (UCC) convention must be used for naming elements and types.  |[link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L122) |

## How to execute the Rules

In this repository there is a [build.xml](../build.xml) file that can be executed by [Apache Ant](https://ant.apache.org/).
Ant is integrated in certain editors, for example within VSCode the user can install the plugin [Ant Target runner](https://marketplace.visualstudio.com/items?itemName=nickheap.vscode-ant).

The build.xml contains 2 steps:
1) validate, to validate the XML schema against the schematron Rules, using the open source [ph-schematron](https://github.com/phax/ph-schematron) engine.
2) report, to transform the report of schematron in HTML reports more easy to understand, using the open source [Saxon-HE](https://github.com/Saxonica/Saxon-HE) XSLT engine.

At the end of the execution, an "output" folder is generated containing the schematron report and the HTML reports for each XML schema.
