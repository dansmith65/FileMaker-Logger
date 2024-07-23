# 2.0.0 #

released 2024-JUL-22

- Switch from Let-notation to JSON as the expected format of the raw log data.
- Remove LogItem table
- Update/improve UI adding various features which I'm going to try to list here



## 1.2.1 ##

released 2019-JAN-04

- bug fixes
	- JSON web viewer failed to parse JSON if it contained an array with a null value

detailed list of changes:
- layouts
	- modified
		- Log: Detail
			- update "JSON Web Viewer: JS" in text object off the visible area of the layout


## 1.2.0 ##

released 2018-JAN-26

- enhancements
	- improve JSON web viewer search feature:
		- improve UI
			- forward slash key will activate search input (when web viewer is active)
		- select prev/next found item
		- expand collapsed items to show selection, if needed


## 1.1.0 ##

released 2017-DEC-01

- bug fixes
	- json web viewer fails to load if any value is an array

- enhancements
	- add search to JSON web viewer via https://markjs.io

detailed list of changes:
- layouts
	- modified
		- Log: Detail
			- add search javascript text to layout
			- update css
				- font to monospace (font stack borrowed from stackoverflow)
				- increase line-height
				- remove line between each value
				- change color of null value to have more contrast
			- update html of web viewer
			- update js
				- search to only match full string


# 1.0.0 #

released 2015-JUN-03

- initial release
