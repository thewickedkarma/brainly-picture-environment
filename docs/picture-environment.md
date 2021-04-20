# Picture Environment - LaTeX on Brainly

\- By Purva, [@QGP](https://brainly.in/app/profile/48021), Brainly India

\- Contributed By Ankit, [@Ankitraj707](https://www.brainly.in/app/profile/23926353/), Brainly India


Environments in LaTeX are a way to group certain type of commands together. You may have used the `array` and `tabular` environments while making tables. Here, we look at the `picture` environment, which is helpful in creating diagrams.



## Pre-Requisites

It will helpful if you understand **Coordinate Geometry** and have a basic understanding of how **Vectors** work. 

Working with the Picture Environment becomes immensely easier if you look at it from a perspective of coordinate geometry.



In case you haven't studied it yet, you can look at these videos about [Coordinate Plane by Khan Academy](https://www.khanacademy.org/math/basic-geo/basic-geo-coord-plane). Watch the videos until Quiz 1. 



---

## The Starting Blocks

In the Picture Environment, we can imagine a canvas area, where we draw our stuff. We need to define the width and height of this canvas area. And then we start putting the things we want on our canvas.



### Defining Unit Length

The first step is defining what 1 unit length means in our system. *1 unit* is an abstract idea of length. On the contrary, 1 cm, 1 mm, 1 inch, etc. are all physical and concrete ideas of length which are well-defined.



We can define 1 unit length to be anything. Examples:

- 1 unit = 1 cm
- 1 unit = 23 mm
- 1 unit = 2 in (inches)



For simplicity, we will define **1 unit = 1 cm**. We declare it as:

```latex
\setlength{\unitlength}{1cm}
```



### Setting the Drawing Canvas Dimensions

The basic syntax of declaring the dimensions is:

**`\begin{picture}(width, height)`**



Similar to the begin command, there is also an _end_ command to mark the end of the picture environment code. It is simply

**`\end{picture}`**



So, for example, we can display a $\sf 6 \times 8$ cm block as:



```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 8)

    code

\end{picture}
```



We could set a different unit length and declare a different canvas area size as required. It will become clearer what numbers to use once you become a bit familiar with the Picture Environment.



This all is just the structure to define the start and end of the picture environment code. Now, we learn how to draw stuff.



### The `\put` command



Think of our canvas as a coordinate plane, as if on a graph sheet. **The lower-left corner is the Origin (0,0).** The `\put` command _"puts"_ an _object_ at the given coordinates. 

The syntax of the put command is:

`\put(x, y){object}`

where (x, y) refers to the coordinates where we want to place the object. What kind of object? It can be lines, arrows, circles, and more, as shown in the next section: Drawing.

We can also put some text simply at some coordinates. Consider placing the text _Brainly_ at (2, 3).

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 8)

    \put(2, 3){\sf Brainly}

\end{picture}
```



Now, we learn to actually draw stuff.



---



## Basic Drawing

There are various kinds of objects that we can draw. Let's look at them. 

**All of these objects go under the \put command.**



### Line Segments

The syntax of a line segment is:

```latex
\put(x, y){\line(x1, y1){length}}
```

Here:

- `(x, y)` are the co-ordinates from where the line-segment will start from (as the put command starts to place the object from there)
- `(x1, y1)` is the direction vector, pointing towards the direction where the line is to be drawn
- `length` is the length of the line-segment



#### The Direction Vector

Imagine an arrow starting from (0, 0) and pointing to (x1, y1). The direction of this arrow is the direction along which the line segment will be drawn. 

So, for example:

- `\line(1, 0){2}` draws a line segment of length 2 units, towards (1, 0). If you imagine, (1, 0) lies on the X-axis. So, this line is drawn towards the horizontal-right of the starting point. 
  - Now, imagine the direction vector to be (x1, y1) = (2, 0). This is also towards the right side, and hence logically the same as (1, 0).
- `\line(1, 1){3}` draws a line segment of length 3 units, towards (1, 1). This points diagonally towards the top-right. Just like a vector pointing towards (1, 1). 
  - Just as in the first example, direction vectors (2, 2), (3, 3) and all are logically equivalent to (1, 1).
- `\line(-1, 0){2.4}` draws a line segment of length 2.4 units towards (-1, 0), which is horizontally to the left. 
- `\line(3, -2){1.5}` draws a line segment of length 1.5 units towards (3, -2). This is somewhere diagonally towards the bottom-right. Not a perfect diagonal bottom-right, but a slightly different direction.



#### Restrictions on the Direction Vector

The syntax of the line segment is 

```latex
\put(x, y){\line{x1, y1){length}}
```



The direction vector `(x1, y1)` has a couple of important restrictions on the values of `x1` and `y1`.

- **`x1` and `y1` can only take integer values from -6 to 6.** We can only assign values from -6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6. We cannot put fractional values, else the line segment won't work.
  - So, (3, 5) is a valid direction vector. However, (3, -7) is not.
  - (1.5, 3.4) is not a valid direction vector, as the values of x1 and y1 are not integers.

- **`x1` and `y1` must be relatively prime.** This means that the HCF (Highest Common Factor) or the GCD (Greatest Common Divisor) of x1 and y1 should be 1. That is to say that there should be no common factors.
  - 2 and 3 are relatively prime. However, 4 and 6 are not relatively prime, as they can be divided by a common factor of 2. Hence, (2, 3) is a valid direction vector. Putting in (4, 6) should be fine too, however, it can have unexpected behaviour. So, avoid it.
  - (1, 1) is a valid direction vector. However, (2, 2), (3, 3), (4, 4) and similar others are not valid. They can be reduced to (1, 1). 
    - If you happen to use (2, 2) or (2, -2) or (-2, 2) or (-2, -2), you will see a stream of arrow-heads instead of a line-segment. Similar unexpected behaviour with variants of (3, 3), (4, 4) and more. 



---



#### Tutorial: Drawing a Square

Let's write out first drawing code. We will draw a square. Let's start by setting up the drawing canvas:

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6,6)

    code for square to be written here

\end{picture}
```



We declared a $\sf 6 \times 6$ cm canvas and now we start by putting in the objects. Let's choose a start point, say (2, 2).

Now, we will first put a line segment starting from (2, 2), pointing vertically upwards, and of length 2 units. 

Taking it step by step, we have:

- _... starting from (2, 2)..._ - `\put(2, 2){}`
- _...pointing vertically upwards..._ - This means towards to the direction vector (0, 1) - `\line(0, 1){}` 

- _...of length 2 units..._ - `\line(0, 1){2}`

Putting it all together, we have `\put(2, 2){\line(0, 1){2}}`. This will draw our first line segment.

Here's the code and screenshot:

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6,6)

    \put(2, 2){\line(0, 1){2}}

\end{picture}
```



![line-segment-0](_media/screenshots/line-segment-0.png ':size=460')



Now, let's draw the top line. Since our first line-segment was 2 units upwards of (2, 2), the end-point is located at (2, 4). 

We can now draw a line-segment starting from (2, 4) towards the right side with a length of 2 units. So...

- _... starting from (2, 4)..._ - `\put(2, 4){}`
- _...towards the right side..._ - This means towards to the direction vector (1, 0) - `\line(1, 0){}` 

- _...a length of 2 units..._ - `\line(1, 0){2}`

 Thus, our second line-segment is: `\put(2, 4){\line(1, 0){2}}`



Putting it together, our code now looks like this:

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6,6)

    \put(2, 2){\line(0, 1){2}}
    \put(2, 4){\line(1, 0){2}}

\end{picture}
```

![line-segment-1](_media/screenshots/line-segment-1.png ':size=460')

If you are having trouble visualizing the co-ordinates, here's a labelled image:

![line-segment-1-labelled](_media/screenshots/line-segment-1-labelled.png ':size=460')



Let's now draw a line-segment starting at (4, 4), towards vertically down and of length 2 units. 

The direction vector for _vertically downwards_ is (0, -1), as like towards the negative y-axis. Hence, the code for our line-segment is `\put(4, 4){\line(0, -1){2}}`.

So, all in all, our code is:

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6,6)

    \put(2, 2){\line(0, 1){2}}
    \put(2, 4){\line(1, 0){2}}
    \put(4, 4){\line(0, -1){2}}

\end{picture}
```



Here's a co-ordinate labelled screenshot of the above code:

![line-segment-2-labelled](_media/screenshots/line-segment-2-labelled.png ':size=460')



Finally, we need to add our fourth line-segment and complete the square. As you might have thought already, we can do it in two ways:

1. Line-segment starting at (2, 2), towards the right with length 2 units - `\put(2, 2){\line(1, 0){2}}`
2. Line-segment starting at (4, 2), towards the left with length 2 units - `\put(4, 2){\line(-1, 0){2}}`

Both ways are correct. I am picking the second way here and completing the code:

**Square**

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6,6)

    \put(2, 2){\line(0, 1){2}}
    \put(2, 4){\line(1, 0){2}}
    \put(4, 4){\line(0, -1){2}}
    \put(4, 2){\line(-1, 0){2}}

\end{picture}
```

Here's how our square looks like:

![square](_media/screenshots/square.png ':size=460')

And that's our first complete diagram with the Picture Environment! 



---



### Arrows / Vectors



Arrows or vectors have the same syntax as a line-segment. The command is `\vector`. The syntax:

```latex
\put(x, y){\vector(x1, y1){length}}
```

Here:

- `(x, y)` are the co-ordinates from where the arrow/vector will start from (as the put command starts to place the object from there)
- `(x1, y1)` is the direction vector, pointing towards the direction where the line is to be drawn
- `length` is the length of the line-segment

The [restrictions related to the direction vector as mentioned for line segments](#restrictions-on-the-direction-vector) apply here too. However, there's a small difference: the range is more restricted.



!> `x1` and `y1` in the direction vector can only take integer values from -4 to 4.

!> `x1` and `y1` must also be co-prime or relatively prime. 



Let's consider a simple example: 

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 6)

    \put(3, 2){\vector(0, 1){3}}
    \put(2, 3){\vector(1, 0){3}}

\end{picture}
```

We have put in two arrows of length 3 units each. One is pointing upwards, i.e. towards (0, 1). The other is pointing towards the right, i.e. towards (1, 0).

![vector-0](_media/screenshots/vector-0.png ':size=460')



Here's the labelled form if you are having trouble visualizing in terms of co-ordinates.

![vector-0-labelled](_media/screenshots/vector-0-labelled.png ':size=460')

As we can see, the upward pointing arrow starts at (3, 2). The rightward pointing arrow starts at (2, 3). 





---



### Circles

The syntax of a circle is a simple one:

```latex
\put(x, y){\circle{diameter}}
```

This puts a circle of the given diameter centred `(x, y)`. Essentially, `(x, y)` is the centre of the circle.

!> The picture environment only allows diameters up to approximately 1.4 cm (14 mm). Also, not every value below 1.4 cm works. You'll have to experiment a bit and adjust co-ordinates of other objects.

Here's a simple example:

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 6)

	\put(3, 3){\circle{1}}

\end{picture}
```

![circle-0](_media/screenshots/circle-0.png 'size=460')

Let's add a line-segment to show the diameter. The diameter is 1 cm, so radius is 0.5 cm. The circle is centred at (3, 3), so we can start a line-segment from (2.5, 3), which is just 0.5 cm left to the centre.



```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 6)
	\put(3, 3){\circle{1}}
	\put(2.5, 3){\line(1, 0){1}}
\end{picture}
```



Here's how it looks:

![circle-1](_media/screenshots/circle-1.png 'size=460')



---



### Shaded/Filled Circles

To get shaded/filled circles or disks, you just use the `\circle*` command. The syntax is the same:

```latex
\put(x, y){\circle*{diameter}}
```

This puts a shaded circle centred at `(x, y)`.

Example:

```latex
\boxed{
	\setlength{\unitlength}{1mm}
	\begin{picture}(45, 20)

		\put(12, 10){\circle*{2}}
		\put(20, 10){\circle*{4}}
		\put(30, 10){\circle*{10}}

	\end{picture}
}
```

Notice a few things here:

- We have put a box around the canvas area with the `\boxed{}` command.
- The _unitlength_ is now 1 mm. So, the canvas area is $\sf 45 \times 20$ mm or $\sf 4.5 \times 2$ cm.

Here's how the code looks:

![shaded-circle-0](_media/screenshots/shaded-circle-0.png ':size=460')



Here's a labelled version to help it understand better:

![shaded-circle-0-labelled](_media/screenshots/shaded-circle-0-labelled.png ':size=460')



