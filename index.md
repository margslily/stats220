library(magick)

#The meme I have created is an adaptation of the meme shown in labs which depicted the opposite of what I created. I am particularly scared and confused when I see my friends work on their Computer Science work and I much rather prefer Statistics. 

image_blank(width = 500, height = 500, color = "black")

# square one
scared_cat <- image_read("https://cdn.pixabay.com/photo/2013/09/07/08/29/cat-179842_960_720.jpg") %>%
  image_scale(500)

#square two
cs_text <- image_blank(width = 500, 
                          height = 500, 
                          color = "#66ccff") %>%
  image_annotate(text = "Computer \nScience",
                 color = "#000000",
                 size = 80,
                 font = "Times New Roman",
                 gravity = "center")

# square three
happy_cat <- image_read("https://cdn.pixabay.com/photo/2016/08/05/23/17/british-shorthair-1573559_960_720.jpg") %>%
  image_scale(500)

# square four
stats_text <- image_blank(width = 500, 
                       height = 500, 
                       color = "#66ccff") %>%
  image_annotate(text = "Statistics",
                 color = "#000000",
                 size = 80,
                 font = "Times New Roman",
                 gravity = "center")

# making each row

# first using the approach we used above
cat_vector <- c(scared_cat, cs_text)
top_row <- image_append(cat_vector)

# second using a different approach
bottom_row <- image_append(c(happy_cat, stats_text))

# making the whole thing!

# using another approach
c(top_row, bottom_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)

image_write(meme, "my_meme.png")
