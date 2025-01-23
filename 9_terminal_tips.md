---
title: 9 Terminal Tips
sub_title: That you may or may not know
author: Daniel
---

## 1. Bang ! operator stuff

Previous command `!!`, you can use - to specify current command minus number `!-2`, or just directly the command line number `!2`

```bash
sudo !!
```

<!-- pause -->

Get the previous arguments for the last command

```bash
mkdir thing
cd !$
```

<!-- pause -->

Get the command that starts with `!{string}`

```bash
echo !mkdir
```

<!-- end_slide -->

## 2. Use the original command of an alias

```bash
cd projects
ls -a
```

<!-- pause -->

```bash
cd projects
\ls
```

<!-- end_slide -->

## 3. Key Bindings

`<Ctrl-L>`: Clear the terminal, same as `clear`

<!-- pause -->

`<Ctrl-R>`: Search your previous commands

<!-- pause -->

For Bash:

`<Ctrl-X><Ctrl-E>`: Edit current command in `$VISUAL`

To do this is ZSH:

```bash
autoload -z edit-command-line
zle -N edit-command-line
bindkey "^X^E" edit-command-line
```

<!-- pause -->

`<Ctrl-D>`: Close the current terminal

<!-- pause -->

`<Ctrl-Z>`: Pause command to background, `bg` to continue it in the background, `fg` to bring it to the foreground

<!-- end_slide -->

## 4. `$VISUAL` and `$EDITOR`

Was specified in the POSIX spec to distinguish visual mode editors and line editors, but nowadays it matters less, just set this to the editor you would like to use

I tried doing this with VsCode but its not working for some scenarios, but I don't use VsCode, more exploration might be needed.

An environment variable used by `<Ctrl-x><Ctrl-e>` and other terminal apps like `git` (ex. `git commit --ammend`)

```bash
export VISUAL=nvim
```

<!-- end_slide -->

## 5. Signify the end of command options

Lets say you are searching through a help file, and you would like to search for what the `-v` flag does

```bash
rg --help | rg --v
```

<!-- pause -->

```bash
rg --help | rg -- --v
```

<!-- pause -->

Other examples that use this as well: `rm -f -- -f`

<!-- end_slide -->

## 6. Git worktrees

Allows you to check out more than one branch at a time, in different folders.

```bash
git worktree list
git worktree add destination_folder branch_to_checkout
git worktree remove worktree_folder
```

<!-- end_slide -->

## 7. Send running command to background (same as Ctrl-Z)

The `&` symbol allows you to send commands to the background

```bash
make test > thing.txt &; tail -f thing.txt
```

use `fg` to bring them back to the foreground

<!-- end_slide -->

## 8. Modern alternatives to built in commands

1. cd: zoxide

   - Fuzzy file navigation

<!-- new_line -->

1. grep: rg

   - Written in rust, multithreading

<!-- new_line -->

1. ls: eza

   - ls but with better ux, colors, icons etc

<!-- new_line -->

1. find: fd

   - Written in rust, faster

<!-- new_line -->

1. cat: bat

   - cat with syntax highlighting, git interaction etc

<!-- new_line -->

<!-- end_slide -->

## 9. Some useful command flags and behaviours

To go back to your last folder location

```bash
cd -
```

<!-- pause -->

To create intermediate directories if necessary

```bash
mkdir -p ./home/{folder_a, folder_b}/{folder_x, folder_y, folder_z}
```

<!-- pause -->

Change file permissions recursively

`u` user, `g` group, `o` others

`+` to add permissions

`=` to give permissions of one to another, leave empty to remove

`-` to give permissions of one to another, leave empty to remove

```bash
chmod -R u+rwx,g=,o= DIRECTORY
```

<!-- end_slide -->

## References

1. <https://unix.stackexchange.com/questions/4859/visual-vs-editor-what-s-the-difference>

1. <https://unix.stackexchange.com/questions/11376/what-does-double-dash-double-hyphen-mean/11382#11382>

1. <https://git-scm.com/docs/git-worktree>

<!-- end_slide -->

## Extras

Using spotlight on the command line: `mdfind`
