# Usage #
```
$.tsv.toArrays(tsv, options) returns an array of arrays, one per line, each containing values from one row.

@param tsv a tab-separated-values input, e.g. "11\t\12\t13\n21\t22\t23"
@param options optional: { valueSplitter: /\t/, lineSplitter: /\r?\n/, parseValue: <a function to parse each value> }
@returns an array of arrays, e.g. [["11", "12", "13"], ["21", "22", "23"]]
```

See tsvOptions for more information on the options.

# Example #

This is of course completely unrealistic, but it illustrates the format.

```
$.get("mydata.tsv").done(function done(data) {
  var tsv = $.toArrays(data);
  var headers = tsv.shift();
  var table = $("#table");
  var thead = table.find("thead");
  for (var h = 0; h < headers.length; j++) {
    // Fill in the headers from the file
    $(thead[h]).text(headers[h]);
  }
  var tbody = table.find("tbody tr");
  for (var i = 0; i < tsv.length; i++) {
    var row = tsv[i];
    var cells = $(tbody[i]).find("td");
    for (var j = 0; j < headers.length) {
        var value = row[j];
        $(cells[j]).text(value);
    }
  }
});
```