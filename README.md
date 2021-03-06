## Synopsis

Guppy is a Javascript-based WYSIWYG editor for mathematics whose
content is stored in an XML format that makes Guppy mathematical
expressions **searchable**, **parseable**, and **renderable**.

The content of the editor can easily be extracted in a very flexible
XML format (for searching or otherwise manipulating), LaTeX (for
rendering), or a plaintext format (for parsing).

## Demo

A live demo can be found at 
[http://daniel3735928559.github.io/guppy/](http://daniel3735928559.github.io/guppy/)

## Code example

A stripped-down version of the demo page would look like:

```
<html>
  <head>
    <link rel="stylesheet" href="lib/katex/katex.min.css">
    <script src="lib/katex/katex-modified.min.js"></script>
    <script src="lib/mousetrap/mousetrap.min.js"></script>
    <script type="text/javascript" src="src/guppy.js"></script>
  </head>
  <body>
    <div id="guppy_div" style="width:400px;height:100px;"></div>
    
    <script>
        Guppy.guppy_init("src/transform.xsl","src/symbols.json");
        new Guppy("guppy_div");
    </script>
    <button onclick="alert(Guppy.instances.guppy_div.get_content('xml'))">See XML</button>
    <button onclick="alert(Guppy.instances.guppy_div.get_content('latex'))">See LaTeX</button>
    <button onclick="alert(Guppy.instances.guppy_div.get_content('text'))">See ASCII</button>
  </body>
</html>
```

## Installation and deployment

* Download the `lib` and `src` folders.

* Include `src/guppy.js` after `lib/katex/katex-modified.min.js`,
  `lib/katex/katex.min.css`, and `lib/mousetrap/mousetrap.min.js`
  files in your page.

* Pass the paths to `src/transform.xsl` and `src/symbols.json` to
  `Guppy.guppy_init` as in the example above.  This only needs to
  happen once per page.

* For each div that you want turned into a Guppy instance, call `new
  Guppy()` passing in as the first argument either the Element object
  for that div or its ID.

## Editor usage

The editor has many of the usual keyboard text-editing features:
Navigation with the arrow keys, backspace, home, end, selection with
shift-left/right, mod-z/x/c/v for undo, cut, copy, paste
(respectively).  Using the mouse to navigate and select is also
supported.

If you type the name of a mathematical object such as `sqrt`, the
editor will automatically replace that entered text with the
corresponding object.  The list of symbols supported by default is
documented in index.html (or just see the demo page).  Further symbols
can be added by modifying `symbols.json`.

## Further documentation

* [The Javascript API for controlling the editor](doc/api.md)
* [The JSON specification used to describe available symbols](doc/symbols.md)
* [The XML format used to represent expressions](doc/format.md)
* [Editor internals](doc/internals.md)

## Tests

The tests can be run by opening /test/test.html in a browser, for
example, by going to
[http://daniel3735928559.github.io/guppy/test/test.html](http://daniel3735928559.github.io/guppy/test/test.html)

## License

Guppy is licensed under the [MIT License](http://opensource.org/licenses/MIT).
