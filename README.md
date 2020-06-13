#README


## 2D CFAR

Steps we simply the follwing:

1. Assign Training Cells and Guard Cells for Each demension
2. Look though every Cell in 2D doppler image
3. For each i j pair, Extract the a kernel associated to the 2D CFAR cell using the Gard and Training cell parameters set in the beginning
4. Convert extracted Kernel to Raw, non-dB values.
5. Sum the whole kernel and subtract out the sum of the gaurd cells + CUT and then divide by the the total number of training cells. This gives you only the average of the training cells
6. Convert average back to dB
7. Find the CUT, and compare it to cfar average in dB plus the offset. If greater than this threshold, set the CUT to 1. If not, set it to 0


## Training and Gaurd Parameters


For this, it was a lot of trial and error. I went with:

Tr = 8
Td = 4
Gr = 4
Gd = 2


## Supression of edges 

I avoided this problem by outputting my results to a prallocated images the size of 'RDM' that was all 0's to being with. When loop thought the RDM image, I never touched the edges and therefore the edges values in my output image stayed 0
