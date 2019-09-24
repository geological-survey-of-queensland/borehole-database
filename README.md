# GSQ Borehole Register

## Terminology

A borehole is a narrow shaft bored in the ground. A borehole may be constructed for many different purposes, including the extraction of water, liquids such as petroleum, or gases such as natural gas, as part of a geotechnical investigation, mineral exploration, temperature measurement, for geothermal installations, or for underground storage of unwanted substances, e.g. in carbon capture and storage.

Well, drillhole, and bore are synonyms of borehole.

## Background
 - Boreholes exist for a wide range of purposes, with varying lifecycles and actors.  
 - There are multiple systems of record for boreholes across government, e.g. [GSQ](https://www.business.qld.gov.au/industries/mining-energy-water/resources/geoscience-information/gsq), [RSH](https://www.business.qld.gov.au/industries/mining-energy-water/resources/safety-health), [OGIA](https://www.business.qld.gov.au/industries/mining-energy-water/resources/landholders/csg/ogia), [DES](https://www.des.qld.gov.au/).  
 - There are varying standards across commodity groups, e.g. [PPDM](https://ppdm.org) and [WITSML](http://docs.energistics.org/) for petroleum and gas, [GeoSciML](http://www.geosciml.org/) for mineral, [CoalLog](https://ausimm.com/coal-log/) for coal.  
 - The requirements for reporting and data submitted by industry vary under the different legislation and Acts.  

## The borehole register 

The Geological Survey of Queensland is creating a new register of boreholes to replace the existing MERLIN system.

The primary focus of the register is to record details of the borehole entity - the narrow shaft bored in the ground.

Borehole entities in borehole register can link to one or many datasets, e.g. wireline logs, cores and cuttings, geochemistry, etc. 

While the borehole entity is generalised, datasets can be specialised for particular commodity groups and purposes.

### Objectives of the borehole register

 1. Queensland Government knows the location, attributes and status of all boreholes in Queensland.  
 2. The register helps government to perform custodianship of the borehole as an asset throughout its lifecycle.   
 3. The register is a single, trusted system of record for all boreholes in Queensland.
 4. The register is integrated with data input mechanisms, data consumers, and data display systems. 

### What the register is not
The register is not a borehole data management system. There are multiple commercial systems that meet this need.  

## Derivation
The borehole register is derived from the following standards:

 - [PPDM](https://ppdm.org) for petroleum and gas
 - [GeoSciML](http://www.geosciml.org/) for mineral
 - [CoalLog](https://ausimm.com/coal-log/) for coal

## Data elements
| Data Element | Description | Rank |
|--|--|--|
|bore_id|A persistent identifier for the borehole.|--|
|bore_name|Unique name and/or number assigned to each borehole.|--|
|bore_alias|Names & identifiers that a well may otherwise be known as. Includes previous or alternate well identifiers assigned to the well by a regulatory agency.|--|
|purpose|The purpose for which the borehole was drilled, e.g. petroleum, CSG, water injection, water observation, etc.|--|
|sub_purpose|A narrower definition of the purpose.|--|
|drilling_method|A term from a controlled vocabulary indicating the drilling method used, e.g rotary air blast, auger, diamond core, air core, etc.|--|
|status|The status of borehole at the end of each activity, e.g. intended, cased and suspended, completed, on injection, on production, plugged and abandoned, suspended.|--|
|status_event|The event that triggered the status change, e.g. lodging of notice of intention to drill, lodging of well completion report.|--|
|status_date|The date of the status event.|--|
|origin_latitude|Angular distance in decimal degrees, east or west of the prime meridian. A negative value represents a west longitude.|--|
|origin_longitude|Angular distance in decimal degrees, north or south of the equator. A negative value represents a south latitude.|--|
|origin_elevation|Elevation of the depth datum used as a reference for other measured well or borehole points.|--|
|depth_datum|The point from which all depths are measured in a well or bore (depth reference datum). For example: kelly bushing (KB), rotary table (RT) or ground level (GL).|--|
|location_confidence|A quantifiable value in metres that represents the positional difference between a geospatial record and reality. See [Australian Map and Spatial Data  Horizontal Accuracy Standard 2009](https://www.icsm.gov.au/sites/default/files/Spatial_Data_Horizontal_Accuracy.pdf)|--|
|total_depth|Total or maximum measured depth of the borehole relative to the origin elevation.|--|
|azimuth|The angle (in degrees) of clockwise departure from true north to the borehole direction. |--|
|inclination|The angle (in degrees) at surface of borehole deviation away from the vertical. 0 degrees inclination is horizontal and -90 degree inclination is vertical (downward). GeoSciML uses a term from a controlled vocabulary indicating the inclination type of the borehole. Terms include vertical; inclined up; inclined down, horizontal.|--|
|surface_circumstance|A term from a controlled vocabulary indicating the named position relative to ground surface where the borehole commenced, e.g. natural ground surface, open pit floor, underground, offshore.|--|
|drill_start_date|Date the drilling operations commenced on the borehole, penetrating the ground surface.|--|
|drill_end_date|Date the drilling operations for the borehole was completed at the total or maximum measured depth of the borehole.|--|
|permit_type|The resource authority under which the borehole activity occurred.|--|
|permit_number|The resource authority under which the borehole activity occurred.|--|
|operator|The organisation responsible for commissioning the borehole (as opposed to actually drilling the borehole).|--|
|driller|The organisation responsible for drilling the borehole (as opposed to commissioning the borehole).|--|
|geometry|A geospatial representation of the borehole as a point, polygon, or 3D geometry. Where  borehole location in XYZ coordinates is not available, surrogate geometries can be used, e.g. permit geometry, block or sub-block, mapsheet.|--|

### Other data elements that require consideration for inclusion


## Data mapping
| Data Element | MERLIN | PPDM | GeosciML | CoalLog |
|--|--|--|--|--|
|bore_id| bore_no | uwi |-|-|
|bore_name | primary_bore_name |--| drillhole_id |borehole_name |
|bore_alias |secondary_bore_name<br>prev_bore_id|well_alias|-|-|
|purpose|bore_type_code|--|purpose|borehole_type<br>borehole_purpose_x|
|sub_purpose|bore_subtype_code|--|--|--|
|drilling_method| |--|drillingmethod|bit_type|
|status|--|--|--|borehole_status_x|
|status_date|status_date|--|--|--|
|status_event| |--|--|--|
|origin_latitude|--|--|location|easting|
|origin_longitude|--|--|location|northing|
|origin_elevation|--|--|elevation|--|
|depth_datum|elev_datum_code|--|borehole-elevation-crs|height_datum|
|location_confidence|loc_method_code<br>loc_accuracy|--|--|location_acc|
|total_depth|--|--|boreholelength?|total_depth|
|azimuth|--|--|--|azimuth|
|inclination|--|--|inclinationtype|inclination|
|surface_circumstance|--|--|startpoint|--|
|drill_start_date|spud_date|--|dateofdrilling|drill_date|
|drill_end_date|completion_date|--|dateofdrilling|complete_date|
|permit_type|tenure_type|--|--|lease_no|
|permit_number|tenure_no|--|--|lease_no|
|operator|operator_code|--|operator|--|
|driller|--|--|driller|drill_company|
|geometry|--|--|--|--|


## See also
* TBA


## Files
* TBA


## License
This code repository's content are licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), the deed of which is stored in this repository here: [LICENSE](LICENSE).


## Contacts
*Vocabularies owner*:  
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
