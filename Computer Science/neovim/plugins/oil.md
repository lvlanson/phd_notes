---
id: oil
aliases: []
tags: []
---
# oil.nvim

## What is `oil.nvim`

## Installation

For `lazy.vim` 

```lua
{
	"https://github.com/stevearc/oil.nvim", -- file browser
	config = function()
		require("oil").setup()
	end,
	keys = {
		{ "-", "<Cmd>Oil<CR>", desc = "Browse files from here" }, -- Activate with -
	},
},
```

## Usage

Note, in our setup, we configured `oil.nvim` to be activated by invoking `-` in normal mode.
- starting with `-` opens a buffer
	- note, the buffer is a editable text buffer
	- **renaming a file** and saving with `:w` will open a prompt if you want to **save the file** as changed
	- putting the cursor over a folder and hitting `enter` will **enter the folder**
	- vim motions, such as multiline edit, copy, paste, search etc. can be used for multifile edit
	- **open a file** in the buffer is simply putting the cursor over the file and hit enter
	- **a new file** can be created by typing in a new filename in a new line and save `:w`
	- **a new folder** can be created by using a `/` at the end of the string, like `myfolder/` and save `:w`
	- **moving a file** delete it from the buffer with `dd`, move to the place you want it to have, paste it with `p` and save with `:w`
## Commands
When in `oil.nvim`
- `-` go folder up
- `enter` open file oder folder
- `g.` show/hide hidden files/directory
- `g?` show commands
- `<C-c>` close oil, go to original buffer
