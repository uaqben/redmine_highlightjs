# HighlightJS Plugin

A redmine plugin to highlight code blocks much better than coderay! :)
135 languages with autodetection feature, 65 color themes, multi language code highlight (like http+json)
Try Your language and choose best theme for You: https://highlightjs.org/static/demo/

Old good coderay:

![](https://raw.githubusercontent.com/dominch/redmine_highlightjs/master/screenshots/coderay.png)

Example highlihts (monokai_sublime theme) - json, http+json:

![](https://raw.githubusercontent.com/dominch/redmine_highlightjs/master/screenshots/highlightjs.png)

It's very easy to use because it works automatically :) finds blocks of code, detects a language (one or more!), highlights it.

Supported languages and markups in build: 1c accesslog actionscript apache applescript armasm asciidoc aspectj autohotkey autoit avrasm axapta bash brainfuck cal capnproto ceylon clojure clojure-repl cmake coffeescript cpp crystal cs css d markdown dart delphi diff django dns dockerfile dos dust elixir elm ruby erb erlang-repl erlang fix fortran fsharp gams gcode gherkin glsl go golo gradle groovy haml handlebars haskell haxe http inform7 ini irpf90 java javascript json julia kotlin lasso less lisp livecodeserver livescript lua makefile mathematica matlab mel mercury mizar perl mojolicious monkey nginx nimrod nix nsis objectivec ocaml openscad oxygene parser3 pf php powershell processing profile prolog protobuf puppet python q r rib roboconf rsl ruleslanguage rust scala scheme scilab scss smali smalltalk sml sql stata step21 stylus swift tcl tex thrift tp twig typescript vala vbnet vbscript vbscript-html verilog vhdl vim x86asm xml xl xquery zephir


# Install

1. Copy `redmine_highlightjs` plugin to your Redmine's `/plugin` directory:
  + Redmine 1.x:

    ```
    cd redmine/vendor/plugins
    git clone git@github.com:dominch/redmine_highlightjs.git
    ```
  + Redmine 2.x or 3.x:

    ```
    cd redmine/plugins
    git clone git@github.com:dominch/redmine_highlightjs.git
    ```
2. This plugin relies on [useragent](https://github.com/gshutler/useragent) `gem`, so make sure you have it installed:

  ```
  cd redmine/
  bundle
  ```
3. This plugin needs an extra table in Redmine's DB, so:
  + Redmine 1.x:

    ```
    rake db:migrate_plugins RAILS_ENV=production
    ```
  + Redmine 2.x or 3.x:

    ```
    rake redmine:plugins:migrate RAILS_ENV=production
    ```
4. Restart Redmine (_this will ensure that the CSS file and other assets are copied to the right place_)
5. (optional) Configure color theme in `Administration -> Plugins -> HighlightJS`

# Browser Restrictions

Plugin is restricted to work with following browsers (or newer):

      Browser.new('Safari', '2'),
      Browser.new('Firefox', '3'),
      Browser.new('Chrome', '10'),
      Browser.new('Internet Explorer', '9')

If You find out that there are some problems with Your browser then report bug in github, so we can turn it off for selected software. Some people still using old browsers like IE8, when others are up to date. IE8 is unsupported by main lib so there is nothing better than turning on coderay again.

# Usage

This plugin will replace existing Coderay highlights,
You can specify target language like usual:

    <pre><code class="json">
    [
          {
            "title": "apples",
            "count": [12000, 20000],
            "description": {"text": "...", "sensitive": false}
          },
          {
            "title": "oranges",
            "count": [17500, null],
            "description": {"text": "...", "sensitive": false}
          }
    ]
    </code></pre>

or use autodetection:

    <pre><code>
    [
      {
        "title": "apples",
        "count": [12000, 20000],
        "description": {"text": "...", "sensitive": false}
      },
      {
        "title": "oranges",
        "count": [17500, null],
        "description": {"text": "...", "sensitive": false}
      }
    ]
    </code></pre>

Autodetection works great with more than one language on the board, like http with appliction/json body:

    <pre><code>
    POST /task?id=1 HTTP/1.1
    Host: example.org
    Content-Type: application/json; charset=utf-8
    Content-Length: 19

    {"status": "ok", "extended": true}
    </code></pre>

To disable highlighting altogether use the nohighlight class:

    <pre><code class="nohighlight">...</code></pre>

Plugin additionaly trims white lines from start and end so  

    <pre><code>{"status": "ok", "extended": true}</code></pre>

is equal to:

    <pre><code>
    {"status": "ok", "extended": true}
    </code></pre>

# Build Your own HighlightJS version

If You need subset of supported languages follow instruction on highlightJS site: http://highlightjs.readthedocs.org/en/latest/building-testing.html
Just replace redmine_highlightjs/assets/javascript/highlight.pack.min.js with Your build

For Your new language definition follow instructions here: http://highlightjs.readthedocs.org/en/latest/language-guide.html

# FAQ:

### Line numbers?

No, that probably never happens! http://highlightjs.readthedocs.org/en/latest/line-numbers.html

This plugin removes line numbers from file-view too in order to get one block to highlight.


# License

This plugin is licensed under the GNU GPL v2.  See [COPYRIGHT.txt](COPYRIGHT.txt) and [GPL.txt](GPL.txt) for details.

# Plugin author

(c) Dominik Chmaj - [http://www.dominik.net.pl](http://www.dominik.net.pl)

# Project help, bugs

If you need help you can contact the maintainers on the project page on GitHub ([https://github.com/dominch/redmine_highlightjs](https://github.com/dominch/redmine_highlightjs)). If you want to report bugs, please open a new issue here: [https://github.com/dominch/redmine_highlightjs/issues](https://github.com/dominch/redmine_highlightjs/issues)
