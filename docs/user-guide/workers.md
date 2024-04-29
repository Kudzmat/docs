# Workers

Workers run code that won't block the "main thread" controlling the user
interface. If you block the main thread, your web page becomes annoyingly
unresponsive. **You should never block the main thread.**

Happily, PyScript makes it very easy to use workers and uses a feature recently
added to web standards called
[Atomics](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Atomics).
You don't need to know about Atomics to use web workers, but the underlying
[coincident library](http://localhost:8000/user-guide/architecture/#coincident)
uses it under the hood.

## HTTP headers

For Atomics to work **you must ensure your web server enables the following
headers** (this is the default behaviour for
[pyscript.com](https://pyscript.com)):

```
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
Cross-Origin-Resource-Policy: cross-origin
```

If you are not able to configure your server's headers, use the
[mini-coi](https://github.com/WebReflection/mini-coi#readme) project to
achieve the same end.

!!! Info

    The simplest way to use mini-coi is to place the
    [mini-coi.js](https://raw.githubusercontent.com/WebReflection/mini-coi/main/mini-coi.js)
    file in the root of your website (i.e. `/`), and reference it as the first
    child tag in the `<head>` of your HTML documents:

    ```html
    <html>
      <head>
        <script src="/mini-coi.js" scope="./"></script> 
        <!-- etc -->
      </head>
      <!-- etc --> 
    </html>
    ```

## Start working

To start your code in a worker, simply ensure the `<script>`, `<py-script>` or
`<mpy-script>` tag pointing to the code you want to run has a `worker`
attribute flag:

```HTML title="Evaluating code in a worker"
<script type="py" src="./my-worker-code.py" worker></script>
```

Code running in the worker needs to be able to access the web page running in
the main thread. This is achieved via [builtin helper utilities](../builtins).

!!! note

    For ease of use, the worker related functionality in PyScript is
    a simpler presentation of more sophisticated and powerful behaviour
    available via PolyScript.

    **If you are a confident advanced user**, please
    [consult the XWorker](https://pyscript.github.io/polyscript/#xworker)
    related documentation from the PolyScript project for how to make use of
    these features.
