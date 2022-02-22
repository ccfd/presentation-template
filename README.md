# CCFD presentation template
## Introduction
This repository contains a beamer presentation template for use by CCFD members.
Please consider it for conference presentations, teaching materials, etc., as it help to build the CCFD brand.

## Prerequisites
To correctly build this template, you will need

- LuaLaTex
- The Fira font family

The former is widely available as part of free LaTex environments, e.g., [TexMaker](https://www.xm1math.net/texmaker/).
Simply select LuaLaTex from the drop-down menu when building.

### Installing Fira
Installing new fonts for LaTex can be a bit tricky, but the following guide should make it quick and breezy.
If you'd like more resources, visit, e.g., [https://www.tug.org/fonts/fontinstall.html](https://www.tug.org/fonts/fontinstall.html).
The following has been tested on Ubuntu 21.04 and 21.10, though it should work just as well on other Linux distributions.
It also assumes you are using Tex Live as your Tex distribution (it is available under `apt install texlive`).

1. Download and unpack Fira from [its CTAN mirror](http://mirrors.ctan.org/fonts/fira.zip). We will assume it has been unpacked in `~/Download/fira`, change the commands below accordingly.
2. Determine the Tex Live installation tree. We will store it in  a variable for convenience:
```bash
TEXLIVE_TREE=$(kpsewhich --var-value TEXMFLOCAL) && echo "Tex tree is in: $TEXLIVE_TREE"
```
3. Copy the font files into the tree, preserving their directory structure. Note that `sudo` is needed.
```bash
sudo mkdir "$TEXLIVE_TREE/fonts"
sudo cp -r ~/Downloads/fira/* "$TEXLIVE_TREE/fonts" # note the wildcard * at the end of the source path!
```
4. Run the following commands (see the link at the beginning of this section for an explanation)
```bash
sudo -H mktexlsr
sudo updmap-sys --force --enable Map=fira.map
sudo -H mktexlsr
```
5. That's it!

## Usage
To use the template, copy the `presentation` directory and get to work on modifying the copy.
Don't forget to compile with LuaLaTex!

### Code snippets
We recommend that you use the `minted` package for code fragments:
```tex
% in the preamble
\usepackage{minted}
% ...
\begin{frame}[fragile]{Hello, World!}
\begin{minted}{c++}
#include <cstdio>
int main() {
  puts("Hello, World!");
}
\end{minted}
\end{frame}
```
Note that the frame is marked `[fragile]`.
You will also need to invoke LuaLaTex with the `shell-escape` flag.
In TexMaker, this can be configured in `Options -> Configure TexMaker -> Commands -> LuaLatex`.

## License
The theme itself is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
This means that if you change the theme and re-distribute it, you **must** retain the copyright notice header and license it under the same CC-BY-SA license.
This does not affect the presentation that you create with the theme.

## Acknowledgement
The theme was originally prepared by Wojciech Gryglas.
We are very grateful for yur work!
