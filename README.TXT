DOCBOOK to HTML Conversion
--------------------------
We use the Saxon XSLT processor <http://saxon.sourceforge.net/> to apply the
DocBook to HTML transformation.  The Saxon engine is found in the
"lib/saxon-<version>" directory.  Currently, we are using Saxon 6.5.5 even
though the most recent version of Saxon is verion 9.1.0.5.  This is because
the most recent versions of Saxon process XSLT 2.0 documents.  The DocBook XSLT
documents are XSLT 1.0 documents.  Saxon 6.5.5 is the most recent stable release
of the XSLT 1.0 processor.  When the DocBook transformations are updated, we
should update the Saxon version that we are using.

We use the Apache commons XML resolver <http://www.apache.org/dist/xml/commons/>
with Saxon to handle XML catalog files.  This library is found in
"lib/xml-commons-resolver-<version>".  (I'm not sure what the catalog files are
all about, but they are described here
<http://www.sagehill.net/docbookxsl/Catalogs.html>.)

We use the "html/docbook.xsl" XSLT style sheet from the DocBook definition
<http://sourceforge.net/project/showfiles.php?group_id=21935> to define the
DocBook to HTML transformation.  This is found in "lib/docbook-xsl-<version>".


DOCBOOK to ECLIPSE HELP Conversion
----------------------------------
Same as above except that we use the "eclipse/eclipse.xsl" transformation from
the DocBook definition project.


DOCBOOK to PDF Conversion
-------------------------
We first convert from docbook to FO using "fo/docbook.xsl" in the DocBook
definition project.

We then use Apache FOP <http://xmlgraphics.apache.org/fop/> to convert from
FO to PDF.  The library files for this are in "lib/fop-<version>".

We use the OFFO library <http://offo.sourceforge.net/index.html> to control
hyphenation.  The library file for this is in "lib/offo-<version>".

