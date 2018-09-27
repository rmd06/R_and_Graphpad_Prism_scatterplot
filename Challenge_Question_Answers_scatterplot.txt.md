1) Yes.
In R, do the following:

        year_summary <- surveys %>% group_by(species_id, year, sex) %>% summarize(mean_weight = mean(weight), mean_hfl = mean(hindfoot_length), n = n())
        # You MUST provide R a means of grouping categorical values or the ggplot() command will fail with an error.
        # if the value is already a factor, you are fine--technically the next line below would not be required since the "sex" column above has the description "<fctr>"
        year_summary$sexAsFactor <- factor(year_summary$sex)
        ggplot(surveys, aes(x=weight, y=hindfoot_length, colour=sex))  + geom_point(shape=1, size=2)

In Graphpad Prism, Follow the same steps, but you will need to create a quantity for the categories, i.e. for each datapoint, set Male == 1, and Female == 2.

2) Yes.
In R, here are a few examples:
        # change alpha and assign color to points
        ggplot(surveys, aes(x=weight, y=hindfoot_length, colour=sex))  + geom_point(alpha=0.01, aes(color=sex))

        # create a line plot
        ggplot(surveys, aes(x=weight, y=hindfoot_length))  + geom_line()

        # create a line plot with distinct points, note that order matters--assigning points first
        # will create points with the provided parameters, otherwise the points will inherit the parameters from geom_line()
        ggplot(surveys, aes(x=weight, y=hindfoot_length, color=sex))  + geom_point() + geom_line()

        # this will apply the provided aes() parameters to all layers, i.e. globally
        ggplot(surveys, aes(x=weight, y=hindfoot_length))  + geom_point() + geom_line() + aes(color=year)

In Graphpad Prism, there are several options under the "Change" menu.
