---
layout: page
title: Argument Injection Explained
---

_The following page focuses on Linux and ELF binaries. Contribution is very welcome for other systems!_

## Terminology

Let's first come back on important terminology:

**Argument Parser**

When running the invoked program, the system passes two parameters to the `main()` entry point:
- `argc`: the number of arguments,
- `argv`: a pointer to an array of size `argc+1` with pointers to the actual arguments and a terminating null pointer.

It's up to the program to make sense of these variables passed to `main()`, following its own conventions.

Common implementations like [`getopt(3)`](https://man7.org/linux/man-pages/man3/getopt.3.html) parse arguments based on, but not limited to, the POSIX specification. 

Programs can also choose to rely on niche argument parsers that may present unexpected behaviors or lack support for the end-of-options switch (`--`).
It becomes increasingly rare but can still happen in historical software (e.g., `fossil` or `zip`).

**Arguments: options, option-arguments, and operands**

Arguments passed to a program can be divided into options, option-arguments, and operands as shown in the following picture:

<img src="{{ site.baseurl }}/assets/arguments.svg" width="500px"/>

Any argument that starts with `-` and is not strictly `-` or `--` is called an option. Parsers usually support two forms of options: long ones like `--foo` and short ones like `-f`, where short forms can sometimes be aliases for long forms. Options can expect arguments, for instance, `--foo 1337`, where `--foo` is the option and `1337` the argument. 

**End-of-options**

POSIX-compliant argument parsers support a special switch named end-of-options, represented as `--`. 
All arguments placed after the end-of-options are treated as operands, even if they start with an hyphen (`-`). 

More information on the end-of-options switch to avoid argument injection vulnerabilities can be found on the [Remediation]({{ "/remediation/" | relative_url }}) page.

## Argument Injection

As described in [CWE-88](https://cwe.mitre.org/data/definitions/88.html), an argument injection (also sometimes named _parameter injection_ or _flag injection_) happens when:

> The software constructs a string for a command to execute by a separate component [...] but it does not properly delimit the intended arguments, options, or switches within that command string. 

Contrary to command injection bugs, which hand over the command line to a new instance of `sh` and ultimately evaluate command substitution and control operators, argument injections do not need it. It means that it can happen even during calls to the `exec*` functions in C, `pcntl_exec` in PHP, etc. 

Argument injection bugs are a really cool class of bugs that tend to be often overlooked during code reviews and completely missed in black-box engagements. 

While it is known that user-controlled values should be correctly neutralized before their interpolation in commands, it is not common knowledge among developers that they could still be treated as options. The neutralization usually involves surrounding the value with single quotes to prevent shell substitutions, and thus only matters in shells. 

Even if only one injection point is available, attackers are not always limited to one argument. They can specify multiple short-form options and even include values. 
For instance in Sonar's [elFinder - A Case Study of Web File Manager Vulnerabilities](https://www.sonarsource.com/blog/elfinder-case-study-of-web-file-manager-vulnerabilities/), researchers could demonstrate the execution of arbitrary commands with only one controlled argument to `zip`. In practice, control of three arguments was required. 

It is very common to find such bugs during external command calls, often susceptible to command injection fixed with proper escaping, but without taking care of the potential argument injection. They also often arise during the expansion of wildcard characters by shells (e.g., `tar *`), `sudo` rules, and URL handlers.
