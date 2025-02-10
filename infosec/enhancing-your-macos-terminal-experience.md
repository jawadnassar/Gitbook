---
cover: >-
  https://images.unsplash.com/photo-1590971862391-06cac0657603?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxjb21wdXRlciUyMHRlcm1pbmFsfGVufDB8fHx8MTcxMDAyMjcyOHww&ixlib=rb-4.0.3&q=85
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🍎 Enhancing Your MacOS Terminal Experience

## Enhancing Your MacOS Terminal Experience with iTerm2

Elevate your terminal experience on MacOS by following this quick tutorial on installing iTerm2 and applying a custom color scheme. This will not only improve the aesthetics of your terminal but also potentially make it easier to read and work with.

### Step 1: Install Homebrew

[Homebrew](https://brew.sh) is a package manager for MacOS that simplifies the process of installing software on MacOS. Run the following command in your terminal to install Homebrew:

{% code overflow="wrap" %}
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
{% endcode %}

### Step 2: Install iTerm2

With Homebrew installed, you can easily install [iTerm2](https://iterm2.com/) by running:

```shell
brew install --cask iterm2
```

### Step 3: Download and Apply iTerm2 Color Scheme

1. Choose your desired iTerm2 color scheme from [iTerm2 Color Schemes](https://iterm2colorschemes.com/).
2. Download the theme file and save it using the following extension: `.itermcolors`.
3. Open iTerm2.
4. Go to iTerm > Preferences > Profiles > Colors tab.
5. Click on Color Presets... at the bottom right > Import...
6. Select your downloaded `.itermcolors` file.
7. Once imported, select it from the list of Color Presets.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### **Step 4: Install Oh My Zsh**

using the following command:

{% code overflow="wrap" %}
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
{% endcode %}

### **Step 5: Install Syntax Highlighting and Auto-Suggestions Plugins**

1. **Syntax Highlighting**:

{% code overflow="wrap" %}
```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
{% endcode %}

2. **Auto-Suggestions**:

{% code overflow="wrap" %}
```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
{% endcode %}

After cloning, add `zsh-syntax-highlighting` and `zsh-autosuggestions` to the `plugins` section in `~/.zshrc`.

```sh
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```



### **Step 6: Install and Configure the Powerlevel10k Theme**

1. Clone the Powerlevel10k repository:

{% code overflow="wrap" %}
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
{% endcode %}

2. Update the `ZSH_THEME` line in your `~/.zshrc` file to use Powerlevel10k:

```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

3. Apply the changes by sourcing `~/.zshrc`:

```sh
source ~/.zshrc
```

### **Step 7: Install a Nerd Font**

To fully enjoy Powerlevel10k, you'll need a Nerd Font. Choose and download your preferred Nerd Font from [Nerd Fonts](https://www.nerdfonts.com/font-downloads). Install the font on your system then set it from iTerm2 preferences.



### Step 8: Beautifying the `ls` Command with `colorls` Ruby gem

**Install `colorls`**:

```sh
sudo gem install colorls
```

To avoid typing `colorls` every time, we'll create an alias in the `.zshrc` file. This will allow us to use `ls` as a substitute command. Open `~/.zshrc` and add:

```sh
alias ls='colorls'
```

**Apply Changes**: For the alias to take effect, source your `.zshrc` file by running:

```sh
source ~/.zshrc
```



Et voilà!&#x20;

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Reference:

{% embed url="https://www.youtube.com/watch?v=wNQpDWLs4To" %}

