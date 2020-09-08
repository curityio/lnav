# lnav Add-ons for the Curity Identity Server

[![Quality](https://img.shields.io/badge/quality-production-green)](https://curity.io/resources/code-examples/status/)
[![Availability](https://img.shields.io/badge/availability-source-blue)](https://curity.io/resources/code-examples/status/)

The Curity Identity Server logs various information in log files. To make it easier to view and navigate these logs, the tool [lnav](http://lnav.org) can be used. This tool provides a number of helpful features that make it easier to view and work with the server's logs, including:

* Syntax highlighting of log messages
* Automatic correlation of log messages when viewing multiple files concurrently 
* Filtering out messages that were logged below a certain log level
* Searching and querying log using SQL
* Live updates of newly added messages (simulating the behavior of `tail -f`)
* Easy navigation using regular expression searches, paging by time intervals
* much, much more

## Formats

lnav recognizes various log file formats out of the box, including generic formatting that makes it easier to work with the Curity Identity Server's logs. To make this even simpler, this repository includes custom formats which improve lnav's generic syntax highlighting. Currently, the formatters included are ones for the following log files:

* Server log
* Request log
* Audit log
* Cluster log
* Configuration Service log

## Installation

To install these formats, ensure that [lnav is installed](http://lnav.readthedocs.io/en/latest/intro.html#installation). Then, follow the [instructions in the lnav manual to install these formats](http://lnav.readthedocs.io/en/latest/formats.html#installing-formats). There are a few ways to do this. Specifically, the following will install the formats:

1. `lnav -i https://github.com/curityio/lnav.git`. This will clone this repository and also make the formats available. It will also make it possible to update the formats easily by executing `lnav -u`.

2. After cloning this repository, do either of these:

	A. Run `lnav -i $REPO_DIR/curity.json` (where $REPO_DIR is the directory created after cloning this repository).

	B. Make a directory under `$HOME/.lnav/formats` called `curity` and place `curity.json` in that directory.

Once this is done, the formats should be available and working. If they aren't [raise an issue](https://github.com/curityio/lnav/issues) or [ping us on Twitter](http://twitter.com/curityio).

## Using lnav

To help you get started using lnav together with the Curity Identity Server here are a few examples:

> lnav $IDSVR_HOME/var/log/audit.log

This example opens the audit log in lnav. Notice how this JSON file is formatted with syntax highlighting.

> $IDSVR_HOME/bin/idsvr | tee -i $IDSVR_HOME/var/log/server.log | lnav

This example starts the Curity Identity Server and tees the output to standard out and the file `$IDSVR_HOME/var/log/server.log`. If the log file isn't needed, the simpler version of this command would be `$IDSVR_HOME/bin/idsvr | lnav`.

> lnav $IDSVR_HOME/var/log/cluster.log

This command opens the cluster log file in lnav. This log file is very verbose and often not very interesting except when debugging cluster-related issues. To make it easier to see issues in this log file, with lnav running, type `:` and then type `set-min-log-level info` (note that tab completion is available).  This will reduce the log to just a handful of messages, making it easier to see the more important log messages.

## More Information

For more information about lnav, refer to the following sources:

* [lnav Web site](http://lnav.org)
* [Lnav documentation](http://lnav.readthedocs.io/en/latest/index.html)
* [lnav blog](http://lnav.org/blog/)
* [lnav forum](https://groups.google.com/forum/#!forum/lnav)

## License

These formats are licensed under the [MIT license](https://github.com/curityio/lnav/blob/master/LICENSE).

## Questions

For questions, contact Curity AB:

> info@curity.io
> https://curity.io


Copyright (C) 2016 Curity AB.


