# ImCo is IMage COder

A Python Tkinter application for coding _lots_ of images.

ImCo ("IMage COder") is a Python-based application for efficiently annotating image directories with pre-defined, categorical values. The app as provided is set up for annotating child-centric daylong photo streams but the input values can of course be edited to your custom needs.

## Setup

You can run the application by double-clicking on `app.py` in the `imco` directory. You may first need to make the file executable on your machine with Python 3. When ImCo first runs, you'll need to open a directory that contains a configuration file and images to code, the imco working directory. This is where the application expects to find the images that you want to code, and it's also where it will save its state for those particular images.

The structure of the working directory is as follows:

- `config.json` (sets a number of options for how to code the images)
- `images` (a directory of directories, each one containing images to code)
  - `P1-39moM` (a directory of images for one participant)
  - `P1-7moF` (another participant)
  - ...
- `state.db` (auto-generated database containing application state; not present unless you have opened the working directory already)

This repository contains an example working directory `workdir` that is already set up with the files you need to initiate a new round of annotation. You only need to copy directories of images corresponding to individual participants into the provided `images` directory in that example working directory, and also delete the example participant directories. Once that's done, you can launch the application, select this working directory, and start coding. When you do, it will create the `state.db` file that stores your annotations and your current progress in the working directory. If you make a mistake selecting images or you want to start from a clean slate for some other reason, delete `state.db`, but keep in mind that this action will cause you to lose any coding work you've already done. If you are done annotating the files in your working directory, please see the instructions below on converting your .db file to a .csv for further analysis. If, at this point, you would like to re-use the working directory with new files, you can save your completed .db file elsewhere, then delete `state.db` and the old images from the `workdir` folder, adding in your new images. Once you launch the app again and select the working directory, a fresh `state.db` file will appear to store your new annotations.

Please note that the application will save automatically as you annotate images, but we recommend that you periodically export your working database file to a csv file, just in case something goes wrong (see how to do this using the instructions below).

Please also note that you can add the annotator's name for a work directory in the `config.json` file. The default value is set to "Annotator".

## Converting .db files to .csv

First, ensure that you make `convert-dbs.sh` executable on your machine. 
 ...

## Navigation

ImCo is set up for quick annotation and navigation via hotkeys—single keystrokes that enable the annotator to enter data and move between photos.

For each annotation category, there should be a unique initial keystroke value (e.g., "A" to enter the number of visible adults) which can then optionally lead to a more refined annotation value (e.g., the numbers 0-9; see below for examples via the default annotation types).

To navigate through the images use the following keystrokes:

* Previous image: left arrow
* Next image: right arrow OR enter
* Last coded image: ctrl + right arrow

## Customizing annotation types

You may customize the annotation types accepted by ImCo by editing the `config.json` file. Note that your initial keystroke values must be unique across your annotation categories (e.g., we can't use 'c' for both 'Kids/Children' and 'Crying' in the example below). Within annotation categories, value keystroke options must also be unique (e.g., we can't use 'o' for both 'Dark/Obscured' and 'Other' in the Unusable annotation category).

## Default annotation types

The default annotation categories are set to be used as follows:

| Annotation category | Initial keystroke | Value keystroke options | Value meaning |
|---|---|---|---|
| Adults | a | 0–9 | The number of people who look to be of child-bearing age or older in the photo, not including the person wearing the camera. More than 9 can be marked with “9”. | 
| Kids | k | 0–9 | The number of people who look to be below child-bearing age in the photo, not including the person wearing the camera. More than 9 can be marked with “9”. |
| Hands | h | C, I, B, N | **C = the target child** is holding/handling something or appears to be mid-activity with a held object/person. **I = one or more of the child’s interactants** is holding/handling something in a way immediately relevant to the target child (e.g., handing them something, cleaning their face). **B = both the target child and one or more of their interactants** are holding/handling something, as defined above. **N = there is no holding/handling behavior.** |
| Crying | c | N/A | Set to no by default. Use of this flag by the annotator indicates that any child in the photo is crying. |
| Breastfeeding | b | N/A | Set to no by default. Use of this flag by the annotator indicates that any child in the photo is being breastfed. |
| Flagged | f | N/A | Set to no by default. Use of this flag by the annotator indicates that the photo is interesting for some reason and we should come back to it later; please make a separate note with the participant and photo number for photos with specific comments. | 
| Unusable | u | D, C, O |  Set to no by default. Otherwise: D = the photo is too dark or too light to see anything. C = the camera cover is on. O = other cases, including the photos at the beginning and the end when the researchers are still present. **NOTE: If you mark a photo as unusable, you do not have to fill in any of the other codes.** |
| Skipped | s | N/A | Set to no by default. Use if you would like to skip this photo, leaving all the other code fields blank. |

These annotation types were designed for an ongoing project. The repository for that project, including original instructions is available here [repository: ADD-LINK; original [annotation table](https://docs.google.com/document/d/1aQlpB9N8LVAfzuac_XqZzhWiKQ6AptsDzHxLDKrJAOA/edit?usp=sharing) and [training tips](https://docs.google.com/document/d/1pbTZkqBBTE_aFawVr5daiIKrKVc1kdvi8lX65cwpn3A/edit?usp=sharing)]. We encourage you to adapt these annotations as needed for your project, though we note that re-use of categories where relevant increases comparability across studies.

## Attribution

If you use ImCo, please cite one of the following:
[ADD CITATION]
