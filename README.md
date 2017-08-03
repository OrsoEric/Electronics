# Electronics
Quick Tables to hasten a few common design tasks.

# E12 Values
1.0 1.2 1.5 1.8 2.2 2.7 3.3 3.9 4.7 5.6 6.8 8.2 10 ...

# E12 Voltage Divider
A very common task is to design a voltage divider.
The equation is K=R1/(R1+R2). R1 is the low side resistor, R2 is the high side resistor. K is the ratio of the divider.
The usual algorithm is to set a resistor to E12 value, use the equation to calculate the other, and approximate to E12, calculate the actual ratio and iterate until the divider has two E12 value with a small enough error.

It's time consuming to do this every time, so I reversed the algorithm.
I made a spreadsheet with all combinations of E12 values and their ratio.
Then I sorted by the ratio and printed the result. Now, if you want to design the two resistors you first calculate the ratio, then search the table for the two E12 resistor with a close enough value. Much faster and often you get better approximation.

# E12 Voltage Divider Example
A short example on how to use this system.
You have an LM317 Linear voltage regulator with an adjust voltage of 1.25V. You want 5.00V in output.

Vout = 5.00V. Vadj = 1.25V

The equation is a divider. You can use this table.

Vout = Vadj/K

Invert the fomula, calculate the wished K value

Kwish = Vadj/Vout = 1.25V/5.00V = 0.250

Search in the table for two suitable E12 resistors with a K close enough to 0.250.

R1 = 33K, R2 = 100K, K = 0.2481

Calculate the actual output

Vout = Vadj/K = 1.25V/0.2481 = 5.038V

Alternative K were:

R1 = 27K, R2 = 82K, K = 0.2477 (higher voltage)

R1 = 120K, R2 = 330K, K = 0.2667 (lower voltage)

And so on. This algorithm make it that much quicker to find resistors and decide if E12 series has a close enough ratio or if you need 1% resistors to do the job.

# Voltage Divider Remarks
This table helps you only in choosing E12 resistor with the right ratio. There are additional considerations.
One is about the sum of resistors.

R1 = 1K, R2 = 1K, K = 0.500

R1 = 100K, R2 = 100K, K = 0.500

Both of those voltage dividers have the same ratio, but the total resistance is 2K in the first case and 200K in the second. The first will drain a lot more bias current, the second will be more sensitive to current flow in the divider output.
The right values depend on your design. Always take into account the current. In the example Iadj of the LM317.
Another consideration is about filter capacitor. The filter frequency depends on the sum of the resistor and the value of the capacitor itself. 



