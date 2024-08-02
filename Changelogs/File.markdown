### 2.0.2 ###

released 2024-AUG-02

detailed list of changes:
scripts
	modified
		Log Viewer module
			- update from 2.1.0 to 2.1.1


### 2.0.1 ###

released 2024-JUL-23

detailed list of changes:
layouts
	modified
		Home
			- switch location of "hide" and "view log" buttons
			- hide the "view log" button when it can't be used
scripts
	modified
		Log Viewer module
			- update from 2.0.0 to 2.1.0


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
