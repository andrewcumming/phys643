# PHYS 643 Astrophysical Fluids, Fall term 2026

## Goals of the course

- To develop physical intuition about astrophysical gas and plasma and use it to understand the behaviour of astrophysical systems
- To gain experience in numerical techniques for simulating astrophysical fluids.

A background of undergraduate physics is assumed, but no prior knowledge of fluid dynamics is required. This course is a part of the PHYS 641 to 645 series at McGill that gives a comprehensive exposure to graduate level astrophysics. In particular, it is complementary to PHYS 642 Radiative Processes in Astrophysics. While PHYS 642 is about why astronomical objects *look* the way they do, PHYS 643 considers why they *behave* the way they do.

## Time and place

Tuesday Thursday 1-2.30pm, BRONF 310.

First class: Tuesday September 1

## Instructor and TA

Andrew Cumming, andrew.cumming@mcgill.ca, office: Rutherford 310

TA: Numa Karolinski

## List of topics

We will focus on one topic per week, with class time mostly devoted to problem solving and student presentations (26 classes in total).

The topics covered will include (subject to change depending on student interests):

- **Basics of fluids**. What we mean by fluids in astrophysics. The fluid equations as conservation laws for mass, momentum and energy. The MHD equations. Simple examples of fluid behaviour to develop intuition: Bernouilli's principle, vorticity, and flux freezing.
- **Stars as fluids in hydrostatic balance.** The equation of state. The structure of hot and cold objects: stars, compact objects, and planets. Stellar evolution.
- **Compressible flows.** Sound waves and Alfvèn waves. The development of shocks. Shock jump conditions.
- **Numerical techniques.** Finite difference schemes and their stability. Spectral methods. Shock propagation in 1D.
- **Examples of astrophysical flows.** Spherically symmetric inflow and outflows. Bondi accretion. Blast waves, supernova remnant evolution, Sedov similarity solution. Jets.
- **Perturbations: waves and instabilities.** Turbulent flows. p and g modes in a plane parallel atmosphere. Perturbations and the energy principle. Convection. Interchange and Parker instabilities. Linear shear flows. Richardson number. Thermal instability. Gravitational instability. Turbulent flows.
- **Rotating fluids.** The dynamics of rotating systems. Planetary atmospheres. Accretion disks. Circular shear flow. Angular momentum transport by the MRI.
- **Plasmas.** Microphysics of plasmas. Debye length. Nuclear reaction rates in stars. Conduction.

The emphasis will be on understanding the basic physical ideas and applying them to examples from across astrophysics, as well as developing experience solving the fluid equations numerically.


## Assessment

The final grade will be based on:
- Weekly reading questions (10%)
- In-class presentations (20%)
- Computational exercises (30%)
- Project (40%)

**Reading questions**:
Each week's reading will have a set of questions that will help you think about the material and highlight the most important points. These must be submitted on myCourses before the start of each Thursday's class.

**Presentation**:
One paper presentation (15 min) per student during the term. The presentation can use slides or blackboard as appropriate, and should summarize the main points of the paper(s) and explain how they are connected to the class notes.

**Computational exercises**:
Computational exercises will be done individually as homework (there will be 3 of these).

**Project**:
The projects will be done in groups of three. The goal is to run a simulation of an astrophysical system and analyze the results. **All groups will present their plan for the project on October 8 in class**. Final presentations will be split over two classes on Nov 26 and Dec 1.

Here are some examples of past projects to give you some ideas:
- Colliding stellar winds with the PLUTO code
- An investigation of different shock-capturing methods
- Simulating a spherical blast wave with the FLASH code
- Investigating the properties of supernova progenitors with MESA
- Using a General Circulation Model (GCM) to model an exoplanet atmosphere
- Simulations of relativistic jets with PLUTO
- Internal gravity waves in massive stars with MESA/GYRE
- Shallow water models of planetary atmospheres with SHTn
- Writing a convection code from scratch
- Modelling a supersonic wind impacting a dense cloud
- Ram-pressure-stripping of galaxies with ENZO

## Useful books and other resources

I will provide notes for each topic on this website. A textbook is not required, but I recommend you look at [Physics of Fluids and Plasmas: An Introduction for Astrophysicists](https://mcgill.on.worldcat.org/search/detail/37492486?queryString=Physics%20of%20Fluids%20and%20Plasmas%3A%20An%20Introduction%20for%20Astrophysicists%20%20&bookReviews=off&newsArticles=off&idDetect=false&citeDetect=false&clusterResults=true&groupVariantRecords=false) which is a great introduction to the subject at the right level.

Other useful books are listed below. The Pringle and King book is a very clean, concise treatment but somewhat more mathematical than Choudhuri and a more restricted range of topics. The book by Thompson has a good section on numerical methods. Shu's book is volume 2 of a classic two volume set on the physics of astrophysics.

- [Astrophysical Flows](https://mcgill.on.worldcat.org/search/detail/567910584?queryString=astrophysical%20flows%20pringle%20king&bookReviews=off&newsArticles=off&idDetect=true&citeDetect=true&clusterResults=true&groupVariantRecords=false) by Jim Pringle and Andrew King
- [An Introduction to Astrophysical Fluid Dynamics](https://mcgill.on.worldcat.org/search/detail/65284316?queryString=thompson%20astrophysical%20fluid%20dynamics&bookReviews=off&newsArticles=off&idDetect=true&citeDetect=true&clusterResults=true&groupVariantRecords=false) by Michael J. Thompson
- The Physics of Astrophysics Volume 2: Gas Dynamics by Frank Shu
- [Physical Fluid Dynamics](https://mcgill.on.worldcat.org/search/detail/17299123?queryString=physical%20fluid%20dynamics%20tritton&bookReviews=off&newsArticles=off&idDetect=true&citeDetect=true&clusterResults=true&groupVariantRecords=false) by D. J. Tritton

Some useful links:

- [Astrophysics source code library](http://ascl.net/)
- Links to some hydro/MHD and other codes: [Dedalus](https://dedalus-project.org/), [Athena++](https://www.athena-astro.app/), [PLUTO](https://plutocode.ph.unito.it/), [PENCIL](https://pencil-code.nordita.org/), [Castro](https://amrex-astro.github.io/Castro/), [Einstein Toolkit](https://einsteintoolkit.org/mp.html), [MITgcm](https://mitgcm.readthedocs.io/en/latest/), [MESA stellar evolution code](http://mesastar.org/), [GIZMO](http://www.tapir.caltech.edu/~phopkins/Site/GIZMO.html), [RAMSES](https://ramses.cnrs.fr/), [AREPO](https://arepo-code.org/wp-content/userguide/index.html)
- [Lectures on Numerical Fluid Dynamics](https://www.ita.uni-heidelberg.de/~dullemond/lectures/num_fluid_2011/index.shtml) by V. Springel and C. P. Dullemond at the University of Heidelberg.


## McGill policy statements

McGill University values academic integrity. Therefore all students must understand the meaning and consequences of cheating, plagiarism and other academic oﬀences under the [Code of Student Conduct and Disciplinary Procedures](https://www.mcgill.ca/secretariat/files/secretariat/code_of_student_conduct_and_disciplinary_procedures.pdf) (approved by Senate on 29 January 2003) (See McGill's guide to academic honesty](https://www.mcgill.ca/students/srr/honest) for more information).

In accord with McGill University's [Charter of Students' Rights](https://www.mcgill.ca/secretariat/files/secretariat/charter_of_student_rights_last_approved_october_262017.pdf), students in this course have the right to submit in English or in French written work that is to be graded. This does not apply to courses in which acquiring proficiency in a language is one of the objectives.

In the event of extraordinary circumstances beyond the University's control, the content and/or evaluation scheme in this course is subject to change. 

Additional policies governing academic issues which aﬀect students can be found in the [McGill Charter of Students' Rights](https://www.mcgill.ca/secretariat/files/secretariat/charter_of_student_rights_last_approved_october_262017.pdf).
