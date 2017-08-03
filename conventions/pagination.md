# Pagination and list sorting

All top-level iBanFirst Fundraising API resources have support for bulk fetches - "list" API methods. By default, all these "list" methods will give you 50 items sorted by descendant creation date.

You can use pagination parameters to modify these default values and refine your search. All these parameters must be provided as GET parameters in the URL.

| Field 	| Type 	    | Description | Default |
|-----------|-----------|-------------|---------|
| page 	    | int 	| index of the page (start to 1) | 1 |
| per_page 	| int 	| number of items returned. | 50 |
| sort   	| String | Either sort items by creation date in descendant or ascendant way. | DESC |