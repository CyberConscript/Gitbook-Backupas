# Hashing

A **hash value** is a fixed-size string or characters that is computed by a hash function. A **hash function** takes an input of an arbitrary size and returns an output of fixed length, i.e., a hash value. We will cover various exciting and clever uses of hash functions and values in this room.

A hash function takes some input data of any size and creates a summary or **digest** of that data. The output has a fixed size. It’s hard to predict the output for any input and vice versa. Good hashing algorithms will be relatively fast to compute and prohibitively slow to reverse, i.e., go from the output and determine the input. Any slight change in the input data, even a single bit, should cause a significant change in the output.

When you log into your computer, hashing plays a role in verifying your password.

The **pigeonhole effect** states that the number of items (_pigeons_) is more than the number of containers (_pigeonholes_); some containers must hold more than one item. In other words, in this context, there are a fixed number of different output values for the hash function, but you can give it any size input. As there are more inputs than outputs, some inputs must inevitably give the same output. If you have 21 pigeons and 16 pigeonholes, some of the pigeons are going to share the pigeonholes. Consequently, collisions are unavoidable. However, a good hash function ensures that the probability of a collision is negligible.

### Commands on Linux:

`md5sum`, `sha1sum`, `sha256sum`, and `sha512sum` produce their outputs in hexadecimal format.







### Commands on Windows:



