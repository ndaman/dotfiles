# dotfiles

## WSL

If WSL has not already been installed:
1. Follow instructions [here](https://learn.microsoft.com/en-us/windows/wsl/install)
2. install windows terminal, edit settings to remove ctl-c and ctl-v bindings
3. setup git credentials
```bash
git config --global credential.helper '/mnt/c/Program Files/git/mingw64/libexec/git-core/git-credential-manager.exe'
```
4. Follow [these](https://github.com/nckslvrmn/arch_linux_wsl2) instructions to get Arch
5. install my standard packages:
```bash
pacman -S --needed $(comm -12 <(pacman -Slq | sort) <(sort pkglist.txt))
```
6. Add sudo
  ```bash
  useradd -m -G wheel -s /usr/sbin/zsh nick
  ```
  1. modify sudoers to include wheel group (by typing `visudo`), uncomment line near end
  ```
  EDITOR=nvim visudo
  ```
  2. if you have configured the default user (per instructions above in boostrap), then relogin by closing the window and typing in powershell
  ```
  wsl --terminate arch
  ```
  and then start Arch again, you should be logged in as the configured user
7. install [yay](https://github.com/Jguer/yay)
  1. install foreign packages from list (may need to su to new user first)
  ```
  yay -S --needed - < pkglist.txt 
  ```

## zsh

Add some handy scripts by symlinking the bin dir:
```bash
ln -nfs ~/dotfiles/bin ~/.local/bin
```
Instead of symlinking, just add the following line to ~/.zshrc:

```bash
source ~/dotfiles/zsh/zshrc
PATH="$PATH:$HOME/.local/bin
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

## platformio

## MOOSE
