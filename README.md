ÅRSTID
======================

> ~~Table lamp with LED bulb, nickel plated/white~~

> Latest evolution of ASTRID, mainly for personal research use.

This version of ASTRID is a packaged version
of both ASTRID and ASTRID-DISCO (not ASTRID-multi). Therefore it handles both ILS datasets, and also
ILS+GDL datasets.
It also benefits from having a direct Python3 binding, via the in-house `asterid` package.

For example, on a "normal" Linux cluster. You
can do `pip install asterid` and then directly use
`arstid.py` without ever installing ASTRID and
you can also have Python3 bindings to ASTRID directly.

## Dependencies

Currently this package only supports i386 Linux architecture due to `asterid` built only for that architecture (which means that the UIUC campus cluster is good).

 - Python3
 - `asterid` (pip package, currently only supporting Linux i386 architecture)
 - `treeswift` (for ASTRID-DISCO)

## Acknowledgements

This codebase directly reuses the DISCO codebase from https://github.com/JSdoubleL/DISCO

## Usage (command line)

```bash
# single-copy trees, automatically uses the -u -n -s mode
python3 arstid.py -i input_gtrees -o output_strees

# the above is equivalent to
python3 arstid.py -i input_gtrees -m uns -o output_strees

# single-copy trees, explicitly uses only the -s mode
python3 arstid.py -i input_gtrees -m s -o output_strees

# NJst, for single-copy trees
python3 arstid.py -i input_gtrees -m j -o output_strees

# multi-copy trees, -u -n -s. The individual labels must be the same as the species labels
python3 arstid.py --disco -i input_gtrees -o output_strees
```

## Usage (Python3 binding)

```Python3
from arstid import astrid, astrid_disco

astrid(gtrees : List[str], methods : str = "uns") -> str

astrid_disco(gtrees : List[str], methods : str = "uns") -> str
```