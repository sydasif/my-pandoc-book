# Markdown - The Art of Book Creation with Pandoc

## A Guide on Self-Publishing Technical Books

If you’re looking for a way to create a PDF or EPUB from a markdown file, you might have come across Pandoc. It’s a versatile document converter that can convert files between different formats, including Markdown, HTML, LaTeX, and more.

[Pandoc](https://pandoc.org/) is a valuable tool for writers, researchers, and anyone dealing with diverse document formats. It can seamlessly transform documents, making it a great choice for converting Markdown to PDF or restructuring HTML into a different format. This tutorial is aimed at those who want to use Pandoc for making PDFs and EPUBs, especially for technical books that have code snippets.

[Markdown](https://www.thepolyglotdeveloper.com/2018/01/write-blog-articles-markdown-the-polyglot-developer/) is a simple markup language that is widely used for web content, documentation, and ebook creation. It’s known for its readability and is a quick, user-friendly way to structure and style text without the complexities of HTML. I hope this guide makes using Pandoc for creating book formats easier for you!

The process of installing Pandoc depends on your operating system. Below are instructions for some common operating systems:

### Installing Pandoc on Linux (Debian/Ubuntu):

- Open the Terminal, and run the following commands:

```bash
sudo apt-get update
sudo apt-get install pandoc
sudo apt-get install texlive-xetex texlive-fonts-recommended texlive-plain-generic
```

These instructions cover the basic installation process for debian based operating system. Make sure to check the official [Pandoc Installation Guide](https://pandoc.org/installing.html) for any additional details or specific requirements related to your system.

## Example - Converting Markdown to PDF

Once pandoc is working on your system, generate a sample pdf without any customization. Let's say you have a Markdown file named `example.md`, and you want to convert it to a PDF using Pandoc.

Here's a simple example:

```markdown
# Example Document

This is a simple example of a Markdown document.

- It has a list.
- It supports **bold** and *italic* text.
```

Use the following command to convert the Markdown file to a PDF:

```bash
pandoc example.md -o example.pdf
```

This command tells Pandoc to take `example.md` as input (`-o` stands for output), and it will generate a PDF file named `example.pdf`. If you want to create an EPUB file, you could replace `example.pfd` with `example.epub`.

After running the command, you should see a new PDF file `example.pdf` in the same directory.

> It is advised to use markdown headers in order without skipping — for example, H1 for chapter heading and H2 for chapter sub-section, etc.

## Enhancing Document Structure with Pandoc

### Custom Chapter Breaks 

In Pandoc, you can insert chapter breaks by using specific headers in your Markdown document. Typically, you would use a header level that indicates the beginning of a new chapter. For example, using `#` for chapter titles:

```md
# Chapter 1
This is the content of Chapter 1.

# Chapter 2
This is the content of Chapter 2.

# Chapter 3
This is the content of Chapter 3.
```

When you convert this Markdown file to a format like PDF using previous Pandoc command, it will recognize these headers as chapter breaks but not page breaks. We can also customize the appearance of the chapter breaks with new page in the output by using a custom LaTeX template.

To force page breaks before each section (`chapter breaks if you're using headers like # Chapter 1`), you can utilize custom LaTeX templates. Here's how you can achieve it using the `-H` option in Pandoc:

```tex
\usepackage{sectsty}
\sectionfont{\clearpage}
```

Using a custom LaTeX template with Pandoc gives you a lot of flexibility in terms of formatting and styling your document. Your Pandoc command with the `-H` option and the specified LaTeX template file (`chapter_break.tex`):

```bash
pandoc example.md -H chapter_break.tex -o example_chapter_break.pdf
```

The `-V` option empowers the customization of variable values, enabling the adjustment of settings such as page size, font, link color, and more. As the number of settings modified increases, using a Python script to invoke Pandoc becomes a more efficient alternative, eliminating the need to manually input lengthy commands in the terminal.

```python
import os
import pypandoc

input_dir = "chapters"
output_dir = "my_book"
output_filename = "book_output.pdf"

# Ensure the output directory exists
os.makedirs(output_dir, exist_ok=True)

# Build the pandoc options as a string
pandoc_cmd = [
    "--include-in-header", "chapter_break.tex",
    "-V", "linkcolor:blue",
    "-V", "geometry:a4paper",
    "-V", "geometry:margin=1.8cm",
    "-V", "mainfont=DejaVu Serif",
    "-V", "monofont=SauceCodePro Nerd Font",
    "--pdf-engine=xelatex",
]

output_path = os.path.join(output_dir, output_filename)
# Convert all markdown files in the chapters/ subdirectory.
pypandoc.convert_file(
    os.path.join(input_dir, "*.md"), "pdf",
    outputfile=output_path,
    extra_args=pandoc_cmd,
)

print(f"Conversion completed. Output saved to: {output_path}")
```

- `mainfont` is for normal text
- `monofont` is for code snippets
- `geometry` for page size and margins
- `linkcolor` to set hyperlink color

The pandoc invocation is now through a script:

```bash
python3 md2pf.py
```

### Syntax highlighting

To customize syntax highlighting for code snippets, one option is to save a Pandoc theme and edit it accordingly.

```bash
pandoc --print-highlight-style=pygments > pygments.theme
```

Edit the generated file, in this demonstration, the following settings are modified:

```json
# Background color changed to a shade of gray for easy code-text distinction
"background-color": "#f8f8f8",

# Italic switched to false to avoid issues with comments
# Comment text-color changed to another shade of gray
"Comment": {
    "text-color": "#9c9c9c",
    "background-color": null,
    "bold": false,
    "italic": false,
    "underline": false
},
```

For inline code snippets, changing the background color:

```latex
\usepackage{fancyvrb,newverbs,xcolor}

\definecolor{Light}{HTML}{F4F4F4}

\let\oldtexttt\texttt
\renewcommand{\texttt}[1]{
  \colorbox{Light}{\oldtexttt{#1}}
}
```

Include the following options in your Python script and regenerate the PDF:

```python
# Rest of the script as above...
# Build the pandoc options as a string
pandoc_cmd = [
    "--include-in-header", "chapter_break.tex",
    "--highlight-style", "pygments.theme",
    "--include-in-header", "inline_code.tex"
    "-V", "linkcolor:blue",
    "-V", "geometry:a4paper",
    "-V", "geometry:margin=1.8cm",
    "-V", "mainfont=DejaVu Serif",
    "-V", "monofont=SauceCodePro Nerd Font",
    "--pdf-engine=xelatex",
]

# Rest of the script as above...
```

### Bullet styling

To customize bullet styling in Pandoc, you can use a custom LaTeX template for that, rename `chapter_break.tex` to `main.tex`. Add below code in your `main.tex`:

```latex
\usepackage{enumitem}
\usepackage{amsfonts}

% level one
\setlist[itemize,1]{label=$\bullet$}
% level two
\setlist[itemize,2]{label=$\circ$}
% level three
\setlist[itemize,3]{label=$\star$}
```

Amend your Python script and regenerate the PDF.

### Table of Contents

Pandoc offers a convenient `--toc` option to effortlessly append a table of contents at the beginning of your generated PDF. Customize the depth of the table of contents with the `--toc-depth` option; the default is set to `3` levels. Additionally, you can personalize the default label `Contents` to your preference using the `-V toc-title` option.

There more option I have add in the script, the file script is:

```python
# Rest of the script as above...
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
    "--pdf-engine=xelatex",
]

# Rest of the script as above...
```

In the journey of book creation with Pandoc, this guide serves as your compass, navigating through the intricacies of Markdown, Pandoc, and the artful customization they offer. From syntax highlighting to table of contents, unleash your creativity and elevate your writing to new heights.

## Reference Blog Post

[learnbyexample](https://learnbyexample.github.io/customizing-pandoc/)
