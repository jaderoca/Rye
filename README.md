This is where I tinker with Rye (https://ryelang.org)

test.rye is where I just try stuff. I'll be mostly commenting out stuff that I got working well enough to start actually using it. I do this to keep it around for my own reference even as I move on to other things.

weather.rye is my first attempt to use Rye for an actually useful application. It will get it's own repository at some point (I'm still learning git).
The objective here is to pull Environment Canada daily weather data for particular weather stations. My original use, which I'm going to attempt to duplicate once I have the basic retreival working the way I want, was to help make a decision regarding the installation of a heat pump.

As it stands right now, all I do is retrieve the list of weather stations and the daily data for the selected station.

Tested on Linux (Ubuntu 20.04) with Rye version 0.0.94

There is no error handling at all, yet, so invalid selections will crash or fail in sometimes obsure ways.

On first run, it will retrieve the list of weather stations. On subsequent runs, it will ask whether to update any existing list.

You will be prompted for a station name. This will usually be a city, town, or village. That name will be used to filter the station list so that you can pick the exact station you want to use.

Once you select the station you want, you will be prompted to select the range of years you are interested in from a "First Year" list and a "Last Year" list. Only valid years will be presented. Use some caution as a large range can run to several MB of data (about .67 MB per decade).

On completion, you will be shown the name and location of the generated file.

Enjoy!
