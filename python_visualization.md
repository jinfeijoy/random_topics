# Python Visualization Tools

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |


|Serial No.|	Package	|Plots |used in this kernel	|Remark	|Nature of plots|
| -------- |:--------:|:----:|:------------------:|:-----:|:-------------:|
|1	|Matplotlib	|1. vendor_id histogram, 2. store and fwd flag histogram	|Matplotlib is oldest and most widely used python visualization package, its a decade old but still its the first name come to our mind when it comes to plotting. Many libraries are built on top of it, and uses its functions in the backend. Its style is very simple and that's the reason plotting is fast in this. It is used to create axis and design the layout for plotting using other libraries like seaborn.||
|2	|Seaborn	|1.Violin plot (passenger count vs trip duration), 2. Boxplots( Weekday vs trip duration, 3. tsplot (hours, weekday vs avg trip duration), 4. distplots of lat-long, and trip_duration	|Seaborn is my favorite plotting library (Not at all a fan of house greyjoy though :P) Plots from this package are soothing to eyes. Its build as a wrapper on matplotlib and many matplotlib's functions are also work with it.colors are amazing in this package's plots||
|3	|Pandas	|1. Parallel coordinates (for cluster characteristics)	|Pandas also offer many plotting functions and it's also a package built on matplotlib, so you need to know matplotlib to tweak the defaults of pandas. It offers Alluvial plots (which are nowhere near what R offers as alluvial plots) which are used in this notebook to show cluster characteristics.||
|4	|Bokeh	|1. Time series plot (day of the year vs avg trip duration)	|Bokeh is one great package which offers interactive plots, you can use bokeh with other libraries like seaborn, data-shader or holoviews, but bokeh its offers various different kind of plots. zoom, axis, and interactive legends makes bokeh different than others	|Interactive|
|5	|Folium	|1.pickup locations in Manhattan, 2. cluster's location in the USA, 3. clusters location in Manhattan	This package offers geographical-maps and that too are interactive in nature. |This package offers a different kind of terrains for maps- stemmer terrain, open street maps to name a few. you can place bubble at the locations, shift the zoom, and scroll the plot left-right-up-down and add interactions, for example - cluster plots shown in this notebook offers information about clusters like number of vehicles going out, most frequently visited clusters etc. kaggle started supporting this package during this competition only	|interactive|
|6	|Pygmaps	|1. location visualizations 2. cluster visualizations	|Pygmaps is available as archive package and can't even be installed using pip install command, but this package was the predecessor of gamps package but offers few great interactions which even gmaps doesn't offer. for example, a scattering of a cluster can be plotting with this one better than with gmaps. This package was way underdeveloped and developed version of it is know as gmaps yet, it was able to generate beautiful vizs. plots made my this package are best viewed in browsers.	|interactive|
|7	|Plotly	|1.bubble plot	|This is another great package which offers colorful visualizations, but some of these beautiful plots require to interact with plotly server so you need API key and it will call the API.	|interactive|
|8	|Gmaps	|To be updated	|gmaps provide great features like- route features, and we all are too used to gmaps, so feel like home.	|interactive|
|9	|Ggplot2	|1. Weather plots of NYC for given period	|gglots are now available in python as well, and its kind of in developing state and documentation is less of this package which makes it a little difficult but at the same time it provides very beautiful plots, so there is a tradeoff ;)	|interactive|
|10	|Basemaps	|Will not be added in this kernel	|As long as you are not developing any maps related library, there are no benefits of using basemaps. They offer many options but using them is difficult, due to lots of arguments, different style, and less amount of documentation, and many lines of codes sometimes will be required to plot a map.||
|11	|No package	|1. heatmaps of NYC taxi traffic	|Instead of depending on data-shadder, I tried plotting the heatmap of traffic data with a row image, you will get to know the basics of image processing( reading image, color schemes that's all :P ) and how such basic exercise can result in traffic heatmap||
|12	|Datashader	|1.locations' heatmap	|If you really have a very large size of data that you want to plot on a map, data shader is one of the best easiest option available in marker. But I found that row image processing and generating plots using a scipy.mics or cv2 is considerably faster than using this package.	|interactive|
|13	|Holoviews	|1. Pairplot for feature interaction.	|Holoviews is another alternative for making interactive visualizations, this package offers artistic plots. But you need really good RAM etc to use this package, else the notebook will get hang. plots exported to HTML works perfectly fine	|interactive|

## Reference
* []()
* []()