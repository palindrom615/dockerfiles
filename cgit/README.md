# Dockerfile for [cgit](https://git.zx2c4.com/cgit/)

simple cgit container with lighttpd. No default additional auth layer. No touch on ssh. Secure your codes by yourself.

[Some tweaks added](./cgitrc) besides default settings. like,

- volume mounted `scan-path`
- built-in syntax highlighting with python pygments enabled
- stats, graph, README page rendering enabled
- web crawler indexing denied by `robot.txt`
- etc...

## Volumes

| mount point                      | description                                                                        |
| -------------------------------- | ---------------------------------------------------------------------------------- |
| `/var/repositories`              | `scan-path` of cgit. your bare repositories stands here.                           |
| `/etc/cgitrc.d`                  | cgit config overriding directory: see https://git.zx2c4.com/cgit/tree/cgitrc.5.txt index file is `cgitrc` |
| `/var/lib/cgit`                  | left for user's own files e.g. lua script or filter                                |
| `/usr/share/webapps/cgit/static` | left for customizing css files                                                     |

## Ports

The only exposed port is 80 for cgit.


## Example

```sh
# host repositories inside `~/repos`
docker run -p 8080:80 -v ~/repos:/var/repositories cgit

# override configs
echo "side-by-side-diffs=1" > custom.cgitrc
docker run -p 8080:80 -v ~/repos:/var/repositories \
    -v $(pwd)/custom.cgitrc:/etc/cgitrc.d/cgitrc cgit

# custom css
echo "div#cgit table.list td { border: medium dashed green }" > custom.css
echo "css=/static/custom.css" > custom.cgitrc
docker run -p 8080:80 -v ~/repos:/var/repositories \
    -v $(pwd)/custom.cgitrc:/etc/cgitrc.d/cgitrc \
    -v $(pwd)/custom.css:/usr/share/webapps/cgit/static/custom.css \
    cgit
```