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

var out = BinaryStream(outPDFPath, 'write');
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

Example (HTML)
--------------
1. Open the file "index.html" in the Web Folder.
2. Drag and drop an SVG; there is a sample document in /Resources/sample.pdf.
3. A link "Open PDF" will appear.
4. Click it. The PDF will show in a new browser tab. (tested Safari, FireFox, Chrome).

![](https://github.com/miyako/wak-rsvg/blob/master/images/1.png)
![](https://github.com/miyako/wak-rsvg/blob/master/images/2.png)
![](https://github.com/miyako/wak-rsvg/blob/master/images/3.png)
