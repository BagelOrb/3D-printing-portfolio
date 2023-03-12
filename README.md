## Dr. Tim Kuipers
Software Engineer

# Adaptive width slicing

A framework for FDM 3D printers for generating toolpaths with varying width to accomodate thin 3D models with varying width.
We use the Medial Axis Transform / Voronoi Diagram to determine the optimal number of extrusion lines from the 'center' skeleton of a shape outward as well as prescribing widths for each of those lines.
This results in better printable instructions and a better filling of shapes, which improves the mechanical performance of 3D printed parts, while keeping the width variation to a minimum and away from the outer controls for a better manageable process control.

Published as ![A Framework for Adaptive Width Control of Dense Contour-Parallel Toolpaths in Fused Deposition Modeling
Author links open overlay panel](https://www.sciencedirect.com/science/article/pii/S0010448520301007) in the journal Computer-Aided Design.
Integrated into ![Cura 5.0](https://ultimaker.com/learn/ultimaker-cura-5-0-stable-release).

![adaptive width slicing](https://storage.googleapis.com/contentful_assets/images.ctfassets.net/7cnpidfipnrw/5qrdKAjpuge0ILbUmWpz8m/e11b5936a1d083f07cba888899ea4b0e/Ultimaker-Cura-Earbud-sliced-SidebySide.gif?fm=webp&w=1080)

before  --------------------------------------------------------------------------------------  after

![adaptive width paper example](https://raw.githubusercontent.com/BagelOrb/3D-printing-portfolio/c2f329c7dc2357d54961b9e2f0454b779344c3f6/sources-validation-gMat_example_all_combined.svg)

colors show deviations from the nominal extrusion width

## Spatially graded gyroid
The above framework can be used to 3D print functionally graded materials, such as a gyroid structure which exhibits a spatial gradient in the density by varying the thickness of the repeating structure.

![spatially graded gyroid shoe sole](https://user-images.githubusercontent.com/8895761/224528451-1d1aeb96-29bb-4c4d-9357-2a06095fc501.png)


# Hatching for 3D prints
A method for recreating black and white surface imagery for dual material FDM 3D printers.
By printing layers alternatingly in black and white material and changing the outline geometry of the layers we can adjust the amount of visible black versus white material at each location.

Published as ![Hatching for 3D prints: Line-based halftoning for dual extrusion fused deposition modeling](https://www.sciencedirect.com/science/article/abs/pii/S0097849318300578) in Computers & Graphics.

![image](https://user-images.githubusercontent.com/8895761/224529309-75d6b720-a2f1-439d-868d-b99fcb77f736.png)
![image](https://user-images.githubusercontent.com/8895761/224529345-2241a93b-0cf0-4e55-8036-1bace6a4a737.png)

# Cross 3D infill
A method for creating an infill geometry which consists of a single continuous extrusion line on each layer, which can be used to recreate a prescribed density gradient.
We define a 3D extension of a novel 2D space filling fractal and use the recursion depth to control the density in various locations.
This is especially useful for printing flexible objects which are required to exhibit spatial variation in the flexibility.

This was published as ![CrossFill: Foam Structures with Graded Density for Continuous Material Extrusion](https://www.sciencedirect.com/science/article/abs/pii/S0010448519301800) in Computer-Aided Design.
It has been integrated in Cura since version 3.0.

![image](https://user-images.githubusercontent.com/8895761/224530047-1fc196c5-5d25-4457-b39e-7db321949f66.png)
![image](https://user-images.githubusercontent.com/8895761/224530079-1c4b2e5e-13be-436d-b44b-b36f47113a60.png)


# Interlocking
A method for generating an interlocking structure between two materials to improve on the adhesion between different parts.
By interlacing horizontal beams we can ensure an interlock in the third dimension, while retaining connectivity and continuous extrusion in the plane of each layer.

Published as ![ITIL: Interlaced Topologically Interlocking Lattice for continuous dual-material extrusion](https://www.sciencedirect.com/science/article/pii/S2214860421006424) in Additive Manufacturing.
Integrated in ![Cura 5.3](https://community.ultimaker.com/topic/42890-ultimaker-cura-53-beta-released/).

![image](https://user-images.githubusercontent.com/8895761/153227686-fde3a8e6-447a-4a25-8dd9-60afcd126eb8.png)

a simple example showing interlocking of two materials

![image](https://user-images.githubusercontent.com/8895761/153227496-14c86a52-5d78-4fd3-8728-87339f99a77a.png)

showing only one material in the layer view to reveal the internal interlocking structure


# Minimizing microgaps
A method for generating toolpaths of varying width in order to reduce the microgaps in between toolpaths.
By iteratively simplifying the medial axis we can generate toolpaths which grow smoother inward;
this smoothness reduces the gaps in between consecutive toolpaths and leads to easily printable paths.
However, in order to achieve this the width variation is maximal, so process control is more difficult.

Published as ![Variable-width contouring for additive manufacturing](https://dl.acm.org/doi/abs/10.1145/3386569.3392448) in ACM Transactions on Graphics.

![image](https://user-images.githubusercontent.com/8895761/224530714-711ba462-5541-4968-abc7-119479d23af3.png)
toolpaths in alternating colors and their 3D prints in orange

# Lightning infill
Reimplementation of a method to generate infill which uses minimal material in order just to support top surfaces inside a 3D print,
while consisting of connected extrusion liens on each layer in order to guarantee printability.
Useful for printing quickly if your end part doesn't require a lot of structural integrity.

Based on ![Ribbed Support Vaults for 3D Printing of Hollowed Objects](https://onlinelibrary.wiley.com/doi/abs/10.1111/cgf.13750).
Integrated into ![Cura 4.12](https://ultimaker.com/learn/enjoy-first-time-right-results-with-ultimaker-cura-4-12-beta).

![lightning infill](https://user-images.githubusercontent.com/8535734/136006729-481a4e41-d087-4b98-af6e-bece99995b72.gif)

# Support generation
I have developed the modern support generation system of Ultimaker Cura and implemented most of the new features to that system (excluding tree support).
While the old support generation system from 2014 worked on the basis of a grid of sampled points,
the system I introduced works on the outlines of each layer, which means it's more accurate and can generate support also for thin pieces of overhang which might be missed by sampling based techniques.

An extensive guide to the settings can be ![found here](https://support.makerbot.com/s/article/1667417606331).

![image](https://user-images.githubusercontent.com/8895761/224531864-2e70f7f7-3103-40c9-ab8d-3683a09ba8b0.png)

a 3D model with support | support with a dense roof for soluble support material | support with a sparse interface for same material as build

![image](https://user-images.githubusercontent.com/8895761/224532088-0318c885-3cf7-4f6a-910c-dbaf3a9b67ef.png)

an internal brim for improving the build plate adhesion of the support structure

# NLP
I worked on a small Natural Language Processing project where I analyzed various techniques for performing topic analysis on a dataset of tweets.
The project contains a birds view analysis of various simple topic analysis techniques and their shortcomings.

The project can be found on ![GitHub](https://github.com/BagelOrb/topic_analysis).

![image](https://user-images.githubusercontent.com/8895761/224532350-34db874e-541b-4cea-923f-724ba3ccf500.png)

a visualization of the most prevalent noun topicsaccording to their specificity score
