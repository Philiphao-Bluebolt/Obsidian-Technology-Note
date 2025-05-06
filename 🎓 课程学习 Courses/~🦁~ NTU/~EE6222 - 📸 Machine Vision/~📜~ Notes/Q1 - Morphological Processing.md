+ **Use on** - binary images
+ **Operations** - Dilation, Erosion, Opening, Closing

Morphology is a category of image processing algorithms for binary images. Its output is yielded from the logic operation of input images $A,B$ and thus greatly based on the set theory. 

The output area in descending sequence: **Dilation** > **Closing** > **Original** > **Opening** > **Erosion**

+ Input $A$
+ Structural Element $B$

+ [Dilation](#Dilation) - $A\oplus B$
+ [Erosion](#Erosion) - $A\ominus B$
+ [Opening](#Opening) - $A\circ B=(A\ominus B)\oplus B$
+ [Closing](#Closing) - $A\bullet B=(A\oplus B)\ominus B$

---
## Dilation

+ **Symbol** - $A\oplus B$

Intuitively, dilation outputs the shape swept by translating $B$ when the center of $B$ is within $A$. The output shape is larger than $A$



---
## Erosion

+ **Symbol** - $A\ominus B$

Intuitively, erosion outputs the shape swept by translating the center of $B$ when $B$ is completely within $A$. The output shape is smaller then $A$


---
## Opening

+ **Symbol** - $A\circ B=(A\ominus B)\oplus B$

Intuitively, opening operation erodes $A$ and then dilates it. This process tends to **erode convex** structures and making them flatter. It has no effect on concave structure. The output shape is smaller then $A$

The name of "opening" implys its ability to "open" (break) a bridge or thin connection.


---
## Closing

+ **Symbol** - $A\bullet B=(A\oplus B)\ominus B$

Intuitively, closing operation erodes $A$ and then dilates it. This process tends to **fill concave** structures and making them flatter. It has no effect on convex structure. The output shape is larger then $A$

The name of "closing" implys its ability to "close" (build) a bridge or thin connection.