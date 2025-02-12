## Modes
There are 4 modes
- Normal Mode - one can scroll through the document (usually accessed by `esc`)
- Insert Mode - one can edit the text (usually accessed by `a` or `i` in *normal mode*)
	- `a` will append, so the cursor spawns right
	- `i` will insert, so the cursor spawns left
- Visual Mode - one can highlight text (usually accessed by `v` or `shift + v` in *normal mode*)
	- `v` is visual mode by character
	- `shift + v` is visual mode by line
- Command Mode - one can type in commands into the editor (usually accessed by `:` in Normal Mode)

### Normal Mode

#### Motions

|                         | Command                  |
| ----------------------- | ------------------------ |
| Move Left/Down/Up/Right | `h`/`j`/`k`/`l`          |
| Next Word               | `w`                      |
| Delete Word             | `wd`                     |
| jump `n` parts          | `$NUM` + `h`/`j`/`k`/`l` |

**Note** every deletion will go into the same buffer as if you would yank something (cut).
#### Editing

|             | Command |
| ----------- | ------- |
| Delete Line | `dd`    |
| Undo        | `u`     |
| Redo        | `r`     |




|                         | Command             |
| ----------------------- | ------------------- |
| Open Terminal           | `esc` + `:terminal` |
| Split Vertically        | `esc` + `:vsplit`   |
|                         | `esc` + `:vsp`      |
| Split Horizontally      | `esc` + `:hsplit`   |
|                         | `esc` + `:hsp`      |
| Toggle Windows (Splits) | `ctl + h/j/k/l`     |

To leave terminal `ctl+alt+\`

### Visual Mode

|            | Command |
| ---------- | ------- |
| Yank (cut) | `y`     |
| Paste      | `p`     |

## Vim Motions

|                                      | Command |
| ------------------------------------ | ------- |
| Beginning of Line                    | `_`     |
| Beginning of Line in insert mode     | `I`     |
| End of Line                          | `$`     |
| End of Line in insert mode           | `A`     |
| Make New Line below in Insert Mode   | `o`     |
| Make New Line above in Insert Mode   | `O`     | 
| 0-th Character in Line               | `0`     |
| Jump on character `?` (forward)      | `f?`    |
| Jump before character `?` (forward)  | `t?`    |
| Jump on character `?` (backward)     | `F?`    |
| Jump before character `?` (backward) | `T?`    |
| Continue jumping forward             | `,`     |
| Continue jumping backward            | `;`     |


# Combinations

One can combine `command` + `count` + `motion`
-> delete 3 lines `d3j`
-> delete from cursor until end of line `d$`
->