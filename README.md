Sublime PDB Finder
===================

A Sublime Text 2 plugin to extract and list Python PDB lines from open files and 
project folders.

Install
-------

The preferred method is to use the [Sublime Package Manager](http://wbond.net/sublime_packages/package_control). Once you have Package Control installed,
just search for *PDB Finder*.

Alternatively, checkout from github:


    $ cd Sublime Text 2/Packages

    $ git clone https://github.com/aleGpereira/sublime-pdb-finder.git


Config
------

All plugin configuration must be placed in user or project-specific settings inside a *pdbfinder* object, for example;

    {
        // other user config ...
        "pdbfinder": {
            "patterns": {}
        }
    }


An example
__________

    "pdbfinder": {
        "file_exclude_patterns": [
            "*.css",
            "*.po",
            "*.mo",
            "*.pyc"
        ],
        "folder_exclude_patterns": [
            "static",
            "vendor",
            "tmp"
        ],
        "case_sensitive": true,
        "result_title": "PDB Results"
    },


Adding patterns
---------------

Extraction uses regular expressions that return one match group 
representing the message. Since this plugin is set to search for Python pdb's,
you can add patterns to provide *PDB* lines in some other language.
To override or provide more patterns, add `patterns` to user settings, e.g.

    "patterns": {
        'PDB': r'(?P<pdb>import[\s]*pdb[\s]*;[\s]*pdb\.set_trace\(\).*)$',
    }


Note that the pattern _must_ provide at least one named group which will be used to group the comments in results.

By default, searching is not case sensitive. You can change this behaviour by adding 

    "case_sensitive": true

to the pdbfinder settings object.


Excluding files and folders
---------------------------

Global settings *folder_exclude_patterns*, *file_exclude_patterns* and *binary_file_patterns* are excluded from search results.

To exclude further directories, add directory names (not glob pattern or regexp) to *folder_exclude_patterns* in Pdbfinder settings:

    "pdbfinder": {
        "folder_exclude_patterns": [
            "vendor", 
            "tmp"
        ]
    }


To add file excludes, add glob patterns to `file_exclude_patterns`:


    "file_exclude_patterns": [
        "*.css"
    ]



Results title
-------------

Override the results view title by setting `result_title`


    "result_title": "PDBs Results"


Usage
-----

* *Find PDBs: Project and open files* scans all files in your project.

* *Find PDBs: Open files only* scans only open, saved files.

Both are triggered from the command palette. No default key bindings are provided.

If we have results, a list is going to be show with:

* The file name.

* The line in wich that pdb can be found.

* The content of the next line, if we have one. If not, EOF is shown.

Navigating results
__________________

Results can be navigated by keyboard and mouse:

 * **n** ext, **p** revious, **c** lear, **enter**
 * **alt-double click** (**shift-double click** in Linux)

Note that due to the lack of support for context in mousemaps right now,
alt-double click will trigger in _any_ document, though it should be a no-op.

VERY IMPORTANT NOTE
-------------------

Sublime PDB Finder has been inherited from **[SublimeTODO](https://github.com/robcowie/SublimeTODO)** by his author **[Rob Cowie](https://github.com/robcowie)**. I really liked that tool. So thanks to him too!!.

License
-------

All of Sublime PDB Finder is licensed under the MIT license.

Copyright (c) 2013 Alejandro Pereira <alepereira86@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
