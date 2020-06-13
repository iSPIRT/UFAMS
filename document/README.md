# Standards Document

This contains markdown that can be compiled into a PDF version of the DigitalSky Technology Standards document.

## Building

### Prerequisites

* Install `make` and `pandoc` and `xelatex`.

#### Install Pandoc

For Debian, Ubuntu, and derivatives or Windows, download and install an appropriate package from [pandoc releases](https://github.com/jgm/pandoc/releases/)

#### macOS
- With `brew`:
```bash
brew install pandoc
```

### Build

1. In case you want to create markdown from a `docx`, save the word doc as `standards.docx` and run `make content/standards.md`.
1. Run
```bash
make
```
Your book will be exported as `standards.pdf`.
