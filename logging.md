Logging and Monitoring
======================

A typical system or application performs many operations (e.g. creates objects,
executes processes and threads, connects to a database etc.) and in the absence
of a logging mechanism, developers are basically flying blind while trying to
get things working correctly.

Without proper logging, development is done based on guesswork and intuition -
with no real indication of what's happening.

There are several types of logging: application log, security log, event log,
transaction log and more.

When done right, logs will help you to better understand the activity of the
system and to debug and diagnose problems.


General
-------
* Create consistent logging standards, to be applied through all processes and
  modules.
* Utilize a **configurable** logging environment or framework.
  Use industry standard logging frameworks and modules (but avoid vendor lock).
* Pay attention to the differences between logging tasks (e.g. security and
  audit logs, event logs etc.) - some of them may require a slightly different
  approach. For example: audit logs are used to monitor activities and attacks
  while application logs may be used for debugging.
* Cheese the right log verbosity (i.e. log level) for each environment.
  Your chatty DEV logger may not be suitable on PROD servers (see **Log Levels**
  section below).
* Make sure to always filter out sensitive data (e.g. passwords, private info etc.)


Format
------
* Log messages should be clear and provide useful information. They should also
  add some context (i.e. which server, process, module, function triggered
  the message).
* Logging format should be readable and clear to humans (typically developers).
  It should also be structured and parseable by machines.
* Messages should answer the WHEN, WHERE, WHO and WHAT questions:

  **WHEN** - Event timestamp. Note that server timestamp may be different from
  the users local date and time.

  **WHERE** - Server/application/service identifiers, module, function etc.

  **WHO** - IP, User, device, OS, user id (if authenticated).

  **WHAT** - Event type, category, description.

* Use single line log messages - do not spread a single message over several lines.
* When possible, use key-val pairs (preferably using an industry standard format
  such as JSON).
* Don't mix various/different message formats in the same log file (as it
  makes log aggregation and analytics harder).
* Properly format event timestamps. Time should include a 4-digits year and be
  in microseconds granularity for accuracy. Include timezone details (opt for
  GMT/UTC).
* Start each message with the timestamp.


Mechanism and Performance
-------------------------
* Prefer logging to local files (not affected by network problems).
* Logging into a database is a valid option, but may slow down your processes.
  When logging into a database, schedule a maintenance plan to avoid bloated tables.
* When logging to files, devise a file rotation policy.
* Loggers should have as little impact as possible on your running processes -
  use fault-tolerant protocols and don't allow loggers to block, slow down or
  fail your processes (in case of log failure).
* Use unique identifiers for each log entry. this may come handy during debugging.
* Aggregate and analyze logs using standard industry tools (e.g. Logstash, Graylog).
* When running in production, automate alerting (on WARNINGs, ERRORs and
  CRITICAL events).


Stats
-----
* Categorize and group log messages. This will allow you to efficiently
  aggregate log messages (and collect system statistics).
* **Know your bottlenecks** - collect performance metrics (start, finish, duration)
  using a standard time-series analytics tool (e.g. Grafana, Statsd).


Log levels/Severity
-------------------
* Use an appropriate log level. This should be a part of the logging configuration.
* Standard log levels (additional, custom, levels may also be defined):

  **TRACE** - Should never be used in production environments (used in
  development to trace bugs).

  **DEBUG** - Typically used during debugging or when diagnosing problems
  (surprise! surprise!). Detailed logging that should not be used in production
  during the normal mode of operation.

  **INFO** - Informative messages. Things are working as expected (User input,
  scheduled processes starting etc.)

  **NOTICE** - Notable events that are not errors but may require special handling.

  **WARNING** - Indicates a possible problem [that might occur in the near future].
  Currently the process can proceed without failure.
  For example: process duration takes too long, memory is reaching it's limit.

  **ERROR** - An error has occurred and the process was not able to proceed.
  Log all error related context.

  **FATAL/CRITICAL** - All hell broke loose. A serious error. You should probably
  be panicking right now. Use scarcely. Typically indicates the termination of
  the process/application.


CREDITS:
-------

Splunk Logging best practices
http://dev.splunk.com/view/logging/SP-CAAAFCK

Write Logs for Machines, use JSON
https://journal.paul.querna.org/articles/2011/12/26/log-for-machines-in-json/

30 best practices for logging at scale
https://www.loggly.com/blog/30-best-practices-logging-scale/

Logging Cheat Sheet
https://www.owasp.org/index.php/Logging_Cheat_Sheet

Python Logging 101
http://plumberjack.blogspot.co.il/2009/09/python-logging-101.html
