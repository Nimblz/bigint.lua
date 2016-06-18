bigint.lua is a library that attempts to remove the restrictions on number size
built into vanilla Lua. In order to achieve this, all numbers using operations
that this library provides must first be passed through the bigint.new(num)
function, which converts the number into a table in which every index is a
single digit:

    bigint.new(132) -> {
        sign: "+",
        digits: { 1.0, 3.0, 2.0 }
    }

To simplify the documentation, serialized strings will, from here on out, be
referred to as being of the imaginary type "bigint".

Strings can also be passed into this function. If the number to be serialized is
already too big to exist in lua (inf), you can pass it as a string:

    bigint.new("132") -> {
        sign: "+",
        digits: { 1.0, 3.0, 2.0 }
    }

To convert a big back into a number, use the unserialize() function:

    big = bigint.new("5880")
    bigint.unserialize(big) -> 5880

Currently, only ints are supported. Floats may be added in the future.

Supported operations:
* bigint.new(num or string)
* bigint.check(bigint) - Check if a variable's "type" is bigint - can be forced 
    internally on all operations if the "strict" variable in bigint.lua is set
    to true (default behavior)
* bigint.unserialize(bigint)
* bigint.compare(bigint, bigint, comparison (see bigint.lua))
* bigint.add_raw(bigint, bigint)

TODO:
* bigint.subtract_raw
* bigint.random
* bigint.multiply
* bigint.power
* bigint.divide
* bigint.modulus

For more detailed documentation, see bigint.lua. The operations appear in the
order that they are listed above.
