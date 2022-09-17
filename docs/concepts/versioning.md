# AddonScript Versioning

## AddonScript Version Numbers

AddonScript version numbers MUST only contain non-whitespace ASCII characters. They SHOULD follow the
[SemVer specifications](https://semver.org/spec/v2.0.0.html). AddonScript version numbers are ordered
according to the [Maven version order specification](#version-order-specification). 

### SemVer Compatible Versions

If an AddonScript version number is valid SemVer, that version of the addon is SemVer compatible and implies 
all semantics according to SemVer. AddonScript implementations MAY provide specific behavior based on the 
semver semantics, for example warning the user before updating to a next major version.

## AddonScript Version Ranges

An AddonScript version range can either be a [SemVer version range](https://github.com/semver/semver/pull/584)
or a [Maven version range](#dependency-version-requirement-specification). If a version range starts with one
of SemVer primitive operators (`<`, `<=`, `>`, `>=`, `=`) it will be considered as a SemVer version range, 
otherwise it will be a Maven version range. SemVer version ranges can only include
[SemVer compatible versions](#semver-compatible-versions). If the version range is required to include
an exact version, for example when using the `included` [relational flag](./flags.md#relational-flags),
it MUST be a Maven version range, which is the targeted version surrounded by `[]`. In all other cases
it is highly RECOMMENDED to use SemVer version ranges, as long as the targeted addon uses 
[SemVer compatible versions](#semver-compatible-versions).

## Maven Versioning Specification

### Version Order Specification

The Maven coordinate is split in tokens between dots ('`.`'), hyphens ('`-`') and transitions between digits and characters. The separator is recorded and will have effect on the order. A transition between digits and characters is equivalent to a hyphen. Empty tokens are replaced with "`0`". This gives a sequence of version numbers (numeric tokens) and version qualifiers (non-numeric tokens) with "`.`" or "`-`" prefixes.

Splitting and Replacing Examples:

- `1-1.foo-bar1baz-.1` -> `1-1.foo-bar-1-baz-0.1`

Then, starting from the end of the version, the trailing "null" values (`0`, `""`, "`final`", "`ga`") are trimmed. This process is repeated at each remaining hyphen from end to start.

Trimming Examples:

- `1.0.0` -> `1`
- `1.ga` -> `1`
- `1.final` -> `1`
- `1.0` -> `1`
- `1.` -> `1`
- `1-` -> `1`
- `1.0.0-foo.0.0` -> `1-foo`
- `1.0.0-0.0.0` -> `1`

The version order is the `lexicographical order` on this sequence of prefixed tokens, the shorter one padded with enough "null" values with matching prefix to have the same length as the longer one. Padded "null" values depend on the prefix of the other version: 0 for '.', "" for '-'. The prefixed token order is:

- if the prefix is the same, then compare the token:
    - Numeric tokens have the natural order.
    - Non-numeric tokens ("qualifiers") have the alphabetical order, except for the following tokens which come first in this order:
"`alpha`" < "`beta`" < "`milestone`" < "`rc`" = "`cr`" < "`snapshot`" < "" = "`final`" = "`ga`" < "`sp`"
        - the "`alpha`", "`beta`" and "`milestone`" qualifiers can respectively be shortened to "a", "b" and "m" when directly followed by a number.
- else "`.qualifier`" < "`-qualifier`" < "`-number`" < "`.number`"


End Result Examples:

- "`1`" < "`1.1`" (number padding)
- "`1-snapshot`" < "`1`" < "`1-sp`" (qualifier padding)
- "`1-foo2`" < "`1-foo10`" (correctly automatically "switching" to numeric order)
- "`1.foo`" < "`1-foo`" < "`1-1`" < "`1.1`"
- "`1.ga`" = "`1-ga`" = "`1-0`" = "`1.0`" = "`1`" (removing of trailing "null" values)
- "`1-sp`" > "`1-ga`"
- "`1-sp.1`" > "`1-ga.1`"
- "`1-sp-1`" < "`1-ga-1`" = "`1-1`" (trailing "null" values at each hyphen)
- "`1-a1`" = "`1-alpha-1`"

Note: Contrary to what was stated in some design documents, for version order, snapshots are not treated differently than releases or any other qualifier.

### Dependency Version Requirement Specification

Version requirements have the following syntax:

- `1.0`: Soft requirement for 1.0. Use 1.0 if no other version appears earlier in the dependency tree.
- `[1.0]`: Hard requirement for 1.0. Use 1.0 and only 1.0.
- `(,1.0]`: Hard requirement for any version <= 1.0.
- `[1.2,1.3]`: Hard requirement for any version between 1.2 and 1.3 inclusive.
- `[1.0,2.0)`: 1.0 <= x < 2.0; Hard requirement for any version between 1.0 inclusive and 2.0 exclusive.
- `[1.5,)`: Hard requirement for any version greater than or equal to 1.5.
- `(,1.0],[1.2,)`: Hard requirement for any version less than or equal to 1.0 than or greater than or equal to 1.2, but not 1.1. Multiple requirements are separated by commas.
- `(,1.1),(1.1,)`: Hard requirement for any version except 1.1; for example because 1.1 has a critical vulnerability.

Maven picks the highest version of each project that satisfies all the hard requirements of the dependencies on that project. If no version satisfies all the hard requirements, the build fails.