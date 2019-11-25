SNAKE-JKU
=========

Snake, written for JKU's PDP-11/03-L, attached to an ADM-3A terminal.
Unfortunately the [JKU](https://www.jku.at/) only has a broken
PDP-11/03-L and it was not possible to fix it in time, so the program
had to "work around" the problem.

Basically the RAM is broken: bit 8 is always 0 in *every* word. That
means the lowest bit in every other byte is always zero. This version of
snake works on a hardware with exactly this problem. All program words
have this bit set to zero, and data words don't need it either (except
the RNG, but it also works if it's always set to zero).

Files
-----

- `snake.s`: The source code of the game (for a custom assembler which
  is *not* MACRO-11).
- `snake.bic`: Compiled program code in standard absolute loader format.
  This binary can be loaded onto the physical PDP-11/03-L via
  console/ODT.

Controls
--------

Movement keys as printed on the ADM-3A keyboard, but without CTRL (`H` =
left, `J` = down, `K` = up, `L` = right), which are the same as the
movement keys in vi/vim.

`R` restarts the game, `Q` halts the CPU.

Why?
----

During the planning of the "[50 years computer science at
JKU](http://informatik.jku.at/50years)" celebration I saw a complete
PDP-11/03-L and I said "wouldn't it be fun to get this thing running?".
I got an ok from a professor, so I started to check if the machine works
at all. After documenting the configuration of the system and replacing
broken capacitors of the power supply, it turned out that the RAM is
partially broken. Since it was not possible to replace the RAM in time,
I developed this version of snake which works with the broken RAM.

Unfortunately it was not possible to implement *all* features I wanted
to implement. The broken RAM means it's impossible to generate
interrupts, and therefore it's impossible to use a timer. That's the
reason why the snake doesn't move on its own unless you press a key.

Photos
-----

![snake](https://raw.githubusercontent.com/pekd/snake-jku/master/photos/snake.jpg)

![snake screen](https://raw.githubusercontent.com/pekd/snake-jku/master/photos/screen.jpg)

![ADM-3A](https://raw.githubusercontent.com/pekd/snake-jku/master/photos/adm-3a.jpg)

![PDP-11/03-L with ADM-3A](https://raw.githubusercontent.com/pekd/snake-jku/master/photos/pdp-11.jpg)

![playing snake](https://raw.githubusercontent.com/pekd/snake-jku/master/photos/playing.jpg)
