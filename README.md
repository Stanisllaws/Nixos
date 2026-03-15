<<<<<<< HEAD
=======
# ❄️ My NixOS Personal Configuration

This repository documents my personal **NixOS setup**, including custom builds of `dwm`, `st`, shell scripts, and examples of building your own packages.

---

# 🧩 Custom DWM Configuration

To declare your own `dwm` configuration in NixOS, create a directory inside `/etc/nixos`.

Example:

```bash
/etc/nixos/dotfiles/
```

Your **NixOS configuration files** (`configuration.nix`, `flake.nix`) should already be located in `/etc/nixos`.

Inside the `dotfiles` directory, place your **dwm source code**.

Example structure:

```
/etc/nixos/
 ├─ configuration.nix
 ├─ flake.nix
 └─ dotfiles/
     └─ dwm/
         ├─ config.h
         ├─ dwm.c
         └─ other source files
```

Then add the following to **configuration.nix**:

```nix
# DWM configuration override
services.xserver.windowManager.dwm = {
  enable = true;

  package = pkgs.dwm.overrideAttrs {
    src = ./dotfiles/dwm; # Path to your dwm source
  };
};
```

### Important

```nix
src = ./dotfiles/dwm
```

`./` means **current directory**.

In this context it refers to:

```
/etc/nixos/
```

---

# 🖥️ Custom ST (Simple Terminal) Build

The process is similar for **st**, but uses `packageOverrides`.

Example configuration:

```nix
nixpkgs.config.packageOverrides = pkgs: {
  st = pkgs.st.overrideAttrs (oldAttrs:
    {
      src = ./dotfiles/st;
      buildInputs = (oldAttrs.buildInputs or []) ++ [ pkgs.harfbuzz ];
    });
};
```

Example directory:

```
/etc/nixos/dotfiles/st
```

---

# 📜 Shell Scripts in NixOS

In `home.nix`, I maintain a section for **custom shell scripts**.

This behaves similarly to:

```
/usr/local/bin
```

But Nix automatically makes the script executable.

Example:

```nix
home.packages = [

  # Custom script
  (pkgs.writeShellScriptBin "hello"
    ''
    #!/bin/bash
    echo "helloWorld"
    exec "$SHELL"
    '')

];
```

After rebuilding your configuration, the command will be available globally:

```bash
hello
```

---

# ⚙️ Creating Your Own Packages

One of the most interesting features of NixOS is the ability to **build your own packages**.

## Step 1 — Create a Package Directory

Example:

```bash
sudo mkdir -p /etc/nixos/HelloWorldPKG
```

---

## Step 2 — Add Source Files

Inside the directory, create:

```
/etc/nixos/HelloWorldPKG
 ├─ default.nix
 └─ main.c
```

Example `main.c`:

```c
#include <stdio.h>

int main() {
    printf("Hello World\n");
    return 0;
}
```

---

## Step 3 — Write `default.nix`

A minimal example:

```nix
{ pkgs ? import <nixpkgs> {} }:

pkgs.stdenv.mkDerivation {
  name = "hello-world";

  src = ./.;

  buildPhase = ''
    gcc main.c -o hello
  '';

  installPhase = ''
    mkdir -p $out/bin
    cp hello $out/bin/
  '';
}
```
>>>>>>> 3697a2f (README)

