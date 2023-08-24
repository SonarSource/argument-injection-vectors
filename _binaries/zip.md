---
description: Most invocations of zip are likely to be vulnerable, as it doesn't support the [end-of-options switch](../../remediation/) before the archive name.
functions:
  command:
    - description: |
        This vector relies on the integrity test feature (`-T`) with an arbitrary
        command (`-TT`). To chain both short names, a dummy option is added (`-m`).
        When injecting during the archive creation process, two positional arguments
        are required: the destination and a file to compress.
      references:
        - title: Multiple vulnerabilities in Dell Unisphere for PowerMax vApp, VASA Provider vApp and Solutions Enabler vApp CVE-2022-45103 / CVE-2022-45104
          url: https://www.synacktiv.com/sites/default/files/2023-02/Synacktiv-Security_Advisory-Dell_EMC_vApp_Manager-Multiple_Vulnerabilities.pdf
        - title: elFinder - A Case Study of Web File Manager Vulnerabilities
          url: https://www.sonarsource.com/blog/elfinder-case-study-of-web-file-manager-vulnerabilities/
      code: zip '-TmTT="$(id>/tmp/foo)foooo".zip' './a.zip' './a.txt'
---
