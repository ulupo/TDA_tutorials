# TDA_tutorials

The recently developed field of Topological Data Analysis (TDA) provides multiple computational methods that can be used to understand complex systems. These techniques include Mapper, persistent homology, path signatures, and sheaf theory. The goal of this repository is to offer an introduction to these ideas by way of a simple example. All notebooks use a Julia kernel, but a few include calls to Python packages.

Please contact annsize at seas dot upenn dot edu for questions.



------
## How to run this tutorial

These collections of notebooks can be used as standalone files, but for ease they can also be run inside a docker container. The following are instrucitons for running in a docker container (recommended).

0. Install docker (I use Docker Desktop).
1. In the terminal, navigate to this directory and execute `make build`.
2. Once the docker image has finished building, you can execute `make run` to use a read-only (no saving) version, or I prefer to mount the directory by instead executing `docker run -it --rm -p 8888:8888 -v $(pwd):/home/jovyan/ ph_tutorial:deploy0520`.
3. Copy the http://127.0.0... path into your favorite browser (warning this code only tested on Chrome).
4. Enjoy learning about topological data analysis!

------


## Persistent Homology

In brief, persistent homology chronicles evolving cavities within a filtered simplicial complex. Please see [1](https://epjdatascience.springeropen.com/articles/10.1140/epjds/s13688-017-0109-5), [2](https://www.ams.org/journals/bull/2009-46-02/S0273-0979-09-01249-X/S0273-0979-09-01249-X.pdf), [3](https://www.mitpressjournals.org/doi/pdf/10.1162/netn_a_00073) for an introduction. In the `PersistentHomologyExample.ipynb` notebook, we use the [Eirene](https://github.com/Eetion/Eirene.jl) package to compute the persistent homology of a subset of the NYC food data from [Open Food Facts](https://world.openfoodfacts.org/). Other packages to compute persistent homology include [Gudhi](http://gudhi.gforge.inria.fr/)(C++, Python), [Javaplex](http://appliedtopology.github.io/javaplex/)(MATLAB), [TDA](https://cran.r-project.org/web/packages/TDA/)(R), and [Dionysus](https://www.mrzv.org/software/dionysus/)(C++, Python).


## Mapper

The Mapper algorithm helps to visualize and intuit high dimensional data. It effectively is a clustering algorithm, but it outputs a graph (or simplicial complex) with nodes as clusters and connections representing similar clusters. More explicitly, Mapper segments the data into overlapping bins, clusters within each bin, and then creates the output graph (or simplicial complex) with each node corresponding to a cluster and connections corresponding to clusters that share data points. For more information, please see [4](https://www.ayasdi.com/wp-content/uploads/2015/02/Topological_Methods_for_the_Analysis_of_High_Dimensional_Data_Sets_and_3D_Object_Recognition.pdf), [5](http://web.stanford.edu/group/bdl/papers/saggar-tda-mapper-cme/). The documentation of `kmapper` is [extensive](https://pypi.org/project/kmapper/), so we include only a short example in the `MapperExamples.ipynb` notebook.


## Path signatures

Computing elements of the path signature helps us understand relationships between elements of a time series, specifically lead-lag relationships. Using ideas from [6](https://arxiv.org/abs/1405.4537), [7](https://projecteuclid.org/euclid.bams/1183539443), the authors of [8](https://www.mitpressjournals.org/doi/full/10.1162/NETN_a_00053) used path signatures to understand differences between brain activity from individuals with tinnitus and from healthy controls. The example in `PathSignaturesExamples.ipynb` uses the `iisignature` [package](https://pypi.org/project/iisignature/) and calculates the lead matrix (matrix showing lead-lag relationships) for generated paths. Additionally the example examines the effect of random noise in the sample on the calculated lead matrix.


## Sheaves

Graphs with data atop nodes that satisfy constraints across edges can often be modeled with the sheaf formalism. For an introduction to sheaves, please see [9](https://www.math.upenn.edu/~jhansen/content/gentleintroduction.pdf), [10](https://arxiv.org/abs/1303.3255), [11](https://arxiv.org/abs/1603.01446). The brief example in `SheavesExample.ipynb` demonstrates how to construct a sheaf and calculate the consistency radius using `pysheaf`. The [pysheaf](https://github.com/kb1dds/pysheaf) package has multiple examples, and ours draws from [this](https://github.com/kb1dds/pysheaf/blob/master/pysheaf/consistencyFiltrationExample.py) example but uses the specific case of Figure 3a in [Blevins and Bassett 2020](https://link.springer.com/referenceworkentry/10.1007%2F978-3-319-70658-0_87-1). To work with sheaf laplacians, please check out [SheafLearning.jl](https://github.com/hansenjakob/SheafLearning.jl).
