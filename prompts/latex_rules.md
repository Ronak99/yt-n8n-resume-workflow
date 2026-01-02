# LaTeX Syntax Rules for AI Models

## Special Characters That MUST Be Escaped

The following characters have special meaning in LaTeX and MUST be escaped with a backslash `\`:

- `&` → `\&`
- `%` → `\%`
- `$` → `\$`
- `#` → `\#`
- `_` → `\_`
- `{` → `\{`
- `}` → `\}`
- `~` → `\textasciitilde{}` or `\~{}`
- `^` → `\textasciicircum{}` or `\^{}`
- `\` → `\textbackslash{}` or `\backslash`

**Exception**: These characters are NOT escaped when used for their intended LaTeX purpose (e.g., `$` for math mode, `_` for subscripts in math, `{}` for grouping).

## Document Structure

Every LaTeX document MUST have:
```latex
\documentclass[options]{class}
% Preamble with packages and settings
\begin{document}
% Content goes here
\end{document}
```

Common document classes: `article`, `report`, `book`, `letter`, `beamer`

## Environments

All environments MUST be properly opened and closed:
```latex
\begin{environment_name}
content
\end{environment_name}
```

Common environments: `itemize`, `enumerate`, `equation`, `figure`, `table`, `center`, `abstract`

## Braces and Grouping

- Every opening `{` MUST have a matching closing `}`
- Braces are used for grouping and as arguments to commands
- Empty braces `{}` are valid and sometimes required

## Commands

LaTeX commands follow these patterns:

1. `\commandname` - simple command
2. `\commandname{required argument}` - command with required argument
3. `\commandname[optional]{required}` - command with optional argument
4. `\commandname{arg1}{arg2}` - command with multiple arguments

Command names:
- MUST start with `\`
- Can only contain letters (a-z, A-Z)
- Are case-sensitive
- End at first non-letter or space

## Whitespace Rules

- Multiple spaces = single space
- Line breaks do NOT create new paragraphs
- Empty line = paragraph break
- `~` = non-breaking space (useful before citations/references)
- `\\` = line break within paragraph (use sparingly)
- `\newline` = alternative line break

## Math Mode

Two types of math mode:

1. **Inline math**: `$expression$` or `\(expression\)`
2. **Display math**: `$$expression$$` or `\[expression\]` or `\begin{equation}`

Math mode rules:
- Spaces are ignored; use `\,` `\:` `\;` `\quad` `\qquad` for spacing
- Underscore `_` for subscripts: `x_1`
- Caret `^` for superscripts: `x^2`
- Multiple characters in sub/superscript need braces: `x_{10}` not `x_10`
- Letters are italicized by default (variables)
- Use `\text{text}` for normal text in math mode

## Lists

**Itemize (bullets)**:
```latex
\begin{itemize}
  \item First item
  \item Second item
\end{itemize}
```

**Enumerate (numbers)**:
```latex
\begin{enumerate}
  \item First item
  \item Second item
\end{enumerate}
```

Rules:
- MUST use `\item` before each list entry
- Can nest lists up to 4 levels
- Cannot have empty lists

## Sections and Structure
```latex
\section{Title}
\subsection{Subtitle}
\subsubsection{Subsubtitle}
\paragraph{Paragraph title}
\subparagraph{Subparagraph title}
```

Rules:
- Titles go in braces `{}`
- Numbering is automatic
- Use `\section*{}` for unnumbered sections

## Font Formatting

- `\textbf{bold text}` - bold
- `\textit{italic text}` - italic
- `\texttt{monospace}` - monospace/typewriter
- `\underline{underlined}` - underline
- `\emph{emphasized}` - emphasis (usually italic)
- `{\large larger}` - size changes
- `{\small smaller}` - smaller size

## Quotation Marks

- Left double quote: ``` `` ``` (two backticks)
- Right double quote: `''` (two apostrophes)
- Left single quote: ``` ` ``` (one backtick)
- Right single quote: `'` (one apostrophe)

**NEVER use straight quotes** `"` or `"` directly.

## Dashes

- Hyphen: `-` (for compound words: "state-of-the-art")
- En-dash: `--` (for ranges: "pages 1--10")
- Em-dash: `---` (for punctuation---like this)

## Comments

- Single line: `%` everything after is ignored
- Multi-line: Use `\iffalse` ... `\fi` or `\begin{comment}` ... `\end{comment}` (requires `verbatim` package)

## Common Packages

Include in preamble with `\usepackage{packagename}`:

- `graphicx` - for images
- `amsmath` - enhanced math
- `hyperref` - hyperlinks and URLs
- `geometry` - page dimensions
- `babel` - language support
- `inputenc` - character encoding (e.g., `\usepackage[utf8]{inputenc}`)
- `fontenc` - font encoding (e.g., `\usepackage[T1]{fontenc}`)

## URLs and Hyperlinks
```latex
\usepackage{hyperref}
\url{https://example.com}
\href{https://example.com}{link text}
```

Rules:
- URLs with special characters should use `\url{}`
- Escape `%`, `#`, `&` even in URLs when not using `\url{}`

## Tables
```latex
\begin{tabular}{|c|l|r|}
\hline
Header 1 & Header 2 & Header 3 \\
\hline
Cell 1 & Cell 2 & Cell 3 \\
Cell 4 & Cell 5 & Cell 6 \\
\hline
\end{tabular}
```

Rules:
- Column alignment: `l` (left), `c` (center), `r` (right)
- `|` creates vertical lines
- `&` separates columns
- `\\` ends rows
- `\hline` creates horizontal lines

## Images
```latex
\usepackage{graphicx}
\begin{figure}[h]
  \centering
  \includegraphics[width=0.5\textwidth]{filename}
  \caption{Caption text}
  \label{fig:label}
\end{figure}
```

Rules:
- Image files should NOT include extension in some cases (LaTeX auto-detects)
- Placement specifiers: `h` (here), `t` (top), `b` (bottom), `p` (page)

## Cross-References
```latex
\label{sec:intro}
\ref{sec:intro}
\pageref{sec:intro}
```

Rules:
- Labels must be unique
- Common prefixes: `sec:`, `fig:`, `tab:`, `eq:`
- Reference AFTER the item is defined

## Bibliography
```latex
\begin{thebibliography}{99}
\bibitem{label}
Author Name. \textit{Title}. Year.
\end{thebibliography}
```

Cite with: `\cite{label}`

## Common Errors to Avoid

1. **Unmatched braces**: Every `{` needs a `}`
2. **Unescaped special characters**: Remember to escape `&`, `%`, `$`, `#`, `_`, etc.
3. **Missing `\end{}`**: Every `\begin{}` needs `\end{}`
4. **Math mode errors**: Don't use `_` or `^` outside math mode
5. **Empty groups**: `\section{}` is invalid; must have content
6. **Wrong quotes**: Use ``` `` ``` and `''`, not `"`
7. **Undefined commands**: Don't use `\command` unless it exists or is defined
8. **Missing packages**: Some commands require specific packages

## Critical Rules Summary

1. ALWAYS escape special characters when using them as literal text
2. ALWAYS match opening and closing braces `{}`
3. ALWAYS match `\begin{}` with `\end{}`
4. ALWAYS use proper quote syntax: ``` `` ``` and `''`
5. NEVER use undefined commands
6. NEVER forget `\documentclass{}` and `\begin{document}`...`\end{document}`
7. NEVER use `_` or `^` outside math mode
8. ALWAYS check that required packages are included for special commands
9. ALWAYS maintain proper nesting of environments
10. ALWAYS use `\\` only for line breaks, blank lines for paragraphs

## Validation Checklist

Before outputting LaTeX code, verify:
- [ ] All special characters are properly escaped
- [ ] All braces are balanced
- [ ] All environments are closed
- [ ] Document structure is complete
- [ ] Math mode is properly used
- [ ] No undefined commands are used
- [ ] Quotes use correct LaTeX syntax
- [ ] Required packages are included