.. _xslt:

======================================================================
XSLT parser
======================================================================

:Maintainer: Masatake YAMATO <yamato@redhat.com>

This parser only supports XSLT 1.0.
If a newer version (2.0 and 3.0) is specified in an input file, ctags
just skips the input. With ``--verbose``, ctags prints the detected
version of the input file.

Scope information generated by the XSLT parser is a bit broken.
Currently a period (`.`) is used as the separator in nested scopes.
This is the default separator value in ctags.

When the XSLT parser captures a node `<xsl:template match="...">` the
value of the `match` attribute is tagged with kind `matchedTemplate`.
When a `matchedTemplate` name is stored as part of the scope information,
client tools may be confused because `.` is used both as the scope separator
and in the XPath match expression.
