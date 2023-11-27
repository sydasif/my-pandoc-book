# Appendix A: Additional Resources {#additional-resources}

This section contains additional resources related to the content of the book.

## Pandoc Command

Use this command to create a pdf book.

```bash
pandoc chapters/*.md -o output.pdf \
--metadata-file=metadata.yml \
--resource-path=. --toc --number-sections \
--include-in-header main.tex \
--highlight-style pygments.theme \
-V geometry:a5paper \
-V geometry:margin=2cm \
-V fontsize=12pt
```

## Pypandoc

Pypandoc provides a thin wrapper for pandoc, a universal document converter.

```python
import os
import pypandoc

input_dir = "chapters"
output_dir = "my_book"
output_filename = "book_output_02.pdf"

# Ensure the output directory exists
os.makedirs(output_dir, exist_ok=True)

# Build the pandoc options as a string
pandoc_cmd = [
    "--toc",
    "--number-sections",
    "--resource-path=.",
    "--metadata-file", "metadata.yml",
    "--include-in-header", "main.tex",
    "--highlight-style", "pygments.theme",
    "-V", "toc-title=Table of contents",
    "-V", "linkcolor:blue",
    "-V", "geometry:a4paper",
    "-V", "geometry:margin=1.8cm",
    "-V", "mainfont=DejaVu Serif",
    "-V", "monofont=SauceCodePro Nerd Font",
    "--pdf-engine=xelatex"
]

output_path = os.path.join(output_dir, output_filename)
# Convert all markdown files in the chapters/ subdirectory.
pypandoc.convert_file(
    os.path.join(input_dir, '*.md'), 'pdf', 
    outputfile=output_path, 
    extra_args=pandoc_cmd
)

print(f"Conversion completed. Output saved to: {output_path}")
```
