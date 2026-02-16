Nixos – Nixos with DWM and ST
Dwm Part

My config allows you to configure dwm according to your own preferences.

⚠️ WARNING – Backup Your Configuration (Recommended)

Back up your configuration before making any changes.

For example:

sudo cp -r /etc/nixos/ ~/mybackups


If you make a mistake, you can always restore your old configuration.

How to Configure Your Own DWM
1. Enable X11

You need to enable X11 in your configuration.nix:

services.xserver.enable = true;
# Enable the X11 windowing system.

2. Clone Dwm

Clone Dwm from the suckless website or, for example, from my repository.

3. Create a Folder

Create a folder in the /etc/nixos/ directory (or wherever your configuration.nix and flake.nix are located if you use flakes).

If it is located in a different directory, it may not work.
It must be in the same directory as configuration.nix.

Example (create a folder called dotfiles):

sudo mkdir -p /etc/nixos/dotfiles


To verify:

ls /etc/nixos/dotfiles/

4. Move Your Dwm Configuration

Move your dwm directory (the one you cloned) to the folder you created:

sudo mv Downloads/dwm /etc/nixos/dotfiles

5. Add the Dwm Override to configuration.nix

Add the following to your configuration.nix:

services.xserver.windowManager.dwm = {
  enable = true;

  package = pkgs.dwm.overrideAttrs {
    src = ./dotfiles/dwm; # Replace with your actual path
  };
};


Make sure the path matches your directory structure.

6. Rebuild Nixos

Save your configuration and run:

sudo nixos-rebuild switch


Or use another rebuild command if needed.

Extra Tip (Testing)

You can test the rebuild without applying changes:

sudo nixos-rebuild dry-build


This checks whether Nixos will rebuild successfully without switching to the new configuration.
