# Specifications

## Technology Stack

- Database: Apache Couchdb	
- Middleware: (Node) Express, couchdb-node
- Utility: (Node) body-parser, 
- Frontend: (Node) EJS template engine, HTML5 
 
## Design

These specifications are derived from a spreadsheet that currently 
 works as an inventory, with some additions
 
> Data is like garbage - you'd better know what you're 
> going to do with it before you collect it
>
> Anon
 
### Iterative Design Specifications

### Item CLasses

- Devices
	- Laptops
	- Desktops
	- Tablets
	- Phones
	- Other 
- Stationery
- Office furniture
- Tools 
- Connectors
- Miscellaneous technology
- Miscellaneous general

### Common to all Item Classes

NB 'req' field = 'required' refers to mandatory fields in frontend forms, not the Database

| field	   | req | datatype | field description | rules / comments |
|----------|---|----------|-------------------|------------|
| _id	   | Y | string  | a unique id issued by the db |
| desc     | Y | string | Description | e.g "Paperclips" |
| date     | Y |  string | date entered into db / last checked | YYYY-MM-DD, [link](https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/datefun.html#date-formats)
| qty	   | Y |int | quantity | 
| item_class | Y | string | device, tool, stationery, furniture, misc_tech, misc_general |
| stored   | N | string |Storage location | rule: is item either has a storage location AND/OR is in use |
| in_use   | N | Boolean |	| RULE: item either has a storage location AND/OR is just "in use" |
| maker    | N | string | Manufacturer |
| model    | N | string | retail name |
| product_id | N | string | manufacturer ID |
| working  | N | string | Yes / No / Unknown |
| pending_donation_sale | N | Boolean |
| donated  | N | Boolean | keep records but remove from current view |
| comments | N | string |Additional info on Item |

### Specific to Devices

| field  | nested field |req| datatype | field description | rules / comments |
|--------|--------------|---|----------|-------------------|------------|
| item_class | 	        | Y | string   |                   | RULE: item_class=device |
| owner  |		        | Y |          |  
|        | name         | Y | string   | TechMate or client |
| 	     | email        | N | string   |
|        | phone        | N | string   |
| alt_id |              | Y | string   | unique human-friendly indentifer or name for item | e.g. "Penny", "NC8051" |
| form_factor |         | Y | string   | laptop, desktop, tablet, phone, other |
| os     |              | N |          | Operating System |
|        | update_date  | N | string   | YYYY-MM-DD; last OS update time |
| maintenance |		    | N |  	      | maintenance status | RULE: owner is TechMate |
|        | pending      | Y | Boolean  | requires maintenance job |
|        | date_logged  | Y | string   | YYYY-MM-DD format | 
|		 | job_desc     | Y | string   | Full description of maintenance job(s) |
|		 | sanitise     | Y | Boolean  | remove all personal data |
|		 | sanitised    | Y | Boolean  | all personal data removed | e.g. factory reset - put details jobs_desc | 
|		 | audit 	    | Y | Boolean  | verify data security ok |
|		 | audited      | Y | Boolean  | verify data security ok |
|		 | debloat      | Y | Boolean  | remove unnecessary apps |
| client_job |          | N |          |                   | RULE: owner is a client
|        | pending      | Y | Boolean  | requires maintenance job |
|        | date_logged  | Y | string   | YYYY-MM-DD format | date client submitted for fix |
|        | date_due     | Y | string  | YYYY-MM-DD format | estimated client pickup  |
|		 | problem_desc | Y | string  | general description | from client| | 
|		 | job_desc     | Y | string   | Full assessment of maintenance job(s), and progress |
|        | completed    | Y | Boolean  | 
|		 | outcome      | Y | string   | description of work done and result | RULE: dependent on completed=true
|		 | success	    | Y | string   | Yes / Partial / No | RULE: dependent on completed=true

### Specific to Connectors

| field  | nested field | nested field |req| datatype | field description | comments |
|--------|--------------|--------------|---|---------|-------------------|------------|
| item-class |          | 			   | Y | string  |                   | RULE:item-class==connector |          
| 		 | type			|              | Y | string  | power / data / AV / audio | RULE:only 4 options; AV include video only e.g. VGA |  
|        | length       |              | N | string  |                   | in approx. metres
|	     | terminal_1   |              | N | 		 |                   | CONVENTION: computer end when relevent
|        | 				| standard     | N | string  | e.g. USB Type-A   |
|        |              | gender       | N | string  | Male / female     | 
|	     | terminal_2   |              | N | 		 |                   | CONVENTION: smartphone end when relevent
|        | 				| standard     | N | string  | e.g USB Type-micro|        
|        |              | gender       | N | string  | Male / female     |

		 
    
