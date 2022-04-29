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
      - pxatbegshi: on (u)pLaTeX

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
  * `autodvidriver`: Negation of `disabled`/`nodvidriver`.  
    Note: Options `dvips` and `dvipdfmx` also negate `disabled`.

#### Priority

**Important**: The `priority` option is not (yet) supported under the
new LaTeX kernel 2020-10-01.

  * `priority=<value>`: In DVI mode, this decides the priority of the
    ‘papersize’ specials issued by this package relative to the
    ‘papersize’ specials issued by others.
    The set of valid values is:
      - `low`: Priotizes specials by others.
      - `middle`/`default` (default): Does not care about priority.
      - `high`: Priotizes specials by this package.
    Note: The priority setting will be ignored in PDF mode.
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

Once the package is loaded, the output paper size will be adjusted,
respecting the settings given by the package options. By default, the
output papersize will be made identical to the layout paper size.

    % For many cases, it's enough.
    \usepackage{bxpapersize}

You can change the settings of this package using `\papersizesetup`
command, invoked as follows:

    \papersizesetup[<key>=<value>,...]

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
        specified values.
      - `<width>*<height>`: The alternative form of `{<width>,<height>}`.
        It is provided because option strings including braces are not
        permitted in the package option list.
      - `<papersize-name>`: The output should be equal to the given
        size. The set of available paper-size names is the same as in the
        [geometry package] and is listed below:  
        a0paper--a6paper, b0paper--b6paper, c0paper--c6paper, b0j--b6j,
        ansiapaper--ansiepaper, letterpaper, legalpaper, executivepaper,
        screen.
      - `landscape`, `truedimen`: These are used in combination with
        `<papersize-name>` options, and have the same meaning as in the
        geometry package.
      - `box`: The output should be the actual size of the TeX box
        to be shipped out. It is provided for advanced users.

[geometry package]: https://www.ctan.org/pkg/geometry

Note that, however, what happens about output paper size when some
settings are changed in the midst of pages differs among TeX engines
and/or DVI drivers. Thus such usage should be employed only by advanced
users.

The comamnd `\bxpapersizesetup` is a synonym for `\papersizesetup`,
so as to cope with command name conflict. Namely, `\papersizesetup`
will be not (re)defined if the command of that name is already defined,
but `\bxpapersizesetup` will be always provided.


Revision History
----------------

  * Version 0.6  ‹2022/04/28›
      - Add `autodvidriver` option.
      - Rearrange spec on driver options.
  * Version 0.5  ‹2020/10/01›
      - Support LaTeX kernel 2020/10/01.
        (But priority setting is not yet supported.)
  * Version 0.4  ‹2019/10/05›
      - Load pxatbegshi to properly handle pTeX tate mode.
      - Remove (experimental) `adjustmag` option.
  * Version 0.3b ‹2017/10/08›
      - Support pTeX-ng (ApTeX) engine properly.
      - (Experimental) Add `adjustmag` option.
  * Version 0.3a ‹2017/05/02›
      - Support format `size=<width>*<height>`
  * Version 0.3  ‹2017/02/08›
      - As to `size=real`, the stock size becomes taken into account,
        and the new value `real*` is provided.
      - Make `nodvidriver` synonym for `disabled`.
      - Make `\papersizesetup` synonym for `\bxpapersizesetup`.
      - Add `olddvips`.
      - Support `size=<papersize-name>`. together with `landscape` and
        `truedimen`.
  * Version 0.2  ‹2016/03/26›
      - The first public version.

--------------------
Takayuki YATO (aka. "ZR")  
https://github.com/zr-tex8r
