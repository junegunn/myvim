myvim
=====

A script that creates a portable bundle of your Vim environment.

Usage
-----

`myvim` script will create an executable named `vim.$(whoami)`.

```sh
curl -L https://raw.githubusercontent.com/junegunn/myvim/master/myvim | bash
```

Why?
----

Having your .vimrc on GitHub or Bitbucket is usually not enough. Because:

- Installing plugins can be time-consuming
- Firewall may disallow access to public network
- You don't want to impose your personal preferences on others when using
  shared accounts on servers

How does it work?
-----------------

`myvim` creates a tar archive of your .vimrc and .vim directory and append it
to a small bash script that temporarily swaps the existing .vim directory on
the system with the one from the archive to reproduce your Vim environment.

Limitation
----------

Since the generated executable swaps `~/.vim` directory while running Vim, the
other Vim processes can be affected as well. It would be ideal if we could
avoid swapping it, but most Vim configurations in the wild are not written in
a portable way and directly refer to the directory.

