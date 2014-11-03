myvim
=====

A script that creates a portable bundle of your Vim environment.

Usage
-----

`myvim` script will create an executable named `vim.$(whoami)`.

```sh
bash <(curl -L https://raw.githubusercontent.com/junegunn/myvim/master/myvim)
```

### Options

- `-e|--edit`

Why?
----

You want your Vim settings and plugins on whichever server you connect to. But
having your .vimrc on GitHub or Bitbucket is usually not enough. Because:

- You need Git and free access to internet
- Even when both conditions are met, downloading plugins can be time-consuming
- When the user account on the server is shared among coworkers, you need to
  restore the default configuration every time when you're done

How does it work?
-----------------

`myvim` creates a tar archive of your .vimrc and .vim directory and append it
to a small bash script that temporarily swaps the existing .vim directory on
the system with the one from the archive and starts Vim with your usual
settings and plugins.

Limitation
----------

Since the generated executable swaps `~/.vim` directory while running Vim, the
other Vim processes can be affected as well. It would be ideal if we could
avoid swapping it, but most Vim configurations in the wild are not written in
a portable way and directly refer to the directory.

