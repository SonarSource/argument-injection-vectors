---
layout: page
title: Contributing
---

## Contributing

We welcome all contributions to this project [on GitHub](https://github.com/SonarSource/argument-injection-vectors). You can either open an Issue to suggest improvements or directly open a Pull Request if you are confident with your suggestion.

Here are a few guidelines for Pull Requests:
- We expect a reference to _at least_ one publication that demonstrates it: code, CTF write-up, blog posts, talks, etc.
- Document all the requirements for the new vector, for instance, how many controlled arguments are required. 
- In general, we prefer vectors leading to command execution and file write primitives. Other impacts, i.e. file read, can be approved when they were demonstrated to be useful in realistic scenarios.

## Structure

We use a slighly modified fork [GTFOBins](https://github.com/GTFOBins/GTFOBins.github.io). 
You can visualize individual vectors in the `_binaries` folder for inspiration. 
Every vector is a YAML front matter that describes its functions, how to trigger it, its requirements, and references. 

For instance, this is the vector for `git ls-remote`:

```yaml
functions:
  command:
    - description: |
        This vector requires an additional positional argument.
      code: |-
        git ls-remote '--upload-pack=id>/tmp/foo;' foo
      references:
        - title: "Agent 008: Chaining Vulnerabilities to Compromise GoCD"
          url: https://www.sonarsource.com/blog/gocd-vulnerability-chain/
```

Pre-defined functions are:
- `command`: It can be used to break out from restricted environments by running non-interactive system commands
- `file-write`: It writes data to files, it may be used to do privileged writes or write files outside a restricted file system
- `file-read`: It reads data from files, it may be used to do privileged reads or disclose files outside a restricted file system
- `library-load`: It loads shared libraries that may be used to run code in the binary execution context

## Building the website

We use Jekyll to generate the website and the search index. Install the required dependencies and then start Jekyll's local server:

```
$ bundle install
$ bundle exec jekyll serve
```
