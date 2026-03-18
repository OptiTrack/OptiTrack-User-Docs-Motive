# Motive Batch Processor

The Motive Batch Processor is a separate stand-alone Windows application, built on the new NMotive scripting and programming API, that can be utilized to process a set of Motive Take files via IronPython or C# scripts. While the Batch Processor includes some example script files, it is primarily designed to utilize user-authored scripts.

Initial functionality includes scripting access to file I/O, reconstructions, high-level Take processing using many of Motive's existing editing tools, and data export. Upcoming versions will provide access to track, channel, and frame-level information, for creating cleanup and labeling tools based on individual marker reconstruction data.

Motive Batch Processor Scripts make use of the NMotive .NET class library, and you can also utilize the NMotive classes to write .NET programs and IronPython scripts that run outside of this application. The NMotive assembly is installed in the Global Assembly Cache and also located in the `assemblies` sub-directory of the Motive install directory. For example, the default location for the assembly included in the 64-bit Motive installer is:

**C:\Program Files\OptiTrack\Motive\assemblies\x64**

The full source code for the Motive Batch Processor is also installed with Motive, at:

**C:\Program Files\OptiTrack\Motive\MotiveBatchProcessor\src**

\
You are welcome to use the source code as a starting point to build your own applications on the NMotive framework.

![](<../.gitbook/assets/image (454).png>)

## Use

**Requirements**

* A batch processor script using the NMotive API. (C# or IronPython)
* _Take_ files that will be processed.

**Steps**

1. Launch the Motive Batch Processor. It can be launched from either the start menu, Motive install directory, or from the [Data pane](../motive-ui-panes/data-pane.md) in Motive.
2. First, select and load a Batch Processor Script. Sample scripts for various pipelines can be found in the `[Motive Directory]\MotiveBatchProcessor\ExampleScripts\` folder.
3. Load the captured _Takes (TAK)_ that will be processed using the imported scripts.
4. Click _Process Takes_ to batch process the _Take_ files.

**Reconstruction Pipeline**

When running the reconstruction pipeline in the batch processor, the reconstruction settings must be loaded using the _ImportMotiveProfile_ method. From Motive, export out the [user profile](motive-basics.md#motive-user-profile-.motive) and make sure it includes the reconstruction settings. Then, import this user profile file into the Batch Processor script before running the reconstruction, or trajectorizer, pipeline so that proper settings can be used for reconstructing the 3D data. For more information, refer to the sample scripts located in the _TakeManipulation_ folder.

![](<../.gitbook/assets/image (409).png>)

## Class Reference

A class reference in Microsoft compiled HTML (.chm) format can be found in the `Help` sub-directory of the Motive install directory. The default location for the help file (in the 64-bit Motive installer) is:

**C:\Program Files\OptiTrack\Motive\Help\NMotiveAPI.chm**

![](<../.gitbook/assets/image (346).png>)

## C# Scripts

The Motive Batch Processor can run C# and IronPython scripts. Below is an overview of the C# script format, as well as an example script.

### C# Script Format

A valid Batch Processor C# script file must contain a single class implementing the `ItakeProcessingScript` interface. This interface defines a single function:

`Result ProcessTake( Take t, ProgressIndicator progress )`.

`Result, Take, and ProgressIndicator` are all classes defined in the `NMotive` namespace. The Take object `t` is an instance of the NMotive `Take` class. It is the take being processed. The `progress` object is an instance of the NMotive `ProgressIndicator` and allows the script to update the Batch Processor UI with progress and messages. The general format of a Batch Processor C# script is:

```
   using NMotive;
   // any other using statements
   public class MyCSharpScript : ITakeProcessingScript
   {
      public Result ProcessTake(Take t, ProgressIndicator progress)
      {
         Result scriptResult;
         // Script processing code here
         progress.SetMessage(“Done processing take “ + t.Name);
         progress.SetProgress( 100 );
         return scriptResult;
      }
   }
```

### C# Example

In the `[Motive Directory]\MotiveBatchProcessor\ExampleScripts\` folder, there are multiple C# (.cs) sample scripts that demonstrate the use of the NMotive for processing various different pipelines including tracking data export and other post-processing tools. Note that your C# script file must have a '.cs' extension.

Included sample script pipelines:

* ExporterScript - BVH, C3D, CSV, FBXAscii, FBXBinary, TRC
* TakeManipulation - AddMarker, DisableAssets, GapFill, MarkerFilterSCript, ReconstructAutoLabel, RemoveUnlabeledMarkers, RenameAsset

<details>

<summary><strong>Batch Processor Script C# Sample (ExporterScript-C3D.cs): Exporting a take to C3D format.</strong></summary>

```
 using System;
 using System.IO;
 using NMotive;
 
 /// <summary>
 /// Motive Batch Processor script for exporting a take file to C3D format.
 /// </summary>
 public class C3DExportScript : ITakeProcessingScript
 {
     /// <summary>
     /// The <c>ProcessTake</c> function is from the <c>ITakeProcessingScript</c> interface.
     /// Exports the given take to C3D format. The exported file is in the same 
     /// directory as the take file, and has the same name, but with a '.c3d' file extension.
     /// </summary>
     /// <param name="take">The take to export.</param>
     /// <param name="progress">Progress indicator object.</param>
     /// <returns>The result of the export process.</returns>
 	public Result ProcessTake(Take take, ProgressIndicator progress)
 	{
         // Construct an NMotive C3D exporter object with the desired
         // options. We will write C3D data for markers and assets.
         C3DExporter exporter = new C3DExporter
         {
 			//-== C3DExporter Class ==-
          		ColonNameSeparator = false,
 			RenameUnlabeledMarkers = false,
 			Units = LengthUnits.Units_Centimeters,
 			UseTimeCode = true,
 			UseZeroBasedFrameIndex = true,
 			WriteFingerTipMarkers = false,
 			WriteUnlabeledMarkers = false,
 			XAxis = Axis.Axis_NegativeX,		// Axis_PositiveX, Axis_NegativeX
 			YAxis = Axis.Axis_PositiveZ,		// Axis_PositiveY, Axis_NegativeY
 			ZAxis = Axis.Axis_PositiveY		// Axis_PositiveZ, Axis_NegativeZ
 			
         };
         
         // Construct the output C3D file. The output file will be co-located with the
         // take file and have the same name as the take file, but with a '.c3d' extension.
 		string outputFileName = Path.GetFileNameWithoutExtension(take.FileName) + ".c3d";
 		string outputDirectory = Path.GetDirectoryName(take.FileName);
 		string outputFile = Path.Combine(outputDirectory, outputFileName);
 
         // Do the export and return the Export functions result object.
 		progress.SetMessage("Writing to File");
 		progress.SetProgress( (float)0.1 );
 		return exporter.Export(take, outputFile, true);
 	}
 }
```

</details>

## IronPython Scripts

[IronPython](http://ironpython.net/) is an implementation of the Python programming language that can use the .NET libraries and Python libraries. The batch processor can execute valid IronPython scripts in addition to C# scripts.

### IronPython Script Format

Your IronPython script file must import the clr module and reference the NMotive assembly. In addition, it must contain the following function:

`def ProcessTake(Take t, ProgressIndicator progress)`

The following illustrates a typical IronPython script format.

```
   #import sys and clr modules
   import sys
   import clr

   # Add a reference to the NMotive assembly
   clr.AddReference("NMotive")
   # Import everything from sys and NMotive.
   from System import *
   from NMotive import *

   # Define the ProcessTake function.
   def ProcessTake(take, progress):
      # Take processing code here
      .
      .
      .
      # return result object
```

### IronPython Script Example

In the `[Motive Directory]\MotiveBatchProcessor\ExampleScripts\` folder, there are sample scripts that demonstrate the use of the NMotive for processing various different pipelines including tracking data export and other post-processing tools. Note that your IronPython script file must have a '.cs' extension.

<details>

<summary><strong>Batch Processor Script IronPython Sample (TrimAndFilter.py):</strong></summary>

The following script performs a trim tails operation followed by a filtering/smoothing operation. If both operations succeed, the resulting take is saved.

```
 import sys
 import clr
 
 
 # Add a reference to the NMotive assembly
 clr.AddReference("NMotive")
 
 from System import *
 # Import everything from NMotive.
 from NMotive import *
 
 
 def ProcessTake(take, progress):
    # Set the message to be displayed next to to the progress bar in the 
    # Motive Batch Processor UI. 
    progress.SetMessage('Triming tails...')

    # Create an NMotive TrimTails object to perform the tail trimming operation.
    tailTrimming = TrimTails()

    # pass the progress object to the trim tails object. It will update 
    # progress that will be rendered in the UI.
    tailTrimming.Progress = progress

    # Set trail trimming options.
    tailTrimming.Automatic = True
    tailTrimming.LeadingTrimSize = 4
    tailTrimming.TrailingTrimSize = 4

    # And execute the trimming process.
    trimResult = tailTrimming.Process(take)

    # If trimming failed for some reason the Success field of the returned
    # NMotive Result object will be false and the Message field will contain
    # information about the failure. The Message field of the returned Result
    # object will be displayed in the UI. 
    if not trimResult.Success: # If trimming failed, return without saving the take.
       return trimResult
   
    # Starting the filtering process...
    progress.SetMessage('Filtering...')

    # Create the NMotive filter object.
    filtering = Filter()

    # We are going to use the progress bar to display the progress of each 
    # individual operation, so reset the progress bar to zero and pass the
    # the progress object to the filtering object.
    progress.SetProgress(0)
    filtering.Progress = progress

    # Set the cutoff frequency and filter.
    filtering.CutOffFrequency = 8 # Hz
    filteringResult = filtering.Process(take)
    if not filteringResult.Success: # If filtering failed, return without saving the take.
    	return filteringResult
 
    # If we get here trimming and filtering succeeded. Save the take file.
    progress.SetMessage('Saving take...')
    fileSaveResult = take.Save()
    if fileSaveResult != FileResult.ResultOK:
    	return Result(False, 'File save failed')
    
    return Result(True, '')
```

</details>
