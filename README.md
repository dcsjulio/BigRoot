[![Actions Status](https://github.com/juliodcs/BigRoot/workflows/test/badge.svg)](https://github.com/juliodcs/BigRoot/actions)

NAME
====

BigRoot - Class for supporting roots with arbitrary precision.

SYNOPSIS
========

    use BigRoot;

    # Can change precision level (Default precision is 30)
    BigRoot.precision = 50;

    my $root2 = BigRoot.newton's-sqrt: 2;
    # 1.41421356237309504880168872420969807856967187537695

    say $root2.WHAT;
    # (FatRat)

    # Can use other root numbers
    say BigRoot.newton's-root: root => 3, number => 30;
    # 3.10723250595385886687766242752238636285490682906742

    # Numbers can be Int, Rational and Num:
    say BigRoot.newton's-sqrt: 2.123;
    # 1.45705181788431944566113502812562734420538186940001

    # Can use other rational roots
    say BigRoot.newton's-root: root => FatRat.new(2, 3), number => 30;
    # 164.31676725154983403709093484024064018582340849939498

    # Results are rounded:

    BigRoot.precision = 8;
    say BigRoot.newton's-sqrt: 2;
    # 1.41421356

    BigRoot.precision = 7;
    say BigRoot.newton's-sqrt: 2;
    # 1.4142136

DESCRIPTION
===========

This module provides a way of having arbitrary precision for roots. In order to do that it calculates the roots using [Newton's method](https://en.wikipedia.org/wiki/Newton%27s_method) and uses raku's `FatRat` primitives.

The module supports rooting `Int`, `Num`, and `Rational` numbers and allows using a Rational number as the root. Also, the level of precision can be changed.

METHODS
=======

method precision
----------------

    method precision is rw

Allows for getting/setting the level of precision. Defaults to 30.

To put precision into scale:

  * [NASA uses 15 decimals for Pi](https://www.jpl.nasa.gov/edu/news/2016/3/16/how-many-decimals-of-pi-do-we-really-need/)

  * 1/10^30: a millimeter compared to the diameter of the universe

  * 1/10^35: diameter of a human hair compared to the diameter of the universe

  * 1/10^42: size of a proton compared to the diameter of the universe

  * 1/10^62: Planck length compared to the diameter of the universe

  * 1/10^86: one atom out of all atoms of the universe

method newton's-root
--------------------

    method newton's-root(RootNumber:D :$root, PositiveNumber:D :$number) returns FatRat

Calculates the nth-root for the given number

method newton's-sqrt
--------------------

    method newton's-sqrt(PositiveNumber:D $number)

Calculates square root for the given number.

Same as `newton's-root(root =` 2, :$number)>

