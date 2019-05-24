# Raycasting guide
![data-generationScreenshot](/docs/images/data-generation.PNG)

## Prerequisites
**Session data file:** Session file generated by VirtualMaze during the experiment.

**.edf file:** .edf file from the eyelink eyetracker.

## Steps to Use
1. Select the files in the respective textboxes
+ Select the destination folder to save the output file
+ Click ***Generate*** to start processing the files.

## Output
A CSV (Comma Seperated Value) file will be generated in the desired destination.

![data-generation-outputScreenshot](/docs/images/data-generation-output.PNG)

#### Columns Reference
1. Type of the data in the row (string/text).
2. Timestamp of the gaze data used to generate the object fixated (unsigned int)
3. Name of the Object fixated by the gaze or Message (string).

*Relative Position ([Unity Units](#unity-units))*

4. 2D X location of the gaze data of the image with reference with the center of the object hit.
5. 2D Y location of the gaze data of the image with reference with the center of the object hit.

See [Relative Position](#relative-position) for more details.

*Gazed Object Location ([Unity Units](#unity-units))*

6. X Worldspace Co-ordinate of the object gazed upon.
7. Y Worldspace Co-ordinate of the object gazed upon.
8. Z Worldspace Co-ordinate of the object gazed upon.

*Gaze hit location ([Unity Units](#unity-units))*

9. X Worldspace Co-ordinate point where the gaze lands on the object.
10. Y Worldspace Co-ordinate point where the gaze lands on the object
11. Z Worldspace Co-ordinate point where the gaze lands on the object

*Raw gaze data (Pixels)*

12. gx data copied from the .edf file used to raycast.
13. gy data copied from the .edf file used to raycast.

*Subject location in Worldspace ([Unity Units](#unity-units))*

14. X Worldspace Co-ordinate of the subject's location in the Worldspace.
15. Y Worldspace Co-ordinate of the subject's location in the Worldspace.
16. Z Worldspace Co-ordinate of the subject's location in the Worldspace.

#### Unity Units
Numbers represented by Unity Units are values unity uses to position the various gameobjects in the Worldspace where the center of the Worldspace and the maze is located at (x: 0, y: 0, z: 0). For reference and scaling, the "rooms" used in VirtualMaze is 25 by 25 Unity Units and the ceiling is 4.93 Unity Units high.

The default settings for units in Unity is 1 Unity Unit = 1 meter however, because the scaling is mutable, feel free to scale these values as required.

#### Object Size Reference

- **Posters:** (width: 2.24, length: 1.4, thickness: 0) Unity Unit
- **Outer Walls:** (width: 5, length: 5, thickness: 0.1) Unity Unit
- **Inner/Colored Walls:** (width: 5, length: 3.11, thickness: 0.1) Unity Unit
- **Ground and Ceiling:** (width: 25, length: 25, thickness: 0) Unity Unit
 - Ceiling Height: 4.93 Unity Unit
- **CueImage:** (width: 0.4, length: 0.2, thickness: 0) Unity Unit
- **HintImage** (width: 0.2, length: 0.1, thickness: 0) Unity Unit
- **Height of Viewport:** 1.85 Unity Units from the floor

See [CueImage and HintImage ](#cueImage-and-hintImage) for definition of CueImage and HintImage.

#### Object Name References

##### CueImage and HintImage
![cue-hint-image](/docs/images/cue-hint-image.png)

There are 2 kinds of cues presented to the subject and for convenience, the larger cue is referred as the CueImage while the smaller image at the top is referred as the HintImage.


## Relative Position
Relative position represents the coordinates of the gaze hit position from the center of the poster.

###### Image cue in 3D space
![relative position explanation](/docs/images/relativePos-explaination.png)

The center of object (represented by the circle) is the 3D coordinates of its position in the virtual space.

The point where the gaze hits the object (represented by the triangle) is also represented by its position in the virtual space.

From the image example, the resultant 2D relative position is **(x: 1, y: 1)** because the center of the 2D image is taken to be the origin of the 2D co-ordinate system.

###### Gaze point with reference to the center of the image on the cue
![reading-relative-position](/docs/images/reading-relative-position.png)