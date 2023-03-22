---
functions:
  file-write:
    - description: When possible, it is advised to select the TAR archive format to avoid compressing the contents.
      references:
        - title: 'HackerOne #587854 Local files could be overwritten in GitLab, leading to remote command execution'
          url: https://hackerone.com/reports/587854
      code: git archive '--output=/tmp/foo'
---
