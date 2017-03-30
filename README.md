# Bringing the Generic Mapping Tools to Python

[Leonardo Uieda](http://www.leouieda.com)
and
[Paul Wessel](http://www.soest.hawaii.edu/wessel/)


Talk proposal for Scipy 2017.


## Abstract

The Generic Mapping Tools (GMT) is an open-source software package widely used
in the geosciences to process and visualize time series and gridded data.
Maps generated by GMT are ubiquitous in scientific publications in areas such
as seismology and oceanography.
We present a new GMT Python wrapper library built by the GMT team.
We will show the design plans, internal implementations, and demonstrate an
initial prototype of the library.
Our wrapper connects to the GMT C API using ctypes and allows input and
output using data from numpy ndarrays and xarray Datasets.
The library is still in early stages of design and implementation and
we are eager for contributions and feedback from the Scipy community.


## Extended Abstract

The Generic Mapping Tools (GMT; http://gmt.soest.hawaii.edu/) is an
open-source software package widely used in the geosciences to process and
visualize time series and gridded data.
GMT is a command-line tool written in C that is able to generate high quality
figures and maps using the Postscript format.
Maps generated by GMT are ubiquitous in scientific publications in areas such
as seismology and oceanography.
GMT has a large, feature rich, mature, and well tested code base.
It has benefited from over 28 years of development and heavy usage within the
scientific community.
It is no wonder that there have been at least three attempts to bridge the gap
between GMT and Python:
gmtpy (https://github.com/emolch/gmtpy),
pygmt (https://github.com/ian-r-rose/pygmt),
and PyGMT (https://github.com/glimmer-cism/PyGMT).
Of the three, only gmtpy has had any development activity since 2014 and is the
only project that has documentation.
gmtpy interfaces with GMT through subprocesses.
It pipes standard input and output to the GMT command-line application.
Piping has it's limitations because all data are handled as text, making it
difficult or impossible to pass binary data such as netCDF grids.
On the Python side, the two main libraries for plotting data on maps are the
matplotlib basemap toolkit (http://matplotlib.org/basemap) and Cartopy
(http://scitools.org.uk/cartopy).
Both libraries rely on matplotlib as the backend for generating figures.
Basemap is know to have its limitations (e.g.,
https://ocefpaf.github.io/python4oceanographers/blog/2013/09/23/cartopy).
Cartopy is a great improvement over basemap that fixes some of those
limitations.
However, Cartopy is still bound by the speed and memory usage constraints of
matplotlib when it comes to very large and complex maps.

We present a new GMT Python wrapper library `gmt-python`
(https://github.com/GenericMappingTools/gmt-python) built by the GMT team.
We will show the design plans, internal implementations, and demonstrate an
initial prototype of the library.
Starting in version 5, GMT introduced a C API that is exposed through a shared
library.
The API allows access to GMT modules as C functions and provides mechanisms
for input and output of binary data through shared memory.
Our Python wrapper connects to this shared library using the ctypes standard
library module.
The wrapper code can thus be written in pure Python, which greatly simplifies
packaging and distribution.
Input and output will be handled using the GMT C API "virtual files" that allow
access to shared memory between C and Python.
We will implement a thin conversion layer between native scientific Python data
types and the GMT internal data structures.
Thus, we can accept input and produce output as numpy ndarrays and pandas
DataFrames for tabular data and xarray Datasets for netCDF grids.
Support for displaying figures inline in the Jupyter notebook is planned from
the start by retrieving PNG previews of the Postscript figures.
This will allow GMT to be seamlessly integrated into the rich scientific Python
ecosystem.

Internally, the `gmt-python` library will contain low-level wrappers around the
GMT C API functions and data structures.
Users will interact with a higher-level API in which each GMT module is
represented by a function.
The module functions can take arguments as a single string representing the
command-line arguments ("-Rg -JN180"), as keyword arguments (R='g',
J='N180'), or as long-form aliases (region='g', projection='N180').
The Python interface relies on new features in GMT that are currently under
development in the trunk of the SVN repository, mainly the "modern" execution
mode, which greatly simplify the building of Postscript figures and maps
(http://gmt.soest.hawaii.edu/projects/gmt/wiki/Modernization).
We are working in close collaboration with the rest of the GMT core developers
to make changes on the GMT side as we exercise the new C API and discover bugs
and missing features.

The capabilities of GMT go beyond the geosciences.
It can produce high-quality line plots, bar graphs, histograms, and 3D
surfaces.
Significant barriers to entry for GMT have been the complexities of programming
in bash and the many command-line options and their meanings.
The Python wrapper library can serve as a backend for new and easier to use
APIs, making GMT more accessible while retaining the high quality of figures.
Work on `gmt-python` is still in early stages of design and implementation.
A prototype is not yet available but is predicted in time for the conference in
July.
We are open and eager for contributions and feedback from the Scipy community.

----

> Include links to source code, articles, blog posts, or other writing that
> adds context to the presentation.

Related resources:

* Github repository for gmt-python: https://github.com/GenericMappingTools/gmt-python
* The GMT website: http://gmt.soest.hawaii.edu/
* Design of the GMT "modern" execution mode: http://gmt.soest.hawaii.edu/projects/gmt/wiki/Modernization


> If you've given a talk, tutorial, or other presentation before, include that
> information as well as a link to slides or a video if they're available.

Past presentations by Leonardo:

* Talk at Scipy 2013 about Fatiando a Terra (http://fatiando.org): http://www.leouieda.com/talks/scipy2013.html
* Poster presented at Scipy 2014 also about Fatiando: http://www.leouieda.com/posters/scipy2014.html
* Slides and information from all the other talks that I have given: http://www.leouieda.com/talks/
* Teaching material for university courses and workshops: http://www.leouieda.com/teaching/


> Do you intend to present a demo?

Yes. I'll show our current efforts and results using Jupyter notebooks.


> Does the work make any new contributions to open-source software?

Yes. We are building a new open-source library.


> Which existing open-source tools does it use?

The library is a wrapper over the open-source Generic Mapping Tools library.
We'll also use numpy and xarray for input and output.


> What science fields are impacted by the work?

Mostly the geosciences but it is also relevant for general purpose plotting in
Python.


> How does the work fit into the Scientific Python community?

We are bringing a widely used tool in our community to the Python ecosystem.
There is potential to recruit existing GMT users to Python as well as new users
to GMT.
