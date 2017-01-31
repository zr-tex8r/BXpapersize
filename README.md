BXpapersize Package
===================

LaTeX: To synchronize output paper size with layout paper size

As is well known, in LaTeX processing layout paper size specified by
document class options is not automatically applied to output paper
size. By employing this package, authors can make output paper size
be identical to layout paper size. They can also set output paper size
to arbitrary values.

It should be noted that there are many packages that try to synchronize
paper sizes, possibly in a slightly different manner. This package
allows authors to decide whether the setting made by this package
should have higher or lower priority over the settings made by others.

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
  * `nodvidriver`: A synonym for `disabled`.

#### Priority

  * `priority=<value>`: In DVI mode, this decides the priority of the
    ‘papersize’ specials issued by this package relative to the
    ‘papersize’ specials issued by others.
    The set of valid values is:
      - `low`: Priotizes specials by others.
      - `middle`/`default` (default): Does not care about priority.
      - `high`: Priotizes specials by this package.
  * `olddvips`: Must be specified when you use dvips older than that
    included in TeX Live 2017, so as to make the `priority` option
    work correctly.

#### Other options

Any key-value pairs that are valid in `\papersizesetup` can be used
as package options.

    % to begin with deactivated state
    \usepackage[active=false]{bxpapersize}

Note that the default values of the `\papersizesetup` command are also
applied when the package is loaded. For example, `size=real` will be
in effect when this package is loaded without the `size` option key.

### Usage

You can change the settings of this package using `\papersizesetup`
command, invoked as follows:

    \bxpapersizesetup[<key>=<value>,...]

The available keys are listed below:

  * `active=true|false`: Temporarily activates/deactivates the function
    of this package.
  * `size=<value>`: Decides what the output paper size should be.
    Available values are:
      - `real`: The output should be equal to the layout paper size
        given by `\paperwidth/height`, except that the stock paper size
        given by `\stockwidth/height` will be employed instead when
        it is available.
      - `real*`: The output should be equal to the layout paper size,
        even if the stock paper size is available.
      - `{<width>,<height>}`: The output should be equal to the
        specified value.
      - `box`: The output should be the actual size of the TeX box
        to be shipped out. For advanced users.

Note that, however, what happens about output paper size when some
settings are changed in the midst of pages differs among TeX engines
and/or DVI drivers. Thus such usage should be employed only by advanced
users.

The comamnd `\bxpapersizesetup` is a synonym for `\papersizesetup`,
so as to cope with command name conflict. Namely, `\papersizesetup`
will be not (re)defined if the command of that name is always defined,
but `\bxpapersizesetup` will be always provided.

Revision History
----------------

  * Version 0.3  ‹2017/02/05›
  * Version 0.2  ‹2016/03/26›
      - The first public version.

--------------------
Takayuki YATO (aka. "ZR")  
https://github.com/zr-tex8r
