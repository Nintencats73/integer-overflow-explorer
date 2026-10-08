# integer-overflow-explorer

An interactive educational visualization that demonstrates **integer overflow** using fixed-width signed integers.

## Overview

The Integer Overflow Explorer helps learners understand what happens when a number exceeds the range that can be represented by a fixed-width integer.

Users can select an integer width, enter a value, and see how the value is represented when it falls outside the available range. The visualization demonstrates the concept of **two's-complement wraparound**.

This project is intended as a teaching tool rather than an exploit or security tool.

## Features

* Select between **4-bit, 8-bit, 16-bit, and 32-bit** signed integers.
* Enter an integer manually.
* Use an interactive slider to explore nearby values.
* See the minimum and maximum values supported by the selected integer width.
* See the value that is actually stored.
* View a number-line visualization of the input and stored values.
* Clearly identify when integer overflow occurs.
* View the wraparound calculation.
* Use preset examples to quickly demonstrate common overflow cases.
* Responsive layout suitable for desktop and mobile browsers.
* Runs entirely in the browser with no external dependencies.

## Example

For an 8-bit signed integer, the representable range is:

```text
-128 to 127
```

If the input is:

```text
128
```

the value is outside the representable range.

Using two's-complement wraparound, the stored value becomes:

```text
128 → -128
```

Similarly:

```text
127  → 127
128  → -128
129  → -127
```

This demonstrates how moving past the maximum representable value can wrap around to the minimum value.

## How to Run

No installation or web server is required.

1. Download `integer_overflow_visualization.html`.
2. Open the file in a modern web browser.
3. Select an integer width.
4. Enter a value or use the slider.
5. Click **Visualize**, or change the value using the interactive controls.
6. Observe the resulting value and number-line visualization.

The page works as a standalone HTML file.

## How It Works

The visualization calculates the range of a signed integer using:

```text
minimum = -2^(bits - 1)
maximum =  2^(bits - 1) - 1
```

For example, with 8 bits:

```text
minimum = -2^7 = -128
maximum =  2^7 - 1 = 127
```

There are:

```text
2^8 = 256
```

possible bit patterns.

The visualization models two's-complement wraparound by mapping an input value back into the selected integer's representable range.

Conceptually:

```text
        127
         |
         v
... 125 126 127 -128 -127 -126 ...
                 ^
                 |
              overflow
```

## Integer Widths

| Width  |        Minimum |       Maximum | Possible Values |
| ------ | -------------: | ------------: | --------------: |
| 4-bit  |             -8 |             7 |              16 |
| 8-bit  |           -128 |           127 |             256 |
| 16-bit |        -32,768 |        32,767 |          65,536 |
| 32-bit | -2,147,483,648 | 2,147,483,647 |   4,294,967,296 |

## Educational Purpose

The visualization is designed to help learners understand:

* Fixed-width integer representation
* Signed integer ranges
* Two's-complement representation
* Integer overflow
* Integer wraparound
* Why adding `1` to a maximum signed integer can produce the minimum value

It intentionally does **not** provide exploit code, shellcode, or instructions for attacking software.

## Browser Compatibility

The page uses standard:

* HTML
* CSS
* JavaScript
* DOM APIs

It does not require a framework, package manager, server, or external JavaScript library.

Modern versions of Chrome, Firefox, Safari, and Edge should support the visualization.

## Project Structure

The project consists of a single file:

```text
integer_overflow_visualization.html
```

The HTML file contains:

```text
HTML
 ├── Interface
 ├── CSS styling
 ├── Number-line visualization
 └── JavaScript interaction
```

## Important Note About Programming Languages

This visualization demonstrates the mathematical concept of fixed-width two's-complement wraparound. Actual programming-language behavior can differ.

For example, Java defines signed integer overflow using two's-complement arithmetic, while C and C++ have language-specific rules for signed integer overflow.

Therefore, this visualization should be used to understand the underlying concept rather than as a universal description of every programming language's behavior.

## License

This project is intended for educational use. Add an appropriate license here if the project is being distributed as open-source software.
