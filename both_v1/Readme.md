
## Available Scripts

* extract_pyinv_examples (in crtomo_tests)
* pycrtomo_test (in crtomo_tests)
* CRMod (in crtomo_wrappers)
* CRTomo (in crtomo_wrappers)
* CutMcK (in crtomo_wrappers)

## Updating CRMod

    ./gen_pycrmod.sh
    cp -r output_pycrmod both_v1/pycrmod_vX
    # in meson.build:
        * remove virtualenv-specific python path
        * remove project(...) call, as we use this project as a subproject

## Building locally

    mkvirtualenv crtomo
    pip install cibuildwheel

## Linux

    export CIBW_BUILD='cp313-manylinux_x86_64'
    cibuildwheel --platform linux  

## Pyiodine

Build does not work at the moment, but these were the steps:

    export CIBW_BUILD='cp313-pyodide_wasm32'
    cibuildwheel --platform pyodide .
