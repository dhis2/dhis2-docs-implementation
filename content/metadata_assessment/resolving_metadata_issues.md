# Addressing common metadata issues

- Assessment tool provides list of metadata objects
- names useful when working in UI
- IDs useful when working direct


## Overall approach
- Use UI (Maintenance), API or Import/export app - helps avoid mistakes and unintentional 
- Don't use SQL/backend unless strictly necessary


## Batch edits
- removing large amounts of trailing/leading spaces
- adding/removing prefix

Default approach: fetch json from API, edit, import with import/export app in merge mode


## Deleting metadata
- guidance for "batch" deleting
- guidance for deleting objects with dependecies

Default approach: fetch json from API based on assessment UIDs, import with import/export app in delete mode

### Data elements with data vallues [if deleting ]
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


### Duplicate defaults


### Category issues



## Appendix: Useful tools

- browser extension for json formatting (for working with API)
- text editor with: 
	- support for json formatting and syntax highlighting
	- good search/replace functionality (ideally with regex support)
