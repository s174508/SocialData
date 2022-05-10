---
title: " "
featured_image: '/images/denmark_figures-1.png'
---

<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<p align="center" style="font-size:60px"> <b>Wind turbines – not in my backyard!</b> </p>

*By: Andreas Ammitzbøll, Mads Westermann, Rikke Rasmussen. Date: 10/05/2022*

North Sealand is home to some of the wealthiest people in Denmark, including presidents of wind turbine companies and ministers who promote wind energy. Meanwhile, North Sealand is the only area in the country with almost no wind turbines. Though these powerful people advocate for more wind energy, they themselves get to live at a comfortable distance from the turbines while the rest of the Danish population has to live with the sight and the noise of these monstrosities.

This is the message put forth in an article by Ekstra Bladet [[1]](https://ekstrabladet.dk/nyheder/samfund/article4813498.ece), claiming that the placement of turbines is unfair to the advantage of the richest people. In a contribution to the debate by Information [[2]](https://www.information.dk/debat/2022/03/placeringen-vindmoeller-klassekamp-fattige-udkant-ved-tabe), the writer perceives the placement of turbines as a class struggle which the poor people in the countryside are losing.

The whole discussion sounds like an example of the phenomenon NIMBY [[3]](https://en.wikipedia.org/wiki/NIMBY) – “not in my backyard”: Most people have a positive attitude towards wind energy in general, but do not want the turbines close to themselves. The transition to green energy is highly important today, and it only seems fair that every part of the country takes their part of the responsibility.

But is the media right to criticize the wealthy parts of Denmark for not having enough turbines? Or are there other factors that could influence the placement of turbines? We are now going to investigate these questions in more depth.


# Where are the wind turbines located?

Let’s start out by taking a look at the locations of the wind turbines in Denmark.

The Danish Energy Agency (Energistyrelsen) published a dataset containing all the wind turbines which contribute to (or have earlier contributed to) the Danish electrical power grid [[5]](https://ens.dk/service/statistik-data-noegletal-og-kort/data-oversigt-over-energisektoren). The data features the GPS coordinates of each individual turbine, along with information about its size, model, kW-capacity, municipality, and other things. Since we are focusing on the turbines in each municipality, we will only consider turbines within the municipal borders, which means that we will disregard the turbines at sea. There are also a portion of low capacity turbines (less than 30 kW) that are missing coordinates and/or municipality information, that we have also excluded.

If we want to fact-check the article by Ekstra Bladet, we need some data describing the wealthiness of each municipality. For this purpose, we collected a dataset from Statistics Denmark (Danmarks Statistik) [[6]](https://www.statistikbanken.dk/INDKP105) with the average income in each municipality in 2020, the most recent year available. Additionally information.dk provides a geojson file containing the borders of all Danish municipalities, which allows us to show the municipalities and their values on a map [[7]](https://lab.information.dk/):

*The turbine locations are shown in the map below. If you click the button in the upper right corner, you can additionally choose to see the municipalities colored after average income. In the upper left corner you can zoom in and out, or double click on the map to zoom in.*

<p align="center">
<iframe src="/SocialData/html/map_loc_inc_hacked.html"
	sandbox="allow-same-origin allow-scripts"
	width="1000"
	height="700"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>
<p>

North Sealand does indeed seem very bare compared to the rest of Denmark, and the colored map shows that North Sealand contains the wealthiest municipalities in Denmark. Let’s explore if there is a trend for all municipalities of Denmark.


# Is there a relationship between wealth and the amount of wind turbines?

To investigate if there is a relationship, one option would be to simply plot the number of turbines against the average income in each municipality. However, the turbines are not identical. The boxplot below shows the distribution of kW-capacities of all the turbines. They range all the way from 10 kW to 10000 kW, with the vast majority being below 2000 kW. High-capacity turbines have the ability to produce much more electricity than the small ones, so we will focus on the capacity of turbines rather than the number of them.

{{< figure src="/SocialData/images/boxplot_kW.png" >}}

Additionally the Danish municipalities vary a lot in size, so it seems unfair to simply use the total kW-capacity of wind turbines in each municipality. We will attempt to take this difference into account by computing the **capacity per square kilometer** for each municipality:

$$kW\\_per\\_km2 = \\frac{sum\\_of\\_kW\\_capacities}{area\\_of\\_municipality}$$

*The figure below shows the kW per km2 plotted against the average income in each municipality. You can hover the cursor over each point in the plot to see which municipality it is.*

<p align="center">
<iframe src="/SocialData/html/scatter_inc.html"
	sandbox="allow-same-origin allow-scripts"
	width="410"
	height="410"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>
</p>

At first glance it looks like there could be somewhat of a relationship between capacity per km2 and average income, though it is not a linear relationship. However, only a few municipalities have an average income above 40,000 kr. It turns out that the 10 municipalities with an average income above 41,000 can be considered statistical outliers, which is shown as the 10 dots in the boxplot below. If we momentarily disregard the 10 richest municipalities, there seems to be no relationship between the two variables for the rest of the municipalities. So we cannot say that there is a relationship in general between wealthiness and lack of wind turbines. Still, the claim that the very richest municipalities have no turbines is correct. The allegation from Ekstra Bladet is that these municipalities are selfish and not willing to take part in the responsibility. But we would like to investigate other possible explanations, since there could be other factors contributing to the placement of wind turbines than just the average income.

{{< figure src="/SocialData/images/boxplot_inc.png" >}}

# Other relevant factors for the placement of turbines

When looking for an explanation for the distribution of wind turbines, several things could be relevant to investigate. Factors like the population density or amount of suitable area naturally limits the amount of spots where wind turbines can be placed, and locations with high wind speeds are more attractive for wind turbines than locations without much wind.

## Suitable areas

It can be difficult to determine which locations would be suitable for wind turbine placement, but the main restriction for new turbines is that the distance to the closest residential buildings must be at least 4 times the height of the turbine [[8]](https://www.retsinformation.dk/eli/lta/2019/923). Protected areas are naturally also out of the question. We don’t have any raw data on these restrictions, but the Danish Business Authority (Erhvervsstyrelsen) provides a map tool that can display these things and more [[9]](https://kort.erst.dk/spatialmap?profile=vindmoeller).

The best we can do in our investigation here is make a crude estimate based on the terrain of each municipality. Another data set from Statistics Denmark [[10]](https://www.statistikbanken.dk/statbank5a/SelectVarVal/Define.asp?MainTable=AREALDK) defines a set of terrain types and indicates how large a percentage of each municipality’s area belongs to each terrain type. The set of terrain types is not particularly detailed, but detailed enough to make a rough split between suitable and unsuitable area (disregarding aforementioned laws):

Suitable:
- Agriculture such as crops, bushes and permanent grass
- Heaths, dunes and other dry nature

Unsuitable:
- Roads
- Buildings and area just around buildings
- Mining areas
- Parks and sports facilities
- Forests
- Wet nature such as lakes, marsh and meadows
- Unclassified area (the municipalities have up to 7% unclassified area)

## Population density

Population density is another way to estimate how much area is suited for wind turbines. The more dense with people the municipality is, the less spots are available for turbines due to the distance requirements. We have calculated the number of citizens per km2 for each municipality from this data set from Statistics Denmark [[11]](https://www.statistikbanken.dk/FOLK1A) along with the area dataset we used earlier [[10]](https://www.statistikbanken.dk/statbank5a/SelectVarVal/Define.asp?MainTable=AREALDK) (but this time using the total area in km2).

## Average wind speed

It is not equally windy everywhere in Denmark. Areas close to the sea have stronger winds, especially the Western coast of Jutland. It seems reasonable to place more turbines in windy areas, where they can utilize as much wind energy as possible. To give you an idea of the wind differences, the figure below is a wind resource map from the Danish Business Authority of Denmark, showing the average wind speed (m/s) at a height of 100 m [[12]](https://planinfo.erhvervsstyrelsen.dk/sites/default/files/vindres_100mean_a4_1_0.png).

{{< figure src="/SocialData/images/vindres_100mean_a4_1_0.png" >}}

This is probably the most accurate representation of the wind resources in Denmark. However, for our analysis, we need the wind resources for each municipality which means that we can’t accurately reflect municipalities with varying wind speeds. The Danish Meteorological Institute (DMI) has published the average wind speed per year for all municipalities for the years 2011-2022. [[13]](https://www.dmi.dk/lokationarkiv) We collected this data and computed the averages over these years, obtaining a wind resource map based on municipalities. 

*The map below initially shows the average wind speed for each municipality in Denmark. You can hover the cursor over the municipalities to see the exact wind speed values. Click the button in the upper right corner to choose between the other categories.*

<p align="center">
<iframe src="/SocialData/html/map_wind_kW_suited_pop_hacked.html"
	sandbox="allow-same-origin allow-scripts"
	width="1000"
	height="700"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>
</p>

By inspecting the different categories in the map, it is clear that the municipalities with the most kW-capacity per km2 are also some of the areas with the most wind. Also note that North Sealand, the main villain of the article of Ekstra Bladet, is one of the least windy areas. Now let’s look at the scatter plots to get a better idea of the relationships between the categories.

*The scatter plots below will help with investigating if there is a connection between wind turbines and other municipality-specific factors. This time you can also click on a point in one scatter plot to highlight that municipality in all four scatter plots.*

<p align="center">
<iframe src="/SocialData/html/scatter_inc_pop_area_wind.html"
	sandbox="allow-same-origin allow-scripts"
	width="750"
	height="800"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>
</p>

These scatter plots show us that the kW-capacity has a connection with both population density, percentage of suitable area and average wind speed. All these three categories seem to have a stronger connection to the kW-capacity than the average income, suggesting that space and wind resources have more influence on the placement of turbines. You can also find the rich municipalities in the upper left plot and highlight them to see that a lot of them have a low percentage of suited area and a low average wind speed. However, we can find some exceptions. For instance, Solrød has around 55% suited area, and Dragør has a decent average wind speed of 5.1. The municipalities København and Hvidovre stand out by having a quite high kW-capacity despite having a very low percentage of suitable area and high population density. This gives hope that finding space for wind turbines is within the realm of possibilities for more of the densely populated municipalities too.


# Some municipalities are more suited for turbines than others - but everyone should still strive to contribute

Our investigation shows clearly that the high-income municipalities of North Sealand, like stated in Ekstra Bladet, indeed don’t have any wind turbines. This naturally begs the question if wealthier municipalities have more power to oppose wind turbine projects, but we don’t find that there is a general trend that higher income means less wind power. This is why we think that other factors might be better at explaining the lack of wind turbines. It turns out that there is a much stronger connection with the amount of suited area and the population density (two factors that are also related themselves), which is also the main explanation given by municipal mayors when asked about their lack of turbines [[14]](https://www.tv2lorry.dk/tv-2/nordsjaellandske-kommuner-takker-nej-til-vindmoeller-i-forvejen-har-de-ikke-en-eneste). The amount of wind could be another factor influencing the willingness to build wind turbines because more wind means more potential for wind energy. We see this connection especially in some of the windy coastal areas having a high amount of turbines.

Municipalities such as København and Hvidovre stick out by scoring very high in kW per km2 considering how small a portion of their total area seems suitable for wind turbines. It should be noted that they are both coastal municipalities and that it’s the coastal areas they use for the turbines, but many municipalities with no turbines are coastal too. The cases of København and Hvidovre make it seem plausible for any municipality to look for places where wind turbines can be built, and in doing so contribute to the increase of wind power all over Denmark.


# References

1. Johnsen, M., “Ingen vindmøller hos de rige”, Ekstra Bladet, 2013, https://ekstrabladet.dk/nyheder/samfund/article4813498.ece, last visited May 10
2. Halberg, E., “Placeringen af vindmøller er en klassekamp, som den fattige udkant er ved at tabe”, Dagbladet Information, 2022, https://www.information.dk/debat/2022/03/placeringen-vindmoeller-klassekamp-fattige-udkant-ved-tabe, last visited May 10
3. “NIMBY”, Wikipedia, 2022, https://en.wikipedia.org/wiki/NIMBY
4. “Vindmøller”, Erhvervsstyrelsen, 2022, https://planinfo.erhvervsstyrelsen.dk/vindmoeller
5. “Data: Oversigt over energisektoren”, Energistyrelsen, https://ens.dk/service/statistik-data-noegletal-og-kort/data-oversigt-over-energisektoren
6. “Statistikbanken”, Danmarks Statistik, https://www.statistikbanken.dk/INDKP105
7. “Danmarks Administrative Geografiske Inddeling”, Dagbladet Information, https://lab.information.dk/
8. “Bekendtgørelse om planlægning for og tilladelse til opstilling af vindmøller”, Retsinformation, 2019, https://www.retsinformation.dk/eli/lta/2019/923
9. “Vindmøller - Data er vejledende og til brug for den videre planlægning!”, Erhvervsstyrelsen, https://kort.erst.dk/spatialmap?profile=vindmoeller
10. “AREALDK: Areal efter arealdække, område og enhed ”, Danmarks Statistik, 2022, https://www.statistikbanken.dk/statbank5a/SelectVarVal/Define.asp?MainTable=AREALDK
11. “FOLK1A: Folketal den 1. i kvartalet efter område, køn, alder og civilstand”, Danmarks Statistik, 2022, https://www.statistikbanken.dk/FOLK1A
12. “Vindressourcekort for 100m over terræn”, Erhvervsstyrelsen https://planinfo.erhvervsstyrelsen.dk/sites/default/files/vindres_100mean_a4_1_0.png
13. “Vejrarkiv”, DMI, 2022, https://www.dmi.dk/lokationarkiv
14. Honoré, D. R., “Nordsjællandske kommuner takker nej til vindmøller - i forvejen har de ikke en eneste”, TV 2 Lorry, 2022, https://www.tv2lorry.dk/tv-2/nordsjaellandske-kommuner-takker-nej-til-vindmoeller-i-forvejen-har-de-ikke-en-eneste


