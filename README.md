# Removing empty lines with C++ and sed

I wrote a small C++ program that invokes GNU sed to remove empty lines from a file named `textfile` in its working directory. A line containing spaces survives because the pattern matches only lines with zero characters. [Source](sed.cpp)

## Try it with a sample file

From the repository root, I use a temporary directory because the program edits the file in place.

```sh
workdir=$(mktemp -d)
c++ sed.cpp -o "$workdir/clean-lines"
(
  cd "$workdir" || exit 1
  printf 'first\n\n   \nlast\n' > textfile
  ./clean-lines
  cat -n textfile
)
```

## License

I license my C++ wrapper under the [MIT License](LICENSE). It calls the separately installed GNU sed program.
