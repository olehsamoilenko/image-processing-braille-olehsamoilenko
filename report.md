## My approach:
###s Preprocessing
1. Calculate corners using Harris algo (for the 1st image)
2. Threshold
3. Find edges using Canny algo (for the 2nd image)

### Dot extraction
1. Find contours
2. Filter contours by area 
3. Check if the contour is a circle: $ S/P^2 = 1/(4*\pi) $

### Translation
**Magic!** (TODO: explain)<br>
I store the Braille alphabet in hex: https://en.wikipedia.org/wiki/Braille_ASCII#Braille_ASCII_values

## Challenges:
1. Had to use different approaches of preprocessing for both images: can not separate dots in 2nd image after using Harris algo.
2. Parameters tuning: some of parameters (e.g. for Harris, Canny) I was selecting blindly, by experiment. Would like to implement Harris or Canny by myself to gain a deeper understanding.
3. The solution is not universal - very probably will not work for another image
2. Translation algo is not the best:
    - no spaces
    - not stable to slighly rotated image
