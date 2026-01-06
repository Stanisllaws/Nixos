{ config, pkgs, pkgs-unstable, ... }:















{
  # Home Manager needs a bit of information about you and the paths it should
  # manage.
  home.username = "rafal";
  home.homeDirectory = "/home/rafal";

  # This value determines the Home Manager release that your configuration is
  # compatible with. This helps avoid breakage when a new Home Manager release
  # introduces backwards incompatible changes.
  #
  # You should not change this value, even if you update Home Manager. If you do
  # want to update the value, then make sure to first check the Home Manager
  # release notes.
  home.stateVersion = "25.05"; # Please read the comment before changing.

  # The home.packages option allows you to install Nix packages into your
  # environment.
  # Use 'pkgs' for stable packages and 'pkgs-unstable' for latest versions
  home.packages = [
    # Custom script for wallpaper management - my command type bash 12.09.24 auto start wallpaper

#Vim comands 
  (pkgs.writeShellScriptBin "vimhelp" ''
    #!/bin/bash
    bat ~/.vimhelp.2025 
    exec "$SHELL"
  '')

#List agenetions and clean up generations
(pkgs.writeShellScriptBin "ls-gen" ''
    #!/lib64/in/bash
    sudo nix-env --list-generations --profile /nix/var/nix/profiles/system 
   
'')







#Copying autput for txt.files 
(pkgs.writeShellScriptBin "cpd" ''
    #!/lib64/in/bash
   echo "Enter file name to copy:"
read filen
 cat "$filen" | xclip -sel c
'')




  (pkgs.writeShellScriptBin "vimh" ''
    #!/bin/bash
    nvim ~/.zarzadznie-nix/pomoc-nix1 
    exec "$SHELL"
  '')


#Bluetooth Start paring 
  (pkgs.writeShellScriptBin "paird" ''
    #!/bin/bash
    bluetoothctl && pair ????????  
    exec "$SHELL"
  '')

  

# Rofi launch 
  (pkgs.writeShellScriptBin "rofimenu" ''
    #!/bin/bash
    rofi -show drun
    exec "$SHELL"
  '')



# START OF DISPLAY SCRIPT{
  
(pkgs.writeShellScriptBin "tv" ''
    #!/bin/bash
    alacritty --command tv2
    exec "$SHELL"
  '')
 (pkgs.writeShellScriptBin "tv2" ''
    #!/bin/bash
   # Display menu options
echo -e "\nSET MONITORS\n"
echo "1 - Set mirroring screens"
echo "2 - Set only HDMI"
echo "3 - Set only computer screen"
echo "4 - Set HDMI: Right | Computer: Left"
echo "5 - Set HDMI: Left | Computer: Right"
echo "Any other key to exit"

# Prompt user for input
read -p "Enter your choice: " i

# Handle choices based on user input
case $i in
  1)
    echo "Mirroring screens"
    xrandr --output HDMI-1 --same-as eDP-1 --mode 1920x1080 
    ;;
  2)
    echo "Screen only HDMI"
    xrandr --output eDP-1 --off --output HDMI-1 --auto 
    ;;
  3)
    echo "Screen only computer screen"
    xrandr --output eDP-1 --auto --output HDMI-1 --off 
    ;;
  4)
    echo "Default screen setting: HDMI Right | Computer Left" 
    xrandr --output HDMI-1 --auto --right-of eDP-1
    ;;
  5)
    echo "Default screen setting: HDMI Left | Computer Right"
    xrandr --output HDMI-1 --auto --left-of eDP-1
    ;;
  *)
    echo "Exit"
    ;;
esac

read -p "Enter q to exit: " input
if [ "$input" = "q" ]; then
    exit 0
fi   



exec "$SHELL"
'')
  
# } END OF DISPLAY SCRIPT 





 
#Close Xmonad 
  (pkgs.writeShellScriptBin "killxmonad" ''
    #!/bin/bash
    pkill xmonad
    exec "$SHELL"
  '')
  
# Xmonad Key Maps 
  (pkgs.writeShellScriptBin "xmonadkeys" ''
    #!/bin/bash
    bat ~/.xmonad/xmonad.hs
    exec "$SHELL"
  '')
 


  (pkgs.writeShellScriptBin "sleep" ''
    #!/bin/bash
    systemctl suspend
    exec "$SHELL"
  '')
 





(pkgs.writeShellScriptBin "on" ''
      #!/usr/bin/env bash
      hyprctl hyprpaper wallpaper ",/home/rafal/Pictures/tapeta-hyprland/NixOS.jpg"
    '')
    
# test 1
(pkgs.writeShellScriptBin "hi" ''
      #!/usr/bin/env bash
      echo "hello"
    '')

## Qtile command keybinging       
  (pkgs.writeShellScriptBin "braveweb" ''
    #!/bin/bash
    brave && exit 
    exec "$SHELL"
  '')
  












  # C programs built from source - now handled via flake input
  # (removed duplicate build that caused pure evaluation error)

## THE C-programming ####


  (pkgs.writeShellScriptBin "pc" ''
    #!/bin/bash
    cd ~/programming/c-code || exit
    exec "$SHELL"
  '')
  (pkgs.writeShellScriptBin "pcl" ''
    #!/bin/bash
    cd ~/programming/c-code/c-lectures || exit
    exec "$SHELL"
  '')
  (pkgs.writeShellScriptBin "pch" ''
    #!/bin/bash
    cd ~/programming/c-code/c-hw || exit
    exec "$SHELL"
  '')
  (pkgs.writeShellScriptBin "pct" ''
    #!/bin/bash
    cd ~/programming/c-code/c-test || exit
    exec "$SHELL"
  '')

(pkgs.writeShellScriptBin "cnotes" ''
    #!/bin/bash
   nvim  ~/programming/c-code/c-lectures/lectur-note
    exec "$SHELL"
  '')

(pkgs.writeShellScriptBin "pcl2" ''
    #!/bin/bash
    cd  ~/programming/c-code/c-lectures.b || exit
    exec "$SHELL"
  '')

#LocalSend Password 19.11.25
(pkgs.writeShellScriptBin "sendpass" ''
    #!/bin/bash
    cat  ~/LocalSend-files/localSendPass
    exec "$SHELL"
  '')

# Skruty

          # Qtile 
(pkgs.writeShellScriptBin "qtileconf" ''
    #!/bin/bash
   nvim ~/.config/qtile/config.py
    exec "$SHELL"
  '')


               






#  likeing files 


(pkgs.writeShellScriptBin "nixhome" ''
    #!/bin/bash
    nvim  /etc/nixos/home.nix
    exec "$SHELL"
  '')

(pkgs.writeShellScriptBin "update" ''
    #!/bin/bash
 cd ~/.nixrc && sudo nix flake update && sudo nixos-rebuild switch --flake .#
  exec "$SHELL"
      
'')

(pkgs.writeShellScriptBin "rebuildnix" '' 
    #!/bin/bash
 cd ~/.nixrc && sudo nixos-rebuild switch --flake .#
  exec "$SHELL"
      
'')



(pkgs.writeShellScriptBin "cleannix" ''
    #!/bin/bash
sudo nix-collect-garbage --delete-older-than 7d && 
sudo nixos-rebuild switch --install-bootloader
'')

# lista generacji NixOs
(pkgs.writeShellScriptBin "generacje" ''
    #!/bin/bash
sudo nix-env --list-generations --profile /nix/var/nix/profiles/system
  exec "$SHELL"


'')






# 24.09.25r. hyprland shortcut
 
   (pkgs.writeShellScriptBin "hypr" ''
    #!/bin/bash
    sudo nvim  ~/.config/hypr/hyprland.conf
    exec "$SHELL"
  '')



# EXAMPLE: Add packages here (uncomment to install)
    # UNSTABLE packages (latest versions):
   # pkgs-unstable.neovim      # Latest Neovim from unstable
    # pkgs-unstable.zed-editor  # Latest Zed editor
    # pkgs-unstable.discord     # Latest Discord
    
    # STABLE packages (tested versions):
    pkgs.emacs               # Stable Emacs
    # pkgs.firefox             # Stable Firefox
    # pkgs.thunderbird         # Stable Thunderbird

    

# # Adds the 'hello' command to your environment. It prints a friendly
    # # "Hello, world!" when run.
    # pkgs.hello

    # # It is sometimes useful to fine-tune packages, for example, by applying
    # # overrides. You can do that directly here, just don't forget the
    # # parentheses. Maybe you want to install Nerd Fonts with a limited number of
    # # fonts?
    # (pkgs.nerdfonts.override { fonts = [ "FantasqueSansMono" ]; })

    # # You can also create simple shell scripts directly inside your
    # # configuration. For example, this adds a command 'my-hello' to your
    # # environment:
    # (pkgs.writeShellScriptBin "my-hello" ''
    #   echo "Hello, ${config.home.username}!"
    # '')

 

  ];

  # Home Manager is pretty good at managing dotfiles. The primary way to manage
  # plain files is through 'home.file'.
  home.file = {
    # # Building this configuration will create a copy of 'dotfiles/screenrc' in
    # # the Nix store. Activating the configuration will then make '~/.screenrc' a
    # # symlink to the Nix store copy.
    # ".screenrc".source = dotfiles/screenrc;

    # # You can also set the file content immediately.
    # ".gradle/gradle.properties".text = ''
    #   org.gradle.console=verbose
    #   org.gradle.daemon.idletimeout=3600000
    # '';
  };

  # Home Manager can also manage your environment variables through
  # 'home.sessionVariables'. These will be explicitly sourced when using a
  # shell provided by Home Manager. If you don't want to manage your shell
  # through Home Manager then you have to manually source 'hm-session-vars.sh'
  # located at either
  #
  #  ~/.nix-profile/etc/profile.d/hm-session-vars.sh
  #
  # or
  #
  #  ~/.local/state/nix/profiles/profile/etc/profile.d/hm-session-vars.sh
  #
  # or
  #
  #  /etc/profiles/per-user/rafal/etc/profile.d/hm-session-vars.sh
  #
  home.sessionVariables = {
    # EDITOR = "emacs";
  };

  # Bash configuration
  programs.bash = {
    enable = true;
    shellAliases = {
      v = "mpv ~/Sounds/shutdownWM && nvim";
      vim = "nvim";
      ll = "ls -l";
      la = "ls -la";
      lsdot = "ls -a";
      #on = "./.zmiana-tapety";
      grep = "grep --color=auto";
      ".." = "cd ..";
      "..." = "cd ../..";
      
      
      

                  

    };
    bashrcExtra = ''
      # Custom bash configuration
      export HISTCONTROL=ignoredups:erasedups
      export HISTSIZE=10000
      export HISTFILESIZE=10000
      
      # Append to history file, don't overwrite
      shopt -s histappend
      
      # Check window size after each command
      shopt -s checkwinsize
      
      # Initialize Starship prompt
      eval "$(starship init bash)"
    '';
    profileExtra = ''
      # Custom profile configuration (equivalent to .bash_profile/.profile)
      # This runs for login shells
    '';
    sessionVariables = {
      EDITOR = "nano";  # Change this to your preferred editor
    };
  };

  # Let Home Manager install and manage itself.
  programs.home-manager.enable = true;
}
