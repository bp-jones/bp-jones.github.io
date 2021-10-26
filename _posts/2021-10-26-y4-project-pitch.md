# Y4 Project Pitch

Having explored a little of [machine](https://bp-jones.github.io/2021/10/10/dec-tree-regression.html) and [deep](https://bp-jones.github.io/2021/10/19/nn-dl-basics.html) learning, the next step is to refine the project idea with a simple pitch to provide a context for applying machine and deep learning, and working towards a scientific goal. From supervisor suggestions and discussions with my project partner, one favoured idea is presented here, with the caveat that some elements can (and probably will) change should this be the project road we head down.

## PBjam Prior Development and Stellar Population Studies

The general outline of this project pitch is to contribute to an already existing open source Python library, [PBjam](https://pbjam.readthedocs.io/en/latest/), and use it to explore observational data of stellar populations. Developed by members of the University of Birmingham's [Sun, Stars and Exoplanets](https://www.birmingham.ac.uk/research/activity/physics/astronomy/solar-and-stellar/index.aspx) research group, PBjam allows non-specialists to use asteroseismology techniques on observational data, using Bayesian inference methods. 

[Asteroseismology](https://en.wikipedia.org/wiki/Asteroseismology) is the study of oscillations in stars, where oscillation modes give physical insight of a star's interior from exterior observations. Subtle changes in a star's brightness are detectable by telescopes, such as [Kepler](https://www.nasa.gov/mission_pages/kepler/main/index.html) (2009-2018), with these variations across the surface of a star categorised using [spherical harmonics](https://en.wikipedia.org/wiki/Spherical_harmonics), analogous to vibrations on a string, but in three dimensions as opposed to one. An example of this is shown below, with the light and dark patches corresponding to different modes on the surface of the sphere. A good, non-technical overview of asteroseismology can be found [here](https://exoplanets.nasa.gov/news/1516/symphony-of-stars-the-science-of-stellar-sound-waves/), provided by NASA.

[Bayesian inference](https://en.wikipedia.org/wiki/Bayesian_inference) is a statistical inference method, that utilises [Bayes theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem) in order to update the probability of a result based on new information, starting from current information. Bayes' theorem is shown below: 

<p align="center">
  <img src="/img/2021-10-26_y4_project_pitch_imgs/bayes_theorem.png"/>
</p>

The components of this expression are as follows:

* **P(D|M)** is the *likelihood*, which is the probability of obtaining the data **D** given the model **M**.

* **P(M)** is the *prior*, which is the probability assigned to the model before we take data.

* **P(M|D)** Is the *posterior*, which is the probability of the model **M** being correct given the data **D**.

* **P(D)** is a normalisation constant for the probability distribution.

Our focus will be the *prior*, and developing an alternative to the currently used method.  

## Refining Prior Calculations

PBjam uses [kernel density estimation](https://en.wikipedia.org/wiki/Kernel_density_estimation) (KDE) to encode the prior probability. This prior probability is our prior knowledge of the physical parameters, which in this instance are the mode frequencies of stars at various stages of stellar evolution, determined by observational data from the Kepler mission. We use this prior to inform the posterior probability, better expressed as new knowledge inferred from previous knowledge.

Two alternative methods to the KDE have been suggested by the project supervisor: Bayesian Gaussian mixture models and normalising flows. The motivation for an alternative approach to using KDE is a method that is ideally faster, as repeated iterations of the code, especially for populations of stars, can be computationally time consuming.

## Science Goals

The final aim of the project is to use the (ideally) improved PBjam prior code as part of a larger science goal. This idea is the least developed, though would involve characterising a population of stars, leveraging the ease of use benefits PBjam provides. Physically, this could be a population constrained in an [open cluster](https://en.wikipedia.org/wiki/Open_cluster), where we could define physical properties and evolutionary stages of these. Alternatively, we could seek to improve the quantity of data the prior could draw from, by using publicly available data from missions such as the Transiting Exoplanet Survey Satellite ([TESS](https://en.wikipedia.org/wiki/Transiting_Exoplanet_Survey_Satellite))
