# Documentation #
  1. [Examples](http://www.pdflabs.com/docs/pdftk-cli-examples/)
  1. [Man Pages](http://www.pdflabs.com/docs/pdftk-man-page/)
# Details #

Merge Two or More PDFs into a New Document
pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf

or (Using Handles):
pdftk A=1.pdf B=2.pdf cat A B output 12.pdf

or (Using Wildcards):
pdftk **.pdf cat output combined.pdf**

Split Select Pages from Multiple PDFs into a New Document
pdftk A=one.pdf B=two.pdf cat A1-7 B1-5 A8 output combined.pdf

Encrypt a PDF using 128-Bit Strength (the Default) and Withhold All Permissions (the Default)
pdftk mydoc.pdf output mydoc.128.pdf owner\_pw foopass

Same as Above, Except a Password is Required to Open the PDF
pdftk mydoc.pdf output mydoc.128.pdf owner\_pw foo user\_pw baz

Same as Above, Except Printing is Allowed (after the PDF is Open)
pdftk mydoc.pdf output mydoc.128.pdf owner\_pw foo user\_pw baz allow printing

Decrypt a PDF
pdftk secured.pdf input\_pw foopass output unsecured.pdf

Join Two Files, One of Which is Encrypted (the Output is Not Encrypted)
pdftk A=secured.pdf mydoc.pdf input\_pw A=foopass cat output combined.pdf

Uncompress PDF Page Streams for Editing the PDF Code in a Text Editor
pdftk mydoc.pdf output mydoc.clear.pdf uncompress

Repair a PDF's Corrupted XREF Table and Stream Lengths (If Possible)
pdftk broken.pdf output fixed.pdf

Burst a Single PDF Document into Single Pages and Report its Data to doc\_data.txt
pdftk mydoc.pdf burst

Report on PDF Document Metadata, Bookmarks and Page Labels
pdftk mydoc.pdf dump\_data output report.txt