# DHIS 2 Documentation Guide { #doc_guide_chapter } 

## DHIS 2 Documentation System Overview { #docs_1 } 

DHIS 2 is a web-based information management system under very active
development with typically two major releases per year. Each release
typically includes a number of new features and additional
functionality. Given the fast pace of development, the system's wide
user base and distributed, global nature of development, a comprehensive
documentation system is required.

In this chapter, we will describe the documentation system of DHIS 2 and how you
can contribute.

## Introduction { #docs_2 } 

The DHIS 2 documentation is written in [Commonmark](https://commonmark.org) markdown format.
One of the main advantages of markdown is
that there is complete separation between the content and presentation.
Commonmark is a strongly defined, highly compatible specification of
markdown.
Since markdown can be transformed into a wide variety of formats (HTML,
PDF, etc) and is a text-based format, it serves as an ideal format for
documentation of the system.

There exist a wide range of text editors which can be used for the
creation of markdown files. For Linux and Windows,
[ghostwriter](https://wereturtle.github.io/ghostwriter/) is a nice option;
it is free and supports side-by-side preview and custom style sheets.

One of the key concepts to keep in mind when authoring documentation in
markdown, or other presentation neutral formats, is that the **content**
of the document should be considered first. The **presentation** of the
document will take place in a separate transformation step, whereby the
source text will be rendered into different formats, such as HTML and
PDF. It is therefore important that the document is well organised and
structured, with appropriate tags and structural elements being
considered.

It is good practice to break your document in to various sections using
the section headings. In this way, very complex chapters can be split into smaller, more manageable pieces.
This concept is essentially the same as Microsoft Word or other word
processing programs. The rendering process will automatically take care of numbering
the sections for you when the document is produced.


## Getting started with GitHub { #docs_3 } 

The DHIS 2 documentation system is managed at
[GitHub](https://github.com/dhis2) across a variety of source
code repositories. GitHub is a platform that enables
multiple people to work on software projects collaboratively. In order
for this to be possible, a version control system is necessary
to manage all the changes that multiple users may make. GitHub uses the
*git* source control system. While it is beyond the scope of this
document to describe the functionality of *git*, users who wish to
create documentation will need to gain at least a basic understanding of
how the system works. A basic guide is provided in the next section. The
reader is referred to the [git manual](https://git-scm.com/book/en/v2)
for further information.

In order to start adding or editing the documentation, you should first
perform a checkout of the source code. If you do not already have a
GitHub account, you will need to get one. This can be done
[here](https://github.com/). Once you register with GitHub, you will
need to request access to the *dhis2-documenters* group if you wish to
modify the source code of the documentation directly. However, anyone 
can clone the documentation into their own repository, commit the
changes to that fork, and request that the changes be merged with
the source of the documentation with a pull request to the parent repository.

The structure of the documentation site is defined in the build repository [dhis2-docs-builder](https://github.com/dhis2/dhis2-docs-builder).
If you wish to add new parts to the structure, changes will have to be made there; this is usually only relevant to the internal DHIS2 team.

> **Tip**
>
> The best way to find the source of the document you wish to edit is to find the document on the docs.dhis2.org website and click the "Edit" icon at the top of the page.

## Getting the document source { #docs_4 } 

In order to edit the documentation, you will need to download the source
of the documentation to your computer. GitHub uses a version control
system known as git . There are different methods for getting Git
working on your system, depending on which operating system you are
using. A good step-by-step guide for Microsoft operating systems can be
viewed
[here](https://help.github.com/articles/getting-started-with-github-for-windows).
Alternatively, if you are comfortable using the command line, you can
download git from [this page](http://git-scm.com/download/win) If you
are using Linux, you will need to install git on your system through
your package manager, or from source code. A very thorough reference for
how git is used is available in a number of different formats
[here](http://git-scm.com/book).

Once you have installed git on your system, you will need to download
the document source. Just follow this procedure:

1.  Make sure you have git installed.

2.  On Windows systems, visit the relevant repository URL and
    press "Clone in Desktop". If you are using the command line, just
    type `git clone git@github.com:dhis2/dhis2-docs.git` (note that in this example
    `dhis2` is owner of the repository and `dhis2-docs` is the name of the repository)

3.  The download process should start and all the documentation source
    files will be downloaded to the folder that you specified.

4.  Once you have the source, be sure to create your own branch for
    editing. Simply execute` git checkout -b mybranch` where *mybranch*
    is the name of the branch you wish to create.

## Editing the documentation { #docs_5 } 

When writing or editing documentation, there are a few **key project-specific conventions that you should be aware of**, which are outlined in this section.
In addition, several markdown extensions are implemented and are demonstrated for convenience in the  [Markdown support and extensions](#markdown_support_and_extensions) later in this document.


### Using images

Image resources should be included as relative paths inside a sub-folder relative to the current document. e.g. for the chapter `content/android/android-event-capture-app.md`, the images are somewhere under `content/android/resources/images/<rest-of-path>` and are referenced like `![](resources/images/<rest-of-path>)`

#### Styling images

If you want to control the alignment and size of images, you can take advantage of a markdown extensionthat we use. It allows you to set attributes such as width, height and class in curly brackets at the end of the image definition. For example:
```
![](resources/images/maintainence/predictor_sequential.png){ width=50% }
```
will make your image 50% of the page width (it is best to use percentages to support a variety of output forms), while
```
![](resources/images/maintainence/predictor_sequential.png){ .center width=50% }
```
will also centre the image on the page (due to the definition of the `.center` class in css).

When images are written like
```
![Approving and accepting](resources/images/data_approval/approval_level_steps.png)
```
i.e. with caption text in the square brackets, they are rendered as figures with captions. These are centred by default, with a centred, italicised caption.

#### Taking screenshots

For screenshots of the DHIS 2 web interface, we recommend using Chrome browser, with the following two extensions:
1. [Window Resizer](https://chrome.google.com/webstore/detail/window-resizer/kkelicaakdanhinjdeammmilcgefonfh?hl=en). Use this to set the resolution to **1440x900**
2. [Fireshot](https://chrome.google.com/webstore/detail/take-webpage-screenshots/mcbpblocgmgfnpjjppndjkmgjaogfceg?hl=en). Use this to quickly create a snapshot of the **visible part**

> *Fireshot can even capture the full page, i.e. scrolled, if desired. It can also capture just a selected area (but the maximum width should always be 1440px)*

When taking screenshots of the Android app, size should be set to **360x640**.

#### Localising images

Localisation of images is supported by storing language-specific versions of an image alongside the original image. The filename should be the same as the original English version, but should include `_` plus the language code at the end of the name, before the extension.

For example, if you want to have a French version of  
`resources/images/my_screenshot.png`  
You can simply create the French version and save it as  
`resources/images/my_screenshot_fr.png`

The link in the documention should still point at the original image. When the documentation site is built for each language, localised images will be identified and used instead of the English originals.

> *The language code is the first part of the URL that you see after the "docs.dhis2.org/" when viewing the localised version of the documentation. At the time of writing, for example, we have `fr`, `es_419`, `pt`, `cs` and `zh`.*


### Section references { #name_of_section } 

In order to provide fixed references (anchors) within the documentation, we can set a fixed text string to be applied to any section. For our markdown processor this is done by adding a hash id in curly brackets at the end of the line with the section title, e.g.
```
## Validation { #webapi_validation }

To generate a data validation summary you can interact ...
```

Will set the section id of the level 2 heading **Validation** to "webapi_validation", which may then be referenced as "#webapi_validation" from *any* html file.

> **Note**
>
> In order to support linking by anchor reference from other documents, please try to keep the section ids unique. For example, if "#webapi_validation" is unique across the documentation, then you can refer to it from any other part of the documentation simply with `[link name](`<!--prevent-replacement-->`#webapi_validation)`.  
> If the section id being referenced is not unique, the document processor will attempt to resolve to the "closest" anchor with that name. *When the linking file belongs to a specific version, the processor will ignore anchors belonging to different versions*.

> **Caution**
>
> Our documentation is compiled into both pages and full documents. For this reason it is not advised to include paths in inter-document references. Please use unique section ids as described above in order for the links to resolve correctly in both document types.

Please follow the convention of lowercase letters and underscores, in order to create id's that are also valid as filenames in cases where we split files as part of the document generation.


### Tables

As an extension to pure commonmark, we also support *GFM tables* (defined with pipes `|`), such as:

```
| Table Type | Description |
|:--|:----|
|Commonmark (HTML)| Tables described in pure HTML |
|Github Flavour Markdown (GFM)| Tables described with pipes: easier to read/edit, but limited in complexity|
```

which produces output like:

| Table Type | Description |
|:--|:----|
|Commonmark (HTML)| Tables described in pure HTML |
|Github Flavour Markdown (GFM)| Tables described with pipes: easier to read/edit, but limited in complexity|

For simple tables these are much more convenient for working with.
They are limited to single lines of text (i.e. each row must be on a single line), but you can, for example use `<br>` tags to create line breaks and effectively split up paragraphs within cells, if necessary.
You can also continue to use HTML tables when you really need more complexity (but you can also consider whether there is a better way of presenting the data).

## DHIS 2 Bibliography

Bilbliographic references are currently not supported in the markdown version of DHIS 2 documentation.


## Handling multilingual documentation { #docs_8 } 

The DHIS 2 documentation has been translated into a number of different
languages including French, Spanish and Portuguese. If you would like to
create a translation of the documentation or contribute to one of the
existing translations, please contact the DHIS 2 documentation team at
the email provided at the end of this chapter.


## Committing your changes back to GitHub { #docs_10 } 

Once you have finished editing your document, you will need to commit
your changes back to GitHub. Open up a command prompt on Windows or a
shell on Linux, and navigate to the folder where you have placed your
documentation. If you have added any new files or folders to your local
repository, you will need to add them to the source tree with the `git
add
` command, followed by the folder or file name(s) that you have added.
Be sure to include a descriptive comment with your commit.

`
git commit
-m
"Improved documentation on organisation unit imports with CSV."
`

Finally, you should push the changes back to the repository with `git
push origin mybranch`, where "mybranch" is the name of the branch which
you created when you checked out the document source or which you
happent o be working on. In order to do this, you will need the
necessary permissions to commit to the repository.When you have
committed your changes, [you can issue a pull
request](https://github.com/dhis2/dhis2-docs/pulls) to have them merged
with the master branch. You changes will be reviewed by the core
documentation team and tested to ensure they do not break the build, as
well as reviwed for quality. As mentioned previously, you can also push
your changes to your own GitHub repo, if you do not have access to the
main repo, and submit a pull request for your changes to be merged.

If you have any questions, or cannot find that you can get started, just
raise a question on our [development community of practice](https://community.dhis2.org/c/development).


## Markdown support and extensions { #markdown_support_and_extensions }

This section attempts to capture the markdown and extensions that are supported for DHIS 2 documentation, and to provide a preview of the applied styles.


### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading

Body text.

### Horizontal Rules

```
___

---

***
```

___

---

***



### Emphasis

**This is bold text**

__This is bold text__

*This is italic text*

_This is italic text_

~~Strikethrough~~


### Blockquotes

=== "Examples"

    > Blockquotes can also be nested...
    >> ...by using additional greater-than signs right next to each other...
    > > > ...or with spaces between arrows.

=== "Markdown"

    ```
    > Blockquotes can also be nested...
    >> ...by using additional greater-than signs right next to each other...
    > > > ...or with spaces between arrows.
    ```

### Code

Inline `code`

Inline highlighted code `#!js var test = 0;` made within

```
`#!js var test = 0;`
```

Indented code

    // Some comments
    line 1 of code
    line 2 of code
    line 3 of code


Block code "fences"

```
Sample text here...
```

Syntax highlighting

```js
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
```

Long lines

```
Buffalo buffalo (the animals called "buffalo" from the city of Buffalo) [that] Buffalo buffalo buffalo (that the animals from the city bully) buffalo Buffalo buffalo (are bullying these animals from that city).
```

Highlight specific lines

=== "Rendered"

    ``` py hl_lines="2 3"
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```

=== "Markdown"

    ````
    ``` py hl_lines="2 3"
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```
    ````

Add a title

=== "Rendered"

    ``` py hl_lines="2 3" title="bubble_sort.py"
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```

=== "Markdown"

    ````
    ``` py hl_lines="2 3" title="bubble_sort.py"
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```
    ````




### Lists

Unordered

+ Create a list by starting a line with `+`, `-`, or `*`
+ Sub-lists are made by indenting 2 spaces:
    - Marker character change forces new list start:
        * Ac tristique libero volutpat at
        + Facilisis in pretium nisl aliquet

	        ```
	        an indented code block
	        ```

        - Nulla volutpat aliquam velit
+ Very easy!

Ordered

1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa


1. You can use sequential numbers...
1. ...or keep all the numbers as `1.`

Start numbering with offset?:

57. foo
1. bar

Multi-Levels

1. firstitem
2. still first level
    1. second level
    2. still second
        1. third level
        ```
        a block of code at the third level
        ```
        2. still third level
    3. second level again
3. back to the first level
    1. second
        1. Oh, do stop it!

### Tables

| Return Parameter | Description |
| :--------------- | :---------- |
| aoc | Attribute option combination identifier |
| pe | Period identifier |
| ou | Organisation Unit identifier |
| permissions | The permissions: 'mayApprove', 'mayUnapprove', 'mayAccept', 'mayUnaccept', and 'mayReadData' (same definitions as for get single approval status.) |
| state | One of the data approval states (same as for get single approval status.) |
| wf | Data approval workflow identifier |


Right aligned and centred columns

| Return Parameter | Description |
| ---------------: | :----------: |
| aoc | Attribute option combination identifier |
| pe | Period identifier |
| ou | Organisation Unit identifier |
| permissions | The permissions: 'mayApprove', 'mayUnapprove', 'mayAccept', 'mayUnaccept', and 'mayReadData' (same definitions as for get single approval status.) |
| state | One of the data approval states (same as for get single approval status.) |
| wf | Data approval workflow identifier |


### Links

[link text](http://docs.dhis2.org)

[link with title](http://docs.dhis2./org "title text!")

Autoconverted link https://github.com/dhis2


### Images

Images are shown full size with a max-width of 100%

```
![](resources/images/dhis2_screenshots.jpg)
```

![](resources/images/dhis2_screenshots.jpg)


Adding a title automatically causes rendering as a figure.
Inline classes and styles can be added in curly brackets.

```
![The Title](resources/images/dhis2_screenshots.jpg){ .center width=50% }

```

![The Title](resources/images/dhis2_screenshots.jpg){ .center width=50% }


### Youtube

Youtube videos can be embedded in a similar way to images. Simply provide the youtube embed link instead of an image file

``` markdown
![](https://www.youtube.com/embed/UqXSMaXBtD8)
```

![](https://www.youtube.com/embed/UqXSMaXBtD8)

> **Note**
> 
> Be sure to use the "embed" youtube link!

As with images, adding a title will render the video as a figure

```
![DHIS2: Information for Action](https://www.youtube.com/embed/UqXSMaXBtD8)
```

![DHIS2: Information for Action](https://www.youtube.com/embed/UqXSMaXBtD8)


### Admonitions

The following admonitions are supported, with pre-defined styles, in addition to general blockquotes.

#### Note

=== "Note"

    > **Note**
    >
    > A note contains additional information which should be considered or a
    > reference to more information which may be helpful.

=== "Markdown"

    ```
    > **Note**
    >
    > A note contains additional information which should be considered or a
    > reference to more information which may be helpful.
    ```

#### Tip

=== "Tip"

    > **Tip**
    >
    > A tip can be a useful piece of advice, such as how to perform a
    > particular task more efficiently.

=== "Markdown"

    ```
    > **Tip**
    >
    > A tip can be a useful piece of advice, such as how to perform a
    > particular task more efficiently.
    ```

#### Important

=== "Important"

    > **Important**
    >
    > Important information should not be ignored, and usually indicates
    > something which is required by the application.

=== "Markdown"

    ```
    > **Important**
    >
    > Important information should not be ignored, and usually indicates
    > something which is required by the application.
    ```

#### Caution

=== "Caution"

    > **Caution**
    >
    > Information contained in these sections should be carefully
    > considered, and if not heeded, could result in unexpected results in
    > analysis, performance, or functionality.

=== "Markdown"

    ```
    > **Caution**
    >
    > Information contained in these sections should be carefully
    > considered, and if not heeded, could result in unexpected results in
    > analysis, performance, or functionality.
    ```

#### Warning

=== "Warning"

    > **Warning**
    >
    > Information contained in these sections, if not heeded, could result
    > in permanent data loss or affect the overall usability of the system.

=== "Markdown"

    ```
    > **Warning**
    >
    > Information contained in these sections, if not heeded, could result
    > in permanent data loss or affect the overall usability of the system.
    ```

#### Work in progress

=== "Work In Progress"

    > **Work In Progress**
    >
    > Information contained in these sections, will indicate that these are issues or errors we are currently working on.

=== "Markdown"

    ```
    > **Work In Progress**
    >
    > Information contained in these sections, will indicate that these are issues or errors we are currently working on.
    ```

#### Example

=== "Example"

    > **Example**
    >
    > A way to bring special attention to examples.
    >
    > Admonitions can include a code blocks
    >
    > ```js
    > var foo = function (bar) {
    >   return bar++;
    > };
    >
    > console.log(foo(5));
    > ```

=== "Markdown"

    ```
    > **Example**
    >
    > A way to bring special attention to examples.
    >
    > Admonitions can include a code blocks
    >
    > ```js
    > var foo = function (bar) {
    >   return bar++;
    > };
    >
    > console.log(foo(5));
    > ```
    ```


### Mathematical equations

[MathJax](https://www.mathjax.org/) provides support for displaying mathematical content
in the browser with support for mathematical typesetting in different notations
(e.g. [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Mathematics), [MathML](https://en.wikipedia.org/wiki/MathML), [AsciiMath](http://asciimath.org/)).

Blocks must be enclosed in `\[ ... \]` or `$$ ... $$` or `\begin{} ... \end{}` on separate lines.  
Inline blocks must be enclosed in `$...$` or `\(...\)`.

=== "Equations"

    \[
    Indicator = {\frac{BcgVaccinationsUnder1Year}{TargetPopulationUnder1Year}} \times 100
    \]

    \[3 < 4\]

    \begin{align}
        p(v_i=1|\mathbf{h}) & = \sigma\left(\sum_j w_{ij}h_j + b_i\right) \\
        p(h_j=1|\mathbf{v}) & = \sigma\left(\sum_i w_{ij}v_i + c_j\right)
    \end{align}

    The wave equation for \( u \) is

    \begin{equation}
      \frac{\partial^2u}{\partial t^2} = c^2\nabla^2u
    \end{equation}

    where \( \nabla^2 \) is the spatial Laplacian and \( c \) is constant.

    This equation $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$ is inline.

    The homomorphism $f$ is injective if and only if its kernel is only the 
    singleton set $e_G$, because otherwise $\exists a,b\in G$ with $a\neq b$ such that $f(a)=f(b)$.

=== "Markdown"

    ```
    \[
    Indicator = {\frac{BcgVaccinationsUnder1Year}{TargetPopulationUnder1Year}} \times 100
    \]

    \[3 < 4\]

    \begin{align}
        p(v_i=1|\mathbf{h}) & = \sigma\left(\sum_j w_{ij}h_j + b_i\right) \\
        p(h_j=1|\mathbf{v}) & = \sigma\left(\sum_i w_{ij}v_i + c_j\right)
    \end{align}

    The wave equation for \( u \) is

    \begin{equation}
      \frac{\partial^2u}{\partial t^2} = c^2\nabla^2u
    \end{equation}

    where \( \nabla^2 \) is the spatial Laplacian and \( c \) is constant.

    This equation $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$ is inline.

    The homomorphism $f$ is injective if and only if its kernel is only the 
    singleton set $e_G$, because otherwise $\exists a,b\in G$ with $a\neq b$ such that $f(a)=f(b)$.
    ```



### Typographic replacements

| Markdown       | Result
| -------------- |--------
| `(tm)`         | (tm)
| `(c)`          | (c)
| `(r)`          | (r)
| `c/o`          | c/o
| `+/-`          | +/-
| `-->`          | -->
| `<--`          | <--
| `<-->`         | <-->
| `=/=`          | =/=
| `1/4, etc.`    | 1/4, etc.
| `1st 2nd etc.` |1st 2nd etc.


### Subscript / Superscript


	- 19^th^
	- H~2~O

- 19^th^
- H~2~O


++Inserted text++

==Marked text==


### [Footnotes](https://github.com/markdown-it/markdown-it-footnote)

Footnote 1 link[^first].

Footnote 2 link[^second].

Inline footnote^[Text of inline footnote] definition.

Duplicated footnote reference[^second].

[^first]: Footnote **can have markup**

    and multiple paragraphs.

[^second]: Footnote text.


### Definition lists

Term 1
:   Definition 1 with lazy continuation.

Term 2 with *inline markup*
:   Definition 2

        { some code, part of Definition 2 }

    Third paragraph of definition 2.

### Keys

Keys is an extension to make entering and styling keyboard key presses easier. Syntactically, Keys is built around the
`+` symbol.  A key or combination of key presses is surrounded by `++` with each key press separated with a single `+`.

> **Example**
>
> === "Output"
>     ++ctrl+alt+delete++.
>
> === "Markdown"
>     ```
>     ++ctrl+alt+delete++
>     ```

The following key rendering is supported.

=== "Modifier"

    Name            | Display           | Aliases
    --------------- | ----------------- | -------
    `alt`           | ++alt++           |
    `left-alt`      | ++left-alt++      | `lalt`
    `right-alt`     | ++right-alt++     | `ralt`
    `alt-graph`     | ++alt-graph++     | `altgr`
    `command`       | ++command++       | `cmd`
    `left-command`  | ++left-command++  | `lcommand`, `lcmd`, `left-cmd`
    `right-command` | ++right-command++ | `rcommand`, `rcmd`, `right-cmd`
    `control`       | ++control++       | `ctrl`
    `left-control`  | ++left-control++  | `lcontrol`, `lctrl`, `left-ctrl`
    `right-control` | ++right-control++ | `rcontrol`, `rctrl`, `right-ctrl`
    `function`      | ++function++      | `fn`
    `meta`          | ++meta++          |
    `left-meta`     | ++left-meta++     | `lmeta`
    `right-meta`    | ++right-meta++    | `rmeta`
    `option`        | ++option++        | `opt`
    `left-option`   | ++left-option++   | `loption`, `lopt`, `left-opt`
    `right-option`  | ++right-option++  | `roption`, `ropt`, `right-opt`
    `shift`         | ++shift++         |
    `left-shift`    | ++left-shift++    | `lshift`
    `right-shift`   | ++right-shift++   | `rshift`
    `super`         | ++super++         |
    `left-super`    | ++left-super++    | `lsuper`
    `right-super`   | ++right-super++   | `rsuper`
    `windows`       | ++windows++       | `win`
    `left-windows`  | ++left-windows++  | `lwindows`, `left-win`, `lwin`
    `right-windows` | ++right-windows++ | `rwindows`, `right-win`, `rwin`

=== "Function"

    Name  | Display | Aliases
    ----- | ------- | -------
    `f1`  | ++f1++  |
    `f2`  | ++f2++  |
    `f3`  | ++f3++  |
    `f4`  | ++f4++  |
    `f5`  | ++f5++  |
    `f6`  | ++f6++  |
    `f7`  | ++f7++  |
    `f8`  | ++f8++  |
    `f9`  | ++f9++  |
    `f10` | ++f10++ |
    `f11` | ++f11++ |
    `f12` | ++f12++ |
    `f13` | ++f13++ |
    `f14` | ++f14++ |
    `f15` | ++f15++ |
    `f16` | ++f16++ |
    `f17` | ++f17++ |
    `f18` | ++f18++ |
    `f19` | ++f19++ |
    `f20` | ++f20++ |
    `f21` | ++f21++ |
    `f22` | ++f22++ |
    `f23` | ++f23++ |
    `f24` | ++f24++ |

=== "Alphanumeric"

    Name    | Display   | Aliases
    ------- | --------- | -------
    `0`     | ++0++     |
    `1`     | ++1++     |
    `2`     | ++2++     |
    `3`     | ++3++     |
    `4`     | ++4++     |
    `5`     | ++5++     |
    `6`     | ++6++     |
    `7`     | ++7++     |
    `8`     | ++8++     |
    `9`     | ++9++     |
    `a`     | ++a++     |
    `b`     | ++b++     |
    `c`     | ++c++     |
    `d`     | ++d++     |
    `e`     | ++e++     |
    `f`     | ++f++     |
    `g`     | ++g++     |
    `h`     | ++h++     |
    `i`     | ++i++     |
    `j`     | ++j++     |
    `k`     | ++k++     |
    `l`     | ++l++     |
    `m`     | ++m++     |
    `n`     | ++n++     |
    `o`     | ++o++     |
    `p`     | ++p++     |
    `q`     | ++q++     |
    `r`     | ++r++     |
    `s`     | ++s++     |
    `t`     | ++t++     |
    `u`     | ++u++     |
    `v`     | ++v++     |
    `w`     | ++w++     |
    `x`     | ++x++     |
    `y`     | ++y++     |
    `z`     | ++z++     |
    `space` | ++space++ | `spc`

=== "Punctuation"

    Name            | Display           | Aliases
    --------------- | ----------------- | -------
    `backslash`     | ++backslash++     |
    `bar`           | ++bar++           | `pipe`
    `brace-left`    | ++brace-left++    | `open-brace`
    `brace-right`   | ++brace-right++   | `close-bracket`
    `bracket-left`  | ++bracket-left++  | `open-bracket`
    `bracket-right` | ++bracket-right++ | `close-bracket`
    `colon`         | ++colon++         |
    `comma`         | ++comma++         |
    `double-quote`  | ++double-quote++  | `dblquote`
    `equal`         | ++equal++         |
    `exclam`        | ++exclam++        | `exclamation`
    `grave`         | ++grave++         | `grave-accent`
    `greater`       | ++greater++       | `greater-than`, `gt`
    `less`          | ++less++          | `less-than`, `lt`
    `minus`         | ++minus++         | `hyphen`
    `period`        | ++period++        |
    `plus`          | ++plus++          |
    `question`      | ++question++      | `question-mark`
    `semicolon`     | ++semicolon++     |
    `single-quote`  | ++single-quote++  |
    `slash`         | ++slash++         |
    `tilde`         | ++tilde++         |
    `underscore`    | ++underscore++    |

=== "Navigation"

    Name          | Display         | Aliases
    ------------- | --------------- | -------
    `arrow-up`    | ++arrow-up++    | `up`
    `arrow-down`  | ++arrow-down++  | `down`
    `arrow-left`  | ++arrow-left++  | `left`
    `arrow-right` | ++arrow-right++ | `right`
    `page-up`     | ++page-up++     | `prior`, `page-up`, `pg-up`
    `page-down`   | ++page-down++   | `next`, `page-dn`, `pg-dn`
    `home`        | ++home++        |
    `end`         | ++end++         |
    `tab`         | ++tab++         | `tabulator`

=== "Editing"

    Name        | Display       | Aliases
    ----------- | ------------- | -------
    `backspace` | ++backspace++ | `back`, `bksp`
    `delete`    | ++delete++    | `del`
    `insert`    | ++insert++    | `ins`

=== "Action"

    Name           | Display          | Aliases
    -------------- | -----------------| -------
    `break`        | ++break++        | `cancel`
    `caps-lock`    | ++caps-lock++    | `capital`, `cplk`
    `clear`        | ++clear++        | `clr`
    `eject`        | ++eject++        |
    `enter`        | ++enter++        | `return`
    `escape`       | ++escape++       | `esc`
    `help`         | ++help++         |
    `print-screen` | ++print-screen++ | `prtsc`
    `scroll-lock`  | ++scroll-lock++  | `scroll`

=== "Numeric Keypad"

    Name            | Display           | Aliases
    --------------- | ----------------- | -------
    `num0`          | ++num0++          |
    `num1`          | ++num1++          |
    `num2`          | ++num2++          |
    `num3`          | ++num3++          |
    `num4`          | ++num4++          |
    `num5`          | ++num5++          |
    `num6`          | ++num6++          |
    `num7`          | ++num7++          |
    `num8`          | ++num8++          |
    `num9`          | ++num9++          |
    `num-asterisk`  | ++num-asterisk++  | `multiply`
    `num-clear`     | ++num-clear++     |
    `num-delete`    | ++num-delete++    | `num-del`
    `num-equal`     | ++num-equal++     |
    `num-lock`      | ++num-lock++      | `numlk`, `numlock`
    `num-minus`     | ++num-minus++     | `subtract`
    `num-plus`      | ++num-plus++      | `add`
    `num-separator` | ++num-separator++ | `decimal`, `separator`
    `num-slash`     | ++num-slash++     | `divide`
    `num-enter`     | ++num-enter++     |

=== "Extra Keys"

    Name                | Display               | Aliases
    ------------------- | --------------------- | -------
    `backtab`           | ++backtab++           | `bktab`
    `browser-back`      | ++browser-back++      |
    `browser-favorites` | ++browser-favorites++ | `favorites`
    `browser-forward`   | ++browser-forward++   | `forward`
    `browser-home`      | ++browser-home++      |
    `browser-refresh`   | ++browser-refresh++   | `refresh`
    `browser-search`    | ++browser-search++    | `search`
    `browser-stop`      | ++browser-stop++      |
    `copy`              | ++copy++              |
    `context-menu`      | ++context-menu++      | `apps`, `menu`
    `fingerprint`       | ++fingerprint++       | `fingerprint`
    `mail`              | ++mail++              | `launch-mail`
    `media`             | ++media++             | `launch-media`
    `media-next-track`  | ++media-next-track++  | `next-track`
    `media-pause`       | ++media-pause++       | `pause`
    `media-play`        | ++media-play++        | `play`
    `media-play-pause`  | ++media-play-pause++  | `play-pause`
    `media-prev-track`  | ++media-prev-track++  | `prev-track`
    `media-stop`        | ++media-stop++        | `stop`
    `power`             | ++power++             |
    `print`             | ++print++             |
    `reset`             | ++reset++             |
    `select`            | ++select++            |
    `sleep`             | ++sleep++             |
    `volume-down`       | ++volume-down++       | `vol-down`
    `volume-mute`       | ++volume-mute++       | `mute`
    `volume-up`         | ++volume-up++         | `vol-up`
    `zoom`              | ++zoom++              |

=== "Mouse"

    Name            | Display           | Aliases
    --------------- | ----------------- | -------
    `left-button`   | ++left-button++   | `lbutton`
    `middle-button` | ++middle-button++ | `mbutton`
    `right-button`  | ++right-button++  | `rbutton`
    `x-button1`     | ++x-button1++     | `xbutton1`
    `x-button2`     | ++x-button2++     | `xbutton2`


### Emojies

Several sets of emojies are supported by entering the emoji name surrounded by colons: e.g `:smile:`.
Below are list of common sets, those that are not rendered are currently not supported.

=== "People"

    :bowtie: :smile: :laughing: :blush: :smiley: :relaxed: :smirk: :heart_eyes: :kissing_heart: :kissing_closed_eyes: :flushed: :relieved: :satisfied: :grin: :wink: :stuck_out_tongue_winking_eye: :stuck_out_tongue_closed_eyes: :grinning: :kissing: :kissing_smiling_eyes: :stuck_out_tongue: :sleeping: :worried: :frowning: :anguished: :open_mouth: :grimacing: :confused: :hushed: :expressionless: :unamused: :sweat_smile: :sweat: :disappointed_relieved: :weary: :pensive: :disappointed: :confounded: :fearful: :cold_sweat: :persevere: :cry: :sob: :joy: :astonished: :scream: :neckbeard: :tired_face: :angry: :rage: :triumph: :sleepy: :yum: :mask: :sunglasses: :dizzy_face: :imp: :smiling_imp: :neutral_face: :no_mouth: :innocent: :alien: :yellow_heart: :blue_heart: :purple_heart: :heart: :green_heart: :broken_heart: :heartbeat: :heartpulse: :two_hearts: :revolving_hearts: :cupid: :sparkling_heart: :sparkles: :star: :star2: :dizzy: :boom: :collision: :anger: :exclamation: :question: :grey_exclamation: :grey_question: :zzz: :dash: :sweat_drops: :notes: :musical_note: :fire: :hankey: :poop: :shit: :+1: :thumbsup: :-1: :thumbsdown: :ok_hand: :punch: :facepunch: :fist: :v: :wave: :hand: :raised_hand: :open_hands: :point_up: :point_down: :point_left: :point_right: :raised_hands: :pray: :point_up_2: :clap: :muscle: :metal: :fu: :walking: :runner: :running: :couple: :family: :two_men_holding_hands: :two_women_holding_hands: :dancer: :dancers: :ok_woman: :no_good: :information_desk_person: :raising_hand: :bride_with_veil: :person_with_pouting_face: :person_frowning: :bow: :couplekiss: :couple_with_heart: :massage: :haircut: :nail_care: :boy: :girl: :woman: :man: :baby: :older_woman: :older_man: :person_with_blond_hair: :man_with_gua_pi_mao: :man_with_turban: :construction_worker: :cop: :angel: :princess: :smiley_cat: :smile_cat: :heart_eyes_cat: :kissing_cat: :smirk_cat: :scream_cat: :crying_cat_face: :joy_cat: :pouting_cat: :japanese_ogre: :japanese_goblin: :see_no_evil: :hear_no_evil: :speak_no_evil: :guardsman: :skull: :feet: :lips: :kiss: :droplet: :ear: :eyes: :nose: :tongue: :love_letter: :bust_in_silhouette: :busts_in_silhouette: :speech_balloon: :thought_balloon:

=== "Nature"

    :sunny: :umbrella: :cloud: :snowflake: :snowman: :zap: :cyclone: :foggy: :ocean: :cat: :dog: :mouse: :hamster: :rabbit: :wolf: :frog: :tiger: :koala: :bear: :pig: :pig_nose: :cow: :boar: :monkey_face: :monkey: :horse: :racehorse: :camel: :sheep: :elephant: :panda_face: :snake: :bird: :baby_chick: :hatched_chick: :hatching_chick: :chicken: :penguin: :turtle: :bug: :honeybee: :ant: :beetle: :snail: :octopus: :tropical_fish: :fish: :whale: :whale2: :dolphin: :cow2: :ram: :rat: :water_buffalo: :tiger2: :rabbit2: :dragon: :goat: :rooster: :dog2: :pig2: :mouse2: :ox: :dragon_face: :blowfish: :crocodile: :dromedary_camel: :leopard: :cat2: :poodle: :paw_prints: :bouquet: :cherry_blossom: :tulip: :four_leaf_clover: :rose: :sunflower: :hibiscus: :maple_leaf: :leaves: :fallen_leaf: :herb: :mushroom: :cactus: :palm_tree: :evergreen_tree: :deciduous_tree: :chestnut: :seedling: :blossom: :ear_of_rice: :shell: :globe_with_meridians: :sun_with_face: :full_moon_with_face: :new_moon_with_face: :new_moon: :waxing_crescent_moon: :first_quarter_moon: :waxing_gibbous_moon: :full_moon: :waning_gibbous_moon: :last_quarter_moon: :waning_crescent_moon: :last_quarter_moon_with_face: :first_quarter_moon_with_face: :moon: :earth_africa: :earth_americas: :earth_asia: :volcano: :milky_way: :partly_sunny: :octocat: :squirrel:

=== "Objects"

    :bamboo: :gift_heart: :dolls: :school_satchel: :mortar_board: :flags: :fireworks: :sparkler: :wind_chime: :rice_scene: :jack_o_lantern: :ghost: :santa: :christmas_tree: :gift: :bell: :no_bell: :tanabata_tree: :tada: :confetti_ball: :balloon: :crystal_ball: :cd: :dvd: :floppy_disk: :camera: :video_camera: :movie_camera: :computer: :tv: :iphone: :phone: :telephone: :telephone_receiver: :pager: :fax: :minidisc: :vhs: :sound: :speaker: :mute: :loudspeaker: :mega: :hourglass: :hourglass_flowing_sand: :alarm_clock: :watch: :radio: :satellite: :loop: :mag: :mag_right: :unlock: :lock: :lock_with_ink_pen: :closed_lock_with_key: :key: :bulb: :flashlight: :high_brightness: :low_brightness: :electric_plug: :battery: :calling: :email: :mailbox: :postbox: :bath: :bathtub: :shower: :toilet: :wrench: :nut_and_bolt: :hammer: :seat: :moneybag: :yen: :dollar: :pound: :euro: :credit_card: :money_with_wings: :e-mail: :inbox_tray: :outbox_tray: :envelope: :incoming_envelope: :postal_horn: :mailbox_closed: :mailbox_with_mail: :mailbox_with_no_mail: :door: :smoking: :bomb: :gun: :hocho: :pill: :syringe: :page_facing_up: :page_with_curl: :bookmark_tabs: :bar_chart: :chart_with_upwards_trend: :chart_with_downwards_trend: :scroll: :clipboard: :calendar: :date: :card_index: :file_folder: :open_file_folder: :scissors: :pushpin: :paperclip: :black_nib: :pencil2: :straight_ruler: :triangular_ruler: :closed_book: :green_book: :blue_book: :orange_book: :notebook: :notebook_with_decorative_cover: :ledger: :books: :bookmark: :name_badge: :microscope: :telescope: :newspaper: :football: :basketball: :soccer: :baseball: :tennis: :8ball: :rugby_football: :bowling: :golf: :mountain_bicyclist: :bicyclist: :horse_racing: :snowboarder: :swimmer: :surfer: :ski: :spades: :hearts: :clubs: :diamonds: :gem: :ring: :trophy: :musical_score: :musical_keyboard: :violin: :space_invader: :video_game: :black_joker: :flower_playing_cards: :game_die: :dart: :mahjong: :clapper: :memo: :pencil: :book: :art: :microphone: :headphones: :trumpet: :saxophone: :guitar: :shoe: :sandal: :high_heel: :lipstick: :boot: :shirt: :tshirt: :necktie: :womans_clothes: :dress: :running_shirt_with_sash: :jeans: :kimono: :bikini: :ribbon: :tophat: :crown: :womans_hat: :mans_shoe: :closed_umbrella: :briefcase: :handbag: :pouch: :purse: :eyeglasses: :fishing_pole_and_fish: :coffee: :tea: :sake: :baby_bottle: :beer: :beers: :cocktail: :tropical_drink: :wine_glass: :fork_and_knife: :pizza: :hamburger: :fries: :poultry_leg: :meat_on_bone: :spaghetti: :curry: :fried_shrimp: :bento: :sushi: :fish_cake: :rice_ball: :rice_cracker: :rice: :ramen: :stew: :oden: :dango: :egg: :bread: :doughnut: :custard: :icecream: :ice_cream: :shaved_ice: :birthday: :cake: :cookie: :chocolate_bar: :candy: :lollipop: :honey_pot: :apple: :green_apple: :tangerine: :lemon: :cherries: :grapes: :watermelon: :strawberry: :peach: :melon: :banana: :pear: :pineapple: :sweet_potato: :eggplant: :tomato: :corn:

=== "Places"

    :house: :house_with_garden: :school: :office: :post_office: :hospital: :bank: :convenience_store: :love_hotel: :hotel: :wedding: :church: :department_store: :european_post_office: :city_sunrise: :city_sunset: :japanese_castle: :european_castle: :tent: :factory: :tokyo_tower: :japan: :mount_fuji: :sunrise_over_mountains: :sunrise: :stars: :statue_of_liberty: :bridge_at_night: :carousel_horse: :rainbow: :ferris_wheel: :fountain: :roller_coaster: :ship: :speedboat: :boat: :sailboat: :rowboat: :anchor: :rocket: :airplane: :helicopter: :steam_locomotive: :tram: :mountain_railway: :bike: :aerial_tramway: :suspension_railway: :mountain_cableway: :tractor: :blue_car: :oncoming_automobile: :car: :red_car: :taxi: :oncoming_taxi: :articulated_lorry: :bus: :oncoming_bus: :rotating_light: :police_car: :oncoming_police_car: :fire_engine: :ambulance: :minibus: :truck: :train: :station: :train2: :bullettrain_front: :bullettrain_side: :light_rail: :monorail: :railway_car: :trolleybus: :ticket: :fuelpump: :vertical_traffic_light: :traffic_light: :warning: :construction: :beginner: :atm: :slot_machine: :busstop: :barber: :hotsprings: :checkered_flag: :crossed_flags: :izakaya_lantern: :moyai: :circus_tent: :performing_arts: :round_pushpin: :triangular_flag_on_post: :jp: :kr: :cn: :us: :fr: :es: :it: :ru: :gb: :uk: :de:

=== "Symbols"

    :one: :two: :three: :four: :five: :six: :seven: :eight: :nine: :keycap_ten: :1234: :zero: :hash: :symbols: :arrow_backward: :arrow_down: :arrow_forward: :arrow_left: :capital_abcd: :abcd: :abc: :arrow_lower_left: :arrow_lower_right: :arrow_right: :arrow_up: :arrow_upper_left: :arrow_upper_right: :arrow_double_down: :arrow_double_up: :arrow_down_small: :arrow_heading_down: :arrow_heading_up: :leftwards_arrow_with_hook: :arrow_right_hook: :left_right_arrow: :arrow_up_down: :arrow_up_small: :arrows_clockwise: :arrows_counterclockwise: :rewind: :fast_forward: :information_source: :ok: :twisted_rightwards_arrows: :repeat: :repeat_one: :new: :top: :up: :cool: :free: :ng: :cinema: :koko: :signal_strength: :u5272: :u5408: :u55b6: :u6307: :u6708: :u6709: :u6e80: :u7121: :u7533: :u7a7a: :u7981: :sa: :restroom: :mens: :womens: :baby_symbol: :no_smoking: :parking: :wheelchair: :metro: :baggage_claim: :accept: :wc: :potable_water: :put_litter_in_its_place: :secret: :congratulations: :m: :passport_control: :left_luggage: :customs: :ideograph_advantage: :cl: :sos: :id: :no_entry_sign: :underage: :no_mobile_phones: :do_not_litter: :non-potable_water: :no_bicycles: :no_pedestrians: :children_crossing: :no_entry: :eight_spoked_asterisk: :eight_pointed_black_star: :heart_decoration: :vs: :vibration_mode: :mobile_phone_off: :chart: :currency_exchange: :aries: :taurus: :gemini: :cancer: :leo: :virgo: :libra: :scorpius: :sagittarius: :capricorn: :aquarius: :pisces: :ophiuchus: :six_pointed_star: :negative_squared_cross_mark: :a: :b: :ab: :o2: :diamond_shape_with_a_dot_inside: :recycle: :end: :on: :soon: :clock1: :clock130: :clock10: :clock1030: :clock11: :clock1130: :clock12: :clock1230: :clock2: :clock230: :clock3: :clock330: :clock4: :clock430: :clock5: :clock530: :clock6: :clock630: :clock7: :clock730: :clock8: :clock830: :clock9: :clock930: :heavy_dollar_sign: :copyright: :registered: :tm: :x: :heavy_exclamation_mark: :bangbang: :interrobang: :o: :heavy_multiplication_x: :heavy_plus_sign: :heavy_minus_sign: :heavy_division_sign: :white_flower: :100: :heavy_check_mark: :ballot_box_with_check: :radio_button: :link: :curly_loop: :wavy_dash: :part_alternation_mark: :trident: :black_square: :white_square: :white_check_mark: :black_square_button: :white_square_button: :black_circle: :white_circle: :red_circle: :large_blue_circle: :large_blue_diamond: :large_orange_diamond: :small_blue_diamond: :small_orange_diamond: :small_red_triangle: :small_red_triangle_down: :shipit:


### Mermaid

[Mermaid.js](https://mermaid-js.github.io/mermaid/) diagrams are now supported natively.


#### Flowcharts

[Flowcharts](https://mermaid-js.github.io/mermaid/#/flowchart) are diagrams that represent workflows or processes. The steps
are rendered as nodes of various kinds and are connected by edges, describing
the necessary order of steps:


=== "Example"

    ``` mermaid
    graph LR
    A[Start] --> B{Error?};
    B -->|Yes| C[Hmm...];
    C --> D[Debug];
    D --> B;
    B ---->|No| E[Yay!];
    ```

=== "Markdown"

    ```

        ``` mermaid
        graph LR
        A[Start] --> B{Error?};
        B -->|Yes| C[Hmm...];
        C --> D[Debug];
        D --> B;
        B ---->|No| E[Yay!];
        ```

    ```

#### Sequence diagrams

[Sequence diagrams](https://mermaid-js.github.io/mermaid/#/sequenceDiagram) describe a specific scenario as sequential interactions 
between multiple objects or actors, including the messages that are exchanged
between those actors:


=== "Example"

    ``` mermaid
    %%{init: {'mirrorActors': false } }%%

    sequenceDiagram

        autonumber
        participant G as package URL<br><br>(github/S3)
        participant M as metatran
        participant T as transifex
        participant F as filesystem<br><br>(path)
        G->>M: package file 
        T->>M: pull latest translation strings
        opt 
            note over M: swap base language
        end

        opt 
            note over M: include/exclude languages
        end
        M->>+F: New package file
    ```

=== "Markdown"

    ```
        ``` mermaid
        %%{init: {'mirrorActors': false } }%%

        sequenceDiagram

            autonumber
            participant G as package URL<br><br>(github/S3)
            participant M as metatran
            participant T as transifex
            participant F as filesystem<br><br>(path)
            G->>M: package file 
            T->>M: pull latest translation strings
            opt 
                note over M: swap base language
            end

            opt 
                note over M: include/exclude languages
            end
            M->>+F: New package file
        ```
    ```



#### git graphs


[Git graphs](https://mermaid.js.org/syntax/gitgraph.html#gitgraph-diagrams) provide a pictorial representation of git commits and git actions on various branches.


=== "Example"

    ``` mermaid
    %%{init: { 'logLevel': 'debug', 'theme': 'dark', 'gitGraph': {
    'showBranches': true, 
    'showCommitLabel':false, 
    'mainBranchName': 'master'}} 
    }%%

    gitGraph
        commit
        commit
        branch "2.39"
        checkout "2.39"
        commit
        checkout master
        commit
        checkout "2.39"
        branch "patch/2.39.0"
        checkout "patch/2.39.0"
        commit
        checkout master
        commit
        checkout "2.39"
        commit
        checkout "patch/2.39.0"
        commit tag: "2.39.0"
        checkout master
        commit
        checkout "2.39"
        commit
        commit
        checkout "master"
        commit
        checkout "2.39"
        branch "patch/2.39.1"
        checkout "patch/2.39.1"
        commit
        commit tag: "2.39.1"
        checkout "2.39"
        commit
        checkout "patch/2.39.1"
        branch "hotfix 2.39.1.1"
        commit tag: "2.39.1.1"
    ```

=== "Markdown"

    ```
        ``` mermaid
        %%{init: { 'logLevel': 'debug', 'theme': 'dark', 'gitGraph': {
        'showBranches': true, 
        'showCommitLabel':false, 
        'mainBranchName': 'master'}} 
        }%%

        gitGraph
            commit
            commit
            branch "2.39"
            checkout "2.39"
            commit
            checkout master
            commit
            checkout "2.39"
            branch "patch/2.39.0"
            checkout "patch/2.39.0"
            commit
            checkout master
            commit
            checkout "2.39"
            commit
            checkout "patch/2.39.0"
            commit tag: "2.39.0"
            checkout master
            commit
            checkout "2.39"
            commit
            commit
            checkout "master"
            commit
            checkout "2.39"
            branch "patch/2.39.1"
            checkout "patch/2.39.1"
            commit
            commit tag: "2.39.1"
            checkout "2.39"
            commit
            checkout "patch/2.39.1"
            branch "hotfix 2.39.1.1"
            commit tag: "2.39.1.1"
        ```

    ```
    
