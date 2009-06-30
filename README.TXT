LOCAL REFS TO THE DOCTYPE
-------------------------
VERY IMPORTANT!
VERY IMPORTANT!
VERY IMPORTANT!

The DocBook files in this project make local references to the DocBook DTD
that is stored in the "lib/docbook-xml-4.5" directory.  These references must
be made using relative URLs.  In particular this means, that you must be careful
to update the relative URL when adding additional subdirectories to a document
directory.

The normal DOCTYPE declaration that is used with DocBook 4.5 is 

<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.5//EN"
"http://www.oasis-open.org/docbook/xml/4.5/docbookx.dtd">

The DOCTYPE declaration that we use in files in the top-level document directories
(for example, the declaration in "src/sierra-guide/sierra-guide.xml") is

<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.5//EN"
"../../lib/docbook-xml-4.5/docbookx.dtd">


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

We use the Xerces XML parser <http://xerces.apache.org/> instead of the built-in
AElfred parser so that we can get XInclude support.  Currently we use version
2.9.1.

We use the Apache commons XML resolver <http://www.apache.org/dist/xml/commons/>
with Saxon to handle XML catalog files.  This library is found in
"lib/xml-commons-resolver-<version>".  (I'm not sure what the catalog files are
all about, but they are described here
<http://www.sagehill.net/docbookxsl/Catalogs.html>.)

We use the "html/profile-docbook.xsl" XSLT style sheet from the DocBook definition
<http://sourceforge.net/project/showfiles.php?group_id=21935> to define the
DocBook to HTML transformation.  This is found in "lib/docbook-xsl-<version>".


DOCBOOK to ECLIPSE HELP Conversion
----------------------------------
Same as above except that we use the "eclipse/profile-eclipse.xsl" transformation from
the DocBook definition project.


DOCBOOK to PDF Conversion
-------------------------
We first convert from docbook to FO using "fo/profile-docbook.xsl" in the DocBook
definition project.

We then use Apache FOP <http://xmlgraphics.apache.org/fop/> to convert from
FO to PDF.  The library files for this are in "lib/fop-<version>".

We use the OFFO library <http://offo.sourceforge.net/index.html> to control
hyphenation.  The library file for this is in "lib/offo-<version>".


Conditional Content
-------------------
We use the "profile-*" versions of the style sheets so that we can generate
some content conditionally, depending on whether we are generating HTML or
FO/PDF.  Elements that are only relevant to HTML should have the attribute
"condition='isHTML'".  Elements that are only relevant to FO should have the
attribute "condition='isFO'".

 