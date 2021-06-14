# LaTeX Setup

Setting up a good LaTeX writing environment can be pretty hard (at least it had been for me 😅).
This is why I share my configuration in this repository.

## Development environment

I am using [VSCode](https://code.visualstudio.com/) as my IDE for writing LaTeX.

You will find my **VSCode settings** (regarding LaTeX) in the `settings.json` file.

### Extensions

I use many VSCode extensions in order to write LaTeX documents faster and easier:

- [Clipboard History](https://github.com/aefernandes/vscode-clipboard-history-extension): allows me to paste previous clipboard elements
- [Code Spell Checker](https://github.com/streetsidesoftware/vscode-spell-checker): used for spell checking in my documents
- [HyperSnips](https://github.com/draivin/hsnips): snippet engine supporting JavaScript code interpolation, VSCode version of vim [UltiSnips](https://github.com/SirVer/ultisnips)
- [LaTeX Utilities](https://github.com/tecosaur/LaTeX-Utilities): add-on to LaTeX Workshop providing some fancy features
- [LaTeX Workshop](https://github.com/James-Yu/LaTeX-Workshop): LaTeX typesetting, preview, compilation and code completion, highly customizable
- [Vim](https://github.com/VSCodeVim/Vim): vim keybindings in VSCode

Extensions specific settings are also available inside the `settings.json` file.

## Snippets

I use two types of snippets: VSCode default snippets and the HyperSnips extension.

Every snippet name starts with `[G]` in order to differentiate them from regular snippets (from LaTeX Workshop for example).

You will find a CheatSheet on top of the `latex.hsnips` file 😉.

If you want to add or modify a snippet, feel free to open an issue or a pull request.  
If you don't understand a snippet feel free to open an issue or send me a message.

### VSCode snippets

You will find my **VSCode LaTeX snippets** in the `latex.json` file.

I don't think any of them needs extra explanation.

### HyperSnips

You will find my **HyperSnips snippets** in the `latex.hsnips` file.

Most of them will only trigger while typing inside a math context.

I explain some of them as there are some complex ones. It should help you to understand their definitions.

Example format: `expression`: `replaced by`

#### Document template

Used to generate boilerplate code for a new document.

When using this snippet, press `<tab>` if you need the content of the selected text or press `<backspace>` if you don't need it. After that you can fill the _Title_, _Author_ and _Date_.

#### Matrix

Used to generate a matrix.

How to activate:
1. The first character must be `M`
2. The second character is the matrix type: `p` for `pmatrix`, `v` for `vmatrix`, etc
3. The third character is the number of rows in the matrix
4. The fourth character is the number of column in the matrix
5. The fifth character is the default character placed in the matrix (often 1 or 0)
6. Last character: `b` means you want to have line breaks after a row and `n` means no line breaks

The snippet will trigger automatically once you typed all the characters.  
On top of that, you can navigate with `<tab>` to input each matrix elements.

Example: `Mp241b` will result in the following
```latex
\begin{pmatrix}
1 & 1 & 1 & 1\\
1 & 1 & 1 & 1
\end{pmatrix}
```

#### Left-right

Used to generate `\left \right` commands.

How to activate:
1. Must start with `lr`
2. The next character can be one of the following: `)`, `]`, `>`, `}`, `v`, `V`

See `latex.hsnips` file for definitions.

#### Greek letter

Used to input Greek letters faster.

How to activate:
1. Must start with `z`
2. The next character must correspond to the greek letter

Examples:
- `za`: `\alpha`
- `zD`: `\Delta`

See `latex.hsnips` file for the other associations.

#### Math bb / Math cal

Used for `\mathbb{}` and `\mathcal{}` commands.

How to activate:
1. The first character must be the letter you want to modify
2. If you input the `#` character just after, it will surround your letter with `\mathbb{}`
3. If you input another `#` after that, it will modify the command and use `\mathcal{}` instead

Examples:
- `R#`: `\mathbb{R}`
- `\mathbb{F}#`: `\mathcal{F}`
- `F##`: `\mathcal{F}`

#### Auto subscript

If you type a one or two digit(s) number directly after a letter or a command, it will be automatically subscripted.

Examples:
- `a1`: `a_1`
- `x34`: `x_{34}`
- `za2`: `\alpha_2` (see Greek letter)

Special subscripts for `n/i + d` or `n/i - d`:
- `np1`: `_{n+1}`
- `nm2`: `_{n-2}`
- `ip3`: `_{i+3}`

#### Fraction auto

Using the `/` character right next to a small expression will result in a fraction.  
Surrounding any expression with parenthesis followed by a `/` will result in a fraction.

Examples:
- `1/2`: `\frac{1}{2}`
- `x/`: `\frac{x}{}`
- `\alpha/`: `\frac{\alpha}{}`
- `(x^2 + 2x - 4)/`: `\frac{x^2 + 2x - 4}{}`
- `(\alpha_3 - 2x^{12} + 9\pi)/`: `\frac{\alpha_3 - 2x^{12} + 9\pi}{}`

#### Square root auto / N root auto

Used for `\sqrt` command.

Surrounding any expression with parenthesis followed by `rt` will result in the square root of the expression.

If a number is typed just after a `\sqrt{}` command, it will result in the n-root (changing the current one if it already exists).

Examples:
- `(x^2 - x + 2)rt`: `\sqrt{x^2 - x + 2}`
- `\sqrt{x^2 - x + 2}4`: `\sqrt[4]{x^2 - x + 2}`
- `\sqrt[4]{x^2 - x + 2}5`: `\sqrt[5]{x^2 - x + 2}`
- `(x^2 - x + 2)rt6`: `\sqrt[6]{x^2 - x + 2}`
