# FileMaker-Logger

A modular open-source logging framework for [FileMaker](http://filemaker.com).


## Components

  - `Logger` module: Provide an interface for logging.
    - Call this module from any script you want to create a log entry from.
  - `Log Writer` modules: Save log data to a single destination.
    - Call Log Writers from the Logger module. 
  - `Log Viewer` modules: View log data.
    - Provide a user interface for viewing log data. 


## File List

  - `Log.fmp12`: Main file for this project.
    -  This file can be included with your current application to handle all your logging needs. It has been designed as both a self-standing logging application as well as an example file/documentation for the included Log-related modules.
  - `LogWriters` directory: Additional Log Writer modules.
