# dotfiles

## zsh

Instead of symlinking, just add the following line to ~/.zshrc:

```bash
source ~/dotfiles/zsh/zshrc
```

## neovim

I've started using [lazyvim](https://github.com/LazyVim/LazyVim).
Config is done by editing files in ~/.config/nvim/lua/config/*.lua.
Plugins are loaded from files found in ~/.config/nvim/lua/plugins/*.lua.
To load the config, first get rid of any old configs:

```bash
mv ~/.config/nvim ~/.config/nvim.bak
mv ~/.local/share/nvim ~/.local/share/nvim.bak
```

Then symlink the new config:

```bash
ln -nfs ~/dotfiles/nvim ~/.config/nvim
```

## other
