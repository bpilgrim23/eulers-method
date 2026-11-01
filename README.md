# Euler's Method

An interactive, single-file web page for numerically solving ordinary differential equations of the form

dy/dx = f(x, y),   y(x₀) = y₀

using **Euler's method**, with an optional **Runge–Kutta 4th-order (RK4)** comparison curve.

## Usage

Open `euler-method.html` in any modern browser. No build step, no dependencies, no server required — it is fully self-contained (HTML + CSS + JavaScript in one file).

## Features

- **Free-form formula input** for f(x, y): operators `+ - * /` and `^` (exponent), functions `sin cos tan asin acos atan sinh cosh tanh exp log log10 log2 sqrt cbrt abs floor ceil round sign pow min max`, and constants `pi`, `e` (e.g. `x - y`, `2*x^2 + sin(y)`, `e^x - y`)
- **Configurable initial condition** (x₀, y₀), **step size** h, and **number of steps** n (up to 100,000)
- **Line graph** of the Euler approximation on an HTML5 canvas, with grid, auto-scaled axes, and tick labels
- **Optional RK4 overlay** (magenta dashed line) on the same step grid, with the plot axes extended to include both curves
- **Data table** of every step (step, x, y, f(x, y))
- **CSV export** for either the Euler or the RK4 results (RFC 4180 compliant, Excel/Sheets/pandas friendly)
- **Safe formula evaluation**: strict token whitelist — unknown names and disallowed characters are rejected, and no arbitrary code can be executed

## Methods

Euler's method iterates

    xₖ₊₁ = xₖ + h
    yₖ₊₁ = yₖ + h · f(xₖ, yₖ)

The RK4 overlay uses the classical four-stage formula

    k₁ = h·f(x, y)
    k₂ = h·f(x + h/2, y + k₁/2)
    k₃ = h·f(x + h/2, y + k₂/2)
    k₄ = h·f(x + h, y + k₃)
    yₙ₊₁ = yₙ + (k₁ + 2k₂ + 2k₃ + k₄) / 6

on the same grid, so the two methods are directly comparable.

## Files

| File               | Description                              |
| ------------------ | ---------------------------------------- |
| `euler-method.html` | The complete self-contained application  |

## Example

For y' = x − y with y(0) = 1 (exact solution y = x − 1 + 2e^(−x)) at x = 5 with h = 0.1:

- Euler: 4.010308
- RK4:   4.013476 (matches the exact 4.013476 to 7 decimal places)

