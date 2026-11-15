---
layout: page
title: "Double-cantilever (LPBF · IN718)"
card_title: "Double-cantilever (LPBF · IN718)"
description: This is the IN718 double-cantilever model. A local thermal–mechanical simulation is used to identify inherent strain, and the
  model calculates residual stress and warpage after releasing the left and right interfaces.
permalink: /benchmarks/double-cantilever/
hub_case: true
published: true
importance: 5
case_type: Computational case
img: /assets/img/cases/double_cantilever/card-cover.png?v=906e32b33a24
image_alt: "Double-cantilever benchmark model."
---

{% assign hub = site.data.residual_stress_hub %}

<link rel="stylesheet" href="{{ '/assets/css/residual-stress-hub.css' | relative_url | bust_file_cache }}">

<div class="rsh rsh-page-brand">
<section class="rsh-hero rsh-hero-with-background" aria-label="Residual Stress Hub">
<img class="rsh-hero-background" src="{{ hub.hero_background | relative_url }}" alt="" aria-hidden="true">
<a class="rsh-hero-brand rsh-site-title" href="{{ '/' | relative_url }}" aria-label="Residual Stress Hub home">
<img class="rsh-logo" src="{{ hub.logo | relative_url }}" alt="" aria-hidden="true" width="200" height="160">
<span class="rsh-brand-name"><span class="rsh-stress-name">Residual Stress</span> <span class="rsh-hub-name">Hub</span></span>
</a>
</section>
</div>

[← All benchmarks](/benchmarks/)

## Overview

This is the IN718 double-cantilever model. A local thermal–mechanical simulation is used to identify inherent strain, and the model calculates residual stress and warpage after releasing the left and right interfaces. <a href="#reference-1">[1]</a>

<div class="rsh-case-figures" markdown="1">

<figure class="rsh-case-figure" markdown="1">

<div class="rsh-case-figure-content" markdown="1">

![Geometry and dimensions.](/assets/img/cases/double_cantilever/geometry-overview.png)

_Figure 1. Geometry and dimensions._

[Download the original geometry PDF](/assets/pdf/cases/double_cantilever/geometry-overview.pdf)

</div>

</figure>

</div>

## Problem set

### Printing parameters

| Parameter                                                         | Value              | Unit |
| ----------------------------------------------------------------- | ------------------ | ---- |
| Manufacturing process                                             | LPBF               | —    |
| Material                                                          | IN718              | —    |
| Heat-source power, $P$                                            | 285                | W    |
| Scan speed, $V$                                                   | 960                | mm/s |
| Physical deposition layer thickness                               | 40                 | µm   |
| Hatch spacing                                                     | 110                | µm   |
| Absorption efficiency                                             | 0.4                | —    |
| Goldak heat-source dimensions (front / rear / transverse / depth) | 50 / 50 / 50 / 125 | µm   |
| Cooling interval (after each deposited layer)                     | 200                | s    |

### Temperature-dependent material parameters

The temperature-dependent thermal and mechanical parameters used in the local scan model for inherent-strain identification are taken from Dunbar et al., Tables 4–6 <a href="#reference-2">[2]</a>.

**IN718 — upper region and lower region.** Density, $\rho$ = 8146 kg/m³. Latent heat, $L$ = 286000 J/kg. Solidus temperature, $T_{\mathrm{s}}$ = 1533 K. Liquidus temperature, $T_{\mathrm{l}}$ = 1609 K. Maximum yield factor = 1.

Symbols: $C_{\mathrm{p}}$, specific heat capacity; $k$, thermal conductivity; $E$, Young’s modulus; $\sigma_{\mathrm{y}}$, initial yield stress; $\alpha$, thermal expansion coefficient; $\nu$, Poisson ratio; $H$, hardening modulus; $\sigma_{\mathrm{max}}$, maximum yield stress.

#### Thermal properties

| $T$ (°C) | $C_{\mathrm{p}}$ (J/(kg·K)) | $k$ (W/(m·K)) |
| -------- | --------------------------- | ------------- |
| 20       | 427                         | 11.4          |
| 100      | 441                         | 12.5          |
| 300      | 481                         | 14            |
| 500      | 521                         | 15.5          |
| 700      | 601                         | 21.5          |
| 1350     | 691                         | 31.3          |

#### Mechanical properties

| $T$ (°C) | $E$ (GPa) | $\sigma_{\mathrm{y}}$ (MPa) | $\alpha$ (µm/(m·K)) | $\nu$ (—) | $H$ (GPa) |
| -------- | --------- | --------------------------- | ------------------- | --------- | --------- |
| 21       | 208       | 1172                        | 12.8                | 0.3       | 0         |
| 93       | 205       | 1172                        | 12.8                | —         | 0         |
| 204      | 202       | —                           | 13.5                | —         | —         |
| 316      | 194       | —                           | 13.9                | —         | —         |
| 427      | 186       | 1089                        | 14.2                | —         | 0         |
| 538      | 179       | 1068                        | 14.4                | —         | 0         |
| 649      | 172       | 1034                        | 15.1                | —         | 0         |
| 760      | 162       | 827                         | 16.1                | —         | 0         |
| 871      | 127       | 286                         | —                   | —         | 0         |
| 954      | 17.8      | 138                         | 16.2                | —         | 0         |
| 1350     | —         | —                           | —                   | 0.3       | —         |

A dash denotes no independent tabulated value at that temperature, not zero. Each property is linearly interpolated on its own temperature grid, with the nearest endpoint held outside that range.

Maximum yield stress, $\sigma_{\mathrm{max}}$, is $1\,\sigma_{\mathrm{y}}$ at each interpolated temperature.

[Download full parameter JSON](/assets/data/cases/double_cantilever/thermal-parameters.json) · [Download temperature-dependent CSV](/assets/data/cases/double_cantilever/temperature-dependent-properties.csv) · [Download simulation YAML](/assets/data/cases/double_cantilever/simulation-parameters.yaml)

### Inherent strain solution parameters

| Parameter                                                                                         | Value / setting                                                             | Unit              |
| ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ----------------- |
| Ambient temperature                                                                               | 25                                                                          | °C                |
| High-temperature material model                                                                   | See tables above                                                            | —                 |
| Elastic parameters (room temperature, constant)                                                   | $E$ = 208<br>$\nu$ = 0.3                                                    | GPa<br>—          |
| Plastic parameters (room temperature, constant)                                                   | $\sigma_{\mathrm{y}}$ = 1172<br>$H$ = 0<br>$\sigma_{\mathrm{max}}$ = 1172   | MPa<br>GPa<br>MPa |
| Identified inherent strain, $\varepsilon_{\mathrm{xx}}^{\ast} = \varepsilon_{\mathrm{yy}}^{\ast}$ | -4.339                                                                      | ‰                 |
| Identified inherent strain, $\varepsilon_{\mathrm{zz}}^{\ast}$                                    | 19.647                                                                      | ‰                 |
| Layer activation                                                                                  | 36 × 0.515                                                                  | Layers × mm       |
| Constraints and release                                                                           | fixed plane $Z$ = 10 mm; release left and right interfaces at $Z$ = 32.2 mm | —                 |
| Thermal strain reference temperature                                                              | 25                                                                          | °C                |
| Thermal strain cutoff                                                                             | solidus                                                                     | —                 |

[Download simulation configuration](/assets/data/cases/double_cantilever/macro-parameters.yaml) · [Download identification results](/assets/data/cases/double_cantilever/identification-results.json)

## Results

<div class="rsh-case-figures" markdown="1">

<figure class="rsh-case-figure" markdown="1">

### Axial elastic-strain field

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever axial elastic-strain field with a color scale in microstrain.](/assets/img/cases/double_cantilever/results-cover.png?v=8e5614f749e8)

<p markdown="0"><em>Figure 2. Double-cantilever axial elastic strain $\varepsilon^{\mathrm{e}}_{\mathrm{xx}}$ (µε).</em></p>

The contour shows the axial elastic-strain component in the IN718 double-cantilever model. Positive and negative values denote extension and contraction. Release displacement is a different quantity and is shown in millimeters below.

[Download the figure PDF](/assets/pdf/cases/double_cantilever/results-cover.pdf)

</div>

</figure>

<figure class="rsh-case-figure" markdown="1">

### Local strain histories

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever local plastic, elastic and mechanical strain histories in three directions.](/assets/img/cases/double_cantilever/thermal-history.png)

<p markdown="0"><em>Figure 3. Saved Double-cantilever local $xx$, $yy$ and $zz$ strain histories (‰).</em></p>

The three panels show the saved plastic, elastic, and mechanical normal-strain components over the local scanning and cooling calculation. One per mille equals 0.001 strain. This figure contains strain histories only. The downloadable PDF also includes three scan-window detail pages.

[Download all local strain-history pages](/assets/pdf/cases/double_cantilever/thermal-history.pdf)

</div>

</figure>

<figure class="rsh-case-figure" markdown="1">

### Local elastic-strain agreement

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever Opt-IS versus DNS elastic-strain parity plots for the xx, yy and zz components.](/assets/img/cases/double_cantilever/strain-parity.png?v=81b43e5130b2)

<p markdown="0"><em>Figure 4. Double-cantilever local calibration: $xx$, $yy$ and $zz$ elastic-strain parity (µε).</em></p>

The panels compare Opt-IS with DNS on 1452 paired active native cells. The dashed diagonal denotes exact agreement. Departures from the diagonal show the remaining mismatch rather than part-scale experimental uncertainty.

[Download the figure PDF](/assets/pdf/cases/double_cantilever/strain-parity.pdf) · [Download archived error metrics](/assets/data/cases/double_cantilever/optimization-metrics.csv)

</div>

</figure>

<figure class="rsh-case-figure" markdown="1">

### Local elastic-strain maps

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever local axial elastic-strain maps.](/assets/img/cases/double_cantilever/strain-spatial-page-1.png?v=b64afa2357f5)

<p markdown="0"><em>Figure 5. Double-cantilever local $\varepsilon^{\mathrm{e}}_{\mathrm{xx}}$ maps (µε).</em></p>

The three panels show DNS, Opt-IS, and the signed difference Opt-IS minus DNS on the local top layer. The color scale measures elastic strain.

[Download the figure PDF](/assets/pdf/cases/double_cantilever/strain-spatial.pdf)

</div>

</figure>

<figure class="rsh-case-figure" markdown="1">

### Local elastic-strain profiles

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever local top-plane elastic-strain profiles.](/assets/img/cases/double_cantilever/strain-spatial-page-2.png?v=18a2965b6dca)

<p markdown="0"><em>Figure 6. Double-cantilever local $xx$, $yy$ and $zz$ elastic-strain profiles (µε).</em></p>

The three normal elastic-strain components are sampled along the native top-plane row and compared between DNS and Opt-IS. These curves describe the local calibration model.

[Download the figure PDF](/assets/pdf/cases/double_cantilever/strain-spatial.pdf)

</div>

</figure>

<figure class="rsh-case-figure" markdown="1">

### Vertical displacement after cutting

<div class="rsh-case-figure-content" markdown="1">

![Double-cantilever vertical displacement at both released ends compared with experiment and reference methods.](/assets/img/cases/double_cantilever/warpage.png?v=cbe3fe967c0c)

<p markdown="0"><em>Figure 7. Double-cantilever post-cut vertical displacement $u_z$ for the 127 mm specimen (mm).</em></p>

Opt-IS, MIS, DIS, the supplied reference simulation, and experiment are compared along the specimen. Both ends lift after cutting, with greater uplift on the left and a low-displacement central region.

[Download the figure PDF](/assets/pdf/cases/double_cantilever/warpage.pdf) · [Download displacement samples](/assets/data/cases/double_cantilever/warpage.csv)

</div>

</figure>

</div>

---

**Reference:**

<span id="reference-1"></span>

[1] Chen, Q., Liang, X., Hayduke, D., Liu, J., Cheng, L., Oskin, J., Whitmore, R., To, A.C. (2019). An inherent strain based multiscale modeling framework for simulating part-scale residual deformation for direct metal laser sintering. _Additive Manufacturing_, **28**, 406–418. [https://doi.org/10.1016/j.addma.2019.05.021](https://doi.org/10.1016/j.addma.2019.05.021).

<span id="reference-2"></span>

[2] Dunbar, A.J., Denlinger, E.R., Gouge, M.F., Michaleris, P. (2016). Experimental validation of finite element modeling for laser powder bed fusion deformation. _Additive Manufacturing_, **12**, 108–120. [https://doi.org/10.1016/j.addma.2016.08.003](https://doi.org/10.1016/j.addma.2016.08.003).
