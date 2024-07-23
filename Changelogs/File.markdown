# 2.0.0 #

released 2024-JUL-22

- Switch from Let-notation to JSON as the expected format of the raw log data.
- move Logger module to ExampleApp file
- updated custom functions and moved them to ExampleApp file



# 1.0.0 #

released 2017-DEC-01

- The first release of this file did not include a separate version script for the file.

detailed list of changes:
- scripts
	- modified
		- updated JSON module to 1.0.6
- fields
	- modified
		- Log::id
			- don't validate unique
			  In a hosted (WAN) file with 120,000 records, doing this cut the log creation time almost in half.
