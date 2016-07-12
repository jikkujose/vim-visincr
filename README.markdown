# Vim Visincr

The visincr plugin facilitates making columns of increasing or decreasing numbers, dates, or daynames.

## Instructions

1. Select a column using visual-block (ctrl-v) and move the cursor.
2. Choose what sort of incremented list you want.

### Types of available increments

Key               | Value
----------------- | ----------------------------
Increment         | `:I`
Description       | Will use the first line's number as a starting point to build a column of increasing numbers (or decreasing numbers if the increment is negative).
Default increment | 1
Justification     | Left (will pad on the right)

Key               | Value
----------------- | ----------------------------
Increment         | `:II [# [zfill]]`
Description       | Will use the first line's number as a starting point to build a column of increasing numbers (or decreasing numbers if the increment is negative).
Default increment | 1
Justification     | right (will pad on the left)
Zfill             | left padding will be done with the given character, typically a zero.

Key               | Value
----------------- | ----------------------------
Increment         | `:IYMD` (year/month/day), `:IMDY` (month/day/year), `:IDMY` (day/month/year)
Description       | Will use the starting line's date to construct an increasing or decreasing list of dates, depending on the sign of the number.
Default increment | 1 (in days)

Key         | Value
----------- | ----------------------------------
Increment   | `:ID`
Description | Will produce an increasing/decreasing list of daynames. Three-letter daynames will be used if the first day on the first line is a three letter dayname; otherwise, full names will be used.

Key        | Value
---------- | -----------------------------------
Increment  | `:IO` & `:IIO`
Similar to | `:I` and `:II`
Exception  | Creates octal numbers.

Key        | Value
---------- | -----------------------------------
Increment  | `:IR` & `:IIR`
Similar to | `:I` and `:II`
Exception  | Uses Roman numerals. Negative and zero counts are not supported for Roman numerals.

Key        | Value
---------- | -----------------------------------
Increment  | `:IX` & `:IIX`
Similar to | `:I` and `:II`
Exception  | Creates hexadecimal numbers.

### Notes

1. For `:I` `:II` `:IO` `:IIO` `:IR` `:IIR`: If the visual block is ragged on the right-hand side (as can easily happen when the "$" is used to select the right-hand-side), the block will have spaces appended to straighten it out.  If the string length of the count exceeds the visual-block, then additional spaces will be inserted as needed.  Leading tabs are handled by using virtual column calculations.
2. For `:IR` and `:IIR`: Since Roman numerals vary considerably in their lengths for nearby numbers, an additional two spaces will be included.
3. For `:IYMD`, `:IMDY`, and `:IDMY`: You 'll need the [<calutil.vim>][calutil] plugin.
4. Use `:he visincr-examples` to see even more examples of each command in action.

## Examples:

```
Use following after selecting the block using ctrl-v:


1. :I

8            8
8            9
8            10
8            11
8            12

2. :I -1

8            8
8            7
8            6
8            5
8            4

3. :II

8             8
8             9
8            10
8            11
8            12

4. :II -1

8            8
8            7
8            6
8            5
8            4

5. :IMDY

06/10/03     6/10/03
06/10/03     6/11/03
06/10/03     6/12/03
06/10/03     6/13/03
06/10/03     6/14/03

6. :IYMD

03/06/10    03/06/10
03/06/10    03/06/11
03/06/10    03/06/12
03/06/10    03/06/13
03/06/10    03/06/14

7. :IDMY

10/06/03    10/06/03
10/06/03    11/06/03
10/06/03    12/06/03
10/06/03    13/06/03
10/06/03    14/06/03

8. :ID

Sun       Sun
Sun       Mon
Sun       Tue
Sun       Wed
Sun       Thu

9. :ID

Sunday     Sunday
Sunday     Monday
Sunday     Tuesday
Sunday     Wednesday
Sunday     Thursday

10. :IA

a          a
a          b
a          c
a          d
a          e

11. :IO

5         5
5         6
5         7
5         10
5         11

12. :IR

II         II
II         III
II         IV
II         V
II         VI

13. :IX

8         8
8         9
8         a
8         b
8         c
```

## Credit

[Charles Campbell][cec] is the original author of the plugin, more info can be found at his [site][site]. The plugin is moved to Github for easy installation using the modern plugin managers.

[cec]: http://vim.sourceforge.net/account/profile.php?user_id=96<Paste>
[site]: http//www.drchip.org/astronaut/vim/index.html#VISINCR
[calutil]: https://github.com/wpug/vim-utl-calutil
