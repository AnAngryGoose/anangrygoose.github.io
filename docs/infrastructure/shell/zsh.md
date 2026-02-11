# Zsh & Terminal Customization
---

### 1. Installation

Install the shell and git, which is required for downloading the theme and plugins.

```bash
# Update package list and install
sudo apt update && sudo apt install zsh git -y

# Verify installation
zsh --version

```

### 2. Oh My Zsh Framework

Oh My Zsh (OMZ) is a configuration framework that manages the Zsh environment.

**Install via Curl:**

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

```

*Note: If prompted to change the default shell to `zsh`, type `Y` and press `Enter`.*

### 3. Powerlevel10k Theme

Powerlevel10k is a high-performance theme that adds context-aware prompts (e.g., Git status, Docker context, execution time).

**A. Download the Theme**
Clone the repository into the custom themes directory:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"

```

**B. Configure `.zshrc`**

Open the configuration file:
`nano ~/.zshrc`

Locate the line `ZSH_THEME="robbyrussell"` and replace it with:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"

```

**C. Apply and Configure**
Apply the changes to start the configuration wizard:

```bash
source ~/.zshrc

```

Follow the on-screen prompts to select the visual style.

> **Important: Font Requirement**
> If icons appear as square placeholders, the client machine (the computer you are typing on) is missing a Nerd Font. Install **MesloLGS NF** on your local machine and set it as the terminal font. Do not install this on the server.

### 4. Essential Plugins

These plugins add syntax highlighting and predictive text based on history.

**A. Install Plugins**
Clone the repositories into the plugins directory:

* **zsh-autosuggestions:**
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

```


* **zsh-syntax-highlighting:**
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

```



**B. Activate Plugins**
Open the config file:
`nano ~/.zshrc`

Locate the line `plugins=(git)` and update it to:

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

```

### 5. Custom Aliases

Append the following block to the bottom of `~/.zshrc` to create shortcuts for common Docker and system tasks.

```bash
# --- Docker & Homelab Aliases ---
alias dcp='docker compose ps'
alias dcl='docker compose logs -f'  # Follow logs
alias dcd='docker compose down'
alias dcup='docker compose up -d'
alias dcr='docker compose restart'

# --- System Management ---
alias update='sudo apt update && sudo apt upgrade -y'
alias ports='sudo ss -tulpn | grep LISTEN' # uses ss instead of netstat
alias reload='source ~/.zshrc'

# --- Navigation ---
alias ..='cd ..'
alias ...='cd ../..'
alias ll='ls -lah'

```

### 6. Finalize

Reload the configuration one last time to apply plugins and aliases:

```bash
source ~/.zshrc

```

### Troubleshooting

* **"Command not found":** Ensure `source ~/.zshrc` was executed after editing the file.
* **Wrong Shell:** If the prompt remains in Bash after a reboot, force the default shell change:
```bash
chsh -s $(which zsh)

```


*Note: A logout/login is required for `chsh` to take effect.*

---