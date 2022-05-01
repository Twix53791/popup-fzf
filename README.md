# popup-fzf
This script just open a pipe into a terminal, so you can push any command you want into from outside to execute them into the "pipe terminal". It was designed for poping a fzf menu.

# Use
Run this script from a terminal:
    `kitty bash -c <thisscript>`
Then `echo "command" > /tmp/dtpipe-<PPID>` from another shell

# Setting a fzf popup menu
- Create a script launching this script into a terminal:

```
#!/bin/bash
pathtoscript="/$HOME/.config/drop_pipe_terminal"
kitty --class pipe_terminal -o background_opacity=0.9 bash -c "$pathtoscript" &
```
- Start the launcher script above at boot (after your window manager, I use bspwm so I launch the script from bspwmrc ; maybe it could be .xinitrc?)
- Set a rule into your window manager to run by default any window of the 'pipe_terminal' class hidden. Mine is bspwm ; into bspwmrc: `bspc rule -a pipe_terminal state=floating sticky=on hidden=on locked=on border=off center=true`
- Bind to a key binding the command you want to send to the pipe. For example in sxhdrc:
