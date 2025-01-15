# Rules

This page illustrates the rules followed by the XML schema.

## Schematron Rules

The below table shows the list the schematron rules applied to structure the XML schema:

| Rule  | Link |
| ------------- | ------------- |
| Simple type definition is top-level  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L23) |
| Simple type has data definition  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L29)  |
| Simple type has semantic annotation | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L35)  |
| Complex type definition is top-level | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L41)  |
| Complex type has data definition | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L47)  |
| Complex type and its elements have semantic annotation | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L53)  |
| Element declaration is top-level | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L74)  |
| Schema has data definition | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L74)  |
| Schema has app info | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L86)  |
| Schema document defines target namespace  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L92)  |
| Schema has version  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L98)  |
| Schema version follows dot-notation  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L104)  |
| xs:import must have namespace  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L110)  |
| Schema component names have only specific characters  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L116)  |
| Attribute name begins with lower case letter  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L122)  |
| Name of schema component other than attribute and proxy type begins with upper case letter  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L129)  |
| Name of type ends in "Type"  | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L141)  |
| Warning for the use of anyType | [link](https://github.com/SEMICeu/XML-schema/blob/main/rules/rules_schematron.sch#L150)  |

### How to execute the Rules

In this repository there is a build.xml file that can be interpreted by [Apache Ant](https://ant.apache.org/).
Ant is integrated in certain editors, for example within VSCode the user can install the  plugin [Ant Target runner](https://marketplace.visualstudio.com/items?itemName=nickheap.vscode-ant).

The build.xml contains 2 steps:
1) validate, to validate the XML schema against the schematron Rules, using the open source [ph-schematron](https://github.com/phax/ph-schematron) engine.
2) report, to transform the report of schematron in HTML reports more easy to understand, using the open source [Saxon-HE](https://github.com/Saxonica/Saxon-HE) XSLT engine.

The output folder contains the schematron report and the HTML reports per XML schema.









