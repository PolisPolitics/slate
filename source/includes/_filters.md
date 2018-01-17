#Filters

## Examples

Subfield bar of field foo is equal to string literal "baz".

`foo/bar eq "baz"`

Field bar of field foo is not equal to string literal "baz", and field qux is greater than or equal to 42.

`/foo/bar neq "baz" and /qux gte 42`

Field bar of field foo is equal to nil (null).

`/foo/bar eq nil`

The conditions field bar of field foo is not equal to string literal "baz" and field qux is greater than or equal to 42 must be true, or the field quux must start with "Hello".

`(/foo/bar neq "baz" and /qux gte 42) or /quux like "Hello*"`

The value of field foo should not be in the array of values 42, "bar", and "baz".

`/foo nin [42,"bar","baz"]`

The value of field foo should be in the array value of field bar.

`/foo in /bar`

The value of field foo is greater than or equal to 0 or less than or equal to 42.

`/foo between 0,42`
