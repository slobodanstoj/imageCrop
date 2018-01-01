#Terence herp meh


def getCropFromPicture(picSource, xCoord, yCoord, xLen, yLen): # defining input arguments this time asking where to start and where to end the crop
  width = xLen 
  height = yLen 
  picCopy = makeEmptyPicture(width, height) # creating a blank canvas with dimensions provided by the user
  y = 0 
  while(y < width): 
    x = 0 
    while(x < height):
      pxSrc = getPixel(picSource,(x+xCoord),(y+yCoord)) 
      pxCopy = getPixel(picCopy,x,y)  
      setColor(pxCopy,getColor(pxSrc)) 
      if (x != height):
        x = x+1 # incrementing x
      else:
        x = height
    if (y != width):
    
      y = y+1 # incrementing y
    else:
      y = width
  
  return picCopy # returning the new image to the driver (painted canvas)
  
  # THIS WORKS ONLY FOR SQUARE CROPS... ERROR FOR RECTANGULAR CROPS
  # getPixel(picture,x,y): y (= 100) is less than 0 or bigger than the height (= 99)
  # The error was:
  # Inappropriate argument value (of correct type).
  # An error occurred attempting to pass an argument to a function.
  
def cropDriver():
  picA = makePicture(pickAFile())
  explore(picA)
  cropXStart = requestInteger("Type x coordinate of crop start")
  cropYStart = requestInteger("Type y coordinate of crop start")
  lenCropX = requestInteger("Width of crop from starting coord in px")
  lenCropY = requestInteger("Height of crop from starting coord in px")
  
  picB = getCropFromPicture(picA,cropXStart,cropYStart,lenCropX,lenCropY) 
  explore(picB) 
