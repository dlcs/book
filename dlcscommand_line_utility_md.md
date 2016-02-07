# DLCS Command Line Utility

A command line utility for interacting with the DLCS, rather than issuing HTTP API requests directly. It can register single images from a local file system or from remote origin endpoints. Customers can use the utility to help build systems integration solutions quickly (it's just another command to pipe things to).

Note - this also acts as a really good test harness for the HTTP API.

Examples

(not to be taken as definitive syntax, just for feel)

Register an image from a local file system and allow the DLCS to assign an ID:

```dlcs --immediate -space 'my-space' my-local-image.tiff```

Register an image from the internet

```dlcs --queued --space 'my-space' --id '09fed887abab65' http://flickr.com/xxx/yyy```

Default settings (customer id, credentials etc) are configured in a config file (although can be overridden as args).

More examples:

Recursively register the contents of folder (dir flag) on FTP site:

```dlcs --space 3 dir -s --suppress-count ftp://myftp.net/images/folder```

(This works for FTP, local files where a directory listing can be obtained but not for http(s)). Without the --suppress-count flag it will warn with "you are about to register 1345654 files, do you wish to continue? y/n". Even so there is still a maximum set in config, say 5000 images at a time. dlcs utility can batch them.

Super simple - default customer, space, credentials and all other options; utility packages local binary into POST:

```dlcs myimage.bmp```