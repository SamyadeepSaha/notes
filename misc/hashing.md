# Hashing

- Static hashing
- Dynamic hashing

## Static hashing

### Division

This hash function which is the most widely used Hash function in
practice, assume the Keys are non-negative integers the modulo %
operator. The key k is divided by some number D, and the remainder is
used as the home bucket for k. More formally h(k) = k % D

### Mid Square

The Mid Square hash function determines the home bucket for a key by
squaring the key and then using an appropriate number of bits from the
middle of square to obtain the bucket address, the key is assumed to be
integer. Since the middle bits of the square usually depends on all bits
of the key, different keys are expected to result in different hash
addresses with high probaility, even when some of the digits are the
same. The number of bits to be used to obtain the bucket address depends
on the table size. If r bits are used the range of values is 0 through
2^r - 1 so the size of hash tables is chosen to be a power of two when
the mid square function is used.

### Folding

In this method the key k is partitioned into several parts, all but
possibly the last being the same length. These partitions are then added
together to obtain the hash address for k.

**Example** Suppose that k = 12320324111220 and we partition it into
parts that are three decimal digits long. The partition are P1 = 123,
P2 = 203, P3 = 241, P4 = 112, P5 = 20. Using shift folding, we obtain
h(k) sum of all partion = 123 + 203 + 241 + 112 + 20 = 699.
When we are folding  at the boundaries is used, we first reverse P2 and
P4 to obtain 302 and 211 respectively. Next the five partitions are
added  to obtain h(k) = 123 + 302 + 241 + 211 + 20 = 897.

### Digit Analysis

This method is particularly useful in the case of a static file where
all the keys in the table are known in advance. Each key is interpreted
as a number using some radix r. The same radix is used for all the key
is interpreted as a number using some radix r, the same radix is used
for all the key in the table. Using the radix the digits of each key
are examined. Digit having the most skewed distributions are deleted.
Enough digits are deleted so that the number of remaining digits is
small enough to give an address in the range of the hash table.

## Secure Hash function

We may encrypt the smaller message or transmit the smaller message on
more expensive but far more secure channel than used for the
transmission of a long message. One way to accomplish our task is to
used for the hash function h nd transmit M's hash value h(m) using the
more secure method, M is transmitted over the insecure channel as
before.

### SHA algorithm

Preprocess the message so that its lenght is q * 512 bits for some
integer q. The preprocessing may entail adding a string of zeroes to the
end of the message. Initialize the 160 bit output buffer OB, which
comprises five 32bits registers A, B, C, D and E, with A = 67452301,
B = efcdab89, C = 98badecfe, D = 10325476, E = c3d2e1f0 call values are
in hexadecimal.

## Overflow Handling

- Open Addressing
    - Linear probing
    - Quadratic probing
- Chaining

### Linear probing

When inserting a new pair whose key is k, we search the hash table
buckets in the order, ht[h(k)+i]%d, 0<=i<=b-1, where h is the hash
function and b is the number of bucket. This search terminates when we
reach the first unfilled bucket and the new pair is inserted into this
bucket. In case no such bucket is found, the hash table is full and it
is necessary to increase the table size.

### Quadratic probing

A quadratic function of i is used as the increament. In particular the
search is carried out by examining buckets h(k), (h(k)+i^2)%d, and
(h(k)-i^2)%b for 1<=i<=(b-1)/2 when b is a prime number of the form
4j+3, for j an integer, the quadratic search described above examines
every bucket in the table.

| Prime | j || Prime | j   |
|-------|---||-------|-----|
| 3     | 0 || 43    | 10  |
| 7     | 1 || 59    | 14  |
| 11    | 2 || 127   | 31  |
| 19    | 4 || 251   | 62  |
| 23    | 5 || 503   | 125 |
| 31    | 7 || 1019  | 254 |

### Chaining

## Dynamic hashing

- Using Directories
- Directoryless
