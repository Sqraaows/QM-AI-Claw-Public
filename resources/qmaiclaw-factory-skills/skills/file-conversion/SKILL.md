# File Conversion

**Source**: Custom workspace skill

Convert between file formats (Markdown, HTML, PDF, etc.).

## Pandoc (Swiss Army Knife)

```bash
# Install
# macOS: brew install pandoc
# Linux: sudo apt install pandoc
# Windows: choco install pandoc

# Markdown to HTML
pandoc input.md -o output.html

# Markdown to PDF
pandoc input.md -o output.pdf

# Markdown to DOCX
pandoc input.md -o output.docx

# HTML to Markdown
pandoc input.html -o output.md

# With templates
pandoc input.md --template=eisvogel -o output.pdf

# Standalone HTML
pandoc input.md -s -o output.html

# With table of contents
pandoc input.md --toc -o output.html
```

## Markdown to PDF (Other options)

```bash
# markdown-pdf (Node)
npm install -g markdown-pdf
markdown-pdf input.md -o output.pdf

# grip (GitHub Preview)
pip install grip
grip input.md

# mdpdf
npm install -g mdpdf
mdpdf input.md -o output.pdf
```

## Image Conversion

```bash
# ImageMagick
convert image.jpg image.png
convert image.png -resize 200x100 image.jpg
convert image.png -quality 50 image.jpg

# Optional: add watermark
composite -dissolve 30% -gravity southeast watermark.png image.jpg output.jpg
```

## Document Conversion

```bash
# LibreOffice (headless)
libreoffice --headless --convert-to docx input.pdf
libreoffice --headless --convert-to pdf input.docx

# Docx to Text
pandoc input.docx -o output.txt

# CSV to JSON
python3 -c "import pandas as pd; df = pd.read_csv('input.csv'); print(df.to_json())"

# JSON to YAML
pip install pyyaml
python3 -c "import yaml, json; print(yaml.dump(json.load(open('input.json'))))"
```

## Audio/Video

```bash
# ffmpeg - must have
ffmpeg -i input.mp4 output.webm
ffmpeg -i input.wav -acodec libmp3lame output.mp3
ffmpeg -i input.mp4 -vn -acodec copy output.aac

# Extract audio
ffmpeg -i video.mp4 -vn -ab 128k audio.mp3

# Compress video
ffmpeg -i input.mp4 -crf 23 -preset fast output.mp4
```

---

*Install date: 2026-04-27*
