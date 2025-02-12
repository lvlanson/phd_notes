## Setup
```bash
pacman -S neovim
alias vim=nvim
echo `alias vim=nvim` >> .zshrc
pamac install ttf-inconsolata-go-nerd
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim       
```

Inside vim
```bash
:TSInstall go
```
for installing better syntax highlighting for go

## Commands

|                                    | Command             |
| ---------------------------------- | ------------------- |
| Themes                             | `esc` + `space t h` |
| File Tree                          | `ctl + n`           |
| Find File                          | `esc` + `space f f` |
| Cheat Sheet                        | `esc` + `space c h` |
| Floating Terminal                  | `alt + i`           | 
| Cycle Through Tabs (Left to Right) | `tab`               |
| Cycle Through Tabs (Right to Left) | `shift + tab`       |
|                                    |                     |


## File Tree Mode
Note, one must have entered `File Tree` -> `ctl+n`

|             | Command |
| ----------- | ------- |
| Create File | `a`     |
|             |         |

## Autosuggestion-Mode

|                       | Command |
| --------------------- | ------- |
| Cancel Autosuggestion | `ctl+e` |
|                       |         |

## Terminals

|                                   | Command           |
| --------------------------------- | ----------------- |
| Open Terminal Vertically          | `esc`+`space + v` |
| Toggle Vertical Terminal On/Off   | `alt + v`         |
| Open Terminal Horizontally        | `esc`+`space + h` |
| Toggle Horizontal Terminal On/Off | `alt + h`         |
