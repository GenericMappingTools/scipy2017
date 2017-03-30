# Bringing the Generic Mapping Tools to Python

[Leonardo Uieda](http://www.leouieda.com)
and
[Paul Wessel](http://www.soest.hawaii.edu/wessel/)


Talk proposal about the
[new Python interface](https://github.com/GenericMappingTools/gmt-python)
for Scipy 2017.


## Abstract

~100 words.



## Extended Abstract


The Generic Mapping Tools (GMT; http://gmt.soest.hawaii.edu/) is an open-source
software package widely used in the geosciences to process and visualize time
series and gridded data.

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

gmtpy interfaces with GMT through subprocesses and pipes standard input and
output to the GMT command-line application.

Piping has it's limitations because all data are handled as text, making it
difficult or impossible to pass binary data such as netCDF grids.

On the Python side, the two main libraries for plotting data on maps are the matplotlib
basemap toolkit (http://matplotlib.org/basemap) and Cartopy
(http://scitools.org.uk/cartopy).

Both rely on matplotlib as the backend for generating figures.

Basemap is know for it's limitations (e.g.,
https://ocefpaf.github.io/python4oceanographers/blog/2013/09/23/cartopy)
and
Cartopy is a great improvement over basemap that fixes some of those
limitations.

However, Cartopy is still bound by the speed and memory usage constraints of
matplotlib when it comes to very large and complex maps.




We will present the design plans and demonstrate the initial prototype of a GMT
Python wrapper library `gmt-python`
(github.com/GenericMappingTools/gmt-python).

Starting in version 5, GMT introduced a C API that is exposed through a shared
library.

The C API allows access to GMT modules as C functions and provides mechanisms
for input and output of binary data through shared memory.

Our Python wrapper connects to the GMT shared library using the ctypes standard
library module.

This will allow us to wrap the C library using pure Python code, which greatly
simplifies packaging and distribution.

Input and output will be handled using the GMT "virtual
files" that allow access to shared memory between C and Python.

Thus, we can pass native scientific Python data types to our functions,
like numpy ndarrays, pandas DataFrames, and xarray Datasets,
using only a thin conversion layer between them and the GMT internal data
structures.

Support for displaying figures inline in the Jupyter notebook is planned from
the start by retrieving PNG previews of the Postscript figures.

This will allow GMT to be seamlessly integrated into the rich scientific Python
ecosystem.

Internally, the `gmt-python` library will contain low-level wrappers around the
GMT C API functions and data structures.

Users will interact with a higher-level API in which each GMT module is
represented by a function.

The module functions can take arguments in three ways: as a single string
representing the command-line arguments ("-Rg -JN180/10i"),
with each command-line option as keyword argument (R='g', J='N180/10i'),
or using long-form aliases (region='g', projection='N180/10i').

`gmt-python` is being developed in close collaboration with the rest of the GMT
core developers.

This collaboration will be crucial because we will need to make changes on the
GMT side as we exercise the new C API and discover bugs and missing features.

The Python interface also relies on new features in GMT that are currently
under development in the trunk of the SVN repository,
mainly the "modern" execution mode, which greatly
simplify the building of Postscript figures and maps.



The capabilities of GMT go beyond the geosciences.
It can produce high-quality line plots, bar graphs, histograms, and 3D
surfaces.
Significant barriers to entry for GMT have been the complexities of programming
in bash and the many command-line options and their meanings.
The Python wrapper library can serve as a backend for new easier to use APIs,
making GMT more accessible while retaining the high quality of figures.
Work on `gmt-python` is still in early stages of design and
implementation.
A working prototype is not yet available but is predicted in time for the
conference in July.
We are currently searching for contributions and feedback to help shape this
tool into something that will benefit the entire Scipy community.




> Include links to source code, articles, blog posts, or other writing that
> adds context to the presentation.

Related resources:

* Github repository for gmt-python: https://github.com/GenericMappingTools/gmt-python
* The GMT website: http://gmt.soest.hawaii.edu/
* Design of the GMT "modern" execution mode: http://gmt.soest.hawaii.edu/boards/2/topics/4930

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

> What science fields are impacted by the work?

Mostly the geosciences but it is also relevant for general purpose plotting in
Python.

> How does it work fit into the Scientific Python community?

We are bringing a widely used tool in our community to the Python ecosystem.
There is potential to recruit existing GMT users to Python as well as new users
to GMT.


## Tips and instructions from the conference website

> Your placement in the program will be based on reviews of your detailed
> description. This should be a roughly 500 word detailed outline of your
> presentation. This outline should concisely describe software of interest to
> the SciPy community, tools or techniques for more effective computing, or how
> scientific Python was applied to solve a research problem. A traditional
> background/motivation, methods, results, and conclusion structure is
> encouraged but not required. Links to project websites, source code
> repositories, figures, full papers, and evidence of public speaking ability
> are encouraged.

Tips from the website:

> Who is the intended audience for your talk?

> What, specifically, will attendees learn from your talk?

> Does it have a traditional background/motivation, methods, results, and
> conclusion structure?
