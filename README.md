# MDtoLateX

An interactive CLI tool that converts Markdown documents into beautifully formatted LaTeX documents and compiles them directly to PDF using XeLaTeX. Built with native support for Obsidian-flavored markdown, advanced math, diagrams (TikZ), and Hebrew/bilingual typesetting.

---

## ✨ Features

- **Interactive CLI Wizard**: Prompt-based wizard powered by `questionary` and `rich` to configure document title, author, date, themes, preambles, headers, and footers.
- **Obsidian Flavored Markdown**:
  - Admonitions / Callouts (`> [!note]`, `> [!theorem]`, `> [!definition]`, etc.)
  - Wikilinks and embeds (`[[link]]`, `![[embed]]`, block IDs)
  - Proof blocks (`**הוכחה:**` ... `\end{proof}`)
- **Diagrams to TikZ / PGFPlots**:
  - Mermaid diagrams (`mermaid`)
  - Graphviz DOT graphs (`dot`)
  - Desmos interactive plots (`desmos-graph` via `pgfplots`)
- **Bilingual & Hebrew Typesetting**:
  - Full RTL support with `polyglossia` and Culmus fonts (*David CLM*, *Nachlieli CLM*).
  - Automatic Hebrew calendar date conversion with Gematria representation.
- **Math & Code Listings**:
  - Rich math support (`amsmath`, `amssymb`, `mathtools`, `cancel`, `physics`).
  - Source code blocks formatted using `listings` with proper LTR directionality.
- **Direct PDF Compilation**: Automatically runs `xelatex` after generating the `.tex` output.

---

## 📋 Prerequisites

1. **Python 3.10+**
2. **TeX Distribution**: A working TeX distribution supporting **XeLaTeX** (such as [TeX Live](https://www.tug.org/texlive/) or [MiKTeX](https://miktex.org/)).
3. **Fonts (for Hebrew documents)**: Hebrew fonts such as `David CLM` and `Nachlieli CLM` (available in standard TeX distributions or via Culmus fonts).

---

## 🚀 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ShakedKod/MDtoLateX.git
   cd MDtoLateX
   ```

2. **Create and activate a virtual environment (optional but recommended):**
   ```bash
   # Windows (PowerShell)
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1

   # Linux / macOS
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

---

## 🛠️ Usage

Run the converter from the project root:

```bash
python src/main.py
```

Follow the interactive prompts:
1. **Input File**: Enter the path to your Markdown file (e.g. `test/UniTest3.md`).
2. **Style**: Select a theme (`regular` or `fancy-academic`).
3. **Preamble**: Optionally include a custom `.sty` / preamble file.
4. **Table of Contents**: Choose whether to include a TOC.
5. **Metadata**: Specify document title, author name, and date (or leave blank for today).
6. **Headers / Footers**: Customize page header and footer.
7. **Language**: Choose document language (`english`, `hebrew`, or `other`).

Once completed, the tool generates:
- `<filename>.tex` - The generated LaTeX source code.
- `<filename>.pdf` - The compiled PDF document (via XeLaTeX).

---

## 📁 Project Structure

```text
MDtoLateX/
├── src/
│   ├── main.py                     # Entry point & interactive CLI wizard
│   └── logic/
│       ├── __init__.py             # LatexFile builder & Hebrew date calculations
│       ├── ast_to_latex.py         # Markdown AST to LaTeX AST translator
│       ├── codeblock_logic.py      # Codeblock router (syntax highlighting & diagrams)
│       ├── desmos_to_tikz.py       # Desmos graph to PGFPlots/TikZ conversion
│       ├── dot_to_tikz.py          # Graphviz DOT to TikZ conversion
│       ├── mermaid_to_tikz.py      # Mermaid diagram to TikZ conversion
│       ├── latex_constants.py      # LaTeX templates, themes, and packages
│       ├── latex_parts.py          # Headings, lists, tables, and inline parsing
│       ├── obs_markdown_extras.py  # Mistune plugin for Obsidian wikilinks and syntax
│       └── obsidian_special_blocks.py # Callout and theorem environment generators
├── test/                           # Sample markdown documents and test preambles
├── requirements.txt                # Python package dependencies
└── README.md                       # Project documentation
```

---

## 📄 License

This project is open-source. Feel free to modify and adapt it for your own note-taking and document-generation workflows.
