# Pype

Pipe files to python.

## Tutorial

Pype has mainly two modes of operations: command line and interactive (`-i`).

It's mode of operation is very simple you need to pipe the output of the file
you need to manipulate to pype's input:

```
cat myfile.txt | pype
```

You will then be apply to apply transformations to the file directly from the
command line. If for example you wish to split on tab and convert the first
entry to uppercase you can do like so:

```
cat myfile.txt | pype '.split(" ")[0].upper()'
```

Any method that applies to strings is allowed.

For more powerful textual manipulations pype also supports interactive mode.
This will spawn an interactive python environment in which you will be given
the first line of the file as input. You will then be able to interact with
such line and then repeat the operation on every other line of the file.

```
cat myfile.txt | pype -i > output.txt
```

Will give you an interactive prompt like so:

```
The current input line available as "i".
Set the transformed line equal to "o".
>>> 
```

All you need to do is set the value you want output to stdout (that will end
into output.txt) to be the value of variable `o` then hit `CTRL-d` and the
operation will be repeated for every other line of the file.


# TODO

* Add support for tokenizing on something different than a line (i.e. add
  support for YAML entries and JSON documents).

* Use bpython for the interactive shell.

