# Addressing common metadata issues
This section provides guidance and examples of addressing common metadata-related issues.
The guidance is useful in particular for addressing metadata issues identified using the 
[Metadata assessment tool](), but some of the approaches may also be useful more generally. 
The tool can output detailed lists of potentially problematic metadata objects as a CSV file, 
generally IDs and names. The names are useful in particular to find objects in the DHIS2 
user interface (UI), whilst the IDs are better if using the outputs to make API queries for example. 

Creating or modifying metadata (deleting, updating, adding) in DHIS2 can be done by different
means, i.e. via the user interface (Maintenance app), through export/import, via the API, 
or directly in the PostgreSQL database. 

This is thus the order we recommend to follow, from the safest to the highest risk.3
1. use the DHIS2 user interface, i.e. Maintenance App
2. use the Web API to export metadata, modify it in a text editor, and import via the API or Import/Export App
3. use a script that communicates with the DHIS2 API
4. use SQL directly in the database


In general, *none* of the procedures described in this guide should be used in a production
instance of DHIS2 until it has been tested throughly in a development or staging instance.
Depending on the changes being made, you should either perform the changes in a development/
staging server and then migrate the changes to the production instance, or first test
the changes in a staging environment and then replicating them exactly in the production 
instance. It is *very important* that the staging/development instance is a recent copy of
the production database - ideally a new copy should be as the first step of any corrections.

## Editing metadata
The metadata assessment may identify several issues that requires editing of metadata. 
Examples include objects that are not grouped (such as data elements not in  data element
group) or object with leading, trailing or double spaces. Some alternative approaches to 
correcting such issues are provided below.

### DHIS2 Maintenance App
As far as possible, metadata changes should be performed in the Maintenance App within DHIS2.
The Metadata assessment tool can provide a list with the names of objects that may require
work, for example objects with trailing spaces or objects that should be considered for
removal.

### Using the API and a text editor
- value type check?
- adding/removing prefix

fetch json from API, edit, import with import/export app in merge mode

API object filter for leading, trailing and double spaces:
`?filter=name:ilike$:%20&filter=name:$ilike:%20&filter=name:ilike:%20%20&rootJunction=OR`

### SQL


## Deleting metadata
- guidance for "batch" deleting
- guidance for deleting objects with dependecies

Default approach: fetch json from API based on assessment UIDs, import with import/export app in delete mode

### Data elements with data values [if deleting ]
- export and import? will not handle values in audit table(?)
- SQL


### Users with associated metadata
- don't delete users, but disable(?) - might not be good recommend from privacy perspective
- ? 


## De-duplication [TBC if doing this]
- manual
- some types [categories etc] can be deleted with deduplication tool


## Special cases
- some advice on specific issues identified in assessment tool, which do not fit in overall categories above
- not a comprehensive guide, as these issues are often too database specific to provide an exact "procedure"

### Geo coordinate issues


### Sort order 


### Duplicate defaults


### Category issues



## Appendix: Useful tools
- SQL queries for identifying dependencies
- browser extension for json formatting (for working with API)
- text editor with: 
	- support for json formatting and syntax highlighting
	- good search/replace functionality (ideally with regex support)
