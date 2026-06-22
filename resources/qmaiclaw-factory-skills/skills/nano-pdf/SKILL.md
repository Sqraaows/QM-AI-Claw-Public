# Nano Pdf

**Source**: https://clawhub.ai/steipete/nano-pdf

Edit PDFs with natural-language instructions using the nano-pdf CLI.

## Installation

```bash
# Install via uv
uv tool install nano-pdf

# Or via pip
pip install nano-pdf
```

## Usage

```bash
# Edit a PDF page with natural language
nano-pdf edit "replace the header with 'Hello World'" input.pdf output.pdf

# View help
nano-pdf --help
```

## Tips

- Be specific about what you want to change
- Provide page numbers when relevant
- Test on non-sensitive PDFs first
- Check output correctness after editing

## Security Notes

- Only process PDFs you trust
- Review nano-pdf source before installing
- Use `--help` to understand all options

---

*Install date: 2026-04-27*
