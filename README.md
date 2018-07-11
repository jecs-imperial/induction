# Induction

A derivation of the axiom of induction for the [Occam](http://djalbat.com/occam) proof assistant.

The image below represents the natural numbers defined with the first eight Peano axioms only, omitting the ninth, the axiom of induction. 
The lighter dominos represent what might be called the well behaved natural numbers. 
The first lighter domino represents zero, with the lighter domino immediately behind that representing its successor, namely one, and so on. 
Beside these well behaved natural numbers stands a ring of what might be called pathological natural numbers. 
None of these pathological natural numbers is a successor of a well behaved natural number. 
Nonetheless, it is a worthwhile exercise to prove that if we augment the well behaved natural numbers with these pathological natural numbers, the first eight Peano axioms still hold.

The axiom of induction can be stated in plain English thus:

*We can reach all the natural numbers by starting at zero and counting.*

You can never reach a pathological natural number by starting at zero and counting because, as already stated, no pathological natural number is a successor of any well behaved natural number. So the axiom of induction effectively *rules out* the pathological natural numbers. 

The following is the axiom of induction defined more formally. 
It is not quite the same as the inference rule derived in this package, there are technical differences. 
It is more what you would find in an introductory text:

\[
\left.
\begin{aligned}
   P(0)& \\
   \forall{k}\,(P(k)\Rightarrow{P(k+1))}&
\end{aligned}
\right\}
\Rightarrow{\forall{n}P(n)}
\]

To see that this more formal definition amounts to the same thing as the plain English one, take the predicate $P$ to mean "is lightly coloured". 
Then the above reads:

*"If the first domino is lightly coloured, and, for all dominoes, if the k'th domino being lightly coloured implies that the k+1'th domino is lightly coloured, then both of these conditions taken together imply that all the dominoes are lightly coloured."*

Now it should be clear that the plain English and more formal definitions amount to the same thing. Both conditions are certainly true, but unless we preclude the darker dominoes, we cannot conclude that all the dominoes are lightly coloured.

To continue, the [natural numbers](https://openmathematics.org/#natural-numbers) package gives a standard construction of the well behaved natural numbers. 
However, we could also, if we chose, construct some additional pathological natural numbers:
```
Type NaturalNumber

// Well behaved natural numbers
Constructors zero:NaturalNumber,successor(NaturalNumber):NaturalNumber 

// Pathological natural numbers
Constructor why:NaturalNumber
Axiom 
  successor(successor(...(why))))))))))))))))=why
```
Here we define another nullary constructor of type `NaturalNumber`, calling it `why` (for want of a better word) and then define its sixteenth successor to be equal to it. 
This gives us a ring of sixteen pathological natural numbers, less than the number shown in the image, but the principle is the same.

It almost goes without saying, however, that we do not construct these pathological natural numbers under normal circumstances. 
We just have the lighter dominoes. 
And we know that with just the lighter dominoes, the axiom of induction holds.
It should therefore be possible to derive the axiom on induction from the construction of the well behaved natural numbers. 
It is indeed possible to do, just as it is possible to derive the first eight Peano axioms. 
This package contains such a derivation.

![domino-effect]

## Acknowledgements

* The 'domino effect' image is reproduced here courtesy of Jochen Burghardt [CC BY-SA 3.0] and is provided by Wikimedia Commons.

## Contact

* jecs@imperial.ac.uk
* http://djalbat.com

[domino-effect]:
https://upload.wikimedia.org/wikipedia/commons/7/79/Domino_effect_visualizing_exclusion_of_junk_term_by_induction_axiom.jpg
