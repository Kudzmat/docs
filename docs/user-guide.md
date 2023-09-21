# User Guide

!!! info

    This guide provides technical guidance and exploration of the PyScript
    platform.

    While we endeavour to write clearly, some of the content in this user guide
    will not be suitable for beginners. We assume readers already have Python
    or web development experience.

    We [welcome feedback](https://github.com/pyscript/docs/issues) to help us
    improve.

This guide has three aims:

1. A clear overview, context setting and sign-posting for all things PyScript.
2. Exploration of PyScript in substantial technical detail.
3. Demonstration of the features of PyScript working together in real-world
   example applications.

_Read this page in full_: you will acquire a comprehensive overview of the
PyScript platform along with suggestions for where next to explore and learn.

For more dynamic support, join in the PyScript conversation on our
[discord server](https://discord.gg/HxvBtukrg2). There you'll find core
developers, community contributors and a flourishing forum for those creating
projects with PyScript. Should you wish to engage with the development of
PyScript, you are welcome to engage and make contributions via
[the project's GitHub organisation](https://github.com/pyscript).

Finally, the examples listed at the end of this page are all freely available
and copiously commented on [pyscript.com](pyscript.com).

!!! note

    Many of these examples come from contributors in our wonderful
    community. If you believe you have a project that would make a good
    demonstration example, please don't hesitate to
    [get in touch](https://discord.gg/HxvBtukrg2).

## What is PyScript?

[PyScript](pyscript.net) is a platform for [Python](python.org) in the
[browser](https://en.wikipedia.org/wiki/Web_browser).

PyScript brings together two of the most vibrant technical ecosystems on the
planet. If [the web](https://en.wikipedia.org/wiki/World_Wide_Web) and Python
had a baby, you'd get PyScript.

PyScript works because modern browsers support
[WebAssembly](https://webassembly.org/) (abbreviated to WASM) - an
[instruction set](https://en.wikipedia.org/wiki/Instruction_set_architecture)
for a [virtual machine](https://en.wikipedia.org/wiki/Virtual_machine) with
an open specification and near native performance. PyScript takes
versions of the Python interpreter compiled to WASM, and makes them easy to use
inside the browser.

At the core of PyScript is a _philosophy of digital empowerment_. The web is
the world's most ubiquitous computing platform, mature and familiar to billions
of people. Python is one of the
[world's most popular programming languages](https://spectrum.ieee.org/the-top-programming-languages-2023):
it is easy to teach and learn, used in a plethora of existing domains
(such as data science, games, embedded systems, artificial intelligence,
finance, physics  and film production - to name but a few), and the Python
ecosystem contains a huge number of popular and powerful libraries to address
its many uses.

PyScript brings together the ubiquity, familiarity and accessibility of the web
with the power, depth and expressiveness of Python. It means PyScript isn't
just for programming experts but, as we like to say, for the 99% of the rest of
the planet who use computers.

## Features

<dl>
    <dt><em>All the web</em></dt>
    <dd>
    <p>Pyscript gives you <a href="#the-dom">full access to the DOM</a> and all
    the <a href="https://developer.mozilla.org/en-US/docs/Web/API">web
    APIs implemented by your browser</a>.</p>

    <p>Thanks to the <a href="#ffi">foreign
    function interface</a> (FFI), it is easy for Python to work within your
    browser, including with third party JavaScript libraries that may be
    included in the page.</p>

    <p>The FFI is bi-directional ~ it also enables JavaScript to access the
    power of PyScript.</p></dd>

    <dt><em>All of Python</em></dt>
    <dd>
    <p>PyScript brings you two Python interpreters:</p>
    <ol>
        <li><a href="https://pyodide.org/">Pyodide</a> - the original standard
        CPython interpreter you know and love, but compiled to WebAssembly.
        </li>
        <li><a href="https://micropython.org/">MicroPython</a> - a lean and
        efficient reimplementation of Python3 that includes a comprehensive
        subset of the standard library, compiled to WebAssembly.</li>
    </ol>
    <div class="admonition warning">
        <p class="admonition-title">Warning</p>
        <p>Currently, only Pyodide is enabled in PyScript.</p>
        <p>This will <strong>change very soon</strong> once we complete our integration testing and
        evaluation steps for MicroPython. However, the documentation relating
        to MicroPython is currently correct and is included to indicate what
        you have to look forward to.</p>
    </div>
    <p>Because it is just regular CPython, Pyodide puts Python's deep and
    <a href="https://pypi.org/">diverse ecosystem</a> of libraries, frameworks
    and modules at your disposal. If you find yourself encountering some sort
    of computing problem, there's probably a Python library to help you with
    it. If you use a favourite library in Python, now you can use it in your
    browser and share your work with ease via a URL.</p>
    <p>MicroPython, because of its small size (170k) and speed, is especially
    suited to running on more constrained browsers, such as those on mobile
    or tablet devices. It includes a powerful sub-set of the Python standard
    library and efficiently exposes the expressiveness of Python to the
    browser.</p>
    <p>Both Python interpreters supported by PyScript implement the same 
    FFI to bridge the gap between the worlds of Python and the browser.</p>
    </dd>

    <dt><em>AI and Data science built in</em></dt>
    <dd>Python is famous for its extraordinary usefulness in artificial
    intelligence and data science. The Pyodide interpreter comes with many of
    the libraries you need for this sort of work already baked in.</dd>

    <dt><em>Mobile friendly MicroPython</em></dt>
    <dd>
    <p>Thanks to MicroPython in PyScript, there is a compelling story for
    Python on mobile.</p>

    <p>MicroPython is small and fast enough that your app will start quickly
    on first load, and almost instantly (due to the cache) on subsequent
    runs.</p></dd>

    <dt><em>Parallel execution</em></dt>
    <dd>Thanks to a browser technology called
    <a href="https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API">web workers</a>
    expensive and blocking computation can run somewhere other than the main
    application thread that controls the user interface. When such work is done
    on the main thread, the browser appears frozen. Web workers ensure
    expensive blocking computation happens elsewhere. Think of workers as
    independent subprocesses in your web page.</dd>

    <dt><em>Rich and powerful plugins</em></dt>
    <dd>
    <p>As you'll see, PyScript has a small, efficient yet powerful core called
    <a href="https://github.com/pyscript/polyscript">PolyScript</a>.</p>
    <p>Most of the functionality of PyScript is actually implemented through
    PolyScript's <a href="#plugins">plugin system</a>.</p>

    <p>This approach means we get a clear separation of concerns: PolyScript
    can focus on being small, efficient and powerful, whereas the PyScript
    related plugins allow us to build upon the generic features provided by
    PolyScript.</p>
    <p>More importantly, because there is a plugin system, folks
    <em>independent of the PyScript core team</em> have a way to create their
    own plugins so we get a rich ecosystem of functionality that reflects the
    unique and diverse needs of PyScript's users.</p>
    </dd>
</dl>

## First steps

It's simple:

* tell your browser to use PyScript, then,
* tell PyScript how to run your Python code.

For the browser to use PyScript, simply add a `<script>` tag, whose `src`
attribute references a CDN url for `pyscript.core`, to your HTML document's
`<head>`. You may also add a reference to optional PyScript related CSS:

**TODO: USE CORRECT CDN URL**:

```html title="Reference PyScript in your HTML"
<!doctype html>
<html>
    <head>
        <!-- Recommended meta tags -->
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width,initial-scale=1.0">
        <!-- optional PyScript CSS -->
        <link rel="stylesheet" href="https://pyscript.net/snapshots/2023.09.1.RC1/core.css">
        <!-- This script tag bootstraps PyScript -->
        <script type="module" src="https://pyscript.net/snapshots/2023.09.1.RC1/core.js"></script>
    </head>
    <body>
        <!-- your code goes here... -->
    </body>
</html>
```

There are two ways to tell PyScript how to find your code.

* With a standard HTML `<script>` tag whose `type` attribute is either `py`
  (for Pyodide) or `mpy` (for MicroPython). **This is currently the
  recommended way**.
* Via the bespoke `<py-script>` (Pyodide) and `<mpy-script>` (MicroPython)
  tags. Historically, this used to be the only way to reference your code.

These should be inserted into the `<body>` of your HTML document.

In both cases either use the `src` attribute to reference a Python
file containing your code, or inline your code between the opening and closing
tags. **We recommend you use the `src` attribute method**, but retain the
ability to include code between tags for convenience.

Here's the `<script>` tag method using the `src` attribute to reference the URL
for a `main.py` Python file.

```html title="Using the script tag with a source file"
<script type="mpy" src="main.py"></script>
```

...and here's the `<py-script>` tag with inline Python code.

```html title="Using the py-script tag with inline code"
<py-script>
import sys
from pyscript import display


display(sys.version)
</py-script>
```

The browser's tab displaying the website running PyScript is an isolated
computing sandbox. Define the Python environment in which your code will
run with [configuration options](#configuration) (discussed later in this
document).

The `<script>` and `<py-script>` / `<mpy-script>` tags can have the following
attributes:

* `src` - the content of the tag is ignored and the Python code in the
  referenced file is evaluated instead. **This is the recommended way to
  reference your Python code.**
* `config` - your code will only be evaluated after the referenced
  configuration has been parsed. Since configuration can be JSON (or a TOML
  file), `config='{"packages":["numpy"]}'` and `config="./config.json"` or
  `config="./config.toml"` are all valid.
* `async` - your Python code is run asynchronously (awaited), rather than in a
  blocking manner.
* `worker` - a flag to indicate your Python code is to be run on a web worker
  instead of the "main thread" that looks after the user interface.

!!! tip 

    If you want to run code on both the main thread and in a worker, be
    explicit and use separate tags.

    ```html
    <script type="mpy" src="main.py"></script>  <!-- on the main thread -->
    <script type="py" src="worker.py" worker config="pyconfig.toml"></script> <!-- on the worker -->
    ```

    Notice how different interpreters can be used in different contexts.

## Architecture

There are two important aspects of PyScript's architecture:

1. A small, efficient and powerful kernel called
   [PolyScript](https://github.com/pyscript/polyscript) is the foundation
   upon which PyScript and plugins are built.
2. The PyScript [stack](https://en.wikipedia.org/wiki/Solution_stack) inside
   the browser is relatively simple and easy to understand.

### PolyScript

[PolyScript](https://github.com/pyscript/polyscript) is the core of PyScript.

!!! info

    Unless you are an advanced user, you probably don't need to know much more
    than PolyScript exists, and it can be safely ignored.

PolyScript's purpose is to bootstrap the platform and provide all the necessary
core capabilities. Setting aside PyScript for a moment, to use
*just PolyScript* requires a `<script>` reference to it, along with a further
`<script>` tag defining how to run some code.

```html title="Bootstrapping with PolyScript"
<!doctype html>
<html>
    <head>
        <!-- this is a way to automatically bootstrap polyscript -->
        <script type="module" src="https://pyscript.net/snapshots/2023.09.1.RC1/core.js"></script>
    </head>
    <body>
        <!--
            Run some Python code with the MicroPython interpreter, but without
            the extra benefits provided by PyScript.
        -->
        <script type="micropython">
            from js import document
            document.body.textContent = 'polyscript'
        </script>
    </body>
</html>
```

PolyScript's capabilities, upon which PyScript is built, can be summarised as:

* Evaluation of code via [`<script>` tags](https://pyscript.github.io/polyscript/#how-scripts-work).
* Handling of
  [browser events](https://pyscript.github.io/polyscript/#how-events-work)
  via code evaluated by an interpreter supported by PolyScript.
* A [clear way to use workers](https://pyscript.github.io/polyscript/#xworker)
  via the `XWorker` class and its related reference, `xworker`.
* [Custom scripts](https://pyscript.github.io/polyscript/#custom-scripts) to
  enrich PolyScript's capabilities.
* A [ready event](https://pyscript.github.io/polyscript/#ready-event)
  dispatched when an interpreter is ready and about to run code.
* [Multipe interpreters](https://pyscript.github.io/polyscript/#interpreter-features)
  (in addition to Pyodide and MicroPython, PolyScript works with Lua and Ruby -
  although these are beyond the scope of this project).

### The stack

The stack describes how the different building blocks _inside_ a PyScript
application relate to each other:

<img src="../assets/images/platform.png"/>

* Everything happens inside the context of the browser (represented by the
  black border). It means the browser tab for your PyScript app is your
  sandboxed computing environment.

!!! failure

    Python solely running in the browser is an unfamiliar concept that some
    fail to remember.

    * PyScript isn't running on a server hosted in the cloud.
    * PyScript doesn't use the version of Python running natively on the user's
      operating system.
    * **PyScript only runs IN THE BROWSER (and nowhere else).**

* At the bottom of the stack are the Python interpreters compiled to WASM. They
  evaluate your code and interact with the browser via the [FFI](#ffi).
* The PyScript layer makes it easy to use and configure the Python
  interpreters. There are two parts to this:
    1. The PolyScript kernel (see above), that bootstraps everything and
       provides the core capabilities.
    2. PyScript and related plugins that sit atop PolyScript to give us an
       easy-to-use Python platform _in the browser_.
* Above the PyScript layer are either:
    1. Application frameworks, modules and libraries written in Python that you
       use to create useful applications.
    2. Your code (that's your responsibility).

## Lifecycle

If the architecture explains how components relate to each other, the lifecycle
explains how things unfold. It's important to understand both: it will
help you think about your own code and how it sits within PyScript.

Here's how PyScript unfolds through time:

* The browser is directed to a URL. The response is HTML.
* As part of parsing the HTML response the browser encounters the `<script>`
  tag that references PyScript. PyScript is loaded and evaluated as a module,
  meaning it doesn't hold up the loading of the page and is only evaluated when
  the HTML is fully parsed.
* The PyScript module does broadly six things:
    1. Discover Python code referenced in the page.
    2. Evaluate any [configuration](#configuration) on the page (either via a
       single `<py-config>` tag or the `config` attribute of a `<script>`,
       `<py-script>` or `<mpy-script>` tag).
    3. Given the detected configuration, download the required interpreter.
    4. Setup the interpreter's environment. This includes any
       [plugins](#plugins), [packages](#packages) or [files](#fetch) that need
       to be loaded.
    5. Make available various
       [builtin helper objects and functions](#builtin-helpers) to the
       interpreter's environment (accessed via the `pyscript` module).
    6. Finally, use the interpreter in the correctly configured environment to
       evaluate the detected Python code.
* When an interpreter is ready the `py:ready` or `mpy:ready` events are
  dispatched, depending which interpreter you've specified (Pyodide or
  MicroPython respectively).

!!! warning

    When using workers, each worker will have a completely separate environment
    to that of the main thread.

    As a result, configuration in the main thread will be different to that for
    an interpreter running on a worker. In fact, you can use different
    interpreters and configuration in each context (for instance, MicroPython
    on the main thread, and Pyodide on a worker).

Finally, various "hooks" are called at different moments in the lifecycle of
PyScript. These can be used by plugin authors to modify or enhance the
behaviour of PyScript. The hooks, and how to use them, are explored further in
[the section on plugins](#plugins).

## Interpreters

Python is an interpreted language, and thus needs an interpreter to work.

PyScript supports two versions of the Python interpreter that have
been compiled to WASM: Pyodide and MicroPython. You should select which one to
use depending on your use case and acceptable trade-offs.

Both interpreters make use of [emscripten](https://emscripten.org/), a compiler
toolchain (using [LLVM](https://llvm.org/)), for emitting WASM assets for the
browser. Emscripten also provides APIs so operating-system level features such
as a sandboxed [file system](https://emscripten.org/docs/api_reference/Filesystem-API.html)
(**not** the user's local machine's filesystem), [IO](https://emscripten.org/docs/api_reference/console.h.html`)
(`stdin`, `stdout`, `stderr` etc,) and
[networking](https://emscripten.org/docs/api_reference/fetch.html) are
available within the context of a browser.

Both Pyodide and MicroPython implement the same robust
[Python](https://pyodide.org/en/stable/usage/api/python-api.html)
⟺ [JavaScript](https://pyodide.org/en/stable/usage/api/js-api.html)
[foreign function interface](#ffi) (FFI). This
bridges the gap between the browser and Python worlds.

### Pyodide

<a href="https://pyodide.org/"><img src="../assets/images/pyodide.png"/></a>

[Pyodide](https://pyodide.org/) is a version of the standard
[CPython](https://python.org/) interpreter, patched to compile to WASM and
work in the browser.

It includes many useful features:

* The installation of pure Python packages from [PyPI](https://pypi.org/) via
  the [micropip](https://micropip.pyodide.org/en/stable/index.html) package
  installer. Some packages with C extensions have versions compiled for WASM
  and these can also be installed with `micropip`. There are plans afoot to
  make WASM a target in PyPI so packages with C extenions can be automatically
  compiled to WASM.
* An active, friendly and technically outstanding team of volunteer
  contributors (some of whom have been supported by the PyScript project).
* Extensive official
  [documentation](https://micropip.pyodide.org/en/stable/index.html), and many
  tutorials found online.
* Builds of Pyodide that include popular packages for data science like
  [Numpy](https://numpy.org/), [Scipy](https://scipy.org/) and
  [Pandas](https://pandas.pydata.org/).

### MicroPython

<a href="https://micropython.org/"><img src="../assets/images/micropython.png"/></a>

[MicroPython](https://micropython.org/) is a lean and efficient implementation
of the Python 3 programming language that includes a small subset of the Python
standard library and is optimised to run on microcontrollers and in constrained
environments (like the browser). 

Everything needed to view a web page in a browser needs to be delivered
over the network. The smaller the asset to be delivered can be, the better.
MicroPython, when compressed for delivery to the browser, is only around
170k in size - smaller than many images found on the web.

This makes MicroPython particularly suited to browsers running in a more
constrained environment such as on a mobile or tablet based device. Browsing
with these devices usually uses (slower) mobile internet connections.
Furthermore, because MicroPython is lean and efficient it still performs
exceptionally well on these relatively underpowered devices.

Thanks to collaboration between the MicroPython and PyScript projects, there is
a foreign function interface for MicroPython. The MicroPython FFI deliberately
copies the API of the FFI originally written for Pyodide - meaning it is
relatively easy to migrate between the two supported interpreters.

## Configuration

Because PyScript is a browser based technology, the tab in which the web page
is displayed is a very secure sandboxed computing environment for running your
Python code. Think of it as similar to the notion of a
[virtual environment](https://docs.python.org/3/tutorial/venv.html)
in the Python world.

This is also the case for web-workers running Python. Despite being associated
with a single web page, workers are all completely separate from each other
(except for some very limited and clearly defined means of interacting which
PyScript looks after for you).

As a result, we often need to tell PyScript about how we want our Python
environment to be configured. This works in the same way for both the main
thread and for web workers.

### TOML or JSON

Configuration can be expressed in two formats:

* [TOML](https://toml.io/en/) is the configuration file format preferred by
  folks in the Python community.
* [JSON](https://www.json.org/json-en.html) is a data format most often used
  by folks in the web community.

Since PyScript is the marriage of Python and the web, and we respect the
traditions of the two technical cultures, we support both.

However, because JSON is built into all browsers by default and TOML requires
an additional download of a specialist parser before PyScript can work, **the
use of JSON is more efficient from a performance point of view**.

The following two configurations are equivalent, and simply tell PyScript to
ensure the packages [arrr](https://arrr.readthedocs.io/en/latest/) and
[numberwang](https://numberwang.readthedocs.io/en/latest/) are installed from
PyPI (the [Python Packaging Index](https://pypi.org/)):

```TOML title="Configuration via TOML"
packages = ["arrr", "numberwang" ]
```

```JSON title="Configuration via JSON"
{
    "packages": ["arrr", "numberwang"]
}
```

### File or inline

The recommended way to write configurations is via a separate file and then
referencing it from the tag used to specify the Python code:

```HTML title="Reference a configuration file"
<script type="py" src="main.py" config="pyscript.toml"></script>
```

If you use JSON, you can make it the value of the `config` attribute:

```HTML title="JSON as the value of the config attribute"
<script type="mpy" src="main.py" config='{"packages":["arrr", "numberwang"]}'></script>
```

For historical and convenience reasons we still support the inline
specification of configuration information via a _single_ `<py-config>` tag in
your HTML document:

```HTML title="Inline configuration via the &lt;py-config&gt; tag"
<py-config>
{
    "packages": ["arrr", "numberwang" ]
}
</py-config>
```

!!! warning

    Should you use `<py-config>`, **there must be only one of these tags on the
    page**.

### Options

There are three core options, and the user is free to define arbitrary
additional configuration options that plugins or an app may require for their
own reasons.

#### Fetch

The `fetch` option fetches files from URLs onto the filesystem emulated by the
browser.

**TODO: Fix this.**

#### Packages

The `packages` option defines a list of Python `packages` to be installed from
[PyPI](https://pypi.org/) onto the filesystem by Pyodide's 
[micropip](https://micropip.pyodide.org/en/stable/index.html) package
installer.

The following two examples are equivalent:

```TOML title="A packages list in TOML"
packages = ["arrr", "numberwang", "snowballstemmer>=2.2.0" ]
```

```JSON title="A packages list in JSON"
{
    "packages": ["arrr", "numberwang", "snowballstemmer>=2.2.0" ]
}
```

!!! warning

    Because `micropip` is a Pyodide-only feature, and MicroPython doesn't
    support code packaged on PyPI, **the `packages` option is only available
    if you use Pyodide as your interpreter**.

The names in the list of `packages` can be any of the following valid forms:

* A name of a package on PyPI: `"snowballstemmer"`
* A name for a package on PyPI with additional constraints: `"snowballstemmer>=2.2.0"`
* An arbitrary URL to a Python package: `"https://.../package.whl"`
* A file copied onto the browser based file system: `"emfs://.../package.whl"`

#### Plugins

The `plugins` enumerate plugins enabled by PyScript to add extra functionality
to the platform.

Each plugin should be included on the web page, as described in the
[plugins](#plugins) section below. Then the plugin's name should be listed.

```TOML title="A list of plugins in TOML"
plugins = ["custom_plugin", "!error"]
```

```JSON title="A list of plugins in JSON"
{
    "plugins": ["custom_plugin", "!error"]
}
```

!!! info

    The `"!error"` syntax is a way to turn off a plugin built into PyScript
    that is enabled by default.

    Currently, the only built-in plugin is the `error` plugin (which displays a
    stack trace and error messages in the DOM). More may be added at a later
    date.

#### Custom 

Sometimes plugins or apps need bespoke configuration options.

So long as you don't cause a name collision with the built-in option names then
you are free to use any valid data structure that works with both TOML and JSON
to express your configuration needs.

**TODO: explain how to programmatically get access to an object representing
the config.**

## The DOM

The DOM
([document object model](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model))
refers to a tree like data structure that represents the web page in the
browser. PyScript needs to be able to interact with the DOM in order to change
the user interface and react to things happening in the browser.

There are currently two ways to interact with the DOM:

1. Through the foreign function interface (FFI) and by directly interacting
   with the objects found in the browser's `globalThis` object.
2. Through the `pydom` module that comes as standard with PyScript.

### FFI

The foreign function interface (FFI) gives Python access to all the
[standard web capabilities and features](https://developer.mozilla.org/en-US/docs/Web),
such as the browser's built-in
[web APIs](https://developer.mozilla.org/en-US/docs/Web/API).

This is available via the `pyscript.window` module which is a proxy for
the main thread's `globalThis` object, or `pyscript.document` which is a proxy
for the `document` object in JavaScript:

```Python title="Accessing the window and document objects in Python"
from pyscript import window, document


my_element = document.querySelector("#my-id")
my_element.innerText = window.location.hostname
```

### PyDom

The built in Python module `pydom` wraps many (although not all) the features
available via the FFI in a more idiomatically Pythonic library.


The PyDom API is extensively described and demonstrated
[on this PyScript page](https://fpliger.pyscriptapps.com/pyweb/latest/pydom.html).

!!! warning

    PyDom is currently a work in progress.

    We welcome feedback and suggestions.
    
## Workers

Workers allow you to run code in a way that won't block the "main thread" that
controls the user interface. If you block the main thread, your web page
becomes annoyingly unresponsive. You should never block the main thread.

Happily, PyScript makes it very easy to use workers. To make this happen
PyScript uses a feature recently added to web standards called
[Atomics](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Atomics).

### HTTP headers

In order for Atomics to work **you must ensure your web server should enable
the following headers** (this is the default behaviour for
[pyscript.com](pyscript.com)):

```
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
Cross-Origin-Resource-Policy: cross-origin
```

If you are not able to configure your server's headers, you could try to use
the [mini-coi](https://github.com/WebReflection/mini-coi#readme) project to
achieve the same end.

### Start working

To start your code in a worker, simply ensure the `<script>`, `<py-script>` or
`<mpy-script>` tag pointing to the code you want to run has a `worker`
attribute flag:

```HTML title="Evaluating code in a worker"
<script type="py" src="./my-worker-code.py" worker></script>
```

Of course, code running in the worker needs to be able to access the web page
running in the main thread. This is achieved via some builtin helper utilities
described in the next section.

!!! note

    The worker related functionality in PyScript is, for the sake of ease of
    use, a simpler presentation of more sophisticated and powerful behaviour
    available via PolyScript.

    Please [consult the XWorker](https://pyscript.github.io/polyscript/#xworker)
    related documentation from the PolyScript project for how to make use of
    these features.

## Builtin helpers

PyScript makes available various convenience objects and functions inside
Python. This is done via the `pyscript` module:

```python title="Accessing the document object via the pyscript module"
from pyscript import document
```

### Common features

These objects / functions are available in both the main thread and in code
running on a web worker:

#### `pyscript.window`

This object is a proxy for the web page's
[global window context](https://developer.mozilla.org/en-US/docs/Web/API/Window).

!!! warning

    Please note that in workers, this is still the main window, not the
    worker's own global context. A worker's global context is reachable instead
    via `import js` (the `js` object being a proxy for `globalThis`).

#### `pyscript.document`

This object is a proxy for the the web page's
[document object](https://developer.mozilla.org/en-US/docs/Web/API/Document).
The `document` is a representation of the
[DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_Document_Object_Model)
and can be used to manipulate the content of the web page.

#### `pyscript.display`

A function used to display content. The function is intelligent enough to
introspect the object[s] it is passed and work out how to correctly display the
object[s] in the web page.

The `display` function takes a list of `*values` as its first argument, and has
two optional named arguments:

* `target=None` - the DOM element into which the content should be placed.
* `append=False` - a flag to indicate if the output is going to be appended to
  the `target`.

There are some caveats:

* When used in the main thread, the `display` function automatically uses
  the current `<script>` tag as the `target` into which the content will
  be displayed.
* When used in a worker, the `display` function needs an explicit
  `target="dom-id"` argument to identify where the content will be
  displayed.
* In both the main thread a worker, `append=False` is the default
  behaviour.

### Main-thread only features

#### `pyscript.PyWorker`

A class used to instantiate a new worker from within Python.

!!! danger 

    Currently this only works with Pyodide.

The following fragment demonstrates who to start the Python code in the file
`worker.py` on a new worker from within Python.

```python title="Starting a new worker from Python"
from pyscript import PyWorker


a_worker = PyWorker("./worker.py")
```

### Worker only features

#### `pyscript.sync`

A function used to pass serializable data from workers to the main thread. 

Imagine you have this code on the main thread:

```python title="Python code on the main thread"
from pyscript import PyWorker

def hello(name="world"):
    display(f"Hello, {name}")

worker = PyWorker("./worker.py")
worker.sync.hello = hello
```

In the code on the worker, you can pass data back to handler functions like
this:

```python title="Pass data back to the main thread from a worker"
from pyscript import sync

sync.hello("PyScript")
```

## Plugins

**TODO: FINISH THIS**

<!--
# Examples

### Lots of DOM manipulation

### Data science-y

### Graphical

### Blocking with workers

### Calling an API -->