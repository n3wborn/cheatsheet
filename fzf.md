![](https://raw.githubusercontent.com/junegunn/i/master/fzf.png)

# [FZF](https://github.com/junegunn/fzf)

FZF stands for **Fuzzy Finder**. It can helps a lot when you have to search files,
recent typed commands, and more.

It can really be as fun as powerful but it's true power is revealed
when used, unix-style, with other tools such as vim,find,git and more.

What you're reading is just a way to show, and remember, how useful this can be.


## Install

Just check [this](https://github.com/junegunn/fzf#installation), it's so simple.


## Usage

You can use it like this :

```bash
vim $(fzf --height 40%)
```

This will show you many file names. All you have is to type some letters.
Once the result you want is shown, use arrow, ctrp/ctrln, or entrer to select it.
Now you enter vim with the selected file.


You also can search through many find search results or git logs. Ex :

```bash
git log | fzf-tmux -d 15
```

See many more examples using **fzf trigger sequence**, by default **\*\*** :

```bash
# You can select multiple items with TAB key
vim **<TAB>

# Files under parent directory
vim ../**<TAB>

# Files under parent directory that match `fzf`
vim ../fzf**<TAB>

# Files under your home directory
vim ~/**<TAB>

# Directories under current directory (single-selection)
cd **<TAB>

# Directories under ~/github that match `fzf`
cd ~/github/fzf**<TAB>
```


## Terminal Keybindings

- **ctrl t** search through files

- **ctrl r** will give balls to backward command search

- **alt c** will `cd` where you want


## Fzf vim integration

Using [vim-plug](https://github.com/junegunn/vim-plug) or another plugin manager
it's possible to use fzf inside vim.

Just add [fzf-vim](https://github.com/junegunn/fzf.vim)
and [fzf](https://github.com/junegunn/fzf).
Configure it a bit, for example this [one](https://github.com/junegunn/fzf/blob/master/README-VIM.md#examples) and you'll
never turn back !

