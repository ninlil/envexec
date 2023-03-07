# envexec
Command-line tool for using .ENV-files

## Syntax
```sh
envexec [-v] [.env-file(s)] -- {command-to-run}
```
`-v` will print all env-files parsed (to StdErr)

## Example

File `vars.env`:
```
A=test-value-1
B=test-value-2
```

File `vars.sh`:
```sh
#!/bin/bash

echo A=$A
echo B=$B
```

Shell:
```sh
$ bash vars.sh
A=
B=

$ envexec.sh vars.env -- bash vars.sh
A=test-value-1
B=test-value-2

$ envexec.sh -v vars.env -- bash vars.sh
parse 'vars.env'...
A=test-value-1
B=test-value-2
```

