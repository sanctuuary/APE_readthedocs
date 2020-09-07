# APE Tutorial (using [ImageMagic](https://imagemagick.org/index.php) tools)


## Run APE from the command line
In order to use the APE library from the command line, simply run the `APE-<version>-executable.jar` file using command:


    java -jar APE-<version>-executable.jar [path_to_ape_configuration_file]
    

As an example, if you would download the [APE-1.0.1-executable.jar](https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar) to the root of APE_UseCases repository on your local machine, you could run this demo by executing the following command:


    cd ~/git/APE_UseCases
    
    java -jar APE-1.0.1-executable.jar ImageMagick/Example1/config.json

The results of the synthesis would be:

	ImageMagick/Example1/sat_solutions.txt	-	First 100 candidate solutions in textual format
	ImageMagick/Example1/Workflows/		-	Data-flow figures corresponding to the first solution (config.json specifies that only 1 solution should be found)
	ImageMagick/Example1/Implementations/	-	Executable shell scripts corresponding to the first solution




### Examples
The run of the synthesis is explained on the following two examples:
- [Example 1: Creating a postcard](Example1)
- [Example 2: Repacing a color](Example2)
