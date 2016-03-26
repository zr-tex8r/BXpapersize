BXpapersize Package
===================

LaTeX: To synchronize output paper size with layout paper size

As is well known, in LaTeX processing layout paper size specified by
document class options is not automatically applied to output paper
size. This package enables LaTeX authors to synchronize both kinds of
paper sizes.

### System requirement

  * TeX format: LaTeX.
  * TeX engine: Anything.
  * DVI driver (in DVI mode): dvips, dvipdfmx, or whatever supports
    ‘papersize’ special.
  * Dependent packages:
      - ifpdf, ifxetex, ifluatex, ifvtex
      - xkeyval
      - atbegshi

### Installation

  - `*.sty` → $TEXMF/tex/latex/BXpapersize

### License

This package is distributed under the MIT License.

The bxpapersize Package
-----------------------

### Package Loading

    \usepackage[<option>,...]{bxpapersize}

The available options are described hereafter.

#### Annihilation

  * `disabled`: Disables all functionality of this package. It may be
    useful to resolve conflict caused by some packages depending on
    the bxpapersize package. Note that once `disabled` is used there
    is no way to enable the functionality.


#### Priority

  * `priority=<value>`: In DVI mode, this decides the priority of the
    ‘papersize’ specials issued by this package relative to the
    ‘papersize’ specials issued by others.
    The set of valid values is:
      - `low`: Priotizes specials by others.
      - `middle` (default): Does not care about priority.
      - `high`: Priotizes specials by this package.

#### Other options

Any key-value pairs that are valid in `\bxpapersizesetup` can be used
as package options.

    % to begin with deactivated state
    \usepackage[active=false]{bxpapersize}

### Usage

You can change the settings of this package using `\bxpapersizesetup`
command, invoked as follows:

    \bxpapersizesetup[<key>=<value>,...]

The available keys are listed below:

  * `active=true|false`: Temporarily activates/deactivates the function
    of this package. Note that, however, what happens about paper size
    synchronization when activation settings are changed in the midst
    of documents differs among TeX engines and/or DVI drivers. Thus
    this should be employed only by advanced users.


Revision History
----------------

  * Version 0.2  ‹2016/03/26›
      - The first public version.

--------------------
Takayuki YATO (aka. "ZR")  
http://zrbabbler.sp.land.to/
