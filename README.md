Structures to generate Vizceral format output from Go
=====================================================

The NetflixOSS Vizceral example project is here: https://github.com/Netflix/vizceral-example

It uses a json format file to drive the display, and contains both a default and a simple format example.

The format is defined here:
https://github.com/Netflix/vizceral/blob/master/DATAFORMATS.md

The examples were copied into this project and had to be modified as described in https://github.com/Netflix/vizceral-example/issues/6
I ran into an issue where "metadata" is sometimes "streaming": true, and sometimes "streaming": 1 in the main example file, which causes an error when marshal/unmarshal from go. I edited a copy of the example files to use "streaming": 1 everywhere and pretty-printed the main example into a more readable format (using python -m json.tool)
This issue has now been fixed to make the files consistent with "streaming": 1.

The top level package contains go structure definitions and code to marshal and unmarshal the example files, along with a test that exercises the code.

The vizceralSpigo sub-package contains code that reads/writes vizceral format files and Spigo architecture format

The vizceral2arch sub-package contains a standalone program that converts files using vizceralSpigo

The arch2vizceral sub-package contains a standalone program that converts Spigo format arch files to vizceral

To view the output, copy the json result files from arch2vizceral to a copy of vizceral-example/src/sample_data.json and rerun npm run dev to load the new configuration.

![test](test_spigo_vizceral_regions.png)

![test](test_spigo_vizceral.png)
