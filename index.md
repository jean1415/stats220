# My meme

## Meme description:

* This meme aims to raise awareness of *digital footprint* with a sense of humor.
* While the boy innocently restates his father's advice, the symbolic face of social media reveals the fact 
(based on the social media users' digital footprints)
that the person who the boy believes to be his father is in fact not the boy's biological father.

## Display Meme:
![](jean_meme.png)
<!---alternative way to display image within the same repo:
![](https://github.com/jean1415/stats220/blob/main/jean_meme.png "My first meme on R") 
--->

## R code used to create the meme:
```r
library(magick)

#top image and text
pic1 <- image_read("https://cdn.pixabay.com/photo/2014/03/12/18/42/boy-286241_960_720.jpg") %>% 
  image_scale("600x600") %>% 
  image_annotate(text = '"My father said not to trust Facebook"', 
                 color = "#000000", 
                 size = 30, 
                 font = "elephant", 
                 location = "+20+50") %>% 
  image_border("#000000", "10x10")

#bottom image and text
pic2 <- image_read("https://imageio.forbes.com/specials-images/imageserve/611e85a6a2ae9f10d0c7870b/0x0.jpg?format=jpg&crop=2946,1657,x0,y0,safe&fit=crop") %>% 
  image_scale("600x600") %>% 
  image_annotate(text = '"He is \n not your \n real father"', 
                 color = "#000000", 
                 size = 30, 
                 font = "elephant", 
                 location = "+370+50") %>% 
  image_border("#000000", "10x10")

#combining pic1 and pic2
pic3 <- image_append(c(pic1, pic2), stack = TRUE)

#additional box
box <- image_blank(width = 600,
                   height = 30,
                   color = "#000000") %>% 
  image_annotate(text = "STATS220 Assignment 1 / My first meme on R / 15 March 2022", 
                 size = 10, 
                 color = "#e6e6e6",
                 font = "Arial", 
                 gravity = "southeast") %>% 
  image_border("#000000", "10x10")

#final meme
combined <- image_append(c(pic3, box), stack = TRUE)
combined

#save my meme as an image file (e.g. png)
image_write(combined, "jean_meme.png")
```
