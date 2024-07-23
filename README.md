# FileMaker-Logger

A modular open-source logging framework for [Claris FileMaker](https://www.claris.com/filemaker/).


## Components

  - `Logger` module: Provide an interface for logging.
    - Call this module from any script you want to create a log entry from.
  - `Log Writer` modules: Save log data to a single destination.
    - Call Log Writers from the Logger module. 
  - `Log Viewer` modules: View log data.
    - Provide a user interface for viewing log data. 


## File List

  - `Log.fmp12`: File that you can host on your server to save log data to.
    - It has been designed as both a self-standing logging application as well as an example file/documentation for the included Log-related modules.
  - `ExampleApp.fmp12`: This holds the code that should be copied into your FileMaker file.
  - `LogWriters` directory: Additional Log Writer modules.


## Getting Started

Most documentation for this project exists in READ ME scripts:

  - File Module > READ ME
  - Modules > Logger > Logger: READ ME
  - Modules > Log Writer: FM > Log Writer: FM: READ ME
  - Modules > Log Viewer: FM > Log Viewer: FM: READ ME

Consider using additional [LogWriters](LogWriters). View the READ ME scripts in each of those files if you choose to implement one.


## Log Level

By including a log level with each call to the Logger module, it allows you to write your scripts with debugging code right from the start and leave that debugging code in your script while in production. By using the `LogWriteEnabled` function, you can reduce the overhead imposed by this logging method on code in production by only calling the `Logger` module if logs of the specified level are supposed to be saved.

An example of this implementation can be seen in the [PluginChecker.fmp12](https://github.com/dansmith65/PluginManager/blob/master/PluginChecker.fmp12?raw=true) file from my [PluginManager](https://github.com/dansmith65/PluginManager) project. Open the `~PluginChecker: Test Plugin ( ... )` script from the `Modules` > `PluginChecker` > `PluginChecker: Private` folder. That script uses the `$$PLUGINCHECKER.LOGLEVELTOWRITE` global variable instead of the `LogWriteEnabled` custom function, but the concept is the same. It also calls the local `PluginChecker: Config: Create Log Entry` script instead of directly calling the `Logger` module, which allows users to configure logging (or not), however they choose.

In the `~PluginChecker: Test Plugin ( ... )` script, you will see many calls to the `...Create Log Entry` script, but most of them are only called if the log level to write is defined as 4 (debug) or 5 (trace). This means that `$$PLUGINCHECKER.LOGLEVELTOWRITE` can be set to 1-3 while in production and the module would only create a single log entry and only if it encountered an error. Or, while developing/debugging an issue, you can set `$$PLUGINCHECKER.LOGLEVELTOWRITE` to 4 or 5 and get many log entries which explain every major decision the script made, along with the data that existed at the time that decision was made.

When using this method of debugging, you don't have to remove your debugging code before going to production mode. That also means you don't have to add that code again when you run into issues while in production. It's also platform agnostic, this method of debugging works just as well for a script being run on the server as it does for one run in FileMaker Pro, or Pro Advanced.


## Recommended log levels and when to use them

### 1 Error

The system is in distress, customers are probably being affected
(or will soon be) and the fix probably requires human intervention.
The "2AM rule" applies here- if you're on call, do you want to be
woken up at 2AM if this condition happens? If yes, then log it as
"error".

### 2 Warn
An unexpected technical or business event happened, customers may be
affected, but probably no immediate human intervention is required. On
call people won't be called immediately, but support personnel will
want to review these issues asap to understand what the impact is.
Basically any issue that needs to be tracked but may not require
immediate intervention.

### 3 Info
Things we want to see at high volume in case we need to forensically
analyze an issue. System lifecycle events (system start, stop) go here.
"Session" lifecycle events (login, logout, etc.) go here. Significant
boundary events should be considered as well (e.g. database calls,
remote API calls). Typical business exceptions can go here (e.g. login
failed due to bad credentials). Any other event you think you'll need
to see in production at high volume goes here.

### 4 Debug
Just about everything that doesn't make the "info" cut. Any message
that is helpful in tracking the flow through the system and isolating
issues, especially during the development and QA phases. We use "debug"
level logs for entry/exit of most non-trivial methods and marking
interesting events and decision points inside methods.

### 5 Trace
For extremely detailed and potentially high volume logs that you don't
typically want enabled even during normal development. Examples
include dumping a full object hierarchy, logging some state during
every iteration of a large loop, etc.
