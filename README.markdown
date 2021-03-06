jQuery Form Input Example Plugin 1.3.4
======================================

This is a jQuery plugin to populate form inputs with example text that
disappears on focus.

Basic usage revolves around the use of the `example` function like so:

    $('input#name').example('Bob Smith');

This will then put the example text "Bob Smith" into the input with the ID
"name". When a user then focuses on this input, the example text will
disappear, allowing them to enter their data. If they then click elsewhere
*without entering any information*, the example will re-appear.

By default, example text is given the class `example`, allowing you to style
it with CSS like so:

    .example { color: #666; }

If this class name conflicts with one you already use, you can override it
with the `class_name` option like so:

    $('input#name').example('Bob Smith', { class_name: 'hint' });

The above example would then be given the class `hint` instead of `example`.

The other option available is `hide_label` which will hide any input's
associated label (and any line-break following it) when set to `true` (it is
`false` by default):

    $('input#name').example('Bob Smith', { hide_label: true });

If you plan to use the same options repeatedly, it is possible to override the
plugin's defaults directly:

    $.fn.example.defaults.class_name = 'not_example';
    $.fn.example.defaults.hide_label = true;

This will cause any uses of the plugin after this point to use the new
defaults.

As well as supplying the example text via a string, a callback function can be
used instead to determine the value at runtime:

    $('input#name').example(function() {
       return $(this).attr('title'); 
    });
    
The above example will set the example text to the `title` attribute of the
input. The callback is executed within the context of the input field so, as
in the example above, `$(this)` will return the input itself.

It is worth noting that the callback is evaluated every time the example text
needs to be inserted and *is not cached*. This makes it possible to
dynamically change the example text of a field after page load like so:

    $('input#name').example(function() {
        var text = $(this).attr('title');
        $(this).attr('title', 'Not the original title anymore');
        return text;
    });
    
The plugin also supports the jQuery Metadata plugin which allows you to 
specify metadata in elements themselves. You can specify the example text and
hide_label options like so:

    <input id="m1" class="{example_text: 'An example', hide_label: true}" />

Please note that you *cannot* set the class_name option using metadata and
that anything specified using metadata will take precedence.

For more usage examples (and something of a test suite), please see
index.html.

Compatibility
-------------

This plugin has been tested with jQuery 1.1 and newer and should work in all
browsers supported by jQuery itself (it has been tested with Safari 3 and
newer, Mozilla Firefox 2 and newer, Opera 9.26 and Internet Explorer 6).

Author
------

This plugin was written by and is maintained by Paul Mucur aka "mudge". Please
do not hesitate to contact me with comments and bug reports through the
plugin's official entry on the jQuery Plugins directory:
http://plugins.jquery.com/project/example

You can view the latest source code (and fork the entire project if you wish)
at http://github.com/mudge/jquery_example

Contributors
------------

The code to support the Metadata plugin was contributed by DeLynn Berry (http://github.com/delynn).

Licensing
---------

Copyright (c) Paul Mucur (http://mucur.name), 2007-2008.

Dual-licensed under the BSD (BSD-LICENSE.txt) and GPL (GPL-LICENSE.txt)
Licenses.

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.