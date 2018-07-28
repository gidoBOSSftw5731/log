# gologme/log #

[![GoDoc](https://godoc.org/github.com/gologme/log?status.png)](https://godoc.org/github.com/gologme/log)

This is a fork of a fork to replace warnings with errors and say what level it 
is in the log.



This package is a drop in replacement for the built-in Go log package. All the 
functionality of the built-in package still exists and is unchanged. In addition, 
this package contains a series of small enhancements and additions. Namely, it 
adds four logging levels. These logging levels are:

- Info
- Error
- Debug
- Trace

In addition to these four defined logging levels, users can also define their 
own arbitrary logging levels.

Unlike other loggers, these logging levels are not enabled in a chain. Meaning, 
once a level is enabled, say Error, all levels above it are not also enabled. 
This package is implemented in such a way that users can individually turn on 
and turn off the various new logging levels. If existing code uses the build-in 
log package, no change is needed to use this package.

Another feature that was added, based on comments seen on the various golang 
boards, is the ability to set the calldepth. 


## Version ##
1.0.1v2


## Installation ##

This package can be installed with the go get command:
```
go get github.com/gidoBOSSftw5731/log
go install github.com/gidoBOSSftw5731/log
```

## Example ##

Just like the built-in package, code can still do simple logging just like:
```
log.Println("some interesting logging message")
```

In addition to this, users can enable info, error, debug, or trace logging like:
```
log.EnableLevel("info")
log.EnableLevel("error")
log.EnableLevel("debug")
log.EnableLevel("trace")
```

Once these levels are enabled, calls to the info, error, debug, or trace loggers 
will print out just like they do for the Print and Fatal built-in loggers. The 
functions / methods definitions that are defined for each level, match exactly 
the ones defined in the built-in package. The new functions/methods are called:
```
log.Info()
log.Infof()
log.Infoln()
log.Error()
log.Errorf()
log.Errorln()
log.Debug()
log.Debugf()
log.Debugln()
log.Trace()
log.Tracef()
log.Traceln()
```

In addition to the defined levels, arbitrary levels can be enabled.  For example:
```
log.EnableLevel("tracedebug")
```

This level can then be used from an application as shown below. All three 
functions/methods are defined for this: log.Level(), log.Levelln(), log.Levelf().
For each of these, the first argument is the level name.
```
log.Levelln("tracedebug", "some other neat logging message for this level")
```

The last thing that was enabled was the ability to define the calldepth. The 
built-in package from the Go authors had this hard coded to a value of 2. A small
change was made to enable this to be set by the application using the log package. 
From the Go authors source code it seems like the normal possible values would 
be 1, 2, or 3.  
```
log.SetCallDepth()
```


## License ##

This is free software, licensed under the same BSD license that the original 
Go log package was licensed.


## Copyright ##

Copyright 2017 Bret Jordan, All rights reserved.
