# Bringing the Generic Mapping Tools to Python

[Leonardo Uieda](http://www.leouieda.com)
and
[Paul Wessel](http://www.soest.hawaii.edu/wessel/)


Talk proposal about the
[new Python interface](https://github.com/GenericMappingTools/gmt-python)
for Scipy 2017.


## Abstract

~100 words.

The Generic Mapping Tools (GMT) is an open-source software package widely used
in the geosciences to process and visualize time series and gridded spacial
data.

GMT is a command-line tool written in C that is able to generate high quality
figures and maps in the Postscript format.

GMT generated maps are ubiquitous in scientific publications in areas such as
seismology and oceanography.

Python has had a large uptake in the geosciences.

Python has two main libraries for generating maps: the matplotlib basemap
toolkit and cartopy.

Both rely on matplotlib as the backend for generating figures.

Basemap is know for it's limitations.

Cartopy tried to fix some of those limitations but is still under development.

GMT has a large, feature rich, mature, and well tested code base.

It has benefited from over 28 years of development and heavy use within the
scientific community.

There have been, to our knowledge, three attempts to bridge the gap between GMT
and Python: gmtpy, pygmt, and PyGMT.

Of the three, only gmtpy has had any development activity since 2014.

gmtpy interfaces with GMT through subprocesses and pipes standard input and
output to the GMT command-line application.

Piping has it's limitations because all data are handled as text, making it
difficult or impossible to pass binary data such as netCDF grids.

Version 5 introduced a C API to GMT that is exposed through a shared library.

The C API allows access to GMT modules as C functions and provides mechanisms
for input and output of binary data through shared memory.

This work was largely motivated by the development of Matlab and Julia
interfaces for GMT.


We are building a GMT Python interface that connects to the GMT shared library
using ctypes.

Input and output between GMT and the Python library will be made through native
scientific Python data types: numpy ndarrays and pandas Dataframes for tabular
data and xarray Datasets for grids in netCDF format.

This will allow GMT to be integrated into the rich scientific Python ecosystem.

The library will contain low-level wrappers around the GMT C API functions and
data structures.

Users will interact with a higher-level API in which each GMT module is
represented by a function.


The module functions can take arguments in three ways: as a single string
representing the command-line arguments ("-Rg -JN180/10i"),
with each command-line option as keyword argument (R='g', J='N180/10i'),
or using long-form aliases (region='g', projection='N180/10i').




The capabilities of GMT go beyond the geosciences.

It can produce high-quality plots, bar graphs, histograms, and 3D surfaces.

The Python interface will rely on new features in GMT that are currently under
development (in the SVN repository trunk), mainly the new "modern" execution
mode.

The Python library will allow us to build higher-level
abstractions on top of it, such as simpler and more modern APIs and sensible
defaults.

Work on the Python interface is still in early stages and design and
prototyping.

We are currently searching for contributions and feedback to help shape this
tool into something that will benefit the entire Scipy community.





## Extended Abstract

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

> Include links to source code, articles, blog posts, or other writing that
> adds context to the presentation.

> Does it have a traditional background/motivation, methods, results, and
> conclusion structure?

> If you've given a talk, tutorial, or other presentation before, include that
> information as well as a link to slides or a video if they're available.



Answer these:


> Do you intend to present a demo?

> Does the work make any new contributions to open-source software?

> Which existing open-source tools does it use?

> What science fields are impacted by the work?

> How does it work fit into the Scientific Python community?
