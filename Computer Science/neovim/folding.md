---
id: vanilla_folding
aliases: []
tags: []
---
# Folding
Note: A plugin is for this more recommended

Folding allows to collapse textblocks to a single line, and unfold them if wanted. There are different methods on how to invoke the folds. The are usually setup by
```vim
:set foldmethod=METHOD
```
Note, if you want to check which value is assigned to a variable, in this case `{vim} foldmethod`, just invoke 
```vim
:set foldmethod
```
which will return its assigned value. To see the folds, you need a `foldcolumn` greater than `1`, therefore we set
```vim
:set foldcolumn=1
```
or greater. Further the `foldlevel` sets how many levels of fold automatic processes should enable. We set
```vim
:set foldlevel=20
```
The fold commands are given here

|                                               | Command |
| --------------------------------------------- | ------- |
| fold codelines on cursor/highlighted (manual) | `zf`    |
| expand codelines on cursor                    | `zo`    |
| fold codelines with predefined fold           | `zz`    |
| toggle fold                                   | `za`    |
| delete all folds under cursor                 | `zD`    |
| delete a single level of folds                | `zd`    |

For the plugin use we have setup additional commands

|                  | Command |
| ---------------- | ------- |
| reveal all folds | `zR`    |
| close all folds  | `zM`    |
| peek into fold   | `zK`    |

## Setting up the plugin
```lua
{
	"kevinhwang91/nvim-ufo",
	dependencies = "kevinhwang91/promise-async",
	event = "VeryLazy",
	config = function(_, opts)
		vim.o.foldenable = true
		vim.o.foldcolumn = "1"
		vim.o.foldlevel = 99
		vim.o.foldlevelstart = 99

		vim.keymap.set("n", "zR", require("ufo").openAllFolds, { desc = "Open all folds" })
		vim.keymap.set("n", "zM", require("ufo").closeAllFolds, { desc = "Close all folds" })
		vim.keymap.set("n", "zK", function()
			local winid = require("ufo").peekFoldedLinesUnderCursor()
			if not winid then
				vim.lsp.buf.hover()
			end
		end, { desc = "Peek fold" })
		require("ufo").setup({
			provider_selector = function(bufnr, filetype, buftype)
				return { "lsp", "indent" }
			end,
		})
	end,
},
```

## Useful settings in the setup file
```vim
vim.opt.foldenable = true -- will start keeping everything closed
vim.opt.foldlevelstart = 99 -- will start with this foldlevel
```

Below you find a short description of the methods and how to use them.

## Manual
```vim
:set foldmethod=manual
```
One has to manually select blocks of text via *visual mode* and fold them with `zf`. All other commands can be applied on manually defined folds.

## Indent
```vim
:set foldmethod=indent
```
Folds are predefined on how lines of the text are indented. Commands work as expected.

## Marker
```vim
:set foldmethod=marker
```
Not recommended, some marker needs to be added into the text to fold

## Expr
```vim
:set foldmethod=nvim_treesitter#foldexpr()
```
The given example requires the neovim treesitter plugin. The plugin will determine where folds show be applied.

## Syntax
```vim
:set foldmethod=syntax
```
Works by using syntax highlighting.

## Diff
The next mode requires vim to be in **diff mode**. You can achieve that by invoking neovim with
```
> nvim -d FILE_1 FILE_2
```
and both files will be displayed next to each other highlighting their differences. Neovim will automatically start with `{vim} foldmethod=diff`.
