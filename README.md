# base16-i3

This repository is meant to work with
[chriskempson/base16](https://github.com/chriskempson/base16).
It provides a simple template that can be used with the base16 color schemes to
generate a functional config file for
[i3/i3](https://github.com/i3/i3),
a tiling and dynamic window manager.

To use, you can copy one of the config files in themes/ or use curl. First up, you'll want to generate a starting i3 configuration using `i3-config-wizard`. Then you can

```
$ curl https://raw.githubusercontent.com/khamer/base16-i3/master/themes/base16-default-dark.config >> ~/.config/i3/config
```

Note that this will create a second bar because it provides a `bar { ... }` section. You can choose which you'd like.

Alternatively, you can fetch just the base16 colors in a format for the i3 config to use them as variables:

```
$ curl https://raw.githubusercontent.com/khamer/base16-i3/master/colors/base16-default-dark.config >> ~/.config/i3/config
```

The benefit of this approach is you can reference the base16 colors through out
your configuration if you want to customize it further (in particular,
customize your `bar { ... }`.)

For example, you might want to put the bulk of your configuration in `~/.config/i3/base`, reference the base16 variables, and then use a binding like this:

```
bindsym $mod+Shift+c exec "cat .config/i3/colors .config/i3/base > .config/i3/config && i3-msg reload"
```

So you can now run

```
$ curl https://raw.githubusercontent.com/khamer/base16-i3/master/colors/base16-default-dark.config > ~/.config/i3/colors
```

And hit **$mod + Shift + c** to load in the new colors.

You can also fetch the separate bar colors and client properties sections of
the full config from the `bar-colors` and `client-properties` directories.
