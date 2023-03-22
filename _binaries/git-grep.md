---
functions:
  command:
    - description: |
        This vector requires to be in a valid Git repository and a single positional argument.
      references:
        - title: GitLib 0.6 RCE
          url: https://web.archive.org/web/20180725110320/https://security.szurek.pl/exploit-bypass-php-escapeshellarg-escapeshellcmd.html
      code: git grep '--open-files-in-pager=id>/tmp/foo;' .
---
