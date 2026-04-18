# CoDupScan

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
git clone https://github.com/yourusername/codupscan.git
cd codupscan
chmod +x codupscan.py
