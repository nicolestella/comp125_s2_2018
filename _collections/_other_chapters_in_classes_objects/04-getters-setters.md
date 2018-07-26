---
title: Getters and Setters
---
Getters and setters
===================

Bad client, bad bad client!
---------------------------

Once the object is created, we can start operating on it.

``` {style="buggy"}
Rectangle r = new Rectangle();
@r.width = -5;@ // :o :O
r.height = 8;
System.out.println(r.area()); 
//displays -40 :'(
```

Changing visibility to private
------------------------------



<img src="./../fig/classesObjects1/classesObjects1-figure5.png"
alt="Drawing" width = "400"\>



Now, the instance variables `width` and `height` are visible only within
the class definition.

How does one access (read/write) private instance variables
-----------------------------------------------------------

We access (read and write) private instance variables through public
methods called `getters` and `setters`.

-   `getters` return the value of the instance variable to the caller.

-   `setters` set the value supplied by the caller to the instance
    variables.

Setters must provide validation where applicable
------------------------------------------------

You can see that we validated the passed values before assigning to the
instance variable as `width = Math.abs(w)`. This is a typical case and
setters are in charge of validating data before assigning it to the
instance variables.



<img src="./../fig/classesObjects1/classesObjects1-figure6.png"
alt="Drawing" width = "400"\>



[8][Add getters and setters] Add getters and setters to class `Circle`.
The setter should result in radius becoming zero if the parameter passed
is not positive.

    //setter
    public void setRadius(double r) {
        if(r < 0)
            radius = 0;
        else
            radius = r;
    }

    //getter
    public double getRadius() {
        return radius;
    }

[6][Write a client] Write a client (code sitting outside `Circle.java`,
for example, in the `main` method of another class) that performs the
following operations,

-   Declare and instantiate object `myCircle` of class `Circle` that has
    a radius of 1.8

-   Display radius of `myCircle`.

-   Increase radius of `myCircle` by 1.4

<!-- -->

    public class Client {
        public static void main(String[] args) {
            Circle myCircle = new Circle();
            myCircle.setRadius(1.8);
            System.out.println(myCircle.getRadius());
            myCircle.setRadius(myCircle.getRadius() + 1.4);
            /* or you can split it up as:
            * double current = myCircle.getRadius();
            * double updated = current + 1.4;
            * myCircle.setRadius(updated);
            */
        }
    }