# Processing Tab-Separated Values in jQuery #

The jQuery.tsv plugin was inspired by Evan Plaice's jQuery.csv plugin. After adapting that in my project, I found I really needed a proper Tab Separated Values plugin.

Tab,Separated Values format is much simpler (and more limited) than Comma-Separated Values. In particular, there is no possibility of a tab being contained in a value, no quoting, etc.

It's not a very _good_ format, but it's a very _simple_ format and an extremely _common_ format.

The IANA description of the text/tab-separated-values media type appears here:

http://www.iana.org/assignments/media-types/text/tab-separated-values

This package comes with an extensive test suite, and the core functionality is functionally complete. I expect to make some adjustments to the function names based on Evan's suggestions in the next few days, but I will retain the old names for compatibility.

# Usage #
Simply load jQuery-tsv after jQuery, and in your code, use it like this:
```
  var tsv = $.tsv.parseRows(data);
  var colHeaders = tsv[0]; // Assuming it has a header row
  var firstRow = tsv[1];   // you have to know or guess.
```

# Functions #
For details, see the [API documentation](https://raw.github.com/BobKerns/jquery-tsv/master/doc/index.html).

Static Functions:
  * $.tsv.[parseRows](parseRows.md) -- parse an entire TSV string as arrays of values
  * $.tsv.[parseRow](parseRow.md) -- parse one line of TSV = as a single array of values
  * $.tsv.[parseValue](parseValue.md) -- parse one TSV value

  * $.tsv.[parseObjects](parseObjects.md) -- parse an entire TSV string as objects
  * $.tsv.[parseObject](parseObject.md) -- parse one line of TSV as one object

  * $.tsv.[arraysToObjects](arraysToObjects.md) -- convert an entire array of row arrays to objects.
  * $.tsv.[objectsToArrays](objectsToArrays.md) -- convert an entire array of objects to an array of row arrays.
  * $.tsv.[arrayToObject](arrayToObject.md) -- convert one row array to an object.
  * $.tsv.[objectToArray](objectToArray.md) -- convert one object to a row array.

  * $.tsv.[formatRows](formatRows.md) -- format an entire array of row arrays to tsv.
  * $.tsv.[formatRow](formatRow.md) -- format a single row array to tsv.
  * $.tsv.[formatObjects](formatObjects.md) -- format an entire array of objects to tsv
  * $.tsv.[formatObject](formatObject.md) -- format one object to one line of tsv

  * $.tsv.[options](options.md) -- default values for the various options.

# Details #

The package provides the following features.
  * Conversion from tsv text to Javascript arrays of array values
    * An array of line arrays, `e.g. `[["header1","header2"], ["val11", "val12"], ["val21", "val22"]]
    * Line-at-a-time, `["val1", "val2"]`
  * Conversion from tsv text to Javascript arrays of objects
    * e.g. `[ {header1: "val11", header2: "val12"}, {header1: "val21", header2: "val22"}]`
    * Column/attribute names can be taken from the tsv header row (if present), or supplied
    * An array of objects, or an object at a time.
  * Conversion from either format above to tsv text.
  * Parsers/formatters can be specified for the data values (so numbers and dates can be read/written as numbers and dates, for example).

# Future work #

  * Integrate this directly with jQuery's ajax facilities?
  * Some sort of merger or coordination of API with jQuery-csv?