---
functions:
  command:
    - description: |
        `git diff` supports the (undocumented) option `--output`, but if no other positional
        parameters are present, the destination file can only be created or truncated.
        If the Git repository is controlled, planting a bare repository at the top-level
        with a malicious configuration (e.g. `core.fsmonitor`), truncating `.git/config`
        and then running another Git command is enough to gain code execution.
      code: |-
        git diff '--output=.git/config'
        git status
      references:
        - title: "Securing Developer Tools: Unpatched Code Vulnerabilities in Gogs (2/2)"
          url: https://www.sonarsource.com/blog/securing-developer-tools-unpatched-code-vulnerabilities-in-gogs-2/
        - title: "CVE-2024-39932"
          url: https://nvd.nist.gov/vuln/detail/CVE-2024-39932
---
