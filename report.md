## My approach:
### Preprocessing
1. Calculate corners using Harris algo (for the 1st image)
2. Threshold
3. Find edges using Canny algo (for the 2nd image)

### Dot extraction
1. Find contours
2. Filter contours by area 
3. Check if the contour is a circle: $$\frac{S}{P^2} = \frac{1}{4\pi}$$

### Translation
1. Get minimal distance (between closest points)
2. Align: if for 2 points difference between y coordinates is small enough (smaller than minimal distance), they are probably at the same row. Same for columns
3. Convert to matrix for convenience, e.g. `⠕` will look like:
```math
\begin{bmatrix}
1&0 \\
0&1 \\
1&0
\end{bmatrix}
```
4. I store the Braille alphabet in hex for converting (e.g. `⠕` is `0x4F` is "o" letter): https://en.wikipedia.org/wiki/Braille_ASCII#Braille_ASCII_values

## Challenges:
1. Had to use different approaches of preprocessing for both images: can not separate dots in 2nd image after using Harris algo.
2. Had letters "o" detected as dots in 2nd image - decided to blur the image to make letters look worse
2. Parameters tuning: some of parameters (e.g. for Harris, Canny) I was selecting blindly, by experiment. Would like to implement Harris or Canny by myself to gain a deeper understanding.
3. The solution is not universal - very probably will not work for another image
2. Translation algo is not the best:
    - no spaces
    - not stable to slighly rotated image
