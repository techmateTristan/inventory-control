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
	- Other 

### Common to all Item Classes


| field		| field description            | additional  |
|-----------|------------------------------|-------------|
| _id |  a unique id issued by the db |
| date | date entered into db / last checked |
| qty | quantity |
| item_class |  device, tool, misc_tech, stationery, furniture, misc_general |
| desc | Description |
| maker | Manufacturer |
| model | retail name |
| product_id | manufacturer ID |
| stored | Storage location |
| working_state | Yes / No / Unknown |
| req_main | Yes / No | requires maintenance job |
| main_desc | Description of maintenance job |
| main_date | maintenance job due date |
| in_use | Yes / No | in office or remote | 
| pending_donation_sale | Yes / No |
| comments | Additional info on Item |

### Specific to Devices

| field     | field description | additional |
|-----------|-------------------|------------|
| owner_name | techmate or client |
| owner_email | |
| owner_phone | | 
| alt_id | unique indentifer or name for item | "Penny", "NC8051" |
| form_factor | laptop, desktop, tablet, phone, other |
| os | Operating System |
| os_update_date | last OS update time |
| sanitized | Yes / No (data wipe performed) | re: personal data |
| reset | Factory Reset or bloatware removed |
 

 
    
