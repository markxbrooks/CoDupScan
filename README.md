# CoDupScan

![PicoGL_Mascot](resources/codupscan_logo_600.png)

**Fast, grep-style detection of duplicated code using n-gram indexing.**

`codupscan` is a zero-dependency CLI tool that identifies duplicated code blocks across files using a single-pass hashing strategy. It supports optional normalization (including Python token-aware mode) to detect structural duplication beyond simple text matching.

---

## ✨ Features

- ⚡ **Single-pass indexing** for performance
- 🔍 **Grep-like CLI workflow**
- 🧱 **N-gram block detection** (configurable size)
- 🔗 **Overlap merging** into maximal regions
- 🧠 **Python-aware token normalization**
- 📄 **JSON output** for tooling integration
- 📊 **Sorted by severity** (occurrences × size)
- 📦 **Stdlib-only** (no dependencies)

---

## 🚀 Installation

Clone and run directly:

```bash
git clone https://github.com/markxbrooks/codupscan.git
python codupscan/codupscan.py ../ElMo/elmo --skip-dir test
```

Scan targets may be directories, individual files, or a mix of both. Directories
are walked recursively (honouring `--extensions` and `--skip-dir`); a file named
on the command line is scanned on its own, regardless of its suffix:

```bash
# just this one file
python codupscan/codupscan.py ../ElMo/elmo/ui/widgets/ramachandran_plot_widget.py

# a couple of files together
python codupscan/codupscan.py ../ElMo/elmo/ui/a.py ../ElMo/elmo/ui/b.py

# a directory plus an extra file outside it
python codupscan/codupscan.py ../ElMo/elmo/gl ../ElMo/elmo/main.py
```

```bash
python codupscan/codupscan.py --help                             
usage: codupscan.py [-h] [-n LINES] [-m MIN_OCCURRENCES] [-e EXTENSIONS]
                    [--no-normalize] [--tokens] [--json] [-q]
                    [--skip-dir NAME] [--no-filter-imports]
                    [--no-filter-whitespace]
                    [PATH ...]

Find duplicated code blocks (stdlib-only)

positional arguments:
  PATH                  Files and/or directories to scan (repeatable). A named
                        file is scanned on its own; directories are walked.
                        Default: current directory

options:
  -h, --help            show this help message and exit
  -n, --block-size LINES
                        Contiguous lines per n-gram (and per reported block).
                        Larger values ignore short boilerplate (e.g. import
                        headers). Default: 8
  -m, --min-occurrences MIN_OCCURRENCES
  -e, --extensions EXTENSIONS
  --no-normalize
  --tokens              Use Python token-based normalization
  --json
  -q, --quiet
  --skip-dir NAME       Skip any file whose path contains a directory
                        component NAME (repeatable). Names may be comma-
                        separated. Example: --skip-dir test --skip-dir
                        tests,legacy_root
  --no-filter-imports   Include import/from lines in hashes (default: blank
                        them for .py files)
  --no-filter-whitespace
                        Do not skip n-grams that have fewer than 2 non-blank
                        lines (default: skip mostly-whitespace windows)
```
