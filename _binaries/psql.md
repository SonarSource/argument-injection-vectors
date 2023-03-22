---
functions:
  command:
    - description: The `--output` argument pipes the data in an external command if prefixed by `|`.
      code: psql -o'|id>/tmp/foo'
      references:
        - title: Implementation of `postgres/src/bin/psql/common.c`
          url: https://github.com/postgres/postgres/blob/2673ebf49acfd83b09c777ced8f21eacd27b51ce/src/bin/psql/common.c#L45-L83
---
