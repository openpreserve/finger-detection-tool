finger-detection-tool
==========================

*The finger on scans detection tool*

Installation Guide
------------------

### Requirements

To install you need:

* Java 7.0
* OpenImaj library v.1.0.5
* Maven 2.0
* Git
* Eclipse (Version: Kepler Service Release 1) can support you by project configuration

### Download

| Version | Size   | SHA1                                                    |                      |
|---------|--------|---------------------------------------------------------|----------------------|
| v1.0    | 23.6 MB| <small>1b34d11f66fe4b847f271a5aaaabb02c7917690c</small> |[download](https://github.com/openplanets/fingerdet/archive/master.zip)            |

### Installing Fingerdet

#### Use Eclipse to create Java Maven project from github sources.
1. Check out project sources from github e.g. using TortoiseGit
2. Build Maven project using Ecliplse menu: File -> Import -> Maven -> Existing Maven Projects

#### Use Eclipse to create runnable JAR file. 

1. First compile your project
2. Right click on your PROJECT -> Export -> Java -> Runnable jar
3. You will get a Dialog box, there select the class name (ait.FingerDetection)
4. Give the export destination (not in the project root - somewhere else)
5. In library handling(radio button): select your desired option(all are self descriptive)
6. In the destination directory create folder 'samples' and put there files intended for analysis
7. Start application by double click on the created JAR file.

Using Fingerdet
--------------

1. Execute in Eclipse the main Java class 'FinderDetection' (right mouse click on this java file in project explorer and run as java application) 
2. or use runnable JAR with associated 'samples' folder that should contain digital collection for analysis

The folder 'samples' in all cases should be in root directory.

### Basic Workflows

#### Finger Detection

The finger detection algorithm is summarized as follows:
1. The workflow starts with loading of data from given file.
2. Since the point- and edge-based features are regarded to be robust against lighting variants, the Canny edge 
detection algorithm is employed in order to retrieve edges of a RGB image. Additionally at this stage we flatten 
the bands of the original image, using the average value of the pixels at each location, in order to obtain a new 
single-band image.
3. We filter the flattened single-band image pixels by applying a threshold parameter P for pixel value, where P is 
a coefficient with value in the range from 0.0 to 1.0.
4. We analyze a given scan image in order to detect finger candidates with associated pixel coordinates. To do so we 
evaluate the next existing pixel on the right from the given position on the X axis and examine its coordinates regarding
association with current finger candidate.
5. Given a preliminary finger candidates list, we apply the parameters evaluated from expert knowledge like finger size,
points count, variance and distance to border to evaluate the extent to which the candidate matches the requirements.
6. In the final step we draw green rectangle around the detected finger areas and display the resulting image for user reasoning.

Command line use
----------------

### Sample usage

	FingerDetection.jar

### Output of finger on scans detection script is a list of possible candidates 

E.g. collection contains 5 documents. The document 00000004.jpg has no fingers, remaining scans comprise fingers.
Additionally the results of analysis are presented in finger candidate images where suspected areas are marked by 
green rectangles. Associated image with detected edges is also presented in a greyscale form. Calculation time is 
given in milliseconds.
In this way the user is able to draw a conclusion as to whether a finger candidate image is actually a finger.

*********************************************
            FIND FINGERS ON SCANS            
*********************************************

********* Collection *****************

00000001.jpg
00000002.jpg
00000003.jpg
00000004.jpg
00000005.jpg
query collection image i: 0
2 finger in current scan detected! 
query collection image i: 1
1 finger in current scan detected! 
query collection image i: 2
1 finger in current scan detected! 
query collection image i: 3
query collection image i: 4
2 finger in current scan detected! 
calculation time: 3500
finger list size: 4 of total 5 files

## Features and roadmap

### Version 1.0

* Finger on scan detection in a digital document collection



