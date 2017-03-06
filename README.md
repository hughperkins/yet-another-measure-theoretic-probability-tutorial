# yet-another-measure-theoretic-probability-tutorial
Yet another measure theoretic probability tutorial

I made these notes after reading the following:

- "A Measure Theory Tutorial ( Measure Theory for Dummies )", by Gupta, 2006
- "Outline of Lebesgue theory: a heuristic introduction", by Wernikoff. 1957 :-)
- MIT Opencourseware "Fundamentals of probability", 2008

^^^ all of these references are awesome :-)

But, there was a question that I couldnt quite figure out for ages, a little tiny gap in my knowledge. And that was, imagine we have two variables $X$ and $Y$, and they're each Gaussians. Some questions in my mind:

- in the measure theoretic framework, how do we represent a Gaussian? Where does the equation for the Gaussian, the exponential in $-x^2$ "go"? Is it in the $X$? in the $\mathbb{P}$? Somewhere else?
- how do we represent both $X$ and $Y$,in the same space? Since we already "used up" $\mathbb{P}$ for $X$, what do we do for $Y$? Do we have two $\mathbb{P}$s? Or ... ?

These notes provide answers to these questions that took me ages to figure out :-)

So, I'm not going to repeat what's in Gupta's tutorial. It's already very complete and awesome :-) I'm going to assume you read that.

Next, imagine we have two Gaussians, represented by random variables $X$ and $Y$, and we want to form $aX + bY$, or perhaps $XY$, for whatever reason. And we wan to use measure theory. Just because. Well, because anything that looks like it will help with figuring out these formulae seems to use measure theory. So, after reading the first couple of references above, for measure theory, we have a probability space $(\Omega, \mathcal{F}, \mathbb{P})$, which is as follows:

- $\Omega$ is the sample space.  It's the space of all possible outcomes. eg if we were to roll a dice, this would be the set $\{1, 2, 3, 4, 5, 6\}$
- $\mathcal{F}$ is a set of subsets of $\Omega$. It represents different things we might want to observe. Like "the dice was at least 3", which would be the set $\{3,4,5,6\}$. $\mathcal{F}$ should basically contain all possible subsets of $\Omega$, in a hand-waving way, which is probably good enough for now
- $\mathbb{P}$ assigns a probability to each $\omega \in \Omega$. Or more concretely, to each the subsets $F \in \mathcal{F}$ ie, we can obtain $\mathbb{P}(\{\omega : \omega \in F \})$, for any $F \in \mathcal{F}$.

Ok, so lets say we have the Gaussian $X$. How does this fit in to this? $X$ is a random variable, which is simply a mapping, from $\Omega$ to some other space $\mathbb{R}$, the line of reals, or technically to $(\mathbb{R}, \mathcal{R})$, since we're not mapping points $\omega$, but sets of points, $F \in \mathcal{F}$, which each map to some subset $R \in \mathcal{R}$.

To define a Gaussian, normally we have some formula like $\exp(-(x - \mu)^2/2\sigma^2)$, normalized appropriately, or a multivariate variation on this. How doees this fit into this framework?

The probability is represented by the $\mathbb{P}$ bit. For each subset of $\Omega$, we have a probability value. In the case of a Gaussian, we'd probably want $\Omega$ to be just the line of reals, $\mathbb{R}$, or possibly in multidimensions, ie $\mathbb{R}^d$. But lets assume its in one dimension for now. And $\mathcal{F}$ will then just be all possible intervals on the real line, and unions of intervals, and intersections of intervals, and so on. And $\mathbb{P}(\omega)$ will be the gaussian equation, ie:

$$
\mathbb{P}(\omega) \propto \exp(- \frac{(\omega- \mu)^2}{2\sigma^2})
$$

Ok ... but .... we have two gaussians, one for $Y$. How does that fit in?

So, let's concretize this a bit. What do our Gaussians represent? Maybe $X$ is the distance it takes a car to stop, in an experiment. It's a real number, and let's say it's a Gaussian. $\Omega$ is all possible stopping distances. $\mathcal{F}$ is all possible subsets of stopping distances, in a hand-waving way. And $\mathbb{P}(\omega)$ is the Gaussian formula above. And $X$ itself? It can simply be $\omega$, ie $X(\omega) = \omega$.

So, now ... $Y$.... it wont have the same $\mathbb{P}$. How do we handle this? But thinking through the concretization, $Y$ might represent the stopping distance of a second car. And now it starts to become obvious: the sample space $\Omega$ should contain the possible outcomes from both experiments combined: each possible stopping distance for the first car, and each possible stopping distance for the second car, combined in a Cartesian way, like eg "(car1 = 1.5, car2= 3.0)", and another sample could be "(car1=2.3, car2=5.7)". How to combine these? Each of these, on their own, was a line in $\mathbb{R}$. We can combine them by simply giving each of them their own axis in $\mathbb{R}$. So the sample space $\Omega$ will now be in $\mathbb{R}^2$.

So, now we will have one single sample space $\Omega$, that combines all possible outcomes for car 1 with all possible outcomes for car 2, in Cartesian way. And then now we can express $\mathbb{P}$ for the first car, and $\mathbb{P}$ for the second car, and $\mathbb{P}$ for each of these possible combined outcomes. If the cars' stopping distances are independent of each other, then $\mathbb{P}$ for each possible outcome $\omega \in \Omega$ is a multivariate Gaussian, where the covariance matrix will be diagonal, since no covariance. The $\mathbb{P}$ for the first and second car can be obtained from this $\mathbb{P}$ by marginalization. Or possibly projection. Either way, we now have one single probability space $(\Omega, \mathcal{F}, \mathbb{P})$, which represents all possible outcomes of an experiment involving the two cars, and all possible subsets of such outcomes, eg "first car stops in less than 3, and second car in more then 2".

$X$ in this case will be simply the value of the first axis in $\omega$, ie the projection onto the first axis. $Y$ similarly will be the projection onto the second axis.

So, now we can consider what is $aX + bY$, or $XY$, since both $X$ and $Y$ are simply functions of the exact same probability space. I'm not going to do that here, since there are plenty of resources describing how to do that, eg the MIT Opencourseware "Fundamentals of probability" course, which is awesome :-)
