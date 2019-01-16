# Data Visualization
```
import matplotlib.pyploy as plt
year = [1950, 1970, 1990, 2010]
pop = [2.519, 3.692, 5.263, 6.972]
plt.plot(year, pop) || plt.scatter(year, pop)  => buid 
plt.show()    => show
plt.clf()
```
## Put the x-axis on a logarithmic scale

>plt.xscale('log')

## Histogram => Distributions

One variable involved

>plt.hist(values, bins=3) 

Also use help(plt.hist) for more

Example: Population pyramid

## Axis Labels

>plt.xlabel("Year")
>plt.ylabel("Population")
>pl.title("World Population Projections")
>plt.yticks([0,2,4,6,8,10])
>plt.yticks([0,2,4,6,8,10], ['0', '2B', '4B', '6B', '8B', '10B'])

## Sizes

>plt.scatter(gdp_cap, life_exp, s = np_pop)

## Colors

How did we make the list col you ask? The **Gapminder data** contains a list continent with the continent each country belongs to. A dictionary is constructed that maps continents onto colors:
```
dict = {
    'Asia':'red',
    'Europe':'green',
    'Africa':'blue',
    'Americas':'yellow',
    'Oceania':'black'
}
```

>plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c=col)

>Change the opacity of the bubbles by setting the alpha argument to 0.8 inside plt.scatter(). Alpha can be set from zero to one, where zero is totally transparent, and one is not at all transparent.

## Plot text

>plt.text(1550, 71, 'India')

>plt.text(5700, 80, 'China')

## Plot Grid

>plt.grid(True)
