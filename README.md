# uznFlags
from turtle import *


def drawSquare (r,s,t):
    
    """Using turtle graphics, draw a square.
    
    Params:
        r (int 2-tuple): coordinates for bottom right corner of square
        s (str): fill color of square
        t (int): side length of square
    """
   
    up ()
    goto (r)
    fillcolor (s)
    begin_fill()
    for i in range(4):
        left (90)
        forward (t)
    end_fill()
  
    
def drawFourSquare (r,s1,s2,w):
    
    """Using turtle graphics, draw a 4x4 "checkerboard"
    
    Params:
        r (int 2-tuple): coordinates for bottom left corner of "checkerboard"
        s1 (str): fill color of top left and bottom right squares
        s2 (str): fill color of bottom left and top right squares
        w (str): side length of "checkerboard"
    """
    
    drawSquare (r,s1, w/2)
    drawSquare ((r[0]-w/2, r[1]), s2, w/2)
    drawSquare ((r[0], r[1]+w/2), s2, w/2)
    drawSquare ((r[0]-w/2, r[1]+w/2), s1, w/2)


def drawTriangle (x, y, z, s):
    
    """Using turtle graphics, draw a triangle.
    
    Params:
        x (int 2-tuple): coordinates for first vertex of triangle
        y (int 2-tuple): coordinates for second vertex of triangle
        z (int 2-tuple): coordinates for third vertex of triangle
        t (str): fill color of triangle
    """
    
    up ()
    goto (x)
    fillcolor (s)
    begin_fill()
    goto (y)
    goto (z)
    goto (x)
    end_fill()



def uFlag(r,w):
    
    """Using turtle graphics, draw the maritime flag for letter "U".
    
    Params:
        r (int 2-tuple): bottom right corner of flag
        w (int): width of flag
    """
    
    drawFourSquare (r,'red','white',w)
 
    
def zFlag (r,w):
    
    """Using turtle graphics, draw the maritime flag for letter "Z".
    
    Params:
        r (int 2-tuple): bottom right corner of flag
        w (int): width of flag
    """
    
    c = (r[0]-w/2, r[1]+w/2)
    L1 = [r, (r[0]-w, r[1]), (r[0]-w, r[1]+w), (r[0], r[1]+w), r]
    L2 = ['red', 'black', 'yellow', 'blue']
    for i in range(len(L2)):
        drawTriangle (L1[i], c, L1[i+1], L2[i])


def nFlag (r,w):
    
    """Using turtle graphics, draw the maritime flag for letter "N".
    
    Params:
        r (int 2-tuple): bottom right corner of flag
        w (int): width of flag
    """
    
    L = [r, (r[0]-w/2, r[1]), (r[0], r[1]+w/2), (r[0]-w/2, r[1]+w/2)]
    for i in range(len(L)):
        drawFourSquare (L[i], 'blue', 'white', w/2)



def drawInitials (ref=(0,0), w=100, spacing=10):

    """Using turtle graphics, draw *your* 3 initials in maritime signal flags.
    
    Params:
        ref (int 2-tuple): bottom right corner, the reference point
        w (int): width of each letter, in pixels
        spacing (int): separation between consecutive letters, in pixels
    """

    nFlag (ref, w)
    zFlag ((ref[0]-w-spacing, ref[1]), w)
    uFlag ((ref[0]-2*w-2*spacing, ref[1]), w)
    done ()
    speed(0)
