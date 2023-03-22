---
functions:
  command:
    - description: |
        `git blame` supports the (undocumented) option `--output`, but if no other positional
        parameters are present, the destination file can only be created or truncated.
        If the Git repository is controlled, planting a bare repository at the top-level
        with a malicious configuration (e.g. `core.fsmonitor`), truncating `.git/config`
        and then running another Git command is enough to gain code execution.
      code: |-
        git blame '--output=.git/config'
        git status
      references:
        - title: "Empowering weak primitives: file truncation to code execution with Git"
          url: https://www.sonarsource.com/blog/empowering-weak-primitives-file-truncation-to-code-execution-with-git/
---
