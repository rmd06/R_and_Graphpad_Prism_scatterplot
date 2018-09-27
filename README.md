## Common Statistical Tests in R and and Graphpad® Prism: X-Y Scatterplot

### Synopsis
A X-Y scatterplot is used to contrast two sets of data, and usually to determine if a linear correlation exists.  

#### Example Data to contrast weight and hindfoot length

        # record_id month day year plot_id species_id sex hindfoot_length weight   genus  species taxa plot_type
        # 845     5   6 1978       2         NL   M              32    204 Neotoma albigula Rodent   Control
        # 1164     8   5 1978       2         NL   M              34    199 Neotoma albigula Rodent   Control
        # 1261     9   4 1978       2         NL   M              32    197 Neotoma albigula Rodent   Control
        # 1756     4  29 1979       2         NL   M              33    166 Neotoma albigula Rodent   Control
        # 1818     5  30 1979       2         NL   M              32    184 Neotoma albigula Rodent   Control
        # 1882     7   4 1979       2         NL   M              32    206 Neotoma albigula Rodent   Control

#### Scatterplot using Graphpad Prism
1) Select "XY", and the radio button under "X" for "Numbers", and the radio button under "Y" for "Enter and plot a single Y value for each point"
2) Copy and paste the data from the hindfoot_length and weight as X and Y, respectively, then select "Analyze", and under "XY analyses", select "Linear Regression.
3) Accept all defaults, and click "Ok".
4) You should get these results:

        "Best-fit values ± SE"	
        "    Slope"	"-4 ± 8.845"
        "    Y-intercept"	"322.7 ± 287.5"
        "    X-intercept"	80.67
        "    1/slope"	-0.25
        	
        "95% Confidence Intervals"	
        "    Slope"	"-28.56 to 20.56"
        "    Y-intercept"	"-475.7 to 1121"
        "    X-intercept"	"39.21 to +infinity"
        	
        "Goodness of Fit"	
        "    R square"	0.04864
        "    Sy.x"	16.55
        	
        "Is slope significantly non-zero?"	
        "    F"	0.2045
        "    DFn, DFd"	"1, 4"
        "    P value"	0.6745
        "    Deviation from zero?"	"Not Significant"
        	
        Equation	"Y = -4*X + 322.7"
        	
        Data	
        "    Number of X values"	6
        "    Maximum number of Y replicates"	1
        "    Total number of values"	6
        "    Number of missing values"	0

#### Scatterplot using R

ggplot requires an X and Y column from a data frame (or something similar) for a scatterplot

        surveys <- read.csv('scatterplot4R.csv')

        head(surveys)
        record_id month day year plot_id species_id sex hindfoot_length weight   genus  species taxa plot_type
        845     5   6 1978       2         NL   M              32    204 Neotoma albigula Rodent   Control
        1164     8   5 1978       2         NL   M              34    199 Neotoma albigula Rodent   Control
        1261     9   4 1978       2         NL   M              32    197 Neotoma albigula Rodent   Control
        1756     4  29 1979       2         NL   M              33    166 Neotoma albigula Rodent   Control
        1818     5  30 1979       2         NL   M              32    184 Neotoma albigula Rodent   Control
        1882     7   4 1979       2         NL   M              32    206 Neotoma albigula Rodent   Control

        # plot the data
        ggplot(surveys, aes(x=weight, y=hindfoot_length)) + geom_point()

        # change point size:
        ggplot(surveys, aes(x=weight, y=hindfoot_length))  + geom_point(shape=1, size=2)

        # see geom_point_values.png for a listing of possible shapes

Optional Challenge Questions:
1) Can you use a categorical value instead?
2) Can you change the color, scale, etc. of the figure or points in the figure?
