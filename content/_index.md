---
title: "Wind turbines – not in my backyard!"
---


North Sealand is the home of some of the wealthiest people in Denmark, including presidents of wind turbine companies and ministers who promote wind energy. Meanwhile, North Sealand is the only area in the country with almost no wind turbines. Though these powerful people advocate for more wind energy, they themselves get to live in a comfortable distance from the turbines while the rest of the Danish population has to live with the sight and the noise of these monstrosities.

This is the message put forth in an article by Ekstra Bladet **[ref]**, claiming that the placement of turbines is unfair to the advantage of the richest people. In a contribution to the debate by Information **[ref]**, the writer perceives the placement of turbines as a class struggle which the poor people in the countryside are losing.

The whole discussion sounds like an example of the phenomenon [NIMBY](https://en.wikipedia.org/wiki/NIMBY) – “not in my backyard”: Most people have a positive attitude towards wind energy in general, but do not want the turbines close to themselves. The transition to green energy is highly important today, and it only seems fair that every part of the country takes their part of the responsibility.

But is the media right to criticize the wealthy parts of Denmark for not having enough turbines? We are now going to investigate this question in more depth.

<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>


# Who is responsible for the placement of wind turbines?

When criticizing the placement of wind turbines, it is relevant to ask who actually decides where they are installed. However, the answer to this question is not so simple. The decisions are a result of discussions and negotiations between several parties such as the government, the municipal politicians and the local populations. The government determines the national climate goals, but they collaborate with the municipalities to determine suitable spots for turbines. Afterwards, companies can propose to build wind turbines in these spots. In some cases the locals protest against a wind turbine project, which leads to delays and sometimes abandonment of the project. So usually a lot of people have an influence on the projects, and we cannot place the responsibility on a single party. **nævn at planlægningen er kommunal og derfor kigger vi på kommuner[reference???]**

**Since a lot of the decisions and planning happen on a municipal level, we are going to** 


# Where are the wind turbines located?

Let’s start out by taking a look at the locations of the wind turbines in Denmark.

The Danish Energy Agency published a dataset containing all the wind turbines which contribute to (or have earlier contributed to) the Danish electrical power grid. The data features the GPS coordinates of each individual turbine, along with information about its size, model, kW-capacity, municipality, and other things. We will only consider turbines on land, since **bla bla.**

The income data is collected from Statistics Denmark **[ref]**.

*The turbine locations are shown in the map below. If you click the button in the upper right corner, you can additionally choose to see the municipalities colored after average income. In the upper left corner you can zoom in and out.*

<iframe src="/SocialData/html/map_loc_inc.html"
	sandbox="allow-same-origin allow-scripts"
	width="1000"
	height="700"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>

We observe that there are indeed very few wind turbines in North Sealand, which is also the richest area in Denmark. But is this a general trend in all of Denmark?


# Is there a correlation between wealth and amount of turbines?

To investigate this correlation, one option would be to simply plot the number of turbines per km2 against the average income in each municipality. However, the turbines are not identical. The boxplot below shows the distribution of kW-capacities of the turbines. They range all the way from 10 kW to 14000 kW, with the vast majority being below 2000 kW.

Since high-capacity turbines have the ability to produce more electricity than the small ones, it does not seem fair to just compare the number of turbines. Instead, we make the following calculation for each municipality:

$$kW\\_per\\_km2 = \\frac{sum\\_of\\_kW\\_capacities}{area\\_of\\_municipality}$$

*The figure below shows the kW per km2 plotted against the average income in each municipality. You can hover the cursor over each point in the plot to see the name of the municipality.*

<iframe src="/SocialData/html/scatter_inc.html"
	sandbox="allow-same-origin allow-scripts"
	width="410"
	height="410"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>

<iframe src="/SocialData/html/scatter_inc2.html"
	sandbox="allow-same-origin allow-scripts"
	width="410"
	height="410"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>

It seems from the plot like there is a negative correlation between average income and density of turbines, and the correlation is indeed -0.39. However, it does not look like there is a linear relationship, so correlation is not the best measure in this situation. Also, notice that a few outliers make the relationship seem a lot stronger. These outliers are a few municipalities with a very high average income, and a few with a very high density of turbines. 

If we really wanted to confirm the claim of Ekstra Bladet, we could show this plot and say: "This demonstrates that wealthier the municipality, the less turbines they have!" But of course that analysis would be incomplete. The fact is, there could be many other factors contributing to the placement of wind turbines.


# Relevant factors for the

We think it’s worthwhile to consider other factors than just wealth when looking for an explanation for the distribution of wind turbines. Factors like the population density or amount of suitable area naturally limits the amount of suitable spots for wind turbines, and locations with high wind speeds might be more attractive for wind turbines than locations without much wind. 

## Suitable areas


It’s difficult to determine which locations would be suitable for wind turbine placement, but there are [laws](https://www.retsinformation.dk/eli/lta/2019/923) that restrict wind turbine placement based on their distance to residential buildings. We don’t have any good data on this, but we can make a crude estimate based on the terrain of each municipality.

*Below you’ll find additional scatter plots with municipal data collected from Statistics Denmark* **[ref]**, **[ref]**, **[ref]***. This time you can also click on a point in one scatter plot to highlight it in all three scatter plots.*

<iframe src="/SocialData/html/scatter_pop_area_wind.html"
	sandbox="allow-same-origin allow-scripts"
	width="100%"
	height="400"
	scrolling="no"
	seamless="seamless"
	frameborder="0">
</iframe>

# Conclusion


