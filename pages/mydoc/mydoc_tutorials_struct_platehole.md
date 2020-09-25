---
title: Plate hole
keywords: tutorial, platehole
summary: 
sidebar: mydoc_sidebar
permalink: mydoc_tutorials_struct_platehole.html
folder: mydoc
---

{% include note.html content="We recommend going through the tutorial in [Get started](mydoc_get_started_download_docker.html) before running this case." %}

The following is a structural optimization case for a plate with a hole in the middle.

<pre>
Case: Structural optimization for the plate hole configuration
Geometry: Plate hole
Objective function: Weight
Design variables: 24 FFD points moving in the x and y directions
Constraints: Symmetry constraint (total number: 18), max stress constraint
Mesh cells: 4K
Solver: DASolidDisplacementFoam
</pre>

To run this case, first download [tutorials](https://github.com/DAFoam/tutorials/archive/master.tar.gz) and untar it. Then go to tutorials-master/PlateHole_Structure and run this command to start the DAFoam docker container.

<pre>
docker run -it --rm -u dafoamuser --mount "type=bind,src=$(pwd),target=/home/dafoamuser/mount" -w /home/dafoamuser/mount dafoam/opt-packages:{{ site.latest_version }} bash
</pre>

**Now you are on the DAFoam Docker container**, run the "preProcessing.sh" script to generate the mesh:

<pre>
./preProcessing.sh
</pre>

Then, use the following command to run the optimization with 1 CPU cores:

<pre>
python runScript.py 2>&1 | tee logOpt.txt
</pre>

{% include links.html %}