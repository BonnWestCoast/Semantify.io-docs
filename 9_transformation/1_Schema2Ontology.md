# Schema to Ontology

## Source
* XSD file
* e.g.: UANodeSet.xsd (http://opcfoundation.org/UA/2011/03/UANodeSet.xsd)
* e.g.: Types.xsd (http://siemens.com/CM_PMA/Types.xsd , http://opcfoundation.org/UA/2008/02/Types.xsd)

## Process
parsing, transformation, serialization

## Analysis: Ontmalizer

### Parsing
Read schema file and generate `schemaset` and `schema`

	// Package: com.sun.xml.xsom
	
	XSOMParser parser = new XSOMParser(SAXParserFactory.newInstance());
	parser.setAnnotationParser(new AnnotationFactory());
	parser.parse(file);
	XSSchemaSet schemaSet = parser.getResult();
	XSSchema schema = schemaSet.getSchema(1);

### Transformation
Transformation rule applied

#### Conversion Rule
XSD tag | Type | Remark
------------- | ------------- | -------------
xs:simpleType | rdfs:Datatype with the suffix “Datatype” on datatype name. |
xs:simpleType with xs:enumeration | rdfs:Datatype with the suffix “Datatype” on datatype name.In addition, for the enumerations, an owl:Class as a subclass of EnumeratedValue is created. Instances are created for every enumerated value. An instance of Enumeration, referring to all the instances, is created as well as the owl:oneOf union over the instances. These are mostly informative, as they are not used directly during the XML data to RDF/OWL transformation.
xs:complexType over xs:complexContent |	owl:Class
xs:complexType over xs:simpleContent	| owl:Class
xs:element (global) with complex type	| owl:Class and subclass of the class generated from the referenced complex type
xs:element (global) with simple type	| owl:Datatype
xs:element (local to a type)	| owl:DatatypeProperty or owl:ObjectProperty depending on the element type. OWL Restrictions are built for the occurrence.
xs:group	| owl:Class
xs:attributeGroup	| owl:Class
Anonymous Complex Type	| As for Complex Type except a URI is constructed as Anon_#. Also, the class is defined as a subclass of Anon.
Anonymous Simple Type	| As for Simple Type except a URI is constructed as Anon_#.
Substitution Groups	| Subclass statements are generated for the members.
xsi:type on an XML element	| Overrides the schema abstract type with the specified type.


### Serialization


## Analysis: PCS2OWL
###Parsing
Custom parser

### Transformation
GenTax Algorithm

### Serialization
