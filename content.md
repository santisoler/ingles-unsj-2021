<!-- .slide: class="slide-title" -->

# Methodologies and computational tools for processing and modelling gravity data


## [Santiago Soler](https://www.santisoler.com)

[*CONICET, Argentina*](https://www.conicet.gov.ar/)
<br>
[*Instituto Geofísico y Sismológico Volponi, UNSJ, Argentina*](http://igsv.unsj.edu.ar/)
<br>
[*Computer-Oriented Geoscience Lab*](https://www.compgeolab.org/)

<div class="container logos">
<div class="logo">
<a href="https://www.conicet.gov.ar/">
<img src="images/logos/conicet.svg">
</a>
</div>
<div class="logo">
<a href="http://igsv.unsj.edu.ar/">
<img src="images/logos/igsv.svg">
</a>
</div>
<div class="logo">
<a href="https://www.compgeolab.org/">
<img src="images/logos/compgeolab.svg">
</a>
</div>
</div>

---

# About me

<div class="container">

<div class="column">
<img src="images/about.jpg" style="margin-top: 5%; border-radius: 50%; width: 80%;">
</div>

<div class="col-2">
<div class="centered">

* Licentiate en Physics (UNR)
* PhD Student in Geophysics (UNSJ)
* CONICET scholarship
* Developer of [Fatiando a Terra](https://www.fatiando.org)
* Member of the [Computer-Oriented Geoscience Lab](https://www.compgeolab.org)

</div>
</div>

</div>

---

# Advisor: Mario Giménez

<img src="images/mario.jpg" alt="" style="height: 400px;">

Researcher at CONICET and</br> at Instituto Geofísico Sismológico Volponi

---

# Co-advisor: Leonardo Uieda

<img src="images/leouieda.jpg" alt="" style="height: 400px;">

Lecturer in Geophysics at University of Liverpool</br>
Head of the Computer-Oriented Geoscience Lab</br>
Core developer of the Fatiando a Terra project</br>

---

# Goals

- Gravitational effects of tesseroids with variable density
- Interpolation of very large gravity datasets through equivalent sources
- Open-source software implementations

---

# What is gravity data?

<img src="images/gravity_magnetic_surveys.svg" alt="" style="height: 600px">

---

# Gravity surveys

<div class="container">
<div class="column">
<img src="images/ground_survey.svg" alt="" style="height: 600px">

Ground survey

</div>
<div class="column">
<img src="images/airborne_survey.svg" alt="" style="height: 600px">

Airborne survey

</div>
</div>

---

# Gravity surveys

- Unevenly distributed
- Variable observation height

---

# Interpolating gravity data

<dl>
    <dt>Interpolation:</dt>
    <dd>Predict the values of a field on unobserved locations.</dd>
    <dt>Gridding:</dt>
    <dd>Interpolate onto a regular grid.</dd>
</dl>

<img src="images/gridding-schematics.svg" alt="" style="height: 400px">

---

# General purpose interpolators

<div class="container">
<div class="column">
<img src="images/not-function-of-height.svg" alt="" style="height: 300px">

Don't take into account the <br> **observation heights**

</div>
<div class="column">
<img src="images/not-harmonic.svg" alt="" style="height: 300px">

Don't produce <br> **harmonic fields**

</div>
</div>


---

# Equivalent sources

<div class="container">

<div class="column">
<img src="images/equivalent-sources.svg" alt="" style="height: 400px">
</div>

<div class="column">

1. Define a set of sources.
1. Estimate source coefficients.
1. Predict field on grid points.

</div>
</div>

---

## Advantages

<div class="container">
<div class="column">
<img src="images/function-of-height.svg" alt="" style="height: 300px">

Take into account the <br> **observation heights**

</div>
<div class="column">
<img src="images/harmonic-field.svg" alt="" style="height: 300px">

Always produce <br> **harmonic fields**

</div>
</div>

---

## Disadvantages

<img src="images/ram-on-fire.svg" alt="" style="height: 300px">

Gridding large datasets require a lot of **computer memory**.

---

## The solution:

# Gradient-boosted equivalent sources

---

## How do gradient-boosted equivalent sources work?

<img src="images/eql-gradient-boosted.svg" style="width: 70%;">

---

## Gradient-boosted equivalent sources

- Removes memory limitations
- Control memory usage through window size
- Randomizing windows improves convergence

---

## Gridding large gravity dataset from Australia

<div class="container" style="max-height: 60%">
<div class="column">

Data

<img src="images/australia-data.jpg" alt="" style="height: 600px; width: auto;">
</div>
<div class="column">

Grid

<img src="images/australia-grid.jpg" alt="" style="height: 600px; width: auto;">
</div>

</div>

<div>

Grid +1.7M data points with less than 16GB of RAM

</div>

---

## Gridding large gravity dataset from Australia

<div class="container" style="max-height: 60%">
<div class="column">

Data

<img src="images/australia-data-zoom.jpg" alt="" style="height: 600px; width: auto;">
</div>
<div class="column">

Grid

<img src="images/australia-grid-zoom.jpg" alt="" style="height: 600px; width: auto;">
</div>

</div>

<div>

Grid +1.7M data points with less than 16GB of RAM

</div>

---

## Scientific publication

<img src="images/gji-eql-gradient-boosted.jpg" alt="" width="70%">

<div class="bottom">

S.R. Soler & Leonardo Uieda (2021).
_Gradient-boosted equivalent sources_.
Geophysical Journal International.
doi: [10.1093/gji/ggab297](https://doi.org/10.1093/gji/ggab297)

Preprint freely available at [EarthArXiv](https://eartharxiv.org/):
[10.31223/X58G7C](https://doi.org/10.31223/X58G7C)

</div>

---

# Wrapping up

---

## Variable density tesseroids

<img src="images/gji-tesseroids-variable-density.jpg" alt="" width="70%">

<div class="bottom">

Soler, Pesce, Giménez & Uieda (2019). _Gravitational field calculation in
spherical coordinates using variable densities in depth_. Geophysical Journal
International. doi: [10.1093/gji/ggz277](https://doi.org/10.1093/gji/ggz277)

Preprint freely available at [EarthArXiv](https://eartharxiv.org/):
[10.31223/osf.io/3548g](https://doi.org/10.31223/osf.io/3548g)

</div>

---

<!-- .slide: data-background-image="images/fatiando-background.svg" -->

<img src="images/fatiando.jpg" alt="" width="100%">

[www.fatiando.org](https://www.fatiando.org)

---

<!-- .slide: class="slide-license" -->

<p class="license-icons">
<i class="fab fa-creative-commons"></i><i class="fab fa-creative-commons-by"></i>
</p>

This work is available under the <br>
[Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/)

---

<!-- .slide: class="slide-title" -->

# Thank you!
