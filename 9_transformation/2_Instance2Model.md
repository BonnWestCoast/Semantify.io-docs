# XML Instance to OWL Instances
## Source
* XML file
* e.g.: Opc.Ua.NodeSet2.xml 
	* xmlns="http://opcfoundation.org/UA/2011/03/UANodeSet.xsd"
	* xmlns="http://opcfoundation.org/UA/2008/02/Types.xsd"
	* xmlns:p5="http://www.w3.org/2001/XMLSchema-instance"
* e.g.: servo_presse.xml
	* xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	* xmlns:uax="http://opcfoundation.org/UA/2008/02/Types.xsd"
	* xmlns="http://opcfoundation.org/UA/2011/03/UANodeSet.xsd" 
	* xmlns:s1="http://siemens.com/CM_PMA/Types.xsd" 
	* xmlns:xsd="http://www.w3.org/2001/XMLSchema"
	* xmlns="http://siemens.com/CM_PMA/Types.xsd"

## Process
* parsing, transformation, serialization
* It generates OWL instances = assertional knowledge
* which is validated by and based on model ontologies - refers to the namespaces of schema(xmlns)

### Parsing
same as XSD.

### Transformation
Transformation rule applied

#### General Rules
* From a single XML instance document, over a (possibly) generated XML Schema, finally to an OWL model with OWL instances. Generating XML Schema is necessary when loading xsd is not possible.
* 


#### Conversion Rule

### Serialization

