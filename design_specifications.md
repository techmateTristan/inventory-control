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


| field	|req| datatype | field description | additional |
|-------|---|----------|-------------------|------------|
| _id	 | Y | string  | a unique id issued by the db |
| date   | Y |  string | date entered into db / last checked | YYYY-MM-DD, [link](https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/datefun.html#date-formats)
| qty	 | Y |int | quantity | 
| item_class | Y | string | device, tool, misc_tech, stationery, furniture, misc_general |
| stored | Y | string |Storage location |
| desc   | Y | string | Description | e.g "Paperclips" |
| maker | N | string | Manufacturer |
| model | N | string | retail name |
| product_id | N | string | manufacturer ID |
| working | N | string | Yes / No / Unknown |
| req_main |  N | Boolean | requires maintenance job |
| main_desc | N | string | Description of maintenance job |
| main_date | N | string | maintenance job due date YYYY-MM-DD |
| in_use | N | Boolean | in office or remote | 
| pending_donation_sale | N | Boolean |
| comments | N | string |Additional info on Item |

### Specific to Devices

| field  |req| datatype | field description | additional |
|--------|---|----------|-------------------|------------|
| owner_name | Y | string | techmate or client |
| owner_email | N | string |
| owner_phone | N | string |
| alt_id | Y | string | unique human-friendly indentifer or name for item | e.g. "Penny", "NC8051" |
| form_factor | Y | string | laptop, desktop, tablet, phone, other |
| os | N | string |Operating System |
| os_update_date | N | string |YYYY-MM-DD; last OS update time |
| sanitized | N | Boolean | data wipe performed re. personal data |
| reset | N | Boolean | Factory Reset or bloatware removed |
 

 
    
