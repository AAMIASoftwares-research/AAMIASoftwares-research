# General Action Plan

The action plan of the whole AAMIA Softwares research branch, in logical order, first to last.

## CenterlineTracker

1. Centerline estimation from thesis.
1. Improovre tracker logic - thicken point cloud.
1. Explore new techniques - Graphs, Attention, combination of both.

Publish paper on it.

Required: Centerlines annotation data (NAS-> FFR/Papers/CAT08 has the most precise annotation pipeline)
Available: CAT08-training
           (Monzino)

## Centerline point cloud to Centerline Directed Grapgh

If centerline tracking output is a point cloud, make this process more seamless and fast.

Use:

- python: NetworkX (, pygraphlib, python-graph, graph-tool
- C++: Boost Graph Library (, graphs in stdlib?)

## Filaments Points Classifier Net

Idea: Having a noisy filamentous point cloud resembling a "long hair", a "spiderweb" or a "very thinn tree branch",
classify every point in the point cloud as:

- "disjointed/alone" (0 relevant neighbours)
- "endpoint" (neighbours in 1 direction only)
- "filament point" (neighbours in 2 directions)
- "3-ways intersection" (neighbours in 3 direction only)
- "4-ways intersection" (neighbours in 4 direction only)
- "5-or-more-ways intersection" (neighbours in 5 or more directions)

Very little state-of-the-art about it. Might be useful in astro-imaging and others.
Interesting challenge useful in the coronary artery tracking pipeline in graph is first extracted as a point cloud.

Finish filaments endpoints classifier for centerline tracker.

Publish paper on the ML method to discrimidate filament endpoints from other types of points (the work you already started).

Even if not super useful in pipeline if graphs networks are used from the start (which is very hard to do and has a lot of limit-cases)
I would try and publish something on it anyway: very few state of the art about it, nieche, good way to compare different ML approaches,
datasets can be created artificially without any numerosity limitation, we also have some real life, chlinical use-cases on which to test it,
and give it relevance.  
Why a point cloud in the first place, and not a graph right from the start? The point cloud is free from any topology constarints,
leaving tracking as free as possible.
Easier to develop post-processing logic, with human interaction if needed.
point clouds allow the tracker to try and find the centerline in many passes, obtaining hopefully a normal distribution of points
with respect to the direction normal to the centerline. Thus, the estimated centerline path can be estimated more precisely,
based on more data than using a single graph right away. Of course this is an assuption, but it makes sense to me and it is easier and faster to develop.
Graphs will be explored later.

## Step 3

Plaques radiomics.

Learn to identify vulnerable plaques with combination above.

Write paper abut it.

Required: Plaque segmentation and CT data.
Available: Monzino

## Step 4

Build Sophisticated plaque segmentation, classification.

Interface it with coronary artery graphs.

## Step 5

Identify vessels geometry (lumen, outer wall, intersections)
All to be used and visualised in 3D.

## Step 6

Start putting everytgìhing together.
options: Standalone GUI
         Slicer module (has the advantage of being an already working environment and has good data structures and docs)

## Step 7

Introduce FFR and other functional studies.

## Step 8

Perfusion.

## Step 9

Heart segmentation and 3D reconstruction of anatomy.

## Step 10

Patient-tailored perfusion (Fusion of coronary anatomy - heart segmentation - heart analysis - perfusion).

## Always

Gather CT (without contrast liquid) and CCTA (with contrast liquid) data.

Gather labelled data:
    Centrelines
    Plaques location and length
    Plaques material analysis

Publish paper ad each step.
