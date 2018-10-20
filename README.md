# Content

- [Content](#content)
- [Description](#description)
- [Prerequisites](#prerequisites)
    - [Visual Studio Code](#visual-studio-code)
    - [npm](#npm)
    - [pug](#pug)
- [Configuration for VScode](#configuration-for-vscode)
- [Compatibility](#compatibility)
- [To do list](#to-do-list)


# Description

This tutorial enables users to auto compile pug to html in vscode. In general, this method can be extended to any other editor.

# Prerequisites

## Visual Studio Code

The simplest way to install VS code is to download and install the package from [VS code official website](https://code.visualstudio.com/#alt-downloads)

## npm

In Debian(or other Debian-based distributions), npm can be installed by

```console
$ sudo apt-get install npm
```
Or visit the [website](https://www.npmjs.com/get-npm) for more installation guide

## pug

With npm, pug can be easily installed by

```console
$ npm install -g pug
$ npm install -g pug-cli
```

If permission is denied, run with sudo

```console
$ sudo npm install -g pug
$ sudo npm install -g pug-cli
```

To check whether pug is installed successfully

```console
$ pug -h
```

The output should be

```console
Usage: pug [options] [dir|file ...]

Options:
  -V, --version          output the version number
  -O, --obj <str|path>   JSON/JavaScript options object or file
  -o, --out <dir>        output the rendered HTML or compiled JavaScript to <dir>
  -p, --path <path>      filename used to resolve includes
  -b, --basedir <path>   path used as root directory to resolve absolute includes
  -P, --pretty           compile pretty HTML output
  -c, --client           compile function for client-side
  -n, --name <str>       the name of the compiled template (requires --client)
  -D, --no-debug         compile without debugging (smaller functions)
  -w, --watch            watch files for changes and automatically re-render
  -E, --extension <ext>  specify the output file extension
  -s, --silent           do not output logs
  --name-after-file      name the template after the last section of the file path (requires --client and overriden by --name)
  --doctype <str>        specify the doctype on the command line (useful if it is not specified by the template)
  -h, --help             output usage information
  Examples:

    # Render all files in the `templates` directory:
    $ pug templates

    # Create {foo,bar}.html:
    $ pug {foo,bar}.pug

    # Using `pug` over standard input and output streams
    $ pug < my.pug > my.html
    $ echo 'h1 Pug!' | pug

    # Render all files in `foo` and `bar` directories to `/tmp`:
    $ pug foo bar --out /tmp

    # Specify options through a string:
    $ pug -O '{"doctype": "html"}' foo.pug
    # or, using JavaScript instead of JSON
    $ pug -O "{doctype: 'html'}" foo.pug

    # Specify options through a file:
    $ echo "exports.doctype = 'html';" > options.js
    $ pug -O options.js foo.pug
    # or, JSON works too
    $ echo '{"doctype": "html"}' > options.json
    $ pug -O options.json foo.pug
```

# Configuration for VScode

First Create a task

```json
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [{
    "label": "pug auto compile",
    "type": "shell",
    "command": "pug ${file} -wsP",
    "isBackground": true,
    "group": {
      "kind": "build",
      "isDefault": true
    }
  }]
}
```
Then Running the task, when pug file is saved, html file (with nested style)will be automatically generated and there is no output logs.


# Compatibility

This program only has been tested in Linux Mint 18.3. But it should work in any OS installed with the prerequisites.

# To do list

- [ ] add more content for prerequisites
- [ ] add demonstration
