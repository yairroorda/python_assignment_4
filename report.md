# Assignment 4

Yair Roorda 5467543
Luc Jonker 4836111

## Differences between Python and C++

_A paragraph (max. 200 words) explaining how the Python and C++ programs are different (How is the information in the
simulation represented:
Which data types do the programs use to represent the data for the simulation?)_

The C++ implementation takes advantage of the object-oriented nature of the language,
for example defining a class 'body' to store the information on the bodies.
They also nicely define a vector3d class and define operations for addition, subtraction, norm, magnitude, etc. which
cuts down on the amount of hard to parse mathematics later on.
The python version precomputes all pairs of bodies before running, and takes advantage of that for its calculations.
It uses a dictionary datatype to store these precomputed values since there is no need for indexing and they make for a
natural way to couple keys(planets) to values(planet properties)

## Reflection on assignment

_A paragraph reflection on how you went about solving the task (max. 400
words). Which steps did you take? How did you measure the runtime?
How did what you learn about Python help you for developing the C++
solution? Did you get stuck? Which sources did you consult when you
got stuck? Did you expect the results you obtained? Etc._

Printing the values for C++ was fairly straightforward given the construction of the data and the code, we just appended
the data for each time step and all required information is included. A bit of looking around on stackoverflow and
cplusplus.com was enough to put this together. The python one surprisingly was more of a challenge because the name was
not originally included whatsoever in the data used to perform the calculations. This stumped us for a little bit as we
attempted some more convoluted solutions at first (zipping names and data, using the whole dictionary, etc.) but
eventually we landed on a simpler approach of simply including the name in the dictionary data.
For measuring the runtime, we simply ran the program manually, recording the runtime before and after execution, and
taking the difference. In C++ this was achieved using std::chrono::system_clock, and in Python perf_counter was used.
As expected, Python was by far the least efficient, followed by C++ debug, and then C++ release. We were a bit surprised
how much better C++ release performed than the debug profile. And of course this effect was amplified by orders of magnitude
between C++ release and Python, with Python taking approximately 180 times longer. 

## Benchmarks

_Timings for Python, C++ Debug and C++ Release, in a table and visualised
in a chart (x-axis: instance size/y-axis: run time). Advice: Use matplotlib
to produce the chart._

| Iterations | Python       | C++ Debug  | C++ Release |
|-----------:|--------------|------------|-------------|
|       5000 | 0.043319300s | 0.0056021s | 0.0005162s  |
|      50000 | 0.423595300s | 0.0450599s | 0.0065116s  |
|     500000 | 3.887917600s | 0.367833s  | 0.0603905s  |
|    5000000 | 34.22389180s | 2.88441s   | 0.287725s   |
|   50000000 | 467.7972619s | 28.0304s   | 2.61263s    |


![runtime_normarithmic.png](runtime_normarithmic.png)
![runtime_logarithmic.png](runtime_logarithmic.png)

## Hardware used

_A short description of the hardware you run the simulation on (CPU,
memory, operating system)._

The system used to perform these tests is an HP Z-book, using Windows 11. The CPU is an Intel(R) Core(TM) i7-8750H CPU @
2.20GHz. It has 16 GB of RAM.

## Spotting errors in C++

![img_1.png](img_1.png)
The screenshot above shows a very simple 'Hello World' program which throws
an syntax error at compile time because of the missing semicolon.
Because we are using Clion as our IDE and the error is very basic the IDE is even able to spot it while writing and
shows a red squiggle to alert us.
The way to remove the error is to add the semicolon back in as the compiler tells us very clearly.

## QGIS

_One (or more, e.g. 1 overview and 1 close-up) screenshot of QGIS, where
you have loaded a CSV file your code did produce for 5’000 iterations. If
you have a recent version of QGIS, you can try to use the 3D map view as
well._

The full solar system looks like this when loaded into QGIS
![Layout 1.png](Layout%201.png)
When we zoom in on just the 'sun' we can see it also wiggles around a little bit, which is what we would expect from a good simulation.
![SunSunSun.png](SunSunSun.png)