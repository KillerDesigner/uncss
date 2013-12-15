# UnCSS #

Remove unused styles from CSS

## Installation: ##

    npm install -g uncss

Usage
-----

### From the command line: ###

  Usage: uncss [options] <file ...>

  Options:

    -h, --help                     output usage information
    -V, --version                  output the version number
    -c, --compress                 Compress CSS output
    -i, --ignore <selector, ...>   Do not remove given selectors
    -C, --csspath <path>           Relative path where the CSS files are located
    -s, --stylesheets <file, ...>  Specify additional stylesheets to process
    -t, --timeout <milliseconds>   Wait for JS evaluation


### Within node: ###

    var uncss = require('uncss');

    var files   = ['my', 'array', 'of', 'HTML', 'files'],
        options = {
            compress: true,
            ignore: ['#added_at_runtime', /test\-[0-9]+/],
            csspath: "../public/css/",
            stylesheets: ["lib/bootstrap/dist/css/bootstrap.css", "src/public/css/main.css"],
            timeout: 1000
        };

    uncss(files, options, function (output) {
        console.log(output);
    });

    /* Look Ma, no options! */
    uncss(files, function (output) {
        console.log(output);
    });

    /* Specifying raw HTML*/
    var raw_html = '...'
    uncss(raw_html, options, function (output) {
        console.log(output);
    });

#### Options in depth: ####
- __compress__ [Boolean]: Whether the CSS output should be compressed.
- __ignore__ [Array]: provide a list of selectors that should not be removed by UnCSS. For example, styles added by user interaction with the page (hover, click), since those are not detectable by UnCSS yet. Both literal names and regex patterns are recognized.
- __csspath__ [String]: Path where the CSS files are related to the html files. By default, UnCSS uses the path specified in the <link rel="stylesheet" href="path/to/file.css"\>
- __stylesheets__ [Array]: Force the list of stylesheets to optimize using a path relative to the `Gruntfile.js`. Otherwise, it extracts the stylesheets from the html files.
- __timeout__ [Number]: Specify how long to wait for the JS to be loaded.

### grunt-uncss ###
If you are looking for the grunt plugin, head over to [grunt-uncss](https://github.com/addyosmani/grunt-uncss), created by @addyosmani

## License ##
Copyright (c) 2013 Giacomo Martino. See the LICENSE file for license rights and limitations (MIT).

### Features planned: ###
- Add PhantomJS integration
