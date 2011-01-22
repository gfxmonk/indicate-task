indicate-task
=============

A command line tool that displays an indicator-applet
menu for the duration of a long-running process ("task").

The indicator can contain:

 - an icon
 - a label

When clicked, the menu contains:

 - descriptive text
 - "show output" button (which shows the currently
   captured STDOUT of the launched program)
 - cancel (sends SIGINT to program)

indicate-task echoes stdin to stdout as well as capturing it,
so you can wrap a program in an indicator and still get the
same output / return code.

**Note**: If you don't already have them, you will need to
install the following packages:

		apt-get install python-appindicator libnotify-bin zenity

------------------------------

## Usage:
    Usage: indicate-task [options] -- command-and-arguments
    
    Options:
      -h, --help            show this help message and exit
      --style=STYLE         
      --long-description=LONG_DESCRIPTION
                            set long description (visible in popup menu)
      -d DESCRIPTION, --description=DESCRIPTION
                            set description (visible in tray, defaults to command
                            executable)
      -p PID, --pid=PID     attach to an already-running PID
      --id=ID               set application ID (defaults to description)
      --no-icon             don't use an icon
      --no-notify           suppress completion notification
      --no-capture          suppress output capture
      --ignore-errors       Suppress automatic output display when process returns
                            nonzero error code
    
    eg: indicate-task -d download -- curl 'http://example.com/bigfile'