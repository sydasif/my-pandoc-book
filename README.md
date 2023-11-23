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

