# Design Specifications

These specifications are derived from a spreadsheet that currently 
 works as an inverntory, with some additions
 
## Item CLasses

- Stationery
- Office furniture
- Office equipment
- Connectors
- Miscellaneous technology
- Miscellaneous general
- devices
	- Laptops
	- Desktops
	- Tablets
	- Phones
 

### Common to all Item Classes


| field		| field description            |
|-----------|-------------------------------|
| _id |  a unique id issued by the db |
| date | date entered into db / last checked |
| qty | quantity |
| Item Class |  device, tool, misc_tech, stationery, furniture, misc_general |
| Desc | Description |
| Maker | Manufacturer |
| Model | retail name |
| Storage | Storage location |
| Working State | Yes / No / Unknown |
| In Use | Yes / No  i.e. currently being used in the office | 
| Comments | Additional info on Item |

### Specific to Devices

| field     | field description |
|-----------|-------------------|
| alt_id | unique indentifer or name for item |
| form_factor | laptop, desktop, tablet, phone, other |
| req_main | Yes / No requires maintenance job |
| OS | Operating System |

 
    
