# Reviews of the talk proposal

This year, [Scipy is using a double-open peer-review
system](https://scipy2017.scipy.org/ehome/220975/532468/), meaning that both
authors and reviewers know each others identities.
These are the reviews that we got for our proposal (posted with permission).


## Review 1 - [Paul Celicourt](http://hydrounits.com/)

The paper introduces a Python wrapper for the C-based Generic Mapping Tools
used to process and analyze time series and gridded data. The content is well
organized, but I encourage the authors to consider the following comments:
While the authors promise to demonstrate an initial prototype of the wrapper,
it is not sure that a WORKING prototype will be available by the time of the
conference as claimed by the authors when looking at the potential
functionalities to be implemented and presented in the second paragraph of the
extended abstract. Furthermore, it is not clear what would be the
functionalities of the initial prototype. On top of that, the approach to the
implementation is not fully presented. For instance, the Simplified Wrapper and
Interface Generator (SWIG) tool may be used to reduce the workload but the
authors do not mention whether the wrapper would be manually developed or using
an automated tool such as the SWIG. Finally, the portability of the shared
memory process has not been addressed.

Rating: 4.0 / 5.0


## Review 2 - [Ricardo Barros Lourenço](https://github.com/ricardobarroslourenco)

The authors submitted a clear abstract, in the sense that they will present a
new Python library, which is a binding to the Generic Mapping Tools (GMT) C
library, which is widely adopted by the Geosciences community. They were
careful in detailing their reasoning in such implementation, and also in
analogue initiatives by other groups.

In terms of completeness, the abstract precisely describes that the design
plans and some of the implementation would be detailed and explained, as well
on a demo of their current version of the library. It was very interesting that
the authors, while describing their implementation, also pointed that the
library could be used in other applications not necessarily related to
geoscientific applications, by the generation of general line plots, bar
graphs, histograms, and 3D surfaces. It would be beneficial to the audience to
see how this aspect is sustained, by comparing such capabilities with other
libraries (such as Matplotlib and Seaborn) and evaluating their contribution to
the geoscientific domain, and also on the expanded related areas.

The abstract is highly compelling to the Earth Sciences community members at
the event because the GMT module is already used for high-quality visualization
(both in electronic, but also in printed outputs - maps - which is an important
contribution to) , but with a Python integration it could simplify the
integration of "Pythonic" workflows into it, expanding the possibilities in
geoscientific visualization, especially in printed maps.

It would be interesting, aside from a presumed comparison in online
visualization with matplotlib and cartopy, if the authors would also discuss in
their presentation other possible contributions, such as online tile generation
in map servers, which is very expensive in terms of computational resources and
is still is challenging in an exclusive "Pythonic" environment. Additionally,
it would be interesting if the authors provide some clarification if there is
any limitation on the usage of such library, more specifically to the high
variance in geoscientific data sources, and also in how netCDF containers are
consumed in their workflow (considering that these containers don't necessarily
conform to a strict standard, allowing users to customize their usage) in terms
of the automation of this I/O.

The topic of high relevance because there is still few options for spatial data
visualization in a "fully pythonic" environment, and none of them is used in
the process of plotting physical maps, in a production setting, such as GMT is.
Considering these aspects, I recommend such proposal for acceptance.

Rating: 4.0 / 5.0


# Review 3 - [Ryan May](https://github.com/dopplershift)

Python bindings for GMT, as demonstrated by the authors, are very much in
demand within the geoscience community. The work lays out a clear path towards
implementation, so it's an important opportunity for the community to be able
offer API and interaction feedback. I feel like this talk would be very well
received and kick off an important dialogue within the geoscience Python
community.

Rating: 5.0 / 5.0
