# SaveOpenFiles_asTIFF - FIJI (ImageJ) Macro

This FIJI (ImageJ) macro script automates the process of saving all currently open image windows as individual TIFF files in a user-specified directory.

## Features

Automatically saves all open images in the FIJI/ImageJ window as .tiff files.
Prompts the user to choose a destination folder.
Maintains the original image window title as the filename.
Closes all images after saving is complete.

## Requirements

FIJI / ImageJ must be installed.
Script is written in the ImageJ macro language (.ijm).

## Installation

Open FIJI.
Go to Plugins > Macros > Edit....
Paste the contents of SaveOpenFiles_asTIFF.ijm into the editor.
Save the macro in your FIJI macros folder or run it directly.

## Usage

Open multiple images in FIJI.
Run the macro.
Select the target folder when prompted.
The macro will:
Loop through all open images.
Save each image as a TIFF file in the selected directory.
Close all open images.

## Macro Code

    // SaveOpenFiles_asTIFF
    // This ImageJ macro saves all open images as TIFF files
    // and saves to a selected directory
    
    dir = getDirectory("Choose a Directory");  // Prompt the user to select a folder and store the path in the     variable 'dir'

    for (i=0; i<nImages; i++) {  // Loop through all open images (nImages is the number of currently open images)

        selectImage(i + 1);  // Select the (i+1)th image (ImageJ uses 1-based indexing)

        title = getTitle;  // Get the title (filename) of the currently selected image

        print(title);  // Print the image title to the log window for tracking

        // ids[i] = getImageID;  // (Commented out) This would store each image’s unique ID if needed

        saveAs("tiff", dir + title);  // Save the current image as a TIFF file in the chosen directory with its     title as the filename
    } 

    run("Close All");  // Close all open images after saving is complete

## License

This project is open source and available under the MIT License.
