# Alien::Build::Plugin::Fetch::Prompt ![linux](https://github.com/plicease/Alien-Build-Plugin-Fetch-Prompt/workflows/linux/badge.svg) ![macos](https://github.com/plicease/Alien-Build-Plugin-Fetch-Prompt/workflows/macos/badge.svg) ![windows](https://github.com/plicease/Alien-Build-Plugin-Fetch-Prompt/workflows/windows/badge.svg)

Alien::Build plugin to prompt a user before making external download

# SYNOPSIS

In your ~/.alienbuild/rc.pl

```
preload 'Fetch::Prompt';
1;
```

# DESCRIPTION

This plugin allows you to force [Alien::Build](https://metacpan.org/pod/Alien::Build) to prompt the user and ask for permission
before downloading anything from the internet.  It uses the [ExtUtils::MakeMaker](https://metacpan.org/pod/ExtUtils::MakeMaker) `prompt`
function, so that it will do the sensible thing, like not infinitely halt install on
non-interactive installs.  The default response is `yes`, which is usually reasonable
(and the default if you do not use this plugin at all), but you may change this by using
the `ALIEN_DOWNLOAD` environment variable (see below).

# ENVIRONMENT

## ALIEN\_DOWNLOAD

Set this environment variable to the default response.  Should be either `yes` or `no`.

# CAVEATS

This plugin depends on the [alienfile](https://metacpan.org/pod/alienfile) using the appropriate channels for downloading external
libraries.  It is perfectly legal to write a [alienfile](https://metacpan.org/pod/alienfile) that downloads using an external
program like `wget` or `curl`, or not go through the normal fetch plugin.  There is also
nothing stopping someone from doing something nefarious when installing a cpan module.  If you
have strict security requirements you really should audit the alienfile and other Perl code
that you are using.

# SEE ALSO

- [Alien::Build](https://metacpan.org/pod/Alien::Build)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017-2024 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
