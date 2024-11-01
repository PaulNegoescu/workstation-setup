# Setup Work Environment

This is a mostly readme repository holding the steps necessary to set up different types of work environments or home environments on PCs and Macs.

Follow the links below to the topic of interest.
## General Stuff

Make sure to install VSCode first! (On Mac also do a <kbd>CMD + SHIFT + P</kbd>, type `code` and select the option "Install 'code' command in PATH").

- Find and install the 'Dank Mono' font (not Nerd patched)
- Install this font:
  - [MesloLGS NF Regular.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
  - [MesloLGS NF Bold.ttf](
      https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
  - [MesloLGS NF Italic.ttf](
      https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
  - [MesloLGS NF Bold Italic.ttf](
      https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
- [VSCode Automatic Plugins Installation](./VSCode/AutoPluginsInstall.md)
- [VSCode Settings](./VSCode/settings.json)

## Windows Machines

First run this line to install all the usual tools of the trade (if winget is not installed install it from the Microsoft store)

```powershell
winget install Microsoft.WindowsTerminal Microsoft.VisualStudioCode Git.Git Mozilla.Firefox.DeveloperEdition mcmilk.7zip-zstd Atlassian.Sourcetree Perforce.P4Merge
```

NVM: `winget install -e --id CoreyButler.NVMforWindows`
Volta: `winget install -e --id Volta.Volta`

- [Windows Terminal Settings](./windows/WindowsTerminal/settings.json) (the main changes are the font used and the two new themes with names))
- If you use nvm (see winget command):
  - `nvm install node` (installs latest)
  - `nvm use node` (uses latest)
- If you use Volta
  - `volta install node@latest`
  - `volta install pnpm@latest`
- [OhMyZsh! Native Setup](./windows/OhMyZsh!.md)
