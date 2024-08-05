### Installing GNU Stow

#### Mac
```sh
brew install stow
```

#### Arch Linux
```sh
sudo pacman -S stow
```

### Creating a directory for your dotfiles
```sh
mkdir ~/dotfiles
```
### Setting up directories within `~/dotfiles`

#### Case 1

For files that usually live in your `$HOME` directory like `.zshrc`:
```
~/
├─ .zshrc
```

Within `~/dotfiles/` you want to recreate the same structure so create a folder labeling whats inside it.
e.g. For `.zshrc`, we can create a folder called `zsh`. 

This `~/dotfiles/zsh` folder will act as a home directory so everything inside it should be layered as if it was the home directory.
```
~/dotfiles/
├─ zsh/
│  ├─ .zshrc
```

#### Case 2

For files that exist inside your `~/.config/` directory like your `nvim` files: 

```
~/
├─ .config/
│  ├─ nvim
│  │  ├─ ...
│  │  ├─ ...
```

You want to create a structure like this:
```
~/dotfiles/
├─ nvim/
│  ├─ .config/
│  │  ├─ nvim/
│  │  │  ├─ ...
```

Here, you have to create a `nvim` directory within `dotfiles`, and a `.config` directory within that `nvim` directory.

### Moving the dotfiles from `~/` to `~/dotfiles/`

Create a backup of your files inside your `$HOME` directory in case something goes wrong:

```sh
cp -r ~/.config/nvim ~/.config/nvim.bak
```

Now you can move your `nvim` config to your `dotfiles` directory like this:

```sh
mv ~/.config/nvim ~/dotfiles/nvim/.config/
```

### Creating the symbolic links in your actual `$HOME` directory

Assuming everything is set up properly within `~/dotfiles/`, we can use the command:
```sh
stow <folder>
```
within your `~/dotfiles/` directory to create the symbolic link from there to your files in your `$HOME` directory.
