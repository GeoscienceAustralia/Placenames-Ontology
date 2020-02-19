![GA logo](./ga-logo.jpg)
# Place Names Ontology
Markdown documentation created by [pyLODE](http://github.com/rdflib/pyLODE)


## Metadata
* **IRI**
  * `http://linked.data.gov.au/def/placenames`
* **Publisher(s)**
  * <a href="http://catalogue.linked.data.gov.au/org/ga">Geoscience Australia</a>
* **Creators(s)**
  * <a href="https://orcid.org/0000-0002-8742-7730">Nicholas Car</a> (<a href="mailto:nicholas.car@surroundaustralia.com">nicholas.car@surroundaustralia.com</a>) of Surround Australia
  * <a href="https://orcid.org/0000-0002-3884-3420">Simon J D Cox</a> (<a href="mailto:simon.cox@csiro.au">simon.cox@csiro.au</a>) of <a href="http://catalogue.linked.data.gov.au/org/csiro">CSIRO</a>
* **Contributor(s)**
  * <a href="https://orcid.org/0000-0002-4643-7289">Irina Bastrakova</a> (<a href="mailto:irina.bastrakova@ga.gov.au">irina.bastrakova@ga.gov.au</a>) of <a href="http://catalogue.linked.data.gov.au/org/ga">Geoscience Australia</a>
  * <a href="https://orcid.org/0000-0003-3425-0780">Armin Haller</a> (<a href="mailto:armin.haller@anu.edu.au">armin.haller@anu.edu.au</a>) of <a href="http://catalogue.linked.data.gov.au/org/anu">Australian National University</a>
* **Created**
  * 2018-08-02
* **Modified**
  * 2020-02-19
* **Imports**
  * <a href="http://linked.data.gov.au/def/loci">http://linked.data.gov.au/def/loci</a>
* **Rights**
  * (c) Commonwealth of Australia (Geoscience Australia) 2019, 2020
* **Ontology Source**
  * <a href="placenames.ttl">RDF (turtle)</a>
### Description
<p>Place Names is an RDF/OWL Ontology to define the structure and relationship of the names of geospatial features, typically collected in a Gazetteer. </p>
<p>A place-name is a text string, which 
- is coined by an agent (person or organization)
- is authorized by a jurisidiction (national, state or local government) 
- is a member item in a gazetteer
- has lifecycle information (status, validity dates, formal identifier) 
- denotes a natural or constructed geospatial feature with a specified classification (inhabited place, administrative area, mountain, school, station, park ...)</p>
<p>This ontology uses classes and properties from existing vocabularies, in particular 
- Loc-I ontology
- GeoSPARQL and GeoSPARQL-Extensions
- SKOS, Dublin Core</p>

## Table of Contents
1. [Classes](#classes)
1. [Object Properties](#objectproperties)
1. [Datatype Properties](#datatypeproperties)
1. [Annotation Properties](#annotationproperties)
1. [Namespaces](#namespaces)  


## Overview
![Placename ontology](./images/placename.png)

**Figure 1:** Ontology overview  
## Classes
[Gazetteer](#Gazetteer),
[Jurisdiction](#Jurisdiction),
[Place](#Place),
[Place Name](#PlaceName),
[Place Name Formality](#PlaceNameFormality),
[Place Type](#PlaceType),
[Point of Interest](#PointofInterest),
[Region](#Region),
[Status ](#Status),
### Gazetteer <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/Gazetteer`
Description | A Gazetteer is a list of Place Names
Super-classes |<a href="http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag">rdf:Bag</a><sup class="sup-c" title="class">c</sup><br />
Restrictions |<a href="http://www.w3.org/2000/01/rdf-schema#member">rdfs:member</a> <span class="cardinality">only</span> <a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
### Jurisdiction <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/Jurisdiction`
Description | Local, State, Territory or National (Commonwealth) Government that has authority to formally establish (i.e. gazette) place names within its jurisdictional area.
Super-classes |<a href="http://purl.org/dc/terms/Agent">dcterms:Agent</a><sup class="sup-c" title="class">c</sup><br />
In range of |<a href="#hasplacenamingauthority">hasPlaceNamingAuthority</a><sup class="sup-op" title="object property">op</sup><br />
### Place <sup>c</sup>
![Place class](./images/place.png)
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/Place`
Description | An identifiable geographic Place as defined by the Composite Gazetteer of Australia. A Place is classified according to an extensible set of types.
Super-classes |<a href="http://www.opengis.net/ont/geosparql#Feature">geo:Feature</a><sup class="sup-c" title="class">c</sup><br />
Restrictions |<a href="#hasplaceclassification">hasPlaceClassification</a><sup class="sup-op" title="object property">op</sup> <span class="cardinality">min</span> 1<br /><a href="http://www.opengis.net/ont/geosparql#hasGeometry">geo:hasGeometry</a> <span class="cardinality">min</span> 1<br />
Sub-classes |<a href="#Region">Region</a><sup class="sup-c" title="class">c</sup><br /><a href="#PointofInterest">PointOfInterest</a><sup class="sup-c" title="class">c</sup><br />
In domain of |<a href="#hasplaceclassification">hasPlaceClassification</a><sup class="sup-op" title="object property">op</sup><br />
### Place Name <sup>c</sup>
![Place class](./images/placename-details.png)
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/PlaceName`
Description | The name of a place, assigned by an official naming authority and included in the Place Names Gazeteer of Australia.
Restrictions |<a href="http://linked.data.gov.au/def/loci#isMemberOf">http://linked.data.gov.au/def/loci#isMemberOf</a> <span class="cardinality">some</span> <a href="#Gazetteer">Gazetteer</a><sup class="sup-c" title="class">c</sup><br /><a href="#name">name</a><sup class="sup-dp" title="datatype property">dp</sup> <span class="cardinality">exactly</span> 1<br /><a href="http://purl.org/dc/terms/identifier">dcterms:identifier</a> <span class="cardinality">min</span> 1<br /><a href="#hasstatus">status</a><sup class="sup-op" title="object property">op</sup> <span class="cardinality">exactly</span> 1<br />
In domain of |<a href="#pronunciation">hasPronunciation</a><sup class="sup-dp" title="datatype property">dp</sup><br /><a href="#hasplacenameformality">hasPlaceNameFormality</a><sup class="sup-op" title="object property">op</sup><br /><a href="#wasnamedby">wasNamedBy</a><sup class="sup-op" title="object property">op</sup><br /><a href="#hasplacenamingauthority">hasPlaceNamingAuthority</a><sup class="sup-op" title="object property">op</sup><br /><a href="#placenameof">placeNameOf</a><sup class="sup-op" title="object property">op</sup><br />
In range of |<a href="#hasplacename">hasPlaceName</a><sup class="sup-op" title="object property">op</sup><br />
### Place Name Formality <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/PlaceNameFormality`
Description | The formality of a Place Name: official, historical, informal
Super-classes |<a href="http://www.w3.org/2004/02/skos/core#Concept">skos:Concept</a><sup class="sup-c" title="class">c</sup><br />
In range of |<a href="#hasplacenameformality">hasPlaceNameFormality</a><sup class="sup-op" title="object property">op</sup><br />
### Place Type <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/PlaceType`
Description | The classification of a place, from the ICSM Permanent Committee on Place Names classification scheme.
Super-classes |<a href="http://www.w3.org/2004/02/skos/core#Concept">skos:Concept</a><sup class="sup-c" title="class">c</sup><br />
In range of |<a href="#hasplaceclassification">hasPlaceClassification</a><sup class="sup-op" title="object property">op</sup><br />
### Point of Interest <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/PointOfInterest`
Description | A specific point Location that someone may find useful or interesting.
Super-classes |<a href="#Place">Place</a><sup class="sup-c" title="class">c</sup><br />
Restrictions |<a href="#wasnamedby">wasNamedBy</a><sup class="sup-op" title="object property">op</sup> <span class="cardinality">only</span> <a href="http://purl.org/dc/terms/Agent">dcterms:Agent</a><sup class="sup-c" title="class">c</sup><br />
### Region <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/Region`
Description | A Region is an area of land that has common features.
Super-classes |<a href="#Place">Place</a><sup class="sup-c" title="class">c</sup><br />
### Status  <sup>c</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/Status`
Super-classes |<a href="http://www.w3.org/2004/02/skos/core#Concept">skos:Concept</a><sup class="sup-c" title="class">c</sup><br />
In range of |<a href="#hasstatus">status</a><sup class="sup-op" title="object property">op</sup><br />

## Object Properties
[has place classification](hasplaceclassification),
[has place name](hasplacename),
[has place name formality](hasplacenameformality),
[has place naming authority](hasplacenamingauthority),
[place name of](placenameof),
[has status](hasstatus),
[was named by](wasnamedby),
[](hasplaceclassification)
### has place classification <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/hasPlaceClassification`
Description | A relation between a Place and a classification of its real world phenomena.
Super-properties |<a href="http://purl.org/dc/terms/type">dcterms:type</a><br />
Domain(s) |<a href="#Place">Place</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="#PlaceType">PlaceType</a><sup class="sup-c" title="class">c</sup><br />
[](hasplacename)
### has place name <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/hasPlaceName`
Description | The Feature has a place name (label) assigned to it
Usage Note | All PlaceName objects names indicated by hasPlaceName should have the role of the name indicated with a Name Type
Domain(s) |<a href="http://www.opengis.net/ont/geosparql#Feature">geo:Feature</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
[](hasplacenameformality)
### has place name formality <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/hasPlaceNameFormality`
Description | The formality of a Place Name
Usage Note | Values for this property must be selected from the Place Name Formality vocabulary
Domain(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="#PlaceNameFormality">PlaceNameFormality</a><sup class="sup-c" title="class">c</sup><br />
[](hasplacenamingauthority)
### has place naming authority <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/hasPlaceNamingAuthority`
Description | The authority (jurisdiction) responsible for formally gazetting the place name.
Super-properties |<a href="http://www.w3.org/ns/prov#wasAttributedTo">prov:wasAttributedTo</a><br />
Domain(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="#Jurisdiction">Jurisdiction</a><sup class="sup-c" title="class">c</sup><br />
[](placenameof)
### place name of <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/placeNameOf`
Domain(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="http://www.opengis.net/ont/geosparql#Feature">geo:Feature</a><sup class="sup-c" title="class">c</sup><br />
[](hasstatus)
### has status <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/status`
Usage Note | This property indicates the status of a Place Name in a Gazetteer.
Range(s) |<a href="#Status">Status</a><sup class="sup-c" title="class">c</sup><br />
[](wasnamedby)
### was named by <sup>op</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/wasNamedBy`
Description | The Agent (person, community, organization) that assigned the name to the Place
Super-properties |<a href="http://www.w3.org/ns/prov#wasAttributedTo">prov:wasAttributedTo</a><br />
Domain(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="http://purl.org/dc/terms/Agent">dcterms:Agent</a><sup class="sup-c" title="class">c</sup><br />

## Datatype Properties
[pronunciation](pronunciation),
[name](name),
[](pronunciation)
### pronunciation <sup>dp</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/hasPronunciation`
Description | The pronunciation of a Place Name, indicated by means of a phonetic alphabet string
Domain(s) |<a href="#PlaceName">PlaceName</a><sup class="sup-c" title="class">c</sup><br />
Range(s) |<a href="http://www.w3.org/2001/XMLSchema#string">xsd:string</a><sup class="sup-c" title="class">c</sup><br />
[](name)
### name <sup>dp</sup>
Property | Value
--- | ---
IRI | `http://linked.data.gov.au/def/placenames/name`
Range(s) |<a href="http://www.w3.org/2001/XMLSchema#string">xsd:string</a><sup class="sup-c" title="class">c</sup><br />

## Annotation Properties
[rights](rights),
[altlabel](altlabel),
[email](email),
[identifier](identifier),
[memberOf](memberOf),
[name](name1),
[uri](uri),
[](rights)
### rights <sup>ap</sup>
Property | Value
--- | ---
IRI | `http://purl.org/dc/terms/rights`
[](altlabel)
### altlabel <sup>ap</sup>
Property | Value
--- | ---
IRI | `http://www.w3.org/2004/02/skos/core#altlabel`
[](email)
### email <sup>ap</sup>
Property | Value
--- | ---
IRI | `https://schema.org/email`
[](identifier)
### identifier <sup>ap</sup>
Property | Value
--- | ---
IRI | `https://schema.org/identifier`
[](memberOf)
### memberOf <sup>ap</sup>
Property | Value
--- | ---
IRI | `https://schema.org/memberOf`
[](name1)
### name <sup>ap</sup>
Property | Value
--- | ---
IRI | `https://schema.org/name`
[](uri)
### uri <sup>ap</sup>
Property | Value
--- | ---
IRI | `https://schema.org/uri`

## Namespaces
* **default (:)**
  * `http://linked.data.gov.au/def/placenames/`
* **:**
  * `http://linked.data.gov.au/def/placenames/`
* **adms**
  * `https://www.w3.org/ns/adms#`
* **asgs**
  * `http://linked.data.gov.au/def/asgs#`
* **dc**
  * `http://purl.org/dc/elements/1.1/`
* **dcat**
  * `http://www.w3.org/ns/dcat#`
* **dcterms**
  * `http://purl.org/dc/terms/`
* **geo**
  * `http://www.opengis.net/ont/geosparql#`
* **geofabric**
  * `http://linked.data.gov.au/def/geofabric#`
* **gnaf**
  * `http://linked.data.gov.au/def/gnaf#`
* **owl**
  * `http://www.w3.org/2002/07/owl#`
* **pn-ext**
  * `http://example.org/pn-ext/`
* **prof**
  * `http://www.w3.org/ns/dx/prof/`
* **prov**
  * `http://www.w3.org/ns/prov#`
* **rdf**
  * `http://www.w3.org/1999/02/22-rdf-syntax-ns#`
* **rdfs**
  * `http://www.w3.org/2000/01/rdf-schema#`
* **reg**
  * `http://purl.org/linked-data/registry#`
* **schema**
  * `https://schema.org/`
* **skos**
  * `http://www.w3.org/2004/02/skos/core#`
* **time**
  * `http://www.w3.org/2006/time#`
* **vann**
  * `http://purl.org/vocab/vann/`
* **xml**
  * `http://www.w3.org/XML/1998/namespace`
* **xsd**
  * `http://www.w3.org/2001/XMLSchema#`

## Legend
* Classes: c
* Object Properties :op
* Functional Properties: fp
* Data Properties: dp
* Annotation Properties: dp
* Properties: p
* Named Individuals: ni