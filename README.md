
Bookmarklet: sane development, familiar format
==============================================

Bookmarklet is a nodejs module for compiling bookmarklets in server-side code and directly from the shell. You can run it on any JavaScript file—it will minify it using uglify-js, wrap it in a self executing function, and return an escaped bookmarklet.

More so, it supports a metadata block—modeled after the [greasemonkey userscript metadata block](http://wiki.greasespot.net/Metadata_Block)—to specify metadata, external stylesheets and script includes, which can look like this:

    // ==Bookmarklet==
    // @name LoveGames
    // @author Old Gregg
    // @style http://www.cornify.com/css/cornify.css
    // @script https://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js
    // @loadOnce true
    // ==/Bookmarklet==

Most notably, you can specify any external scripts that you’d like your bookmarklet to include via the `@script` rule, which can be repeated as many times as you’d like.

NOTE: currently with script includes you have to handle `noConflict` scenarios yourself, e.g., you might want to start off a script with `var $ = jQuery.noConflict(true)`.

In addition, any css files included with `@style` will be injected.

By default, every time the bookmark is hit, it will add the script and style tags again. This can be limited to only adding them on the first run by setting `@loadOnce` to `true`.

This project is open to suggestions & pull requests.

Also, if you’re just looking for a quick way to throw together a bookmarklet, try my [browser-based bookmarklet creator](http://mrcoles.com/bookmarklet/).

### Installation

The dependency can be found on [NPM as “bookmarklet”](https://www.npmjs.org/package/bookmarklet). You can install it with:

```bash
npm install -g bookmarklet
```

### Usage

You can easily see usage by running `bookmarklet -h`:

```bash
> bookmarklet -h
Bookmarklet v0.0.1 usage: bookmarklet source [destination]

source      - path to file to read from or `-` for stdin
destination - path to file to write to
```
