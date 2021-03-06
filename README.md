[![PyPI version](https://badge.fury.io/py/webviz-core-components.svg)](https://badge.fury.io/py/webviz-core-components)
[![Build Status](https://travis-ci.org/equinor/webviz-core-components.svg?branch=master)](https://travis-ci.org/equinor/webviz-core-components)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/equinor/webviz-core-components.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/equinor/webviz-core-components/alerts/)
[![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/equinor/webviz-core-components.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/equinor/webviz-core-components/context:javascript)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/equinor/webviz-core-components.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/equinor/webviz-core-components/context:python)
[![Python 3.6 | 3.7 | 3.8](https://img.shields.io/badge/python-3.6%20|%203.7%20|%203.8-blue.svg)](https://www.python.org/)
[![Code style: black](https://img.shields.io/badge/code%20style-black%20%28Python%29-000000.svg)](https://github.com/psf/black)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier%20%28JavaScript%29-ff69b4.svg)](https://github.com/prettier/prettier)

# Webviz core components

`webviz_core_components` is a Dash component library for use in `webviz`.

You can quickly get started with:

1.  Run `pip install webviz-core-components`
2.  Run `python usage.py`
3.  Visit http://localhost:8050 in your web browser

## How to contribute

### Install dependencies

If you want to build and develop yourself, you should fork + clone the repository, and
then:

1. Install npm packages
    ```
    npm ci --ignore-scripts
    ```
2. Run the project's own `postinstall` script
    ```
    npm run postinstall
    ```
3. Install python packages required to build components.
    ```
    pip install .[dependencies]
    pip install dash[dev]
    ```
4. Install the python packages for testing.
    ```
    pip install .[tests]
    pip install dash[testing]
    ```
    The second of these commands appears to be necessary as long as
    [this `pip` issue is open](https://github.com/pypa/pip/issues/4957).

### Write component code in `src/lib/components/<component_name>.react.js`

- The demo app is in `src/demo` and is where you will import an example of your
  component. To start the existing demo app, run `npm start`.
- To test your code in a Python environment:
    1. Build your code
        ```
        npm run build
        ```
    2. Install the Python pacakge in development mode (if not already done and
       assuming you are using a virtual environment):
        ```
        pip install -e .
        ```
    3. Create a new example in `examples/` which uses your new component.

-   Write tests for your component.
    -   Tests exist in `tests/`. Take a look at them to see how to write tests using
        the Dash test framework.
    -   Run the tests with `pytest tests`.

-   Add custom styles to your component by putting your custom CSS files into
    your distribution folder (`webviz_core_components`).
    -   Make sure that they are referenced in `MANIFEST.in` so that they get
        properly included when you're ready to publish your component.
    -   Make sure the stylesheets are added to the `_css_dist` dict in
        `webviz_core_components/__init__.py` so dash will serve them
        automatically when the component suite is requested.
