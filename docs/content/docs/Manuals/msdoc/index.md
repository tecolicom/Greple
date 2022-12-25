---
layout: page
title:  greple -Mmsdoc
weight: 10
description: Greple module for access MS office docx/pptx/xlsx documents
---

[![Actions Status](https://github.com/kaz-utashiro/greple-msdoc/workflows/test/badge.svg)](https://github.com/kaz-utashiro/greple-msdoc/actions) [![MetaCPAN Release](https://badge.fury.io/pl/App-Greple-msdoc.svg)](https://metacpan.org/release/App-Greple-msdoc)
## NAME

msdoc - Greple module for access MS office docx/pptx/xlsx documents

## VERSION

Version 1.06

## SYNOPSIS

greple -Mmsdoc pattern example.docx

## DESCRIPTION

This module makes it possible to search string in Microsoft
docx/pptx/xlsx file.

Microsoft document consists of multiple files archived in zip format.
String information is stored in "word/document.xml",
"ppt/slides/\*.xml" or "xl/sharedStrings.xml".  This module extracts
these data and replaces the search target.

By default, text part from XML data is extracted.  This process is
done by very simple method and may include redundant information.

Strings are simply connected into paragraph for _.docx_ and _.pptx_
document.  For _.xlsx_ document, single space is inserted between
them.  Use **--separator** option to change this behavior.

After every paragraph, single newline is inserted for _.pptx_ and
_.xlsx_ file, and double newlines for _.docx_ file.  Use
**--space** option to change.

## OPTIONS

- **--dump**

    Simply print all converted data.  Additional pattern can be specified,
    and they will be highlighted inside whole text.

        $ greple -Mmsdoc --dump -e foo -e bar buz.docx

- **--space**=_n_

    Specify number of newlines inserted after every paragraph.  Any
    non-negative integer is allowed including zero.

- **--separator**=_string_

    Specify the separator string placed between each component strings.

- **--indent**

    Extract indented XML document, not a plain text.

- **--indent-mark**=_string_

    Set indentation string.  Default is `| `.

## INSTALL

### CPANMINUS

cpanm App::Greple::msdoc

## SEE ALSO

[App::Greple](https://metacpan.org/pod/App%3A%3AGreple),
[https://github.com/kaz-utashiro/greple](https://github.com/kaz-utashiro/greple)

[App::Greple::msdoc](https://metacpan.org/pod/App%3A%3AGreple%3A%3Amsdoc),
[https://github.com/kaz-utashiro/greple-msdoc](https://github.com/kaz-utashiro/greple-msdoc)

[App::optex::textconv](https://metacpan.org/pod/App%3A%3Aoptex%3A%3Atextconv),
[https://github.com/kaz-utashiro/optex-textconv](https://github.com/kaz-utashiro/optex-textconv)

## AUTHOR

Kazumasa Utashiro

## LICENSE

Copyright 2018-2022 Kazumasa Utashiro.

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.