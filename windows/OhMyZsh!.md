# OhMyZsh! Shell on Native Windows (no WSL)

In order to get native OhMyZsh! you need git bash (msysgit). Make sure you install git first (maybe using the provided bash script for choco in the software setup readme).


## Installing Zsh

Thanks go to [Dominik Rys](https://dominikrys.com/posts/zsh-in-git-bash-on-windows/) for the original post on his website!

1. Download the latest MSYS2 zsh package from the [MSYS2 package repository](https://packages.msys2.org/packages/zsh?repo=msys&variant=x86_64). The file is named something along the lines of `zsh-5.9-2-x86_64.pkg.tar.zst`.

2. Install an archiving utility that can open ZST archives such as [PeaZip](https://peazip.github.io/) or [7-Zip](https://www.7-zip.org/) (might still not support zst, there is a version that you installed by winget that does support thatzst).

3. Extract the contents of the archive 

4. Copy the `etc` and `usr` folders into your Git Bash installation directory (`C:\Program Files\Git`), merging the contents (there should be no overwrites).

5. Open Git Bash and run: `zsh`

## Configuring ZSH

**IMPORTANT**: configure the tab completion and history in the Zsh first use wizard. If for some reason it doesn’t appear, or you skip it, re-run it:

```sh
autoload -U zsh-newuser-install
zsh-newuser-install -f
```

Press 1, change the values if you like by pressing 1-3, and then press 0.

To configure the completion, press 2 to “Use the new completion system”, and then press 0.
Press 0 to save the settings.

Configure Zsh as the default shell by appending the following to your ~/.bashrc file:

```sh
code ~/.bashrc
```

```sh
if [ -t 1 ]; then
  exec zsh
fi
```

## Install OhMyZsh!

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## OMZ! Plugins and Themes

### [Theme PowerLevel10k](https://github.com/romkatv/powerlevel10k)

#### The Recommended Font
1. Download these four ttf files:
   - [MesloLGS NF Regular.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
   - [MesloLGS NF Bold.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
   - [MesloLGS NF Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
   - [MesloLGS NF Bold Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
1. Double-click on each file and click "Install"
1. Configure your terminal to use this font:
  - **Windows Terminal** by Microsoft (the new thing): Open *Settings* (<kbd>Ctrl+,</kbd>), click
     either on the selected profile under *Profiles* or on *Defaults*, click *Appearance* and set
     *Font face* to `MesloLGS NF`.

  - **Visual Studio Code**: <kbd>CTRL + ,</kbd> to open settings, enter `terminal.integrated.fontFamily` in the search box at
     the top of *Settings* tab and set the value below to `MesloLGS NF`.

#### The Theme Itself

1. Clone the repository:
    ```sh
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    ```
1. 
    ```sh
    code ~/.zshrc
    ```
1. Set `ZSH_THEME="powerlevel10k/powerlevel10k"`

1. Restart the terminal or
   ```sh
    exec zsh
   ```

1. `p10k configure` if the wizard did not start automatically

1. Answer the questions

1. For options select:
  - 1 (lean)
  - 1 (unicode)
  - 2 (24 hour)
  - 2 (2 lines)
  - 3 (solid)
  - 4 (full)
  - 3 (dark)
  - 2 (sparse)
  - 2 (many icons)
  - 2 (fluent)
  - n (not transient)
  - 1 (verbose instant prompt)
  - y (apply changes)

### Quick Plugin Install Instructions

If you need details about what is being installed check below. Otherwise copy and paste this:

```sh
winget install fzf
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```

In `code ~/.zshrc`:
```sh
plugins=( 
    # other plugins...
    zsh-autosuggestions zsh-syntax-highlighting zsh-history-substring-search
)

ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#555555"
source <(fzf --zsh)
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
```

**Restart your terminal!!!**

---

## !STOP! Only Need to Go Here for Details!

### [Plugin Auto-suggestions](https://github.com/zsh-users/zsh-autosuggestions)

1. Run
```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2. `code ~/.zshrc`

3. Add this in zshrc:
```sh
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```

4. Also add this to fix the highlight color which is too dark.

```sh
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#555555"
```

### [Not a plugin but useful, fzf](https://github.com/junegunn/fzf)

```sh
winget install fzf
```

In `.zshrc`

```sh
source <(fzf --zsh)
```

Restart the terminal!

### [ZSH Syntax Highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```


In `./zshrc`:

```sh
plugins=( [plugins...] zsh-syntax-highlighting)
```

### [ZSH Completions](https://github.com/zsh-users/zsh-completions)

```sh
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```

In `~/.zshrc` add:

```sh
 fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
 ```

## [ZSH History Substring Search](https://github.com/zsh-users/zsh-history-substring-search)


```sh
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```


In `./zshrc`:

```sh
plugins=( [plugins...] zsh-history-substring-search)
```
