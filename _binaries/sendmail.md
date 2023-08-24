---
functions:
  file-write:
    - description: |
        Injection with this command usually requires injecting two arguments.
        In the case of PHP's `mail()`, it has been successfully exploited with
        a single injection point because of the use of faulty sanitization
        functions.
      code: sendmail '-OQueueDirectory=/tmp' '-X/tmp/foo'
      references:
        - title: Why mail() is dangerous in PHP
          url: https://www.sonarsource.com/blog/why-mail-is-dangerous-in-php/
        - title: CVE-2022-39265 in MyBB < 1.8.31
          url: https://github.com/mybb/mybb/security/advisories/GHSA-hxhm-rq9f-7xj7
---
