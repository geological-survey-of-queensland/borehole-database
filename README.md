# Boreholes in GSQ

## Terminology

A borehole is a narrow shaft bored in the ground. A borehole may be constructed for many different purposes, including the extraction of water, liquids such as petroleum, or gases such as natural gas, as part of a geotechnical investigation, mineral exploration, temperature measurement, for geothermal installations, or for underground storage of unwanted substances, e.g. in carbon capture and storage.

A well, a drillhole, and a bore are synonyms of borehole.

## Background
 - Boreholes exist for a wide range of purposes, with varying lifecycles and actors.  
 - There are multiple systems of record for boreholes across government, e.g. [GSQ](https://www.business.qld.gov.au/industries/mining-energy-water/resources/geoscience-information/gsq), [RSH](https://www.business.qld.gov.au/industries/mining-energy-water/resources/safety-health), [OGIA](https://www.business.qld.gov.au/industries/mining-energy-water/resources/landholders/csg/ogia), [DES](https://www.des.qld.gov.au/).  
 - There are varying standards across commodity groups, e.g. [PPDM](https://ppdm.org) and [WITSML](http://docs.energistics.org/) for petroleum and gas, [GeoSciML](http://www.geosciml.org/) for mineral, [CoalLog](https://ausimm.com/coal-log/) for coal.  
 - The requirements for reporting and data submitted by industry vary under the different legislation and Acts.  

## The borehole register 

The Geological Survey of Queensland is creating a new register of boreholes to replace the existing MERLIN system.

The primary focus of the register is the borehole entity - the narrow shaft bored in the ground.

Borehole entities in borehole register can link to multiple datasets with specialisation across commodity groups and purposes.

### Objectives of the borehole register

 1. Queensland Government knows the location, attributes and status of all boreholes in Queensland.  
 2. The register helps government to perform custodianship of the borehole as an asset throughout its lifecycle.   
 3. The register is a single, trusted system of record for all boreholes in Queensland.

### What the register is not
The register is not a borehole data management system. There are multiple commercial systems that meet this need.  

### Minimum mandatory information:
|Data Element|Definition|
|--|--|
|Bore ID|A persistent identifier|
|Bore name|  |


1. A persistent identifier, 
2. A name with aliases
  - a borehole may be known by other names and identifiers, both from company and regulatory agencies

A location
Geographic coordinates 
Surface location in X Y Z 
Within permit boundary
Mapsheet
Block/sub-block


## Derivation
The borehole register is derived from the following standards:

 - [PPDM](https://ppdm.org) for petroleum and gas
 - [GeoSciML](http://www.geosciml.org/) for mineral
 - [CoalLog](https://ausimm.com/coal-log/) for coal

## Data mapping
| Data Element | MERLIN | PPDM | GeosciML | CoalLog |
|--|--|--|--|--|
|bore_id| bore_no | uwi | |
|bore_name | primary_bore_name | | drillhole_id |borehole_name |
|bore_alias |secondary_bore_name<br>prev_bore_id|well_alias|-|
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

