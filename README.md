This is where I tinker with Rye (https://ryelang.org)

weather.rye is my first attempt to use Rye for an actually useful application. It will get it's own repository at some point (I'm still learning git).
The objective here is to pull Environment Canada daily weather data for particular weather stations. My original use, which I'm going to attempt to duplicate once I have the basic retreival working the way I want, was to help make a decision regarding the installation of a heat pump.

As it stands right now, all I do is retrieve the list of weather stations and the daily data for the selected station.

Tested on Linux (Ubuntu 20.04) with Rye version 0.0.96

There is no error handling at all, yet, so invalid selections will crash or fail in sometimes obsure ways.

On first run, it will retrieve the list of weather stations. On subsequent runs, it will ask whether to update any existing list.

You will be prompted for a station name. This will usually be a city, town, or village. That name will be used to filter the station list so that you can pick the exact station you want to use. Not finding a station name should be pretty rare. In the event that happens, either enter just the first few characters to get a partial match or go to https://weather.gc.ca/canada_e.html to find your station.

Once you select the station you want, you will be prompted to select the range of years you are interested in from a "First Year" list and a "Last Year" list. Only valid years will be presented. Use some caution as a large range can run to several MB of data (about .67 MB per decade).

On completion, you will be shown the name and location of the generated file.

Enjoy!

**NOTE:** I have started a major rewrite of what I've got so far to dramatically simplify the code.

Environment Canada provides two main CSV files:
* A static file with the list of all the weather stations and basic information associated with those stations.
* An on-demand file, generated based on the parameters provided to them. This file contains the actual weather data for the desired station.

The files have different structures:
* The static station list has descriptive text before the actual data begins. This confuses (ie crashes) my program, so I do some preprocessing to get it into shape.
* The dynamic station data has something in the use of quotation marks that crashes my program, so I do some preprocessing to get it into shape.

If that was all, there would be no problem. But there are a variety of other differences that complicate the preprocessing.

This has complicated the function I use for retrieving data to the point that it has six parameters and is in need of more. In other words, it's looking more and more like a fully generic CSV processing function. That is niether desirable nor even really feasible given all the variety of CSV structures in the wild. I don't care about the general case, only the specific cases of the Environment Canada structures. Therefore, I'm trashing that generic function in favour of two highly-targeted ones. And since I'll only ever deal with those two structures, it may even be reasonable to just do everything in line without creating new functions.

Stay tuned!
