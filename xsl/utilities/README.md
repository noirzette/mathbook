# Utilities

## Source-to-Source conversions

For utility programs here which rewrite your source, be **sure** to use version control (collect and review changes on a branch, stash and drop undesirable outcomes), or have backups handy.  The effects are not reversible.  Stylesheets will output to standard output, so you can redirect their output, or you can use something like the `-o` flag on the `xsltproc` command-line invocation.  Experiment first.

### `fix-deprecations.xsl`
This will convert any obsolete element names or constructions to their replacements.  As deprecations are added, you may run it anew, and only the new changes will be applied.  Despite the name, it does make some minor changes.  Empty tags will get a single space prior to the closing backslash.

Be sure to read all the details in the Author's Guide before using this on your source.  Here is an absolute minimal example.
```
$ xsltproc /path/to/xsl/utilities/fix-deprecations.xsl -stringparam fix all /path/to/examples/sample-errors-and-warnings.xml > new-sample.xml

$ diff /path/to/examples/sample-errors-and-warnings.xml new-sample.xml
```

(Updated: 2017-07-04)
