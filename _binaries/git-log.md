---
functions:
  file-write:
    - references:
        - title: "HackerOne #658013 - Git flag injection - local file overwrite to remote code execution"
          url: https://hackerone.com/reports/658013
      code: git log '--output=/tmp/foo'
---
