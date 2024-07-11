---
functions:
  command:
    - description: |
        The `--split-string` vector requires a positional argument in addition to
        the injected argument. If possible, use a colon in the positional argument
        to always trigger the command.
        The `--split-string` allows supplying multiple additional arguments. The first
        positional argument not containing an equals sign (`=`) will be executed as a
        command, all following arguments are passed to that command as arguments.
      code: |-
        env '--split-string=sh -c "id > /tmp/pwned"' foo 
      references:
        - title: "Securing Developer Tools: Unpatched Code Vulnerabilities in Gogs (1/2)"
          url: https://www.sonarsource.com/blog/securing-developer-tools-unpatched-code-vulnerabilities-in-gogs-1/
        - title: "CVE-2024-39930"
          url: https://nvd.nist.gov/vuln/detail/CVE-2024-39930
---
