---
id: Vanilla
aliases: []
tags: []
---
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

### Splitting Windows 

|                                  | Command             |
| -------------------------------- | ------------------- |
| Open Terminal                    | `esc` + `:terminal` |
| Split Vertically                 | `esc` + `:vsplit`   |
|                                  | `esc` + `:vsp`      |
| Split Horizontally               | `esc` + `:hsplit`   |
|                                  | `esc` + `:hsp`      |
| Toggle Windows (Splits)          | `<C> + w + h/j/k/l` | 
| Open Terminal                    | :term               |
| To leave terminal                | `ctl+alt+\`         |
| N - resize by +N/-N horizontally | :res +/             |
| resize by +N/-N vertically       | :res vert +/        |
| resize to N horizontally         | :res N              |
| resize to N vertically           | :res vert N         |



### Visual Mode

|                                        | Command         |
| -------------------------------------- | --------------- |
| Yank (copy)                            | `y`             |
| Paste                                  | `p`             |
| Delete (cut)                           | `d`             |
| highlight text                         | `h`/`j`/`k`/`l` |
| cut                                    | `c`             |
| paste                                  | `p`             |
| delete the character under the cursor  | `x`             | 
| delete the character before the cursor | `X`             |
| delete word forward/backward           | `dw`, `db`      |
| delete an entire line                  | `dd`            |
| change word forward/backward           | `cw`, `cb`      |
| change entire line                     | `cc`            |
| to lowercase                           | `u`             |
| to uppercase                           | `U`             |

### Visual Line Mode
| | Command |
| -- | -- |
|   multiline edit (note, it looks like you only edit a single line, after pressing esc all the other lines are edited too), analogous for A (append) and C (change) | <C-V> + select lines + I |
## Vim Motions

#### General 

|                         | Command                  |
| ----------------------- | ------------------------ |
| Move Left/Down/Up/Right | `h`/`j`/`k`/`l`          |
| ----------------------- | ------------------------ |
| Next Word               | `w`                      |
| Delete Word             | `wd`                     |
| jump `n` parts          | `$NUM` + `h`/`j`/`k`/`l` |
| Delete Line             | `dd`                     | 
| Undo                    | `u`                      |
| Redo                    | `r`                      |

#### Horizontal

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

#### Vertical

|                                     | command   |
| ----------------------------------- | --------- |
| Go up by Paragraph                  | `{`       |
| Go down by Paragraph                | `}`       |
| Jump Half Page Up                   | `ctl + d` |
| Jump Half Page Down                 | `ctl + u` |
| Go all the Way Down                 | `G`       |
| Go all the Way Up                   | `gg`      |
| Go to line 50                       | `:50`     |
| Go down to end of paragraph         | `{`       | 
| Go up to the beginning of paragraph | `}`       |
| Jump half page down                 | `<C-d>`   |
| Jump half page up                   | `<C-u>`   |

## Useful Commands
|                                            | command |
| ------------------------------------------ | ------- |
| index all commands                         | `:h`    |
| place cursor on variable and refactor it   | `grn`   |
| search for string VAR                      | `/VAR`  | 
| in search after enter you can go next      | `n`     |
| " - " you can go previous                  | `N`     |
| search backwards for VAR                   | `/VAR?` |
| search for word under the cursor           | `*`     |
| search for word under the cursor backwards | `#`     |

## Plugin-Related:
|                                                                                                                                                        | command     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- |
| when installing new packages into venv while being in vim, hot reload the Language server, such that it loads the new packages into the autocompletion | :LspRestart |
| when installing new plugins while in vim or wanting to update plugins                                                                                  | :Lazy sync  |
| open telescope in the current working directory                                                                                                        | <leader> ff |
| open telescope for searching over opened buffers                                                                                                       | <leader> fb |

## Buffer-related:

|                   | command |
| ----------------- | ------- |
| create new buffer | `:enew` |
| delete current buffer | `:bd` | 
| delete all buffers | `:%bd` |

## Macros

Recording a macro:
1. (Normal Mode) press `q` + some key to record the macro to, lets say `a`, i.e `qa`
2. (Record Mode) press any key combination to record, lets say `vf-hx` (`v` - go visual mode, `f-` find first '-' and go there, `h` - move one step left, `x` -  cut)
3. (Record Mode) press `q` to stop recording

Invoking a recorded macro:
- (Normal Mode) press `@q` + the letter where the macro is stored at, in our example `a`, i.e. `@qa`

