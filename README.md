Bash scripts to run java applications in daemon mode
====================================================

Minimalistic bash scripts which can run (start and stop) java application in daemon mode.

You can run your Java app on remote server through SSH and app won't stop after SSH logout. Tested in Linux and Solaris.

Direct links to scripts:

 * [startup script](https://github.com/alexkasko/java-daemon/blob/master/src/main/app-dir/bin/java-daemon/start-daemon.sh)
 * [shutdown script] (https://github.com/alexkasko/java-daemon/blob/master/src/main/app-dir/bin/java-daemon/stop-daemon.sh)

Run included example
--------------------

 * download [example binaries](https://github.com/downloads/alexkasko/java-daemon/java-daemon-1.0-distr.tar.gz)
 * use `./bin/startup.sh` and `./bin/shutdown.sh` to start/stop the daemon
 * you may see app std output in `logs/std.out`
 * scripts may be run from any directory, `.pid` file always goes to app root

How does it work
----------------

 * runs jar with [nohup](http://en.wikipedia.org/wiki/Nohup) command
 * gets JVM process id and writes it's PID to `.pid` file
 * to shutdown sends TERM signal to PID from `.pid` file
 * process std out goes int `logs/std.out` file

Note: to get it work properly with Spring Framework based applications you should [register JVM shutdown hook for the Spring context](http://static.springsource.org/spring/docs/3.1.x/javadoc-api/org/springframework/context/support/AbstractApplicationContext.html#registerShutdownHook%28%29)

How to build example
--------------------

 * build project with `mvn clean package`
 * app root folder will be in `java-daemon/target/java-daemon-1.0-distr`

License information
-------------------

This project is released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)