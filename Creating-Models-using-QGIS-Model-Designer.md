# Workshop Setup

## QGIS
- [ ] Ensure you have **QGIS 3.28** or better installed.

## Install Workshop Files

- [ ] Download the Workshop.zip file from  https://data.whanganui.govt.nz/wdc/foss4g/2023/Workshops.zip

- [ ] Unzip the contents to the folder **C:\Workshops**

  ![Alt text](assets/image-setup-1.png)

## Run the Workshop Project

- [ ] *Double click* the QGIS project file **qgis_models_workshop.qgz** to run QGIS and open the workshop project

### Set additional path for python scripts
- [ ] From the **Settings** menu choose **Options**

- [ ] Select the **Processing** Panel

- [ ] Expand **Scripts**

- [ ] *Double click* the current path value for Scripts folder

- [ ] Click the **Options** button ![Alt text](assets/image-option-button.png) on the left hand side of the path value

- [ ] Add the path to the workshops scripts folder e.g. **"C:\Workshops\scripts"**

  ![Alt text](assets/image-setup-2.png)

- [ ] Click the **OK** button

- [ ] Click the **OK** button to exit the options dialog










---

---

# Processing Models

The objectives of this workshop are to learn about:

* Processing Models
* The Model Designer

---

## Processing Models and the Model Designer

The Model Designer is a powerful QGIS component that we can use to define a workflow that will run a chain of algorithms (a processing model).

A normal session with the Model Designer includes more than running a single algorithm. Usually several of algorithms are run to obtain a result, and often the outputs of some of those algorithms are used as input for other algorithms.

Using the Model Designer, that workflow can be put into a processing model, which will run all the necessary algorithms in a single run, thus simplifying the whole process and automating it.


![Alt text](assets/image-1.png)

---


---


## Locate Affected Buildings Model

In this workshop we will create a processing model in the Model Designer that displays buildings affected by a single point event within a distance from the event location.  

The affected buildings are determined by 
* Clicking a point on the map canvas to define an event location,
* travelling a distance along the road network from the event location, 
* buffering the travel distance to intersect land parcels, 
* extracting building footprints that then intersect the land parcels.

![Alt text](assets/image-67.png)

#### Inputs

-   Event location point chosen on the Map Canvas

-   Road network layer

-   Travel distance value

-   Travel distance buffer value

-   Land parcel layer

-   Building footprints layer

#### Outputs 

-   Event location point layer

-   Affected road network line layer

-   Travel distance buffer polygon layer

-   Affected buildings polygon layer

---

### Creating the model

- [ ] In the **Processing Toolbox**, click the **Models** tool ![Alt text](assets/image-models.png)
  

- [ ] Choose **Create New Model...**
  
  ![Alt text](assets/image-2.png)

  Note that an empty **Model Designer** window opens
  ![Alt text](assets/image-3.png)


- [ ] In the **Model Properties** panel, set the **Name** to ***Locate Affected Buildings***

  ![Alt text](assets/image-4.png)
- [ ] In the **Model Properties** panel, set the **Group** to ***Training***

  ![Alt text](assets/image-5.png)



- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the Model Designer windows toolbar

    The **Save Model** dialog will be displayed...
    ![Alt text](assets/image-6.png)

- [ ] Set the File name to ***locate affected buildings.model3***
   
   For this workshop, set the save path for your model to…

   ***C:\Workshops***

- [ ] Click the **Save** button


---

## Adding the first Input parameter

Our first input parameter is the **Event Location (x,y)** point that will be chosen from the Map Canvas by the end user

- [ ] In the **Inputs** panel, *double click* the **Point** input

  ![Alt text](assets/image-7.png)

  Note that a **Point Parameter Definition** dialog opens...

  ![Alt text](assets/image-8.png)

- [ ] Set **Description** to ***Event Location (x,y)***

  ![Alt text](assets/image-9.png)
  
- [ ] Click the OK button

  Note that we now have the first input parameter in our Model Designer…

  ![Alt text](assets/image-10.png)
 
  > **HINT** - Any input parameter can be dragged in the window to re-position and to edit the input parameter simply *double click*.


---


### Adding the first algorithm and output
Our next task is to assign this input parameter to an algorithm

- [ ] Switch to the **Algorithms** panel (use the tabs at the bottom of the Inputs panel)

  Note that the panel now displays the different categories of algorithms available to the Model Designer…

  ![Alt text](assets/image-11.png)


- [ ] Expand the **Scripts** category, then expand **Custom scripts**

- [ ] *Double click* the **Pick point on map** script

  Note that a dialog opens for the **Pick point on map** script…

  ![Alt text](assets/image-12.png)




- [ ] Change the **Pick a point on the map** option to **Model Input**

  ![Alt text](assets/image-13.png)

- [ ] Set the **Pick a point on the map**  dropdown list for **Using model input** to **Event Location (x,y)** (that’s the input parameter we defined previously)

  ![Alt text](assets/image-14.png)

- [ ] Set **Output layer** to **Event location** (this will be the name of the output layer displaying the event location point in QGIS)

  ![Alt text](assets/image-15.png)

- [ ] Click the **OK** button

  Note that the Pick point on map script has been added to the Model Designer, along with the output layer…

  ![Alt text](assets/image-16.png)

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-17.png)

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar


---

### Testing the model
We now have an input parameter, an algorithm and an output – let’s test the model.

- [ ] Close the **Model Designer** window

- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  > **HINT** - *"agh! I dont see the training group!"* 
  >
  > - [ ] From the Settings menu choose Options
  > - [ ] Select the Processing Panel
  > - [ ] Expand Models
  > - [ ] Double click the current path value for Models folder
  > - [ ] Click the options button on the left hand side of the path value
  > - [ ] Add the path to where you saved your model e.g. "C:\Workshops"
  > - [ ] Click the OK button
  > - [ ] Click the OK button to exit the options dialog

  ![Alt text](assets/image-18.png)



- [ ] *Double click* the model named **Locate Affected Buildings**

  Note that **Locate Affected Buildings** dialog is displayed…

  ![Alt text](assets/image-19.png)


- [ ] Click the Option button ![Alt text](assets/image-option-button.png) next to the **Event Location** textbox

  Note that we are switched to the Map Canvas and we can click a location for the event on the Map Canvas.

- [ ] Click a location as indicated below on the Map Canvas…

  ![Alt text](assets/image-20.png)



  The **Event location (x,y)** textbox will now be populated with the coordinates of the location we clicked on the Map Canvas...

  ![Alt text](assets/image-21.png)



- [ ] Leave the **Event Location** output set to **[Create temporary layer]**

- [ ] Click the **Run** button

  Note that the **Locate Affected Buildings** dialog swithces automatically to the log tab to display a log of the entire process that was run...

  ![Alt text](assets/image-22.png)



- [ ] In the **Locate Affected Buildings** dialog, click the **Close** button

  The **Map Canvas** should now show a point feature for the location we chose, and the **Layers Panel** will display a new temporary layer named **Event Location**…

  ![Alt text](assets/image-23.png)



---

### Edit the existing Model


- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  ![Alt text](assets/image-18.png)


- [ ] *Right click* the model named **Locate Affected Buildings**, choose **Edit Model…** to open the Model Designer window

  ![Alt text](assets/image-24.png)


---



### Add input parameter for Road network layer
Let’s add the input parameter for the road network layer

- [ ] Switch to the **Inputs** panel (use the tabs at the bottom of the **Algorithms** panel)

  ![Alt text](assets/image-25.png)

- [ ] *Double click* the **Vector Layer** input

  Note that a **Vector Layer Parameter Definition** dialog opens...

  ![Alt text](assets/image-26.png)

- [ ] Set **Description** name to ***Road Network layer***

  ![Alt text](assets/image-27.png)

- [ ] Set **Geometry Type** to ***Line***

  ![Alt text](assets/image-28.png)



- [ ] Click the **OK** button


- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-29.png)




- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar




---


### Add input parameter for Travel distance
Now let’s add the travel distance input parameter

- [ ] From the **Inputs** panel, *Double click* the **Number** input

  Note that a **Number Parameter Definition** dialog opens...

  ![Alt text](assets/image-30.png)

- [ ] Set **Description** to ***Travel Distance***

- [ ] Set **Minimum value** to ***1***

- [ ] Set **Maximum value** to ***10000***

- [ ] Set **Default value** to ***200***

  The **Number Parameter Definition** dialog should look like this...

  ![Alt text](assets/image-31.png)




- [ ] *Click* the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-32.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar



----


### Add algorithm for Service area (from point)
Now we'll add an algorithm that calculates the service area from the event location along our road network.

- [ ] Switch to the **Algorithms** panel (use the tabs at the bottom of the **Inputs** panel)

- [ ] In the **Algorithms** panel, type ***service*** in the search bar

  Note that the list of algorithms is automatically filtered as we type in the search value…

  ![Alt text](assets/image-33.png)




- [ ] *Double click* the **Service area (from point)** algorithm

  Note that the **Service area (from point)** properties dialog opens…

  ![Alt text](assets/image-34.png)


- [ ] Set **Vector layer representing network** to ***Road Network Layer***

- [ ] Set **Start point** to use the model input ***Event Location (x,y)***

- [ ] Set the **Travel cost** to use the model input ***Travel Distance***

- [ ] Set the **Service area (lines)** output to ***Affected Road Network***

  The **Service area (from point)** properties dialog should look like this...

  ![Alt text](assets/image-35.png)



- [ ] Click the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-36.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar



----




### Add input parameter for road network buffer
Now let’s add the input parameter for the road network buffer

- [ ] Switch to the **Inputs** panel (use the tabs at the bottom of the **Algorithms** panel)

- [ ] *Double click* the **Number** input

  Note that a **Number Parameter Definition** dialog opens...

  ![Alt text](assets/image-37.png)

- [ ] Set **Description** name to ***Travel Distance Buffer***

- [ ] Set **Minimum value** to ***1***

- [ ] Set **Maximum value** to ***1000***

- [ ] Set **Default value** to ***20***

  The **Number Parameter Definition** dialog should look like this...

  ![Alt text](assets/image-38.png)


- [ ] *Click* the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-39.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar



---





### Add algorithm for buffer
Now let’s add the buffer algorithm

- [ ] Switch to the **Algorithms** panel (use the tabs at the bottom of the **Inputs** panel)

- [ ] In the **Algorithms** panel, type ***buffer*** in the search bar

  ![Alt text](assets/image-40.png)



- [ ] *Double click* the QGIS **Buffer** algorithm

  Note that the **Buffer** properties dialog opens…

  ![Alt text](assets/image-41.png)

  
- [ ] Set **Input layer** to use the algorithm output ***'Service area (lines)' from algorithm 'Service area (from point)'***

- [ ] Set **Distance** to use the model input ***Travel Distance Buffer***

- [ ] Set the output layer **Buffered** to ***Travel Distance Buffer to Land***

  The **Buffer** properties dialog should look like this...

  ![Alt text](assets/image-42.png)



- [ ] *Click* the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-43.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar




---



### Add input parameter for land parcel layer
Now let’s add the input parameter for the land parcel layer

- [ ] Switch to the **Inputs** panel (use the tabs at the bottom of the **Algorithms** panel)

- [ ] *Double click* the **Vector Layer** input

  Note that a **Vector Layer Parameter Definition** dialog opens

  ![Alt text](assets/image-44.png)

- [ ] Set **Description** to ***Land Parcel Layer***

- [ ] Set **Geometry Type** to ***Polygon***

  The **Vector Layer Parameter Definition** dialog should look like this...

  ![Alt text](assets/image-45.png)



- [ ] Click the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-46.png)



- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar





---

### Add algorithm for extracting by location for land parcels
Now let’s add the extract by location algorithm

- [ ] Switch to the **Algorithms** panel (use the tabs at the bottom of the **Inputs** panel)

- [ ] In the **Algorithms** panel, type ***extract by*** by in the search bar

  ![Alt text](assets/image-47.png)


- [ ] *Double click* the **Extract by location** algorithm

  Note that the **Extract by location** properties dialog opens…

  ![Alt text](assets/image-48.png)



- [ ] Set **Extract features from** to the model input ***Land Parcel Layer***

- [ ] Set **Where the features (geometric predicate)** to ***intersect***

- [ ] Set **By comparing to the features from** to use the algorithm output ***'Buffered' from algorithm 'Buffer'***

  The **Extract by location** properties dialog should look like this...

  ![Alt text](assets/image-49.png)



- [ ] *Click* the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-50.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar





---







### Add input parameter for building footprints layer
Now let’s add the input parameter for the building footprints layer

- [ ] Switch to the **Inputs** panel (use the tabs at the bottom of the **Algorithms** panel)

- [ ] *Double click* the **Vector Layer** input

  Note that a **Vector Layer Parameter Definition** dialog opens

  ![Alt text](assets/image-51.png)

- [ ] Set **Description** to ***Buildings Footprints Layer***

- [ ] Set **Geometry Type** to ***Polygon***

  The **Vector Layer Parameter Definition** dialog should look like this...

  ![Alt text](assets/image-52.png)



- [ ] Click the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-53.png)



- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar





---




### Add algorithm for extracting by location for building footprints
Now let’s add the extract by location algorithm

- [ ] Switch to the **Algorithms** panel (use the tabs at the bottom of the **Inputs** panel)

- [ ] In the **Algorithms** panel, type ***extract by*** by in the search bar

  ![Alt text](assets/image-47.png)


- [ ] *Double click* the **Extract by location** algorithm

  Note that the **Extract by location** properties dialog opens…

  ![Alt text](assets/image-54.png)



- [ ] Set **Extract features from** to the model input ***Building Footprints Layer***

- [ ] Set **Where the features (geometric predicate)** to ***intersect***

- [ ] Set **By comparing to the features from** to use the algorithm output ***'Extracted (location)' from algorithm 'Extract by location'***

- [ ] Set **Extracted (location)** to ***Affected Buildings***



  The **Extract by location** properties dialog should look like this...

  ![Alt text](assets/image-55.png)



- [ ] *Click* the **OK** button

- [ ] Re-position the items to look like below…

  ![Alt text](assets/image-56.png)


- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar





---





### Running the model
We now have our processing model completed – let’s run the model.

- [ ] Close the **Model Designer** window

- [ ] In the **Layers** panel remove the layer named **Event Location** that was generated from our previous testing.

- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  ![Alt text](assets/image-18.png)



- [ ] *Double click* the model named **Locate Affected Buildings**

  Note that the **Locate Affected Buildings** dialog is displayed…

  ![Alt text](assets/image-57.png)





- [ ] Set **Building Footprints Layer** to the layer ***building_footprints_urban_2020***

- [ ] Set **Event Location (x,y)** by clicking the Option button ![Alt text](assets/image-option-button.png) next to the **Event Location** textbox

  Note that we are switched to the Map Canvas and we can click a location for the event on the Map Canvas.

- [ ] Click a location as indicated below on the Map Canvas…

  ![Alt text](assets/image-20.png)





- [ ] Set **Land Parcel Layer** to the layer ***land***

- [ ] Set **Road Network Layer** to the layer ***nz_road_addressing***

- [ ] Set **Travel Distance** to ***500***

- [ ] Set **Travel Distance Buffer** to ***20***

  The **Locate Affected Buildings** dialog will l;ook like this...

  ![Alt text](assets/image-58.png)


- [ ] Click the Run button

  Note that the **Locate Affected Buildings** dialog switches automatically to the log tab to display a log of the entire process that was run...

  ![Alt text](assets/image-59.png)


- [ ] In the **Locate Affected Buildings** dialog, click the Close button

The Map Canvas should now show the results of the **Locate Affected Buildings** processing model…

![Alt text](assets/image-60.png)




---





### Setting pre-defined styles for the output layers
Whenever the Affected Buildings model is run the output layers styles are determined randomly by QGIS.

We can extend our model by applying a QGIS **.qml** style file to each layer output so that we have consistent styling of the layer ouput each time we run the model.

For this workshop we have the following pre-defined style files available:

- **C:\Workshops\styles\AffectedBuildings_event_location.qml**
- **C:\Workshops\styles\AffectedBuildings_travel_distance_buffer.qml**
- **C:\Workshops\styles\AffectedBuildings_affected_road_network.qml**
- **C:\Workshops\styles\AffectedBuildings_affected_buildings.qml**

These style files define the following styles:

  ![Alt text](assets/image-styles.png)



> >>>>>>>>>>>>>>>>>>>>>>>>>>>---
#### Let’s start editing our model

- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  ![Alt text](assets/image-18.png)


- [ ] *Right click* the model named **Locate Affected Buildings**, choose **Edit Model…** to open the **Model Designer** window

  ![Alt text](assets/image-24.png)



> >>>>>>>>>>>>>>>>>>>>>>>>>>>---
#### Add the Event Location style

- [ ] In the **Algorithms** panel, type ***style*** in the search bar

  ![Alt text](assets/image-61.png)



- [ ] *Double click* the **Set layer style** algorithm

  Note that the **Set layer style** properties dialog opens…

  ![Alt text](assets/image-62.png)

- [ ] Set **Layer** to **'Output layer' from algorithm 'Pick point on map'**

- [ ] Set **Style file** to **C:\Workshops\styles\AffectedBuildings_event_location.qml**

  ![Alt text](assets/image-63.png)




- [ ] Click the **OK** button

- [ ] Re-position the items

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar





> >>>>>>>>>>>>>>>>>>>>>>>>>>>---
####  Add the Affected road network style

- [ ] *Double click* the **Set layer style** algorithm

- [ ] Set **Layer** to **'Service area (lines)' from algorithm 'Service area (from point)'**

- [ ] Set **Style file** to **C:\Workshops\styles\AffectedBuildings_affected_road_network.qml**

  ![Alt text](assets/image-64.png)


- [ ] Click the **OK** button

- [ ] Re-position the items

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar




> >>>>>>>>>>>>>>>>>>>>>>>>>>>---
#### Add the Travel distance buffer style

- [ ] *Double click* the **Set layer style** algorithm

- [ ] Set **Layer** to **'Buffered' from algorithm 'Buffer'**

- [ ] Set **Style file** to **C:\Workshops\styles\AffectedBuildings_travel_distance_buffer.qml**

  ![Alt text](assets/image-65.png)


- [ ] Click the **OK** button

- [ ] Re-position the items

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar




> >>>>>>>>>>>>>>>>>>>>>>>>>>>---
#### Add the Affect buildings style

- [ ] *Double click* the **Set layer style** algorithm

- [ ] Set **Layer** to **'Extracted (location)' from algorithm 'Extract by location'**

> [!NOTE]
>
>  There are two **'Extracted (location)' from algorithm 'Extract by location'** options!
>
>  Choose the second one.

- [ ] Set **Style file** to **C:\Workshops\styles\AffectedBuildings_affected_buildings.qml**

  ![Alt text](assets/image-66.png)


- [ ] Click the **OK** button

- [ ] Re-position the items

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar


> >>>>>>>>>>>>>>>>>>>>>>>>>>>---



Our model should look like this now…

![Alt text](assets/image-67.png)



---
### Running the final model with styling
We now have our processing model completed – let’s run the model.

- [ ] Close the **Model Designer** window

- [ ] In the **Layers** panel remove the layers from previous running of the model

  - Event Location
  - Affected road network
  - Travel distance buffer
  - Affected buildings


- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  ![Alt text](assets/image-18.png)



- [ ] *Double click* the model named **Locate Affected Buildings**

  Note that the **Locate Affected Buildings** dialog is displayed…

  ![Alt text](assets/image-57.png)





- [ ] Set **Building Footprints Layer** to the layer ***building_footprints_urban_2020***

- [ ] Set **Event Location (x,y)** by clicking the Option button ![Alt text](assets/image-option-button.png) next to the **Event Location** textbox

  Note that we are switched to the Map Canvas and we can click a location for the event on the Map Canvas.

- [ ] Click a location as indicated below on the Map Canvas…

  ![Alt text](assets/image-20.png)





- [ ] Set **Land Parcel Layer** to the layer ***land***

- [ ] Set **Road Network Layer** to the layer ***nz_road_addressing***

- [ ] Set **Travel Distance** to ***500***

- [ ] Set **Travel Distance Buffer** to ***20***

  The **Locate Affected Buildings** dialog will l;ook like this...

  ![Alt text](assets/image-58.png)


- [ ] Click the Run button

  Note that the **Locate Affected Buildings** dialog switches automatically to the log tab to display a log of the entire process that was run...

  ![Alt text](assets/image-59.png)


- [ ] In the **Locate Affected Buildings** dialog, click the Close button

The Map Canvas should now show the results of the **Locate Affected Buildings** processing model, complete with output layers styled…

![Alt text](assets/image-68.png)




---

### Editing model help
We can document our models from within the Model Designer itself.

To document our Locate Affected Buildings model, let’s start by editing our model

- [ ] In the **Processing Toolbox**, expand the **Models** category, then expand the **Training** group

  ![Alt text](assets/image-18.png)


- [ ] *Right click* the model named **Locate Affected Buildings**, choose **Edit Model…** to open the **Model Designer** window

  ![Alt text](assets/image-24.png)


Now let’s edit the model help

- [ ] In the Model Designer window, click the **Edit model help** tool ![Alt text](assets/image-help.png)

  Note that **Edit Model Help** dialog opens…

  ![Alt text](assets/image-69.png)

- [ ] Select the element named **Algorithm description** in the **Select element to edit** panel

- [ ] Click inside the **Element Description** panel, and type a description for the model

> **TIP** – Copy and paste the text saved in the file **C:\Workshops\AffectedBuildings_help_text.txt** into the **Element Description** panel.

  ![Alt text](assets/image-70.png)

- [ ] Click the **OK** button

- [ ] Save the model by clicking the **Save** tool ![Alt text](assets/image-save.png) on the toolbar



- [ ] In the Model Designer window, click the Run model tool ![Alt text](assets/image-run-model.png) on the toolbar


  Note that the Model now displays a description panel on the right-hand side of the model dialog…

  ![Alt text](assets/image-71.png)























