
The logging module in Python is a powerful built-in module so you can quickly add logging to your application.
import logging

#### Log Level

There are 5 different log levels indicating the serverity of events. By default, the system logs only events with level WARNING and above

* DEBUG: Detailed information, typically of interest only when diagnosing problems.

* INFO: Confirmation that things are working as expected.

* WARNING: An indication that something unexpected happened, or indicative of some problem in the near future (e.g. ‘disk space low’). The software is still working as expected.

* ERROR: Due to a more serious problem, the software has not been able to perform some function.

* CRITICAL: A serious error, indicating that the program itself may be unable to continue running.


#### Configuration

With basicConfig(**kwargs) you can customize the root logger. The most common parameters are the level, the format, and the filename. 

#### Logging in modules and logger hierarchy

Best practice in your application with multiple modules is to create an internal logger using the __name__ global variable. This will create a logger with the name of your module and ensures no name collisions. 

* The logging module creates a hierarchy of loggers, starting with the root logger, and adding the new logger to this hierarchy. If you then import your module in another module, log messages can be associated with the correct module through the logger name. Note that changing the basicConfig of the root logger will also affect the log events of the other (lower) loggers in the hierarchy.


#### LogHandlers

Handler objects are responsible for dispatching the appropriate log messages to the handler's specific destination. For example you can use different handlers to send log messaged to the standard output stream, to files, via HTTP, or via Email. Typically you configure each handler with a level (setLevel()), a formatter (setFormatter()), and optionally a filter (addFilter()). See https://docs.python.org/3/howto/logging.html#useful-handlers for possible built-in handlers. Of course you can also implement your own handlers by deriving from these classes.


#### Rotating FileHandler

When you have a large application that logs many events to a file, and you only need to keep track of the most recent events, then use a RotatingFileHandler that keeps the files small. When the log reaches a certain number of bytes, it gets "rolled over". You can also keep multiple backup log files before overwriting them.

*   roll over after 2KB, and keep backup logs app.log.1, app.log.2 , etc.
    handler = RotatingFileHandler('app.log', maxBytes=2000, backupCount=5)


#### TimedRotatingFileHandler

If your application will be running for a long time, you can use a TimedRotatingFileHandler. This will create a rotating log based on how much time has passed. Possible time conditions for the when parameter are: - second (s) - minute (m) - hour (h) - day (d) - w0-w6 (weekday, 0=Monday) - midnight

*   This will create a new log file every minute, and 5 backup files with a timestamp before overwriting old logs.
    handler = TimedRotatingFileHandler('timed_test.log', when='m', interval=1, backupCount=5)


    