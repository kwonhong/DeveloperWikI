## Terminal & Vim & Bash Theme Customization

#### 1. Download Custom Terminal & Vim Theme 
- The theme package should contain **{theme_name}.terminal** and **{theme_name}.vim** files. Otherwise, you will not be able to upload to your terminal & vim editor.

##### Recommended Theme
1. http://color.smyck.org/
2. https://github.com/lysyi3m/osx-terminal-themes

#### 2. Changing the terminal scheme/theme.
1. Open Terminal App.
2. Go to Preferences.
3. Select **Profiles** tab on the top.
4. Click **setting button** at the bottom.
5. Choose ** import ..** option & find your **{theme_name}.terminal** file.
6. Find your theme on the left slide panel & Click **Default** Button
7. Restart your terminal App.

#### 3. Changing Vim Configuration
- Make **colors** directory in **./vim** directory
``` shell
# Making colors directory
mkdir ~/.vim/colors

# Copying vim color theme into colors directory
cp {theme_name}.vim ~/.vim/colors/{theme_name}.vim
```
- Open vim configuration file ```vim ~/.vimrc ```
- Insert these two lines
``` xml
# changing the default color scheme to {theme_name}
colo {theme_name} 

# Putting syntax on
syntax on 
```

- Save and exit & restart vim: **:wq**

#### 4. Customizing Bash Profile
- Open bash configuration file ```vim ~/bash_profile
- Insert these lines
``` shell
# Coloring folder/directory different from file
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
```
