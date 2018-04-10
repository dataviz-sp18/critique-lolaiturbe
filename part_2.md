Data Vizualization
================
Dolores De Iturbe
10/04/2018

Part 2: ggplot2 and the grammar of graphics
-------------------------------------------

``` r
internet <- read.csv ("Internet users mex.csv", header = T, na.strings ="?")
names(internet)
```

    ## [1] "year"           "age_groups"     "internet_users" "percentage"

``` r
internet <- mutate(internet, millions = internet_users/1000000)
```

``` r
ggplot(internet, aes(year, millions)) +
  geom_line(aes(colour = age_groups)) +
  labs(
    title = "Total number of Internet Users in Mexico by age group",
    subtitle = "2001-2017",
    caption = "Data: http://www.beta.inegi.org.mx/temas/ticshogares/",
    x = "Year",
    y = "Internet Users (millions)",
    colour = "Age group") +
  theme_minimal()
```

![](part_2_files/figure-markdown_github/unnamed-chunk-3-1.png)

The visualization I designed is a representation of the number of Internet users in Mexico from 2001 to 2017. The data was obtained from the statistics institute in Mexico, Institutio Nacional de Estadística y Geografía, which is the equivalent to the Census Bureau of the United States. The data was downloaded from the following link: <http://www.beta.inegi.org.mx/temas/ticshogares/> and the specific dataset I used was: Internet users according to age group (Usuarios de Internet, según grupos de edad). Since the data was not tidy and the csv file had formatting, cleaning it was the most time consuming part.

This data is extremely important, specifically for policymakers, Internet service providers and academic researchers. The data could be used by policymakers to better understand if there is an age gap in Internet use, to know the total number of users by age in order to implement policies such as: teaching programs for adults ages 45 and above. Internet Service Providers can also use this visualization in order to better target their marketing strategies towards untapped markets. For researchers, this data is extremely important to make comparisons with other countries Internet penetration, for example.

The visualization presented above clearly portrays an increasing trend in the number of Internet users in Mexico from 2001 to 2017. It is important to point out that the data set does not include data for the year 2003. This is obvious as Internet penetration in developing nations began in the late 90s and has been rapidly increasing all around the world. We can see that, in Mexico, since the year 2014, there has been a quicker adoption of the Internet for all age groups. The lines in the graph show a steep increase from that year onwards. It would be interesting to know if this rapid change happened because of a public policy or more affordable pricing.

Additionally, it is clear that the age groups with the highest number of users are the younger generations: ages 12 to 17, 18 to 24, and 25 to 34 (excluding ages 6 to 11 since some of them might probably be too young to use the Internet). We can also observe that the age groups with the least amount of Internet users are the oldest ones (ages 55 and older and age group 45 to 54).

I selected a line graph for my visualization since it is a time series and people are familiarized to seeing the years in the x-axis and whatever variable we are measuring on the y-axis. A line graph clearly shows how, as time changes, the variable on the y-axis behaves. In this case, we can see that from 2001 to 2017 the number of Internet users has largely increased. I decided to show the different age groups with different colors in order to easily recognize each age group. I believe that the since there are seven age groups this color pallet is very useful because all the age groups are distinguishable between each other.

The only data transformation I did in order to facilitate the effective communication of the graph was to transform the number of Internet users, which was in millions of people, into a more easily readable number in the graphic. If I left the variable number of Internet users as it was, once R plot the graph, the numbers shown on the y-axis would be something like 5”.0e+06”. This number is not straightforward and it could be complicate to understand by the general public. Furthermore, it does not look aesthetically good. This is why, I did the transformation where I divided the value by one million and I specify on the label of the y-axis that the numbers of Internet users are in millions. This way, it easy to read that in 2015 around 12.5 million Mexicans between the ages of 25 to 34 are Internet users.

I chose the minimal theme because I think it is the most beautiful and simple way to present the information. I also included the source of the data in the labels in order for anybody looking at the graphic to know where the data was taken from. In general, I believe this is a very simple graph that depicts the information in a clear way.
