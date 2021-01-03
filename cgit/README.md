# dockerfile for [cgit](https://git.zx2c4.com/cgit/)

simple cgit container with lighttpd. No default additional auth layer. No touch on ssh. Secure your codes by yourself.

## volumes

| mount point                      | description                                                        |
| -------------------------------- | ------------------------------------------------------------------ |
| `/var/repositories`              | `scan-path` of cgit. your bare repositories stands here.           |
| `/etc/cgitrc.d`                    | cgit config overriding directory: see https://git.zx2c4.com/cgit/tree/cgitrc.5.txt |
| `/var/lib/cgit`                  | left for user's own files e.g. lua script or filter                |
| `/usr/share/webapps/cgit/static` | left for customizing css files                                     |

## ports

The only exposed port is 80 for cgit.
