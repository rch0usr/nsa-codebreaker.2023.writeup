# Task 1 - Find the Unknown Object - (General programming, database retrieval)

The US Coast Guard (USCG) recorded an unregistered signal over 30 nautical miles away from the continental US (OCONUS). 
NSA is contacted to see if we have a record of a similar signal in our databases. 
The Coast guard provides a copy of the signal data. 
Your job is to provide the USCG any colluding records from NSA databases that could hint at the object’s location. 
Per instructions from the USCG, to raise the likelihood of discovering the source of the signal, 
they need multiple corresponding entries from the NSA database whose geographic coordinates are within 1/100th of a degree. 
Additionally, record timestamps should be no greater than 10 minutes apart.

Downloads:
file provided by the USCG that contains metadata about the unknown signal ([USCG.log](https://nsa-codebreaker.org/files/task1/USCG.log?1707529470))
NSA database of signals ([database.db](https://nsa-codebreaker.org/files/task1/database.db?1707529470))

Prompt:
Provide database record IDs, one per line, that fit within the parameters specified above.

`cat UCSG.log`  
This will output the contents of the file, the data inside is what you'll use to find
corrosponding entries within `database.db`
`sqlitebrowser --table location database.db`  
In sqlite find the latitude and longitude with the provided data and submit it in the format requested  
A program can be created to read the UCSH.log and database.db files to find the latitude and logitude
which most closley matches the provided information.
