# Initial build
Following the guide at: https://rustc-dev-guide.rust-lang.org/building/how-to-build-and-run.html

While building using `./x.py build -i --stage 1 src/libstd`, I came across the error:

```
  = note: /usr/bin/ld: cannot find -lstdc++
          collect2: error: ld returned 1 exit status

error: aborting due to previous error

error: could not compile `rustc_driver`.
```

I searched a bunch for solutions, most involved installing more deps.

Solution came from https://github.com/box/augmented_types/issues/11 , I ended up having to symlink with
```
ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/lib/x86_64-linux-gnu/libstdc++.so
```
