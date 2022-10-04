# BlueSkyStatisticsV7
SPSS Equivalent for the Open Source R Project.
The code/Solution is organized into the multiple projects.

Follow the open source project plan and progress at https://www.blueskystatistics.com/category-s/113.htm
## Tool
The project has been developed using Visual Studio (VS).

## Framework
.NET Framework 4.8 is required.

## Project Setup
The 'Solution' is organized into 17 projects. BlueSky is the main startup project. To open the project in VS locate the ".sln' solution file for the main project and open it using VS. This solution file can be found in BlueSkyStatisticsV7\BlueSkyProject\libs\BlueSky\BlueSky.sln
Once the 'Solution' is loaded use NuGet Package Manager (NPM) to install dependencies for each of 17 projects. From VS go to
Tools > NuGet Package Manager > Manage NuGet Packages for Solution...

As soon as NPM window appears it may offer us a "Restore" button to restore the dependencies automatically. Click "Restore" and the NPM based dependencies will be resolved. Alternatively, you can resolve dependencies manually too. Each NuGet package (dependency) is required by one or more projects in the 'Solution'. Using the options provided in the NPM window you need to install dependencies in the projects where they are needed. See list below.

### NuGet Packages

#### Cquential.Microsoft.Practices.Unity (2.0.414)
Required by:
BlueSky, BSky.Controls,  BSky.Database.Interface, BSky.LifeTime, BSky.Output.Viewer, BSky.OutputGenerator, BSky.RecentFileHandler, Bsky.Service.StatisticsEngine, BSky.Statistics.Common, Bsky.Statistics.R

#### DynamicInterop (0.9.1)
Required by:
BlueSky, BSky.Database.Interface, BSky.LifeTime, Bsky.Service.StatisticsEngine, BSky.Statistics.Common, Bsky.Statistics.R

#### log4net (2.0.14)
Required by:
BlueSky, BSky.LifeTime

#### Microsoft.Office.Interop.Excel (15.0.4795.1001)
Required by:
MSExcelInterop

#### Microsoft.Office.Interop.Word (15.0.4797.1004)
Required by:
MSWordInteropLib

#### PDFsharp-MigraDoc-wpf (1.50.5147)
Required by:
BSky.ExportToPDF

#### PDFsharp-wpf (1.50.5147)
Required by:
BSky.ExportToPDF

#### R.NET (1.9.0)
Required by:
BlueSky, BSky.Database.Interface, BSky.LifeTime, Bsky.Service.StatisticsEngine, BSky.Statistics.Common, Bsky.Statistics.R

#### Scintilla.NET (5.1.5.4)
Required by:
BlueSky

#### SharpZipLib (1.3.3)
Required by:
BlueSky, BSky.Controls, BSky.Output.Viewer, BSky.OutputGenerator

### Other Requirements

#### ComponentOne WPF controls version 4.0.20162.524.
visit : [ComponentOne download](https://www.grapecity.com/componentone/download)
The download is a ComponentOne Control Panel app where you can select required components in install from web. From the list select 'WPF Edition' and select 2016v2(524) from the dropdown and proceed with installation.

Once ComponentOne is installed, it will be useful if you copy the required ComponentOne UI control DLLs to our 'Solution'. You don't need all UI controls. Create a new directory "ThirdParty" in the root of the 'Solution'. Create a sub-folder "C1" in the "ThirdParty" folder. Navigate to "C:\Program Files (x86)\ComponentOne\WPF Edition\bin\v4" and copy following DLLs to the "C1" folder.
C1.WPF.4.dll
C1.WPF.DataGrid.4.dll
C1.WPF.DataGrid.Filters.4.dll
C1.WPF.DataGrid.Summaries.4.dll
C1.WPF.DateTimeEditors.4.dll
C1.WPF.Docking.4.dll
C1.WPF.FlexGrid.4.dll
C1.WPF.FlexGridFilter.4.dll
C1.WPF.FlexSheet.4.dll
C1.WPF.Pdf.4.dll
C1.WPF.RichTextBox.4.dll
C1.WPF.RichTextBox.Toolbar.4.dll
C1.WPF.SpellChecker.4.dll
C1.WPF.Toolbar.4.dll
C1.WPF.Zip.4.dll

From Visual Studio, go to Solution Explorer and open each project node, navigate to "Reference" and fix the reference for ComponentOne DLLs by pointing to DLLs in "C1" folder (created above).

#### R and Required R packages

Install R-4.1.3 

Launch RGUI from installed R-4.1.3 and install all required R packages using the R script in the 'BSkyRpackage' folder in the root of the 'Solution'.

From RGUI also install BlueSky R package (BlueSky_7.96.zip) that is in the 'BSkyRpackage' folder in the root of the 'Solution'.

Execute .libPaths() command from RGUI console and save the results of this command as it may useful during troubleshooting.

## Building and Launching
To build the project/Solution from VS, right click on the BlueSky project from the Solution Explorer and select "Build".

Once you see build success message (in Visual Studio IDE) you can launch the application either by clicking the 'Start' button given in Visual Studio toolbar or you can also launch the application by double clicking the **BlueSky.exe** from the "BlueSkyProject/bin"

## Troubleshoot

### Build unsuccessful

If you see errors in VS during the build process, based on the error message go to Solution Explorer and navigate to 'References' for that particular project and see if all the dependencies are properly satisfied. Fix the NPM dependencies using NPM window or fix ComponentOne DLL references by checking if they are pointing to the right DLLs. Once the references are fixed "Build" again.

### R or required R packages not found

#### Setting rhome and userRlib
From Visual Studio's Solution Explorer, expand BlueSky project and locate app.config. Open this file in VS and set new values for **rhome** and **userRlib** keys. 
**rhome** should point to the installed R-4.1.3 root folder, see example below. If you have installed R in some other location use that path instead.
<add key="rhome" value="C:/Program Files/R/R-4.1.3"/>

**userRlib** should point to the location where all the required R packages has been installed (default is "Documents/R/win-lib/4.1" for R-4.1.3). You can run **.libPaths()** command from RGUI console to get the library locations and then check each location that has the required R packages. Use that path for **userRlib** value. see example below.
<add key="userRlib" value="C:/Users/USERNAME/Documents/R/win-library/4.1"/>

#### Clean temporary directory
visit: [our support page](https://www.blueskystatistics.com/category-s/115.htm) and find the technote **Cleaning BlueSky Statistics temporary directory and files.**

#### Rebuilding
Now, you need to rebuild the project (from VS Solution Explorer) by right clicking on BlueSky project and selecting "Rebuild" option.

