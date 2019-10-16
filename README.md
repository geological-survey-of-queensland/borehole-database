# GSQ Borehole Database

## Purpose of this document
Provide a specification for the new GSQ Borehole Database that:  
* Accurately defines the business requirements
* Is a key input to the software design process for a software developer  

## Terminology

A borehole is the generalised term for any narrow shaft drilled in the ground, either vertically, horizontally, or inclined. 

A borehole may be constructed for many different purposes, including the extraction of water, oil, and natural gas, as part of a geotechnical investigation, mineral exploration, temperature measurement, for geothermal installations, or for underground storage of unwanted substances, e.g. in carbon capture and storage.

'Borehole' is synonymous with a range of terms including 'well', 'bore', 'drillhole' and 'corehole'.

## Background
 - Boreholes exist for a wide range of purposes, with varying lifecycles and [actors](https://en.wikipedia.org/wiki/Actor_(UML)).  
 - There are multiple systems of record for boreholes across government, e.g. [Geological Survey of Queensland](https://www.business.qld.gov.au/industries/mining-energy-water/resources/geoscience-information/gsq), [DNRME Resources Safety and Health](https://www.business.qld.gov.au/industries/mining-energy-water/resources/safety-health), [Office of Groundwater Impact](https://www.business.qld.gov.au/industries/mining-energy-water/resources/landholders/csg/ogia), [Department of Environment and Science](https://www.des.qld.gov.au/).  
 - There are varying standards across commodity groups, e.g. [PPDM](https://ppdm.org) and [WITSML](http://docs.energistics.org/) for petroleum and gas, [GeoSciML](http://www.geosciml.org/) and [GeoSciML Lite](http://docs.opengeospatial.org/is/16-008/16-008.html#403)for minerals, and [CoalLog](https://ausimm.com/coal-log/) for coal.  
 - The requirements for reporting and data submitted by industry vary under the different legislation and Acts.  

## The Borehole Database 

The Geological Survey of Queensland is creating a new borehole database to replace the existing borehole functionality in the MERLIN system.

The primary focus of the database is to record details of the borehole entity and its primary attributes. This **does not** mean that we lose all of the other borehole-related data, we just capture and manage that data in a smarter way.

Borehole entities in borehole database can link to one or many datasets, e.g. wireline logs, cores and cuttings, geochemistry, etc. 

While the borehole entity is generalised, datasets can be specialised for particular commodity groups and purposes.

### Objectives of the Borehole Database

 1. Queensland Government knows the location, attributes and status of all boreholes in Queensland.  
 2. The database helps government to perform custodianship of the borehole as an asset throughout its lifecycle.   
 3. The database is a single, trusted system of record for all boreholes in Queensland.
 4. The database is integrated with data input mechanisms, data consumers, and data display systems.  
 5. The database leverages schema-on-read (instead of schema-on-write) to be able to store all borehole data variations.

### What the borehole database is not
The borehole database is not a borehole data management system. There are multiple commercial systems that meet the extended data requirements of specific industries.  

## Derivation
The borehole database is derived from the following standards:

 - [PPDM](https://ppdm.org) for petroleum and gas
 - [GeoSciML](http://www.geosciml.org/) for minerals
 - [GGIC National Guideline Data templates](http://www.australiaminerals.gov.au/__data/assets/pdf_file/0004/60772/National_Guidelines_Version_4.5_February_18.pdf) for mineral reporting
 - [CoalLog](https://ausimm.com/coal-log/) for coal
 
## Borehole data categories
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/borehole-register/blob/master/images/simplified_borehole_data_model.png" width="680"><br>
Figure 1: Borehole data categories</p>

The above diagram shows the broad categories of data that are recorded for boreholes and is not exhaustive. The intention of this diagram is to cause us to think of our data in a categorical way.

## Borehole conceptual data model
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/borehole-register/blob/master/images/borehole_conceptual_data_model.svg" width="680"><br>
Figure 2: Borehole conceptual data model</p>

## Borehole data elements
| Data Element | Description | Rank |
|---|---|---|
|borehole_id|A persistent identifier for the borehole.|--|
|borehole_name|Unique name and/or number assigned to each borehole.|--|
|borehole_alias|Names & identifiers that a borehole may otherwise be known as. Includes previous or alternate borehole identifiers assigned to the borehole by a regulatory agency.|--|
|association|Relationship to other boreholes, e.g. parent, previous, etc.|--|
|purpose|The purpose for which the borehole was drilled, e.g. petroleum, CSG, water injection, water observation, etc.|--|
|sub_purpose|A narrower definition of the purpose, for example ‘Exploration’, ‘Appraisal’, ‘Development’, ‘Water supply’.|--|
|drilling_method|A term from a controlled vocabulary indicating the drilling method used, e.g rotary air blast, auger, diamond core, air core, etc. NOTE: Should this be 'bit type' instead?|--|
|status|The current status of the borehole, e.g. intended, cased and suspended, completed, on injection, on production, plugged and abandoned, suspended.|--|
|status_event|The event that triggered the status change, e.g. lodging of notice of intention to drill, lodging of well completion report.|--|
|status_date|The date of the status event.|--|
|origin_latitude|Angular distance in decimal degrees, east or west of the prime meridian. A negative value represents a west longitude.|--|
|origin_longitude|Angular distance in decimal degrees, north or south of the equator. A negative value represents a south latitude.|--|
|origin_elevation|Elevation of the depth datum used as a reference for other measured well or borehole points.|--|
|origin_circumstance|A term from a controlled vocabulary indicating the named position relative to ground surface where the borehole commenced, e.g. natural ground surface, open pit floor, underground, offshore.|--|
|depth_datum|The point from which depths are measured in a well or bore (depth reference datum). For example: kelly bushing (KB), rotary table (RT) or ground level (GL).|--|
|location_confidence|An estimate of the accuracy of the location of the borehole collar location in metres. See [Australian Map and Spatial Data  Horizontal Accuracy Standard 2009](https://www.icsm.gov.au/sites/default/files/Spatial_Data_Horizontal_Accuracy.pdf)|--|
|total_depth|Total or maximum measured depth of the borehole relative to the origin elevation.|--|
|well_design|A term from a controlled vocabulary indicating the inclination type of the borehole. Terms include vertical; inclined up; inclined down, horizontal, deviated.|--|
|azimuth|The angle (in degrees) of clockwise departure from true north to the borehole direction. |--|
|inclination|The angle (in degrees) at surface of borehole deviation away from the vertical. 0 degrees inclination is horizontal and -90 degree inclination is vertical (downward). Note: Inclination is dealt with differently by minerals and petroleum. Vertical is -90° in minerals and 0° in petroleum.|--|
|drill_start_date|Date the drilling operations commenced on the borehole, penetrating the ground surface.|--|
|drill_end_date|Date the drilling operations for the borehole was completed at the total or maximum measured depth of the borehole.|--|
|rig_release_date|Date the drilling rig was released from operations on the borehole.|--|
|permit_type|The permit type under which the borehole activity occurred. A lookup to the permit register.|--|
|permit_number|The permit number under which the borehole activity occurred. A lookup to the permit register.|--|
|operator|The organisation responsible for commissioning the borehole (as opposed to actually drilling the borehole). A lookup to the organisation register.|--|
|driller|The organisation responsible for drilling the borehole (as opposed to commissioning the borehole). A lookup to the organisation register.|--|
|geometry|A geospatial representation of the borehole as a point, polygon, or 3D geometry. Where  borehole location in XYZ coordinates is not available, surrogate geometries can be used, e.g. permit geometry, block or sub-block, mapsheet.|--|
|see_also|Contains reference to JSON metadata and data files. Can also reference related documents or datasets.|--|
|remarks|Any narrative comments or remarks about this borehole.|--|

### Inferred borehole data elements
Data duplication is avoided by creating a **reference** to data held in other registers, instead of copying that data into the borehole database. This reference allows us to **infer** the data relationships.

| Data element | How is it inferred? | 
|---|---|
|Survey plan no|Survey plans will be migrated from GEM to CKAN. The survey plan record will contain a reference to the borehole identifier. This data is currently held in MERLIN table bhf_borehole_survey_plan. Alternatively (or in addition), the survey plan could be stored in the geometry.|
|Company report number|QDEX reports will be migrated to the new report database and will contain a reference to the borehole identifier. This data is currently held in MERLIN table bhf_borehole.|
|Wireline log|Wireline logs will migrated to the samples and observations database and will have a reference to the borehole identifier. This data is currently held in MERLIN table bhf_wireline_logs.|
|Held|Data for cuttings, cores and sidewall cores are currently held in MERLIN and should be migrated to the samples and observations database, with a reference to the borehole they were taken from.|
|Hold location|This data is displayed in GeoResGlobe. Data should be migrated to the samples and observations database with a reference to the 'Held' data element.|
|Result|Results will be migrated to the samples and observations database and will have a reference to the borehole identifier. This data is currently held in MERLIN table bhf_boreholes with a lookup to cpf_drill_results.|


### Other borehole data elements that require consideration
| Data element | Description | Decision |
|---|---|---|
|QWRC RN|This data is displayed in GeoResGlobe. Source is MERLIN bhf_boreholes table.|--|
|Hylog release date|This data is displayed in GeoResGlobe. Of the 56000 boreholes in MERLIN, 306 have a record in this field.|--|
|Total depth logger|This data is displayed in GeoResGlobe.|--|
|Perforation|This data is displayed in GeoResGlobe.|--|


## Borehole data mapping to industry reporting templates
| Data Element | Mineral | P&G | Coal | PGGD01 | PGGD02|
|---|---|---|---|---|---|
|borehole_id|yes|---|yes|yes |yes|
|borehole_name|---|yes|yes|yes |yes|
|borehole_alias|---|---|---|--- |---|
|association|---|---|yes|---|---|
|purpose|---|yes|yes|yes|yes|
|sub_purpose|---|yes|yes|yes|yes|
|drilling_method|drill_type|yes|yes|---|---|
|status|---|yes|yes|yes|yes|
|status_event|---|---|---|yes|yes|
|status_date|---|---|---|yes|yes|
|origin_latitude|easting|---|yes|yes|yes|
|origin_longitude|northing|---|yes|yes|yes|
|origin_elevation|yes|---|yes|---|---|
|depth_datum|---|yes|yes|---|---|
|location_confidence|---|---|---|---| ---|
|total_depth|yes|yes|yes|planned|yes|
|azimuth|yes - numeric|yes - numeric|---|---|---|
|inclination|yes - numeric|yes - numeric|yes - textual|yes|yes|
|origin_circumstance|---|---|---|---|---|
|drill_start_date|yes|yes|spud_date|estimated |yes|
|drill_end_date|yes|yes|yes|estimated|yes|
|rig_release_date|---|yes|---|---|yes|
|permit_type|yes|yes|yes|yes |yes|
|permit_number|yes|yes|yes|yes|yes|
|operator|yes|---|yes|yes|yes|
|driller|---|yes|yes|---|---|
|geometry|---|---|---|---|---|


## Borehole data mapping to standards
| Data element | MERLIN | PPDM | GeosciML | CoalLog |
|---|---|---|---|---|
|borehole_id| bore_no | well_num |-|-|
|borehole_name | primary_bore_name |well_name| drillhole_id |borehole_name |
|borehole_alias |secondary_bore_name<br>prev_bore_id|well_alias|-|-|
|purpose|bore_type_code|--|purpose|borehole_type<br>borehole_purpose_x|
|sub_purpose|bore_subtype_code|--|--|--|
|drilling_method|drill_method_code|--|drillingmethod|bit_type|
|status|bore_status_code|current_status|--|borehole_status_x|
|status_date|status_date|current_status_date|--|--|
|status_event| |--|--|--|
|origin_latitude|bhf_locations|surface_latitude|location|easting|
|origin_longitude|bhf_locations|surface_longitude|location|northing|
|origin_elevation|ground_level_rl<br>+ collar_height|depth_datum_elev|elevation|--|
|depth_datum|elev_datum_code|depth_datum|borehole-elevation-crs|height_datum|
|location_confidence|loc_method_code<br>loc_accuracy|--|--|location_acc|
|total_depth|total_depth_driller_MD|final_td|boreholelength|total_depth|
|azimuth|bhf_orientations<br>azimuth|--|--|azimuth|
|inclination|well_path|--|inclinationtype|inclination|
|origin_circumstance|--|--|startpoint|--|
|drill_start_date|spud_date|spud_date|dateofdrilling|drill_date|
|drill_end_date|completion_date|completion_date|dateofdrilling|complete_date|
|rig_release_date|rig_release_date|rig_release_date|--|--|
|permit_type|tenure_type|lease_name|--|lease_no|
|permit_number|tenure_no|lease_num|--|lease_no|
|operator|operator_code|operator|operator|--|
|driller|--|--|driller|drill_company|
|geometry|bhf_orientations|--|--|--|

## Borehole vocabularies
The following vocabularies are required:

| Vocabulary | MERLIN | GeoSciML | PPDM | CoalLog |
|---|---|---|---|---|
|borehole purpose|greenhouse gas storage, petroleum, water, stratigraphic, mineral, coal, coal seam gas|--|produce, inject, cycle, service, minerals, research, observation|blasthole, coal quality, environmental, gas, geotech, hydrological, lox, service, structure|
|borehole sub-purpose|exploration well, line of oxidation borehole, observation bore, geotechnical borehole, supply bore, collaborative drilling borehole, water injection well, test bore, scout well, reference bore, appraisal well, petroleum injection well, quality borehole, gas content borehole, structure borehole, coal seam gas injection well, exploration borehole, spontaneous combustion borehole, development well, collaborative drilling initiative well, geothermal heat flow bore, mineral & extractive industries appraisal borehole|--|supply, storage, disposal, relief, strat hole|--|
|borehole drilling method|--|See [vocab](https://vocabs.ands.org.au/viewById/124)|--|auger, blades/drag blade, hammer, mill claw, poly crystalline diamond open, rock roller/tricone, surface/wing, diamond core (wireline), poly crystalline diamond core (conventional), poly crystalline diamond core (wireline), tungsten carbide core (conventional)|
|borehole status|plugged and abandoned, producing hydrocarbons, water bore, suspended/capped/shut-in, proposed to be drilled, never drilled, injecting|--|active, in-active, plugged and abandoned, reclaimed|backfilled, casing removed, cemented, completed, equipment in borehole, hazard in borehole, infrastructure, in progress, mined, piezometer, plugged, rehabilitated, unknown, water bore|
|borehole status event|--|--|--|--|
|borehole inclination|vertical, horizontal, vertical and horizontal|--|vertical, horizontal, directional|--|
|borehole origin circumstance|--|--|--|--|

### Reporting guideline lookup values
| Vocabulary | P&G | Mineral | Coal |
|---|---|---|---|
|borehole purpose|csg, petroleum, petroleum injection well, water injection well, water observation bore, water supply bore|--|--||
|borehole sub-purpose|exploration, appraisal, development|--|--|
|borehole drilling method|core impregnated, core PDC, core surface set, core TSD, fixed cutter PDC, hammer, roller cone, roller cone insert, roller cone milled tooth |air core, auger mechanical, calweld large diameter, diamond drill hole, pre-collared drillhole, open hole percussion, rotary air blast hole, reverse circulation percussion, rotary mud, unknown drill type, vacuum bedrock drill hole, vibratory drill hole, sonic, water bore, navi drilling, sonic drilling|--|
|borehole status|cased and suspended, completed, on injection, on production, plugged and abandoned, suspended|--|backfilled, casing removed, cemented, completed, equipment in borehole, hazard in borehole, infrastructure, in progress, mined, piezometer, plugged, rehabilitated, unknown, water bore|
|borehole status event|--|--|--|
|borehole inclination|vertical, deviated|--|--|
|borehole origin circumstance|--|--|--|
|depth datum|rotary table, kelly bushing, ground level, other|ground level, drillpipe collar, rotary table, other|--|

## Software design
The current MERLIN Oracle database is a relational database with 58 borehole-related tables:  
* 6 tables with current data updates  
* 5 tables last updated mid 2018  
* 12 tables last updated mid 2017  
* 9 tables last updated betweeen 2012 and 2016  
* 8 tables last updated in early 2010  
* 3 tables last updated 1996-2007  
* 9 tables with no data  


The new software design will feature a relational database for the primary metadata, with the remaining metadata and data being stored as key-value pairs. For example, if the **driller = ACME Drilling**, the key is **driller** and the value is **ACME Drilling**. Another example is **Rig Release Date** (key) = **25-01-2018** (value).  

For an example of borehole key-value pairs, load this [borehole data extract](https://github.com/geological-survey-of-queensland/borehole-register/blob/master/files/63801_borehole_data.json) into the online tool
http://jsoneditoronline.org/. 

### Reporting & analytics
Borehole data compilations can be created in Amazon Redshift (data warehouse). For example, we could create a prepared view of all boreholes by region. 

### Data migration
Existing MERLIN data will be extracted from the Oracle database. Primary metadata will be written to the database, the remainder of the data written to JSON key-value pairs. ALL historical data required to be preserved will be stored in the new system.

### Data extraction from new reporting guidelines
As data is submitted by industry through the lodgement portal, the borehole data can be harvested from the submitted Excel files. Primary metadata is written to the database, other data written to JSON key-value pairs.

### Application programming interfaces (APIs)
APIs (a software intermediary that allows software applications to talk to each other) will be built to enable data sharing with other businesses.

## See also
* [Borehole dataset profile](https://github.com/geological-survey-of-queensland/gsq-borehole-profile)
* PPDM [What is a Well?](https://ppdm.org/ppdm/PPDM/Standards/What_is_a_Well/PPDM/What_is_a_Well.aspx)
* PPDM [International Petroleum Data Standards](https://ppdm.org/ppdm/PPDM/IPDS/PPDM/IPDS.aspx)
* GeoSciML [Borehole Class](http://docs.opengeospatial.org/is/16-008/16-008.html#285)
* GeoSciML Lite [Borehole View](http://docs.opengeospatial.org/is/16-008/16-008.html#403)
* [CoalLog Standard](https://ausimm.com/coal-log/)


## License
This code repository's content are licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), the deed of which is stored in this repository here: [LICENSE](LICENSE).


## Contacts
*System owner*:  
**Mark Gordon**  
Geological Survey of Quensland  
Department of Natural Resources, Mines and Energy  
Brisbane, QLD, Australia  
<mark.gordon@dnrme.qld.gov.au>  

*Author*:  
**David Crosswell**  
Enterprise Architect  
Cross-Lateral Enterprises   
<https://crosslateral.com.au>  
