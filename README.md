env.d
================================================================================

It is exactly as insane and silly as it looks. It also may come with some risk depending on how the computer permissions are set up.

Inspiration for this came from
  - https://wiki.archlinux.org/index.php/XDG_Base_Directory_support
  - https://specifications.freedesktop.org/basedir-spec/basedir-spec-0.7.html

## Getting Started

### Step 1 -- Install Script

Add the following snippet to a POSIX compliant shell startup files:
```sh
if [ -d "$XDG_CONFIG_HOME/shell/env.d" ]; then
  for i in $XDG_CONFIG_HOME/shell/env.d/* ; do
    if [[ -f $i && -r $i ]] ; then . $i ; fi
  done ; unset i
fi
```

### Step 2 -- Fix all the S#!T

Fix the many things that just broke due to your naïve attempt to micromanage your operating system into behaving.

On macOS this included making sure `$XDG_CONFIG_HOME` is set at startup *one way or another*. Take note that if you don't have the permissions correct, you will have a bad day when someone or more likely something decides to delete modify you bodge. Your first sign of this, depending on how aggressively you modified your config, will be that none of your programs are working correctly.

### Step 3 -- Regret

Perhaps now is the time to reconsider your trajectory and all of the decisions that led you to this point.
