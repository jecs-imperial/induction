# Induction

A derivation of the axiom of induction for the [Occam](http://djalbat.com/occam) proof assistant.

The image below represents the natural numbers defined with the first eight Peano axioms only, omitting the ninth, the axiom of induction. 
The lighter dominos represent what might be called the well behaved natural numbers. 
The first lighter domino represents zero, with the lighter domino immediately behind that representing its successor, namely one, and so on. 
Beside these well behaved natural numbers stands a ring of pathological natural numbers. 
None of these pathological natural numbers is a successor of a well behaved natural number. 
Nonetheless, it is a worthwhile exercise to prove that if we augment the well behaved natural numbers with these pathological natural numbers, the first eight Peano axioms are still obeyed.

The axiom of induction might be defined in plain English thus:

*We can reach all the natural numbers by starting at zero and counting.*

So the axiom of induction *rules out* the pathological natural numbers. 
You can never reach a pathological natural number by starting at zero and counting, because no pathological natural number is a successor of any well behaved natural number. 
This is the essence of the axiom of induction. 
It precludes any pathological natural numbers and allows us only the well behaved ones. 

Here is the axiom of induction defined formally:
\[
\frac{\rho\vdash{R::P(0)}\;\;\sigma\vdash{S::P(k)\to{P(k+1)}})}{\tau(n)\vdash{R(n)::P(n)}}\quad\quad{0,k,n:\mathbb{N}}
\]
This may not at first sight appear to be the same as the plain English definition, admittedly the former definition makes no mention of what appears to be a predicate, for example. 
But for all intents and purposes the two definitions can be considered to amount to the same thing. 

To continue, the [natural numbers](https://openmathematics.org/#natural-numbers) package gives a standard construction of the well behaved natural numbers. 
However, we could also, if we chose, construct some pathological natural numbers:
```
Type NaturalNumber

// Well behaved natural numbers
Constructors zero:NaturalNumber,successor(NaturalNumber):NaturalNumber 

// Pathological natural numbers
Constructor why:NaturalNumber
Axiom 
  successor(successor(...(why))))))))))))))))=why
```
Here we define another zero-arity constructor of type `NaturalNumber`, calling it `why` (for want of a better word) and then define its sixteenth successor to be equal to it. 
This gives us a ring of sixteen pathological natural numbers, less than the number shown in the image, but the principle is the same.

It almost goes without saying, however, that we do not construct these pathological natural numbers under normal circumstances. We just have the lighter dominoes. 
So it should therefore be possible, therefore, to derive the axiom on induction from the construction of the well behaved natural numbers. 
This is indeed the case, and this package contains such a derivation.

<img class="domino-effect" src="https://upload.wikimedia.org/wikipedia/commons/7/79/Domino_effect_visualizing_exclusion_of_junk_term_by_induction_axiom.jpg" alt="Domino effect" />

## Acknowledgements

* The 'domino effect' image is reproduced here courtesy of Jochen Burghardt [CC BY-SA 3.0] and is provided by Wikimedia Commons.

## Contact

* jecs@imperial.ac.uk
* http://djalbat.com
