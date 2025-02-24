---
description: |
  This vector can be used to execute arbitrary shell commands.
functions:
  command:
    - code: busctl set-property org.freedesktop.systemd1 /org/freedesktop/systemd1 org.freedesktop.systemd1.Manager LogLevel s debug --address=unixexec:path=firefox,argv1=https://www.example.com
      references:
        - title: D-Bus Specification
          url: https://dbus.freedesktop.org/doc/dbus-specification.html
        - title: man buctl
          url: https://www.freedesktop.org/software/systemd/man/busctl.html
---
