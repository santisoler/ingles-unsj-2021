# Methodologies and computational tools for processing and modelling gravity data

Santiago Soler

> CONICET, Argentina
>
> Instituto Geofísico Sismológico Volponi


## Advisor: Mario Giménez

- Researcher at CONICET and Instituto Geofísico Sismológico Volponi, UNSJ,
    Argentina


## Co-advisor: Leonardo Uieda

- Lecturer in Geophysics at University of Liverpool
- Head of the Computer-Oriented Geoscience Lab
- Core developer of the Fatiando a Terra project: open-source tools for
    geophysics


## Goals

- Develop a new methodology for computing the gravitational effects of
    tesseroids (spherical prisms) with variable density.
- Research on reducing the computational load needed to interpolate gravity and
    magnetic data through equivalent sources.
- Write open-source software implementations of any new method following best
    practices of software development


## What is gravity data?

Measurements of the gravity field generated by the Earth due to its mass.
Most techniques allow us to measure the module of the gravity acceleration.

Gravity data can be used to get information about the bodies that are buried
under the Earth's surface.
- Denser bodies lead to higher values of the gravity field
- Less dense bodies lead to lower values of the gravity field

Gravity data can then be harness for resource exploration, better understanding
of Earth's structure, monitoring mass flows, etc.


Before we can start interpreting gravity data, we need to process it first.

Gravity data is often gathered through different methods:
- Ground surveys. Data is obtained on Earth's surface following irregular paths
    or in scattered points.
- Airborne surveys. Data is taken by plane following almost straight lines.

Data is often unevenly distributed along the survey area, and the observation
height may vary from point to point (ground data follows the topography,
plane's height can change during flight).

Because gravity acceleration depends on the distance to the source mass
distribution, the observed gravity values depend on the observation height.


## Interpolating gravity data

The interpolation of gravity data can help us to produce a homogeneous map of
our observed gravity data across our area of interest.
This process is known as gridding.

The interpolation process consist in estimating the value of our observed field
on unobserved locations based on the gathered data.

There are several general purposes method for interpolating data, although most
of them show some disadvantages while working with gravity data:
- They don't take into account the height of the observation points.
- They don't guarantee to produce harmonic fields.


## The equivalent sources technique

There's a method widely known for interpolating and applying other different
processing tasks to gravity data: the equivalent sources technique.

It consists in:
1. defining a set of fictitious sources located beneath the observed data points,
1. estimating their coefficients so they generate the same gravity field than the
   one that has been observed,
1. using these sources to predict the values of the gravity field on any other
   location.

### Advantages

The equivalent sources have a few advantages over general purpose interpolation
methods:
- They always generate harmonic fields
- They take into account the height of the observation points

### Disadvantages

The main problem with the equivalent sources is they require heavy
computational power to estimate the source coefficients.

When working with very large gravity datasets, we would need to construct and
allocate a Jacobian matrix that could grow bigger than the available computer
memory, making impossible to apply this technique.


## The solution: Gradient-boosted equivalent sources

During my thesis I've managed to develop a new interpolation method based on
the equivalent sources technique that allows us to grid very large datasets
while heavily reducing the computational requirements.

It incorporates the gradient boosting algorithm from machine learning into
the equivalent sources technique by splitting the original problem into smaller
easy-to-solve problems which are solved by accumulation.


## How gradient-boosted equivalent sources work

We start by diving the survey area into square overlapping windows of equal
size.
Each window has a 50% overlap with their neighbouring ones.

We choose the first window and select the data and sources that fall inside it,
and use these smaller set of data points to estimate the coefficients of these
sources.

Then we use the estimated sources to compute their gravitational effect on
every data point of the dataset and remove it from the original data values,
obtaining a set of residuals.

Now we move to the next window, select the residuals and the sources that fall
inside it, estimate their coefficients using only the selected residuals and
then compute their gravitational effect on every observation point updating the
residuals.

We would repeat this process for every other window.

The gradient boosting removes the memory limitations from the equivalent
sources.
Moreover, we can control how much memory will be used by changing the size of
the windows: bigger windows require more computer memory.


## Gridding large gravity data from Australia

We managed to apply the gradient-boosted equivalent sources to a real-world
application: gridding a very large dataset of gravity data over Australia.
This dataset consist in more than 1.7M observations scattered all over
Australia.
We applied the gradient-booting algorithm to estimate the source coefficients
on a modest computer in ~1.5 hours requiring less than 16GB of RAM.
We then used these sources to generate a regular gravity grid at a constant
height.


## Scientific publication

This research was recently published in Geophysical Journal International after
following a peer-review process.
The version of record of the article can be found in:
[10.1093/gji/ggab297](https://doi.org/10.1093/gji/ggab297)

And a preprint is freely available in EarthArXiv:
[https://doi.org/10.31223/X58G7C](https://doi.org/10.31223/X58G7C)