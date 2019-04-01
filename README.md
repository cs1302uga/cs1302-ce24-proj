# cs1302-ce24 Differential Univariate Calculus Fun with the Stream API and Lambda Expressions

> Curiouser and curiouser!
> **--Alice, _Alice in Wonderland_ by Lewis Carroll**

This class exercise introduces students the five-point stencil method for numerical differentiation,
computed efficiently using the Java 8 Stream API and lambda expression representations of real-valued
funtions in a reproducing kernel space. 

## Prerequisite Knowledge

* [Project 4 Description](https://github.com/cs1302uga/cs1302-gallery/)

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the Nike server. 

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

### Getting Started

1. As you know from your precalculus class in junior high / middle school, the **derivative** of 
   a function of a real variable measures the sensitivity to change of the function value 
   (output value) with respect to a change in its argument (input value). Derivatives are 
   a fundamental tool of mathematics. For example, the derivative of the position of a moving 
   object with respect to time is the object's velocity: this measures how quickly the 
   position of the object changes when time advances.
   
   ![A labelled tangent to a curve.](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Tangent_to_a_curve.svg/2560px-Tangent_to_a_curve.svg.png)
   
   The derivative of a function of a single variable at a chosen input value, when it exists, 
   is the **slope of the tangent line to the graph of the function at that point**. The tangent 
   line is the best linear approximation of the function near that input value. For this reason, 
   the derivative is often described as the "instantaneous rate of change", the ratio of the 
   instantaneous change in the dependent variable to that of the independent variable.
   
   A first order derivative can be estimated using the five-point stencil method:
   
   ![five-point stencil method](https://wikimedia.org/api/rest_v1/media/math/render/svg/554d2e3e5894dc11cffad91024372276eab6987a)
   
   where
   
   ![five-point stencil method constant](https://wikimedia.org/api/rest_v1/media/math/render/svg/666c60123c8e7ff40bbb58e46c1af3c5fbb5e688)
   
   **The two paragraphs above are adapted from Wikepedia.**
   Wikipedia contributors. (2019, March 23). 
   Derivative. In _Wikipedia, The Free Encyclopedia._
   Retrieved 22:09, March 30, 2019, from 
   https://en.wikipedia.org/w/index.php?title=Derivative&oldid=889095793

1. **April Fools!** Breathe in. Breathe out. You just need to work on your project today.

1. Please work on your project until the end of the period. You can only get a checkpoint
   signature today when you turn your slip in near the end of the period (last five minutes).

**CHECKPOINT**

For those who really are curious about methods for numerical differentiation, you might
create a functional interface to represent a function of a real variable, then provide a
default method to approximate the derivative:

```java
import java.util.function.Function;

public interface RealFunction extends Function<Double, Double> {

   /** The value used for determining if two <code>double</code> values are essentially equal. */
   static final double E = 1E-11;
   
   /** The half-width used for two-sided differentiation. */
   static final double H = E;

   /**
    * Returns the first derivative of the function using a symmetric difference quotient.
    * @return the first derivative of the function
    */
   public RealFunction derivative() {
       return return x -> (apply(x + H) - apply(x - H)) / ((x + H) - (x - H));
   } // derivative

} // RealFunction
```

**NOT A CHECKPOINT**

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
