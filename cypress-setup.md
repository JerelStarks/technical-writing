C. Late 2020, Early 2021 - Technical Writing Sample - Jerel Nelson Starks

---
# Cypress Setup
#### Prerequisites
* [VPN]() is set up. (<- For TFS access, this is now deprecated as of 10/20/20)
* `SSH Key access` is configured and linked to GitHub
* GitHub account has access to the [automation-ui-tests]() and [codename2-automation-ui-tests]() repositories.

## Installation
Setup and installation of the Cypress E2E project and dependencies can be performed partially through your operating system’s GUI and CLI or entirely through the CLI (e.g, Terminal, CMD, iTerm2). Select an option below that is most comfortable with your skill level, the result should be the same.
### GUI/Direct Download
On your local machine, you can manually install each of these through the GUI or use the command-line commands listed below.
* [Git](https://git-scm.com/downloads)
* [Node ](https://nodejs.org/en/download/current/)(Includes NPM and NPX)
* [Visual Studio Code](https://code.visualstudio.com) (Recommended Editor)
* [VPN]() (either [Priuntl](https://client.pritunl.com/) for Windows or [Tunnelblick](https://tunnelblick.net/) for mac) is set up and configured with [OVPN]() file.
* Google Chrome
  * Optional: [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/), [Microsoft Edge](https://www.microsoft.com/en-us/edge) for cross-browser testing.
* [iTerm2](https://iterm2.com/downloads.html) (Optional: macOS terminal alternative)
* [Windows Terminal](https://github.com/Microsoft/Terminal) (Optional: Windows CMD/Bash-terminal alternative, [Windows Store Link](https://apps.microsoft.com/detail/9n0dx20hk701?rtc=1&hl=en-us&gl=US))
* [Neovim](https://neovim.io) (Optional: terminal editor, [vscode-neovim](https://github.com/asvetliakov/vscode-neovim), or [VSCodeVim](https://github.com/VSCodeVim/Vim) can be used to integrate with VSCode)

### macOS Installation via CLI
Run these commands in the terminal before installing the aforementioned items.
* Install Command Line Tools: `xcode-select --install`
* Install [Homebrew](https://brew.sh/): `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Use these brew commands to install the aforementioned items:
* Install Git: `brew install git`
* Install Node: `brew install node`
* Install Tunnelblick: `brew cask install tunnelblick`
* Install VS Code: `brew cask install visual-studio-code`
* Install Google Chrome: `brew cask install google-chrome`
* Install Mozilla Firefox Developer Edition: `brew cask install /caskroom/version/firefoxdeveloperedition`
* Install Microsoft Edge: `brew cask install microsoft-edge`
* Install iTerm2: `brew cask install iterm2`
* Install Neovim (optional): `brew install neovim`

### Windows Installation via CLI
The new Windows Package manager can install most of the aforementioned items.
* Enable Developer Mode 
  * Go to the search within the taskbar and type in **Developer Settings**.
  * On the “For Developers” page, select the **Developer Mode** radio button.
* Download Microsoft [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701) from Microsoft app store.
* Download Microsoft [App Installer](https://www.microsoft.com/en-us/p/app-installer/9nblggh4nns1) from Microsoft app store or directly from [Microsoft Git Project](https://github.com/microsoft/winget-cli/releases). (**Very** New Windows Package Manager)

Open Windows Terminal and use these winget commands to install the aforementioned items:
* Install Git: `winget install git`
* Install Node: `winget install node`
* Install VSCode: `winget install Microsoft.VisualStudioCode`
* Install Google Chrome: `winget install Google Chrome`
* Install Mozilla Firefox Developer Edition: `winget install Mozilla.FirefoxDeveloperEdition`
* Install Microsoft Edge: `winget install Microsoft.Edge`
* Install Vim (optional): `winget install vim`
* Install Windows Terminal (if not done yet): `winget install Microsoft.WindowsTerminal`

These setup commands will be updated to include new packages when they are added to the manifest (e.g. Priuntl, Neovim, etc.).

---
## Cypress Initialization
1. Navigate to the prospective project folder and run:

- For codename1: 
```shell
git clone git@github.com:company/automation-ui-tests.git
```
* For codename2:
```shell
git clone git@github.com:company/codename-automation-ui-tests.git
```

2. Install Cypress and dependencies.
```shell
npm i
```

### Running Cypress
To run Cypress GUI tools, run this command from the project folder.
```shell
npx cypress open
```
To run Cypress headlessly (No UI), run this command from the project folder. With no options, this will run all Cypress Tests. This will also record the run to [TestRail]().
```shell
npx cypress run
```
To run a specific spec file headlessly, run this command from the project folder. More documentation on how to run specific spec files can be found [here]().
```shell
npx cypress run -s "cypress/integration/<specpathname>"
```   
---

## Notable Cypress Command-Line Options 
   
#### Browsers
To run headlessly with a specific browser use the --browser option with a browser argument. Valid arguments (depending on installed browsers) are `chrome`, `edge`, `firefox`, `electron`, and `chromium`, for example:
```shell
npx cypress run --browser chrome
```   


#### Recording
To record a Cypress run to the Cypress Dashboard, run Cypress with the `--record` command. If this argument is used in the CLI on your local machine, make sure to pass the `--key` to report to the correct Cypress instance.

On codename1, this would be:
```shell
npx cypress run --record --key <unique-key>
```
On codename2, this would be:
```shell
npx cypress run --record --key <unique-key>
```
   
#### Environments
   To run cypress at a specific environment, use the --env option with the flag configFile=<environment> . Valid arguments are `qa`, `dev`, `prod`, `pm`, `demo`, and `prod`. If the cypress run command is run without an `--env` option, the environment will default to `qa`. For example:
```shell
npx cypress run --env configFile=dev
```   

---
If you have any suggestions or have questions about this setup document, please contact @Jerel Nelson Starks.
