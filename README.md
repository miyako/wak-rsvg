About
-----
Wakanda module to create PDF or PNG from SVG.

Example
-------
```js
var modulesFolder = FileSystemSync('Modules');
var svg = require(modulesFolder.path + 'rsvg');

var inSVGPath = getFolder().path + 'Resources/sample.svg';
var outPDFPath = FileSystemSync('Desktop').path + 'sample.pdf';
var outPNGPath = FileSystemSync('Desktop').path + 'sample.png';

//example 1: use file for input and output

var options = {
	'input':inSVGPath,	
	'output':outPNGPath
	};

svg.toPNG(null, options);
	
//example 2: use Buffer for input, BLOB for output

var options = {};
		
var src = File(inSVGPath);
src = src.exists ? BinaryStream(src) : null;
src = src ? src.getBuffer(src.getSize()) : null;

var result = svg.toPDF(src, options);

var out = BinaryStream(FileSystemSync('Desktop').path + generateUUID() + '.pdf', 'write');
out.putBlob(result.console.stdOut);
out.close();
```

Vaild properties for the options object are:

* dpi_x (number)
* dpi_y (number)
* zoom_x (number)
* zoom_y (number)
* width (number)
* height (number)
* keep_aspect_ratio (boolean)
* base_url (string)
* input (string)
* output (string)

If no input is provided, stdIn is used. (string or Bufffer).
If no output is provided, stdOut is used.
-----
