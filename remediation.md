---
layout: page
title: Remediation
---

Remediating this bug class requires knowing about the behavior of the callee's argument parsing.

## With POSIX-compliant argument parsing

For most Linux binaries, parsers will be compliant with the POSIX specification and support the end-of-options switch. 

[POSIX specifies that](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap12.html):

> The first -- argument that is not an option-argument should be accepted as a delimiter indicating the end of options. Any following arguments should be treated as operands, even if they begin with the '-' character.

You can try out this behavior by creating and then removing a file whose name starts with a dash like `-h`:

```console
bash-3.2$ touch -h
usage:
touch [-A [-][[hh]mm]SS] [-acfhm] [-r file] [-t [[CC]YY]MMDDhhmm[.SS]] file ...
bash-3.2$ touch -- -h
bash-3.2$ ls -alh
total 0
-rw-r--r--  1 [...] -h
drwxr-xr-x  3 [...]  .
drwxrwxrwt  9 [...]  ..
bash-3.2$ ls *
-h
bash-3.2$ rm *
rm: illegal option -- h
usage: rm [-f | -i] [-dPRrvW] file ...
       unlink file
bash-3.2$ rm -h
rm: illegal option -- h
usage: rm [-f | -i] [-dPRrvW] file ...
       unlink file
bash-3.2$ rm -- -h
bash-3.2$ ls -alh
total 0
drwxr-xr-x  2 [...] .
drwxrwxrwt  9 [...] ..
```

## Without POSIX-compliant argument parsing

When dealing with programs that do not handle end-of-options, for instance [`zip`](/binaries/zip) and its custom argument parsing, the safest way to proceed is to prefix any user-controlled path by `./` or `/`. 

See the fix for elFinder's [CVE-2021-32682](https://github.com/Studio-42/elFinder/commit/a106c350b7dfe666a81d6b576816db9fe0899b17#diff-85602823cf2cdaf2502dc4f1b97001ffc0f083652aef175d9f068a5bfe90ca71R6875-R6882 ) for an implementation example.

## Windows

_Open for contribution!_
