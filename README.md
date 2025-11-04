
# Front Loader LaTeX Package

TODO

## Overview

TODO

Issues and feature requests can be submitted on GitHub at [github.com/pwintz/frontloader](https://github.com/pwintz/frontloader). 

## Features

- TODO 

## Usage

### Basic Example

```latex
\documentclass{article}
\usepackage{frontloader}

\begin{document}

TODO

\end{document}
```


## Package options
| Key             | Type   | Description                                                 | Default                    |
| --------------- | ------ | ----------------------------------------------------------- | -------------------------- |
| `todo`   | bool   | Front Loader in draft mode.                                  | `true`                     |




## Change Log

### v1.0 (????) 


## License
The `frontloader` package is licensed under the [LaTeX Project Public License](https://www.latex-project.org/lppl/).


# Development

## Packaging and Uploading `frontloader` to CTAN

To package `frontloader`:

1. Compile the documentation.
2. Run 
    ```bash
    .package_for_CTAN.sh
    ```
The ` .package_for_CTAN.sh` script executes the following steps:


### 1. Package `.dtx` file
Run the `makedtx` tool to package the documentation and `.sty` files into a `.dtx` file.
Often, `makedtx` is packaged with your LaTeX installation, so it does not need to be installed separately. 
Run 
```bash
makedtx --version
```
to check it is installed. 
To build the `.dtx` file, run, 
```bash
makedtx -src "frontloader\.sty=>frontloader.sty" -doc frontloader-doc.tex frontloader
```
In the `-src` argument, the left-hand side of `=>` is a regular expression indicating the source file (hence the need to escape `\.`) and the right-hand side is the output file.

### 2. Convert Windows line endings (CRLF) to Unix line endings (LF)
CTAN wants LF line endings instead of CRLF (See [here](https://www.ctan.org/file/help/ctan/CTAN-upload-addendum#:~:text=Line%20terminators%20of%20text%20files)). 
We use `td` to delete the `'\r'` character from each file.
```bash
tr -d '\r'  < $file > frontloader/$file
```

### 3. Package into a Zip folder
To upload to CTAN, we create a Zip folder with this structure: 

- `frontloader.zip`
    
    - `frontloader/`
    
      - `frontloader-doc.tex`
      - `README.md`
      - `frontloader.dtx`
      - `frontloader.ins`
      - `frontloader-doc.pdf`

