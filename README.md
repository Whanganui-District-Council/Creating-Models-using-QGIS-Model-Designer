# Creating Models using QGIS Model Designer

A FOSS4G SotM Oceania 2023 Workshop

> Workshop Requirements:
>
> * QGIS 3.28+ LTR
> * Workshop files https://data.whanganui.govt.nz/wdc/foss4g/2023/Workshops.zip


The Model Designer is a powerful QGIS component that we can use to define a workflow that will run a chain of algorithms (a processing model).

A normal session with the Model Designer includes more than running a single algorithm. Usually several of algorithms are run to obtain a result, and often the outputs of some of those algorithms are used as input for other algorithms.

Using the Model Designer, that workflow can be put into a processing model, which will run all the necessary algorithms in a single run, thus simplifying the whole process and automating it.


In this workshop we will create a processing model in the Model Designer that displays buildings affected by a single point event within a distance from the event location.  

The affected buildings are determined by 
* Clicking a point on the map canvas to define an event location,
* travelling a distance along the road network from the event location, 
* buffering the travel distance to intersect land parcels, 
* extracting building footprints that then intersect the land parcels.

[Start here...](Creating-Models-using-QGIS-Model-Designer.md)
