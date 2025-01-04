---
title: 'Log4net Extended Tutorial'
date: 2011-10-16T21:48:00.001-05:00
draft: false
url: /2011/10/log4net-extended-tutorial.html
---

Logging is one of the most effective debugging and troubleshooting techniques although some engineers claim that it is not that helpful or it will slow the application. My experience with it is always positive.

I use [log4net](http://logging.apache.org/log4net/index.html) from the [Apache Software Foundation](http://www.apache.org/) as my logging layer for .Net applications. log4net is available [here](http://logging.apache.org/log4net/download.html) as a zip archive.

##### Hello World Example \[uses _BasicConfigurator_\]

1.  Download log4net from [here](http://logging.apache.org/log4net/download.html).
2.  Open Visual Studio and create a new Console application project.
3.  Add to the project a reference to the \\bin\\net\\2.0\\release\\log4net.dll assembly in the log4net distribution.
4.  Modify your Main() method like so:

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

```
 1: using System;
```  
  
```
 2: namespace ConsoleApplication1
```  
  
```
 3: {
```  
  
```
 4:    class Program
```  
  
```
 5:    {
```  
  
```
 6:        static void Main(string\[\] args)
```  
  
```
 7:        {
```  
  
```
 8:            log4net.Config.BasicConfigurator.Configure();
```  
  
```
 9:            log4net.ILog log = log4net.LogManager.GetLogger(typeof(Program));
```  
  
```
 10:  
```  
  
```
 11:            log.Debug("Hello World!");
```  
  
```
 12:            log.Info("Just info.");
```  
  
```
 13:            log.Warn("careful this is a warning.");
```  
  
```
 14:            log.Error("Bad news: Error occurred.");
```  
  
```
 15:            log.Fatal("Here is the end.");
```  
  
```
 16:        }
```  
  
```
 17:    }
```  
  
```
 18: }
```  

  
  

Compile and run the application, and you'll see output to the console like so:

  
  

[![log4net1](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh6-4Tq5IT4B2tG1nFdx-pz20fovXidsk1RzU4wdsRLE3KmoSSk7FSK8b0JfPaxDALtrQv2A1Q3_SuBAnepLYE3mBrgjohm5Jc5cuws9Tbtrk3-k1oLOPDJO1199a-mhMQ1VrHbDaAstg/?imgmax=800 "log4net1")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiwIpnot_ZIeySGNfbHxnVVx-3_tr4JeHU49qBDYR69dtU46PxIplfM79yC7w9NQ2P4rVtOxUUcVqc_8SV6a4xjglNW8KzC69dRKcffzFRdEfV4NzkCr3z5qU2yJvvTwJEzPJEsSKikLQ/s1600-h/log4net14.jpg)

  
  

In the Hello World example we configured log4net in the most basic way possible just to get started. Using the BasicConfigurator (line 8) will cause log4net to output log entries to the console using the default layout. Line 9 requests a _logger_ from the LogManager object.  Logger objects implement the ILog interface, which is what your application will use to instrument itself and percolate log entries.

  
  

Lines 11-15 use the logger to log a few statements with various _severity levels_.  log4net defines 5 such levels:

  
  

  
*   **Debug**: fine-grained statements concerning program state, typically used for debugging;
  
  
*   **Info**: informational statements concerning program state, representing program events or behavior tracking;
  
  
*   **Warn**: statements that describe potentially harmful events or states in the program;
  
  
*   **Error**: statements that describe non-fatal errors in the application; this level is used quite often for logging handled exceptions;
  
  
*   **Fatal**: statements representing the most severe of error conditions, assumedly resulting in program termination.
  

  
  

##### XML Configurator

  
  

In the previous example we used the BasicConfigurator. If we just changed the configurator to XmlConfigurator and run the application you will get the following output error:

  
  

log4net:ERROR XmlConfigurator: Failed to find configuration section 'log4net' in  
  
the application's .config file. Check your .config file for the <log4net> and <  
  
  
configSections> elements. The configuration section should look like: <section n  
  
  
ame="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler,log4net" /  
  
  
\>

  
  

This error resulted because XMLConfigurator relies on an XML document to supply configuration for log4net. The static Configure method have 10 overloads to accept the XML configuration from a file, stream, URI, or an XmlElement object. The parameterless overload of the method we used instructs log4net to load the XML from the application’s configuration file. Since our application doesn’t contain any configuration files (till now), the Configure method returned the above error.

  
  

To overcome this error, add Application Configuration File to the project and add the following XML configuration:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <configuration\>  
```  
  
```
 2:  <configSections\>  
```  
  
```
 3:    <section name\="log4net" type\="log4net.Config.Log4NetConfigurationSectionHandler, log4net"/>  
```  
  
```
 4:  </configSections\>  
```  
  
```
 5:  
```  
  
```
 6:  <log4net\>  
```  
  
```
 7:    <appender name\="ConsoleAppender" type\="log4net.Appender.ConsoleAppender"\>  
```  
  
```
 8:      <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 9:    </appender\>  
```  
  
```
 10:  
```  
  
```
 11:    <root\>  
```  
  
```
 12:      <level value\="ALL" />  
```  
  
```
 13:      <appender-ref ref\="ConsoleAppender" />  
```  
  
```
 14:    </root\>  
```  
  
```
 15:  </log4net\>  
```  
  
```
 16: </configuration\>  
```  

  
  

Compile and run, you will see output changed to be like so:

  
  

[![log4net2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi_qIbf2EmNKW45-1c85_ITkni2Q3ZkmHvd3wisOUm4Bc2_AUlrf-JT29A4v_kRq2U9ZaZnl9iUBth50WOtjertpe2XcijxfjbGdU5iUmeTwGSyBjxInIFE6jiSa2vGzahAxmMRwbO76w/?imgmax=800 "log4net2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhOxKiDXBtLuTTydXvRQjw5TsM4fQLirlKkbVagg46HHAo7LoHPmt5IiClS70ek9mhtAkXjQ7br6E2Cveiktsldqn47UCJpxlO0mZvpNE8RXzwoagT8AXQy2I-NtMEghzr2aaH-cUyiew/s1600-h/log4net26.jpg)

  
  

In addition to the Configure method, XmlConfigurator offers a static ConfigureAndWatch() method that accepts a FileInfo reference. ConfigureAndWatch() will monitor the XML configuration file and reconfigure log4net when a change is detected in this file.  This allows you to alter logging behavior while the application is running to fit your current troubleshooting requirements.

  
  

If we look at the application configurations file, the declaration of the log4net configuration section on line 3 is mandatory. The log4net configurations section \[lines 6-15\] consists of two sub-sections: _appender_ and _root._ log4net appender is the place where your application log entries end up (Console in our example). We will talk about appenders later. The root logger controls the general behavior of log4net.  In this example, the root logger is told to send everything to the console appender.

  
  

##### Taming log4net Output

  
  

In the previous examples we were logging all types of severity levels. If you want to filter the logging output to fit your application’s life current phase (development, production) or troubleshooting needs, you can just change the value of <level /> XML element in your app.config.  The level value instructs the logger of the minimum level at which log entries should be processed. It can be: ALL (everything is enabled), DEBUG (identical to ALL), INFO (everything except DEBUG), WARN (warn, Error, and Fatal), ERROR (Error and Fatal), FATAL (only Fatal), OFF (logging is disabled).

  
  

The Structure of log4net
------------------------

  
  

Before going further with log4net, let’s talk about its structure. log4net built using the layered approach, with four main components inside of the framework. These are Logger, Repository, Appender, and Layout.

  
  

The _Logger_ is the main component with which your application interacts. It is also the component that generates the log messages.

  
  

The _Repository_ is responsible for maintaining the logical organization of loggers inside the framework. Currently log4net only supported the hierarchical organization through `log4net.Repository.Hierarchy` namespace. If you want to extend log4net to implement new organization, you have to implement the `log4net.Repository.ILoggerRepository` interface or inherit class `log4net.Repository.LoggerRepositorySkeleton`. Almost all developers do not use any of these `Repository` classes; they only use the `LogManager` class to automatically manage the repositories and the loggers.

  
  

The _Appender_ is used to define the output medium that log statements will go for it at the end of the day. As the name suggests, these components append themselves to the Logger component and relay the output to an output stream. You can append multiple appenders to a single logger. There are several appenders provided by the `log4net` framework. If you want to write your own appender, you can start by inheriting the`log4net.Appender.AppenderSkeleton` class, which works as an adapter between your class and the `IAppender` interface. You can use _Appender Filters_ to filter logging events sent from appenders before processing it.

  
  

The _Layout_ component is used to display the final formatted output to the user. The output can be shown in multiple formats, depending upon the layout we are using. It can be linear or an XML file. The layout component works with an appender. There is a list of different layouts in the API documentation. You cannot use multiple layouts with an appender. To create your own layout, you need to inherit the`log4net.Layout.LayoutSkeleton` class, which implements the `ILayout` interface.

  
  

Appenders
---------

  
  

An appender is an object that persists your log messages someplace. In the table below a list of the appenders provided by log4net.

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

Appender

Description

AdoNetAppender

Appender that logs to a database.

AnsiColorTerminalAppender

Appends logging events to the terminal using ANSI color escape sequences.

AspNetTraceAppender

Appends log events to the ASP.NET TraceContext system.

BufferingForwardingAppender

Buffers events and then forwards them to attached appenders.

ColoredConsoleAppender

Appends logging events to the console colored.

ConsoleAppender

Appends logging events to the console.

DebugAppender

Appends log events to the Debug system.

EventLogAppender

Writes events to the system event log.

ForwardingAppender

This appender forwards logging events to attached appenders.

FileAppender

Appends logging events to a file.

LocalSyslogAppender

Logs events to a local syslog service.

MemoryAppender

Stores logging events in an array.

NetSendAppender

Logs entries by sending network messages using the NetMessageBufferSend native function.

OutputDebugStringAppender

Appends log events to the OutputDebugString system.

RemoteSyslogAppender

Logs events to a remote syslog daemon.

RemotingAppender

Delivers logging events to a remote logging sink.

RollingFileAppender

Appender that rolls log files based on size or date or both.

SmtpAppender

Send an e-mail when a specific logging event occurs, typically on errors or fatal errors.

SmtpPickupDirAppender

Send an email when a specific logging event occurs, typically on errors or fatal errors. Rather than sending via smtp it writes a file that another service, such as the IIS SMTP agent, can use to manage sending the messages.

TelnetAppender

Appender that allows clients to connect via Telnet to receive log messages.

TraceAppender

Appends log events to the Trace system.

UdpAppender

Sends logging events as connectionless UDP datagrams to a remote host or multicast using the UdpClient class.

  
  

##### FileAppender and RollingFileAppender

  
  

These appenders write log messages to files. A typical configuration for the FileAppender might look like this:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <appender name\="FileAppender" type\="log4net.Appender.FileAppender"\>  
```  
  
```
 2:    <file value\="log.txt" />  
```  
  
```
 3:    <appendToFile value\="true" />  
```  
  
```
 4:    <encoding value\="utf-8" />  
```  
  
```
 5:    <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 6: </appender\>  
```  

  
  

Configuration attributes and its description are:

  
  

  
*   **file**: the full or relative path to the log file;
  
  
*   **appendToFile**: boolean indicating whether the log file should be appended (true) or overwritten (false).  If false, the file overwrite occurs during log4net initialization.  If unspecified, the log file is appended;
  
  
*   **immediateFlush**: boolean indicating whether to flush the log file TextWriter after each log message is written.  The default is true (flush each message after its written);
  
  
*   **lockingModel**: allows control over the log file locking strategy.  This can be either "log4net.Appender.FileAppender+MinimalLock" to allow for loose file locking or "log4net.Appender.FileAppender+ExclusiveLock" to lock the file during program execution. 
  

  
  

Keep in mind that the log file managed by FileAppender will be allowed to grow without bounds. The RollingFileAppender provides basic log file management, configurable size- or date-boxing of the log file, and limited rolling backups of the log file.

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <appender name\="RollingFileAppender" type\="log4net.Appender.RollingFileAppender"\>  
```  
  
```
 2:    <file value\="log-file.txt" />  
```  
  
```
 3:    <appendToFile value\="true" />  
```  
  
```
 4:    <rollingStyle value\="Size" />  
```  
  
```
 5:    <maxSizeRollBackups value\="10" />  
```  
  
```
 6:    <maximumFileSize value\="1MB" />  
```  
  
```
 7:    <staticLogFileName value\="true" />  
```  
  
```
 8:    <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 9: </appender\>
```  

  
  

Configuration attributes and its description are:

  
  

  
*   **rollingStyle**: this controls how log files are "rolled," and can be one of the following values:  
      
    
      
    *   **Once**: the log file is rolled every time log4net is initialized (typically at application startup);
      
      
    *   **Size**: the log file is rolled once it breaches a certain size;
      
      
    *   **Date**: the log file is rolled based on the current date;
      
      
    *   **Composite**: the log file is rolled based on size constraints and the current date;
      
    
      
    
  
  
*   **maximumFileSize**: the size cap on the log file.  This is an expression of size in the form of "#(KB|MB|GB)".  For instance, "100KB" or "10MB";
  
  
*   **maxSizeRollBackups**: the maximum number of rolled log file backups to maintain when rollingStyle is SIZE; when rollingStyle is COMPOSITE, this indicates the maximum number of roll-offs maintained _per day_; this property has no effect when rollingStyle is ONCE or DATE;
  
  
*   **datePattern**: the date pattern used to roll files based on date.  The value of this parameter needs to adhere to the format used by the SimpleDateFormatter class;
  
  
*   **staticLogFileName**: a bit of a misnomer - when true this setting indicates whether log4net should actively write logs to the configured file (log-file.txt in our example configuration) and maintain rolling backups by copy.  When false, this setting indicates that log4net will actively log to the latest roll-off file (e.g., log-file1.txt, log-file2.txt, log-file3.txt, etc);
  
  
*   **countDirection**: indicates how roll-off file numbering is managed.  When this parameter is >= 0, the newest log file will have the largest number; e.g., log-file.txt.5 will be newer than log-file.txt.4.  When countDirection < 0, the newest log file will have the lowest number; e.g., log-file.txt.1 will be newer than log-file.txt.2.  If unspecified, countDirection defaults to (-1);
  

  
  

Keep in mind that when using a file appender, the user running the logging process must have rights to create and/or modify the log file in order for log messages to be written properly.  In addition, log4net will create the log file if it does not exist, but it will not create directories in the log file path that do not already exist.  If log4net encounters a problem initializing the file appender (e.g., it cannot create the log file for security reasons), the log file will not be written but your application will continue to execute normally.

  
  

##### Using multiple appenders

  
  

You can use multiple appenders by specifying each appender you need under the root logger.

  
  

Layouts and patterns
--------------------

  
  

A layout is just a template for your log messages.  Layouts are specified per-appender, and you can specify only one layout for an appender:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <appender name\="ColoredConsoleAppender" type\="log4net.Appender.ColoredConsoleAppender"\>  
```  
  
```
 2:    <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 3: </appender\>  
```  

  
  

The PatternLayout allows you to specify a printf-style template for your log entries using a "conversion pattern," and gives you the opportunity to decorate each entry with some valuable instance data. For instance, this configuration:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <appender name\="ColoredConsoleAppender" type\="log4net.Appender.ColoredConsoleAppender"\>  
```  
  
```
 2:    <layout type\="log4net.Layout.PatternLayout"\>  
```  
  
```
 3:        <conversionPattern value\="%date \[%thread\] %-5level %logger - %message%newline" />  
```  
  
```
 4:    </layout\>  
```  
  
```
 5: </appender\>  
```  

  
  

produces a log that appears like so:

  
  

[![log4net4](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiP2QYY-iJKqibVjWYZrwr_R2FIhG9o38efgcwov9lBD0Syvo00yO0My-vUDQvXR7OVDyMDq2nFI8MLM8-k3PMFwbATkAZ_lVLhtQYcVpN3JgVNgVwqNUdishJ8j6DQHejEH1Iy0GCRNQ/?imgmax=800 "log4net4")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh_0BuJkJrb9hV2QmIsRqR6ZdSmloVPM27fGfEDFFv-alO2_qFDitKIxPttbk2YtU00ve00Bnnp1u7xeExlo9tBObgg6ZsSJP59xxgJlkAr5V5hvv0-SSomg3EcL1Z8SmOcahgRlKwMNg/s1600-h/log4net45.jpg)

  
  

The conversion pattern string can include literal text and the following format expressions:

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

**expression**

**value**

%appdomain

the friendly name of the appdomain from which the log entry was made

%date

the local datetime when the log entry was made

%exception

a formatted form of the exception object in the log entry, if the entry contains an exception; otherwise, this format expression adds nothing to the log entry

%file

the file name from which the log entry was made; note that using %file has a significant performance impact and I don't recommend using it

%identity

the user name of the active user logging the entry; this one is less reliable than %username; note that using %identity has a significant performance impact and I don't recommend using it

%level

the severity level of the log entry (DEBUG,INFO, etc)

%line

the source code line number from which the log entry was made; slow

%location

some rudimentary call stack information, including file name and line number at which the log entry was made; using

%logger

the name of the logger making the entry; more on this in a bit

%method

the name of the method in which the log entry was made; also slow

%message

the log message itself (don't forget this part!)

%newline

the value of Environment.NewLine

%timestamp

the milliseconds between the start of the application and the time the log entry was made

%type

the full typename of the object from which the log entry was made

%username

the Windows identity of user making the log entry; slow

%utcdate

the UTC datetime when the log entry was made

%%

a percent sign (%)

  
  

A common usage of the %logger expression is to identify the source class in the log entries. Give the class name to the logger like:

  
  

private static log4net.ILog Log = log4net.LogManager.GetLogger( System.Reflection.MethodBase.GetCurrentMethod().DeclaringType ); 

  
  

and the output will be something like:

  
  

ConsoleApplication1.Program \[INFO\]- this is an info message

  
  

Using this technique can help you control logging concerns of your objects. For example, add a new class “MyClass” to your ConsoleApplication and use the above approach in declaring your loggers. Add the following after the <root> section in your app.config :

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <logger name\="ConsoleApplication1"\>  
```  
  
```
 2:      <level value\="ALL" />  
```  
  
```
 3:      <appender-ref ref\="FileAppender" />  
```  
  
```
 4: </logger\>  
```  
  
```
 5: <logger name\="ConsoleApplication1.Program"\>  
```  
  
```
 6:      <level value\="ALL" />  
```  
  
```
 7:      <appender-ref ref\="ConsoleAppender" />  
```  
  
```
 8: </logger\>  
```  
  
```
 9: <logger name\="ConsoleApplication1.MyClass"\>  
```  
  
```
 10:      <level value\="ALL" />  
```  
  
```
 11: </logger\>  
```  

  
  

This way, the console output will display only the log statements from the Program class, the log file will contain the log statements from both Program class and MyClass class. Although MyClass doesn’t have an appender associated with it, the container namespace does and that appender who processes MyClass log statements. If you changed the level value to “OFF” for ConsoleApplication1.MyClass, the log file will not contain log statements from MyClass. When applying the previous technique keep into consideration the following:

  
  

  
*   Appenders accumulate through the hierarchy: if both the Program class and ConsoleApplication1 namespace are each configured to append to the console, any log from the Program class will show up twice in the console (once for the class logger and once for the namespace logger).
  
  
*   Specific logger levels deeper in the hierarchy overcome the general levels : if the Program class logging level is set to ALL and the ConsoleApplication1 namespace logging level is set to OFF, logs from the program class are still written to the appenders configured for ConsoleApplication1.
  

  
  

#### Log event context

  
  

Beside the expressions mentioned above, sometimes you need to log context information. Modify your console application to look so:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: using System;
```  
  
```
 2: namespace ConsoleApplication1
```  
  
```
 3: {
```  
  
```
 4:    class Program
```  
  
```
 5:    {
```  
  
```
 6:        private static log4net.ILog log = log4net.LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);
```  
  
```
 7:        static void Main(string\[\] args)
```  
  
```
 8:        {
```  
  
```
 9:            log4net.Config.XmlConfigurator.Configure();
```  
  
```
 10:            log4net.ThreadContext.Properties\["myContext"\] = "Logging from Main";
```  
  
```
 11:            log.Info("Just info.");
```  
  
```
 12:            Console.ReadLine();  
```  
  
```
 13:        }
```  
  
```
 14:    }
```  
  
```
 15: }
```  

  
  

Now update the app.config to look like:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <?xml version\="1.0" encoding\="utf-8" ?\>
```  
  
```
 2: <configuration\>
```  
  
```
 3:  <configSections\>
```  
  
```
 4:    <section name\="log4net"
```  
  
```
 5:      type\="log4net.Config.Log4NetConfigurationSectionHandler, log4net"/>
```  
  
```
 6:  </configSections\>
```  
  
```
 7:  
```  
  
```
 8:  <log4net\>
```  
  
```
 9:  
```  
  
```
 10:    <appender name\="ConsoleAppender" type\="log4net.Appender.ConsoleAppender"\>
```  
  
```
 11:      <layout type\="log4net.Layout.PatternLayout"\>
```  
  
```
 12:        <conversionPattern value\="%logger (%property{myContext}) \[%level\]- %message%newline" />
```  
  
```
 13:      </layout\>
```  
  
```
 14:    </appender\>
```  
  
```
 15:  
```  
  
```
 16:    <root\>
```  
  
```
 17:      <level value\="ALL" />
```  
  
```
 18:      <appender-ref ref\="ConsoleAppender" />
```  
  
```
 19:    </root\>
```  
  
```
 20:  </log4net\>
```  
  
```
 21: </configuration\>
```  

  
  

Compile and run, you will got a log statement similar to:

  
  

ConsoleApplication1.Program (Logging from Main) \[INFO\]- Just info.

  
  

What we did here is that we added a property “myContext” to the ThreadContext static class and assigned a simple string value. This property processed by the appender through the %property{myContext} expression in the layout conversion pattern.  
  
  

  
  

There are three hierarchy logging contexts available in log4net, where properties in the more granular contexts override property values in less granular contexts.

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

Context

Description

**log4net.GlobalContext**

A global context shared across all application threads and app domains. If two threads set the same property on the GlobalContext, one value will overwrite the other.

**log4net.ThreadContext**

Any properties set in this context are scoped to the calling thread. In other words, in this context two threads can set the same property to different values without stomping on each other.

**log4net.ThreadLogicalContext**

This context behaves similarly to the ThreadContext, except that the scope is defined by logical thread boundaries. I'll be honest and say that I've never used the ThreadLogicalContext in my career, but if you're working with a custom thread pool algorithm or hosting the CLR, you may find some use for this one.

  
  

##### Calculated context values

  
  

Context property values don't have to be strings. You can set the value of a context property to any object reference; then the object's ToString can be used to obtain the needed context property when a logging event occurs. This technique could be used to log whatever state you want at the time of each logging event.

  
  

##### ThreadContext Stacks

  
  

ThreadContext and ThreadLogicalContext can store property values in stacks available via the Stacks static property of each class. Pushing a property value onto a stack returns an IDisposable that, when disposed, pops the property value off of the stack.  The logging output reflects the state of the context stack at each logging event; the stack is represented as a space-delimited list, with newer items appearing later in the list. Its like printing the current call stack in every log statement. check this example:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: using System;
```  
  
```
 2: namespace ConsoleApplication1
```  
  
```
 3: {
```  
  
```
 4:    class Program
```  
  
```
 5:    {
```  
  
```
 6:        private static log4net.ILog log = log4net.LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);
```  
  
```
 7:        static void Main(string\[\] args)
```  
  
```
 8:        {
```  
  
```
 9:            log4net.Config.XmlConfigurator.Configure();
```  
  
```
 10:            using (log4net.ThreadContext.Stacks\["myContext"\].Push("Main"))
```  
  
```
 11:            {
```  
  
```
 12:                FirstAction();
```  
  
```
 13:                SecondAction();
```  
  
```
 14:            }
```  
  
```
 15:            Console.ReadLine();  
```  
  
```
 16:        }
```  
  
```
 17:  
```  
  
```
 18:        static void FirstAction()
```  
  
```
 19:        {
```  
  
```
 20:            using (log4net.ThreadContext.Stacks\["myContext"\].Push("FirstAction"))
```  
  
```
 21:            {
```  
  
```
 22:                UtilityRoutine();
```  
  
```
 23:            }            
```  
  
```
 24:        }
```  
  
```
 25:  
```  
  
```
 26:        static void SecondAction()
```  
  
```
 27:        {
```  
  
```
 28:            using (log4net.ThreadContext.Stacks\["myContext"\].Push("SecondAction"))
```  
  
```
 29:            {
```  
  
```
 30:                UtilityRoutine();
```  
  
```
 31:                FirstAction();
```  
  
```
 32:            }
```  
  
```
 33:        }
```  
  
```
 34:  
```  
  
```
 35:        static void UtilityRoutine()
```  
  
```
 36:        {
```  
  
```
 37:            using (log4net.ThreadContext.Stacks\["myContext"\].Push("UtilityRoutine"))
```  
  
```
 38:            {
```  
  
```
 39:                log.Info("this is an info message");
```  
  
```
 40:            }
```  
  
```
 41:        }  
```  
  
```
 42:    }
```  
  
```
 43: }
```  

  
  

Compile and run, you will get these log messages:  
  
ConsoleApplication1.Program (Main FirstAction UtilityRoutine) \[INFO\]- this is an info message  
  
  
ConsoleApplication1.Program (Main SecondAction UtilityRoutine) \[INFO\]- this is an info message  
  
  
ConsoleApplication1.Program (Main SecondAction FirstAction UtilityRoutine) \[INFO\]- this is an info message  
  
  

  
  

  
  

Filters
-------

  
  

Filters are applied to individual appenders via the log4net configuration, and they help the appender determine whether a log event should be processed by the appender. The following configuration defines two file appenders, each with a unique filter applied:

  
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <?xml version\="1.0" encoding\="utf-8" ?\>  
```  
  
```
 2: <configuration\>  
```  
  
```
 3:  <configSections\>  
```  
  
```
 4:    <section name\="log4net" type\="log4net.Config.Log4NetConfigurationSectionHandler, log4net"/>  
```  
  
```
 5:  </configSections\>  
```  
  
```
 6:  <log4net\>  
```  
  
```
 7:    <appender name\="LogFileAppender" type\="log4net.Appender.FileAppender"\>  
```  
  
```
 8:      <file value\="log.txt" />  
```  
  
```
 9:      <filter type\="log4net.Filter.LevelRangeFilter"\>  
```  
  
```
 10:        <levelMin value\="DEBUG" />  
```  
  
```
 11:        <levelMax value\="WARN" />  
```  
  
```
 12:      </filter\>  
```  
  
```
 13:      <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 14:    </appender\>  
```  
  
```
 15:    <appender name\="ErrorFileAppender" type\="log4net.Appender.FileAppender"\>  
```  
  
```
 16:      <file value\="errors.txt" />  
```  
  
```
 17:      <filter type\="log4net.Filter.LevelRangeFilter"\>  
```  
  
```
 18:        <levelMin value\="ERROR" />  
```  
  
```
 19:        <levelMax value\="FATAL" />  
```  
  
```
 20:      </filter\>  
```  
  
```
 21:      <layout type\="log4net.Layout.SimpleLayout" />  
```  
  
```
 22:    </appender\>  
```  
  
```
 23:    <root\>  
```  
  
```
 24:      <level value\="DEBUG" />  
```  
  
```
 25:      <appender-ref ref\="LogFileAppender" />  
```  
  
```
 26:      <appender-ref ref\="ErrorFileAppender" />  
```  
  
```
 27:    </root\>  
```  
  
```
 28:  </log4net\>  
```  
  
```
 29: </configuration\> 
```  

  
  

The filter on the first appender will log statements with levels DEBUG, INFO, and WARN; the filter on the second appender will log statements with levels ERROR and FATAL. There are many filters available in log4net, we will review them quickly.

  
  

**log4net.Filter.LoggerMatchFilter** Filters log events based on the name of the logger object from which they are emitted. This filter can be configured using the following properties:

  
  

  
*   loggerToMatch: a string value to match against the message's logger name.  The match is made using the String.StartsWith method;
  
  
*   acceptOnMatch: a boolean value indicating whether a matching logger name results in accepting the message (true) or rejecting it (false).  This defaults to true, meaning that only matching logger names will be allowed into the appender.
  

  
  

**log4net.Filter.LevelMatchFilter** Filters log statements that match (or don’t match) a specific logging level. This filter can be configured using the following properties:

  
  

  
*   levelToMatch: the log level to match - either DEBUG, INFO, WARN, ERROR, or FATAL;
  
  
*   acceptOnMatch: a boolean value indicating whether to accept log levels matching the levelToMatch property (true), or reject log levels matching the levelToMatch property (false).  Defaults to true.
  

  
  

**log4net.Filter.LevelRangeFilter** Similar to the LevelMatchFilter, except that instead of filtering a single log level, this filters on an inclusive range of contiguous levels. This filter can be configured using the following properties:

  
  

  
*   levelMin: the minimum log level to match - either DEBUG, INFO, WARN, ERROR, or FATAL;
  
  
*   levelMax: the minimum log level to match - either DEBUG, INFO, WARN, ERROR, or FATAL;
  
  
*   acceptOnMatch: a boolean value indicating whether to accept log levels matching the levelToMatch property (true), or to punt filtering to the next filter in the chain (false).  Defaults to true.  Note that any log level outside of the \[levelMin, levelMax\] range is denied by this filter.
  

  
  

**log4net.Filter.StringMatchFilter** Filters log events based on a string or regular expression match against the log message. This filter can be configured using the following properties:

  
  

  
*   regexToMatch: a regular expression to match against the log message.  Note this regex is created with the Compiled option enabled for performance;
  
  
*   stringToMatch: a static string to match against the log message.  The match is made using the String.IndexOf method to see if the static string exists in the log message, which is a case-sensitive search.
  
  
*   acceptOnMatch: a boolean value indicating whether to accept log messages matching the string or regex (true), or to deny log messages matching the string or regex (false).  Defaults to true. 
  

  
  

**log4net.Filter.PropertyFilter** Filters log events based on a value or regular expression match against a specific context property.

  
  

  
*   key: the name of the property value to match;
  
  
*   regexToMatch: a regular expression to match against the specified property value.  Note this regex is created with the Compiled option enabled for performance;
  
  
*   stringToMatch: a static string to match against the specified property value.  The match is made using the String.IndexOf method to see if the static string exists in the property value, which is a case-sensitive search.
  
  
*   acceptOnMatch: a boolean value indicating whether to accept messages with a property value matching the string or regex (true), or to deny messages with a property value matching the string or regex (false).  Defaults to true.
  

  
  

**log4net.Filter.DenyAllFilter** This filter simply denies all filtering.  When this is used, it's always at the end of a filter chain to block unwanted log messages from the appender.

  
  

Lossy logging
-------------

  
  

If you want comprehensive log to be there in case of errors but you worry about the resources consumed by logging, you might use lossy logging.  Lossy logging gives the best of both worlds, under normal operation your application will not log any messages; however, if your application logs an error, a small batch of messages leading up to the error is placed into the log, giving you the error and a snapshot of system activity just before it happened.

  
  

Lets modify our code to be like:

  
<br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: using System;
```  
  
```
 2: namespace ConsoleApplication1
```  
  
```
 3: {
```  
  
```
 4:    class Program
```  
  
```
 5:    {
```  
  
```
 6:        static log4net.ILog Log = log4net.LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);
```  
  
```
 7:        static void Main( string\[\] args )
```  
  
```
 8:        {
```  
  
```
 9:            log4net.Config.XmlConfigurator.Configure();
```  
  
```
 10:            for( int i = 0; i < 100; ++i )
```  
  
```
 11:            {
```  
  
```
 12:                Log.DebugFormat( "this is debug msg #{0}", i );
```  
  
```
 13:            }                
```  
  
```
 14:            Log.Error( "error: an error occurred!" );           
```  
  
```
 15:            Log.Warn( "warning: you've been warned" );
```  
  
```
 16:            
```  
  
```
 17:            Console.ReadLine();
```  
  
```
 18:        }
```  
  
```
 19:    }
```  
  
```
 20: }
```  

  
  

Let's modify our app.config to look like:

  
<br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: <?xml version\="1.0" encoding\="utf-8" ?\>
```  
  
```
 2: <configuration\>
```  
  
```
 3:  <configSections\>
```  
  
```
 4:    <section name\="log4net" type\="log4net.Config.Log4NetConfigurationSectionHandler, log4net"/>
```  
  
```
 5:  </configSections\>
```  
  
```
 6:  
```  
  
```
 7:  <log4net\>
```  
  
```
 8:    <appender name\="ConsoleAppender" type\="log4net.Appender.ConsoleAppender"\>
```  
  
```
 9:      <layout type\="log4net.Layout.SimpleLayout" />
```  
  
```
 10:    </appender\>
```  
  
```
 11:  
```  
  
```
 12:    <appender name\="LossyConsoleAppender" type\="log4net.Appender.BufferingForwardingAppender"\>
```  
  
```
 13:      <bufferSize value\="20" />
```  
  
```
 14:      <lossy value\="true"/>
```  
  
```
 15:      <evaluator type\="log4net.Core.LevelEvaluator"\>
```  
  
```
 16:        <threshold value\="ERROR" />
```  
  
```
 17:      </evaluator\>
```  
  
```
 18:      <appender-ref ref\="ConsoleAppender" />
```  
  
```
 19:    </appender\>
```  
  
```
 20:  
```  
  
```
 21:    <root\>
```  
  
```
 22:      <level value\="DEBUG" />
```  
  
```
 23:      <appender-ref ref\="LossyConsoleAppender" />
```  
  
```
 24:    </root\>
```  
  
```
 25:  </log4net\>
```  
  
```
 26: </configuration\>
```  

  
  

Compile and run, you will see output like:

  
  

[![log4net5](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiPw9r1GXrxr3FR_tj-0LhblvjTEoqotvHzpiQsec1IgWaGMAWe5_4Nn1C042XKw5z68CEpkc_2a53Oqy2MdHbwYKtvqK9PMtajs5pLhurjmhDu07hM-7nIjvQrC0AG0QWskDsS5CqXUQ/?imgmax=800 "log4net5")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhuwni4Avqiz-PLc9iXNhYaB-shef0cItOWieZ0iM3qH8quVKYLlBdHE3NS1WHdZ9A1H-CwvlXjS8nVT7AIikuk9-csChp46AuAJpPxtGvA9mx0pSxGhThhYBP-bgO8vVDBF0skRvcuvA/s1600-h/log4net5%25255B1%25255D.jpg)

  
  

The logging configuration defines two appenders, one very generic Console appender and a BufferingForwardingAppender.  As the name implies, the latter appender buffers log messages and forwards them in batches to one or more other appenders.  You can probably tell from the configuration XML that I've set this appender up with a 20-message buffer.  The lossy and evaluator parameters work together to define when the log message buffer is forwarded to the "base" appender.

  
  

The program issues a total of 102 log messages (100 DEBUG, one ERROR, and one WARN), but the console only contains 20 messages (19 DEBUG and 1 ERROR).  So what happened to the other 82 DEBUG and WARN messages?

  
  

When the BufferingForwardingAppender's lossy property is enabled, the appender will buffer log messages without forwarding them.  If the buffer fills up, the oldest messages are dropped from the buffer to make room for the new messages. 

  
  

The evaluator property determines when the appender forwards the messages from the buffer to its base appenders.  There is only one evaluator defined in log4net - the LevelEvaluator.  The LevelEvaluator triggers the forward when a log message is received that meets or exceeds the configured threshold.  The example above is configured so that an ERROR message triggers the appender to forward its buffer to the ConsoleAppender.

  
  

Lossy Appender Types log4net provides the following appenders that can operate “lossy” :

  
  

log4net.Appender.AdoNetAppender  
  
log4net.Appender.RemotingAppender  
  
  
log4net.Appender.SmtpAppender  
  
  
log4net.Appender.SmtpPickupDirAppender  
  
  
log4net.Appender.BufferingForwardingAppender

  
  

##### Configuring log4net Programmatically

  
  

Sometimes we are in the mood to code as quickly as possible without getting into configuration files. Normally, that happens when we are trying to test something. In that case, you have another way to do the configuration. All of the long configuration files that we saw in the previous section can be defined programmatically using a few lines of code. See the following code:

  
<br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }  
  

  
```
 1: // using a FileAppender with a PatternLayout
```  
  
```
 2: log4net.Config.BasicConfigurator.Configure( new log4net.Appender.FileAppender(new log4net.Layout.PatternLayout("%d \[%t\]%-5p %c \[%x\] &lt;%X{auth}&gt; - %m%n"),"testfile.log"));
```  
  
```
 3:  
```  
  
```
 4: // using a FileAppender with an XMLLayout
```  
  
```
 5: log4net.Config.BasicConfigurator.Configure( new log4net.Appender.FileAppender(new log4net.Layout.XMLLayout(),"testfile.xml"));
```  
  
```
 6:  
```  
  
```
 7: // using a ConsoleAppender with a PatternLayout
```  
  
```
 8: log4net.Config.BasicConfigurator.Configure( new log4net.Appender.ConsoleAppender(new log4net.Layout.PatternLayout("%d \[%t\] %-5p %c \[%x\] &lt;%X{abc}&gt; - %m%n")));
```  
  
```
 9:  
```  
  
```
 10: // using a ConsoleAppender with a SimpleLayout
```  
  
```
 11: log4net.Config.BasicConfigurator.Configure( new log4net.Appender.ConsoleAppender(new log4net.Layout.SimpleLayout()));
```  

  
  

You can see that while it is easy to code here, you can't configure settings for individual loggers. All of the settings that are defined here are applied to the root logger.

  
  

Log4net Best Practices
----------------------

  
  

1- Use a unique logger object for each type in your application and give it the class name. Like so:

  
  

`static` `log4net.ILog Log = log4net.LogManager.GetLogger(``System.Reflection.MethodBase.GetCurrentMethod().DeclaringType``);`

  
  

2- Whenever you catch an exception, log it.  Even if you just plan to throw it again, log it.  In addition, log4net knows how to format Exception objects, so don't try and build your own string from the exception data, just pass the exception to the logging statement. Like So:

  
  

`Log.Error(``"An exception raised due to XYZ"``,` `e``);`

  
  

3- Log to mark the activity and steps of your code.

  
  

4- Check for null references before logging any property. Logging code is code, and it should be treated the same way.

  
  

5- If an argument to the log method is expensive to obtain, be sure to guard your log statement with a check of the appropriate Is\*Enabled property

  
  

`if``( Log.IsDebugEnabled )``{ /* log statement */ }`

  
  

6- Before an object calls on a shared dependency, consider pushing a tag onto the log context stack.  This will allow you to determine the caller of the shared code that logged a particular message.

  
  

7- Whenever you use a formatted log statement, surround the format argument placeholders (the {}'s) with brackets or parentheses. This will mark the areas in each log message. This make the log scan a bit easier and makes empty or null formatting arguments more obvious. 

  
  

Suggested logging levels
------------------------

  
  

**INFO Level**

  
  

  
*   The start and end of the method
  
  
*   The start and end of any major loops
  
  
*   The start of any major case/switch statements
  

  
  

**DEBUG Level**

  
  

  
*   Any parameters passed into the method
  
  
*   Any row counts from result sets I retrieve
  
  
*   Any datarows that may contain suspicious data when being passed down to the method
  
  
*   Any "generated" file paths, connection strings, or other values that could get mungled up when being "pieced together" by the environment.
  

  
  

**ERROR Level**

  
  

  
*   Handled exceptions
  
  
*   Invalid login attempts (if security is an issue)
  
  
*   Bad data that I have intercepted forreporting
  

  
  

**FATAL Level**

  
  

  
*   Unhandled exceptions.
  

  
  

  
  

In this post I tried to cover as much as possible about logging using log4net. Although logging is extremely useful, keep in mind that it is not free, it consumes resources and the more you log the less you can find. So be careful, and Good Luck.