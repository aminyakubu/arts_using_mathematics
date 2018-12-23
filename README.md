Drawing flowers using mathematics
================

For the love of arts, I’m going to make a flower in R.

Let's start by drawing 50 points on a circle of radius 1. As every (x, y) point should be in the unit circle, it follows that x² + y² = 1.We can get this using the Pythagorean trigonometric identity which states that sin²(θ) + cos²(θ) = 1 for any real number θ.

``` r
t <- seq(0, 2*pi, length.out = 50)
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

# Make a scatter plot of points in a circle
p <- ggplot(df, aes(x, y))
p + geom_point()
```

<img src="README_files/figure-markdown_github/unnamed-chunk-1-1.png" width="90%" />

### Golden Angle

Plants arrange their leaves in spirals. A spiral is a curve which starts from the origin and moves away from this point as it revolves around it. In the plot above all our points are at the same distance from the origin. A simple way to arrange them in a spiral is to multiply x and y by a factor which increases for each point. We could use t as that factor, as it meets these conditions, but we will do something more harmonious. We will use the Golden Angle:

Golden Angle = π(3 − √5)

This number is inspired by the Golden Ratio, one of the most famous numbers in the history of mathematics. Both the Golden Ratio and the Golden Angle appear in unexpected places in nature. Apart of flower petals and plant leaves, you'll find them in seed heads, pine cones, sunflower seeds, shells, spiral galaxies, hurricanes, etc.

``` r
# Defining the number of points
points = 500

# Defining the Golden Angle
angle = pi * (3 - sqrt(5))

t <- (1:points) * angle
x <- sin(t)
y <- cos(t)
df <- data.frame(t, x, y)

# Make a scatter plot of points in a spiral
p <- ggplot(df, aes(x*t, y*t))
p + geom_point()
```

<img src="README_files/figure-markdown_github/unnamed-chunk-2-1.png" width="90%" />

### Time to clean up!

The code below sets the background color to white, and removes all elements of the x and y axes.

``` r
df <- data.frame(t, x, y)

# Make a scatter plot of points in a spiral
p <- ggplot(df, aes(x*t, y*t))
p + geom_point() + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'white'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-3-1.png" width="90%" />

### Coloring

Simply playing around the color schemes to get a good feel

``` r
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(size = 8, alpha = 0.5, color = "darkgreen") + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'white'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-4-1.png" width="90%" />

Let's play with the aesthetics to see how our flower changes

``` r
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(aes(size = t), color = 'black', alpha = 0.5, shape = 8) + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'white'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-5-1.png" width="90%" />

Let's change the color of the points and the shape!

``` r
p <- ggplot(df, aes(x*t, y*t))
p + geom_point(aes(size = t), color = 'yellow', alpha = 0.5, shape = 17) + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'darkmagenta'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-6-1.png" width="90%" />

### Angles

These patterns are very sensitive to the angle between the points that form the spiral; small changes to the angle can generate very different images

``` r
angle <- 2.0
points <- 1000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)

df <- data.frame(t, x, y)

p <- ggplot(df, aes(x*t, y*t))

p + geom_point(aes(size = t), color = 'yellow', alpha = 0.5, shape = 17) + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'darkmagenta'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-7-1.png" width="90%" />

### All together

Let's increase the number of points (theoretically we can make an infinite number of patterns), change the size and color of our point.

``` r
angle <- 13 * pi/180
points <- 2000

t <- (1:points)*angle
x <- sin(t)
y <- cos(t)

df <- data.frame(t, x, y)

p <- ggplot(df, aes(x*t, y*t)) 

p + geom_point(size= 80, color = 'magenta4', alpha = 0.1, shape = 1) + theme(legend.position = "none",
        panel.grid = element_blank(),
        axis.title = element_blank(),
        axis.text = element_blank(),
        axis.ticks = element_blank(),
        panel.background = element_rect(fill = 'white'))
```

<img src="README_files/figure-markdown_github/unnamed-chunk-8-1.png" width="90%" />

I hope you've enjoyed the journey between that simple circle and this beautiful flower!
