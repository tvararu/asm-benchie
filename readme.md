Naïve asm.js benchmark
===

Just a quick test I did to see what the difference is between native C code, JS and Emscripten-powered asm.js. It's a simple QuickSort that runs over 1 million (hardcoded) random numbers.

**Warning**: Files are extremely fat. They have 7.9MB of random numbers.

Here are the results I got:

```bash
$ gcc bench.c -o bench.out
$ ./bench.out
0.162025
$ node bench.js
bench: 629ms
$ node bench-asm.js
0.176000
```

Then [a friend](https://github.com/ihalip) pointed out that I can use `-O2` to get better C performance.

```bash
$ gcc bench.c -o bench.out -O2
$ ./bench.out
0.087932
```

`bench-asm.js` was compiled with [emscripten](https://github.com/kripken/emscripten/wiki/Emscripten-SDK).

License
===
[MIT](license.txt).
