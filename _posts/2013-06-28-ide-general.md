---
layout: article
title: Web IDE overview
published: true
categories: [web ide]
---

The Nitrous.IO Web IDE is a powerful, one stop shop for (almost) all of your development needs.

### File Browser

Like most IDEs, the action file browser sits at the left-hand side of the window. You'll see the box-name at the top of the file browser, followed by a directory tree of your application.

Directories will have a small > arrow icon and can be clicked to be expanded.

![File Browser](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-browser.png)

Right-clicking any directory will allow you to "refresh" the directory to get any new files you might have added as well as make that directory the "root" directory to help clean up viewing of your files.

_Show Hidden_

At the bottom of the file browser, you can also toggle to show or hide hidden files (e.g. .gitignore, .rvm, .nvm … )

![Show Hidden](https://raw.github.com/action-io/action-assets/master/support/screenshots/show-hidden.png)

### File Editor

To open a file, simply click the file name in the file-browser, or click the "+" icon at the top of the file editor.

Once you have a file open and would like to save it, simply hit:

    ^S
    # CNTRL + S

Or you can click the "Save" button at the top of the file editor if you prefer.

_Change Syntax Highlighting_

Our file editor should automatically detect the file extension sand highlight the syntax accordingly. However, if you need to set the syntax highlighting manually, simply select from the dropdown at the top of the file browser.

_Indentation_

We recommend using "soft tabs" for tab-indentation, which is 2 spaces. However if you'd like to change this number, simply select a different indentation setting from the dropdown menu at the top of the file browser. If you want to know why, you can read about [why tabs are evil](http://www.emacswiki.org/emacs/TabsAreEvil).

### File Uploads

To upload a file, simply click the "Upload Files" button at the bottom of the file browser or right-click the folder where you'd like to upload files:

![File Uploads](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-uploads-1.png)

### Action Console

The Nitrous.IO Web IDE also provides a full shell at the bottom of the screen. This allows you to handle your command line tasks with your code editing all in one place.

_New Console Window_

![Console Tabs](https://raw.github.com/action-io/action-assets/master/support/screenshots/console-tabs.png)

To open new console windows, simply click the "+" icon. You can open pretty much an infinite amount of console windows…if you need that many. To close the window, just click the "X" in the console's tab.

_Full Screen the Console_

If you want to just code in your browser using the web console (good for iPad coding), just click the "expand" icon at the right of the console header.

### Previewing Application

We supply some sensible default ports to enable you to preview your work in the browser. Simply click the "Preview" menu at the top of the IDE and select the port where your web server is running.  For ruby on rails, this is usually Port 3000.
