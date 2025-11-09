---
title: Laws and Orders
author: Thomas Lumley
date: '2025-10-30'
slug: laws-and-orders
math: true
categories: []
tags: []
---

This is approximately my Belz Lecture for the Statistical Society of Australia (Vic/Tas), from earlier this week. 'Approximately', because it's from my notes. 

<hr>

<img src="images/Screenshot 2025-10-30 at 3.40.25 PM.png" width="90%"/>

Kia ora tātou

Thanks for the introduction and thanks to the Statistical Society of Australia for inviting me  .


It's traditional in a public lecture like this to have some sort of polemic. I did a polemic on Data Science for the NSW branch some years ago.  I don't want to do one on AI, because it would be obsolete like next Wednesday. I considered one on the importance of software, but that's a bit obvious and it's hard to make a full lecture about it. Also, you have plenty of people like Di Cook and Rob Hyndman to ask. 

Instead, I want to talk about a basic foundational issue in statistics: orderings.  A lot of data analysis is about saying one group is better than another: number go up or number go down.  A lot of statistics is about *uncertainty* in whether number go up or number go down, and how much.  I want us to go back a step and look at when "go up" or "go down" **are well-defined statements**.
"Laws", in this context, is the old-fashioned term meaning distributions. 

I gave a talk on somewhat this topic for Vic Biostat about ten years ago, but that one was focused more on testing. 

<hr>

<img src="images/Screenshot 2025-10-30 at 3.43.33 PM.png" alt="" width="90%"/>

The agenda: what do orders look like as data, what do people say about analysing ordinal data, what gets complicated with orders on distributions and orders as conclusions, and finally, what I want

<hr>

<img src="images/Screenshot 2025-10-30 at 3.49.01 PM.png" alt="" width="90%"/>

This is a popular self-rated general health question, from the SF-36 questionnaire. People sometimes call it the SF-1.   This question, especially in older people, is **amazingly** good at predicting future health over the next few years.  It can be answered over the phone, and presumably over the internet, and is more predictive than most health variables doctors can measure in person. 

<hr>

<img src="images/Screenshot 2025-10-30 at 3.52.08 PM.png" alt="" width="90%"/>

The Kiwi/Strayan translation.

These variables are ordinal: it's clear that each level is better than the next, but there isn't any obviously preferable set of numbers to assign

<hr>

<img src="images/Screenshot 2025-10-30 at 3.53.53 PM.png" alt="" width="90%"/>

A generic set of numbers to use is just 5, 4, 3, 2, 1.  My Seattle colleague Paula Diehr and her co-workers came up with the second set of numbers. These are based on probabilities of being alive and in good health at a later time point, using data from multiple cohort studies. 

<hr>

<img src="images/Screenshot 2025-10-30 at 3.57.11 PM.png" alt="" width="90%"/>

This is another example from health research. 

This "Desirability of Outcome Ranking" or DOOR was proposed for antibiotic trials, where adverse reactions to drugs can be a serious problem, especially for people already in poor health. 

There are lots of examples like this: you can get more information than with a binary variable, but it looks like an easy option because you don't have to assign numbers.

<hr>

<img src="images/Screenshot 2025-10-30 at 5.12.54 PM.png" alt="" width="90%"/>

And there are lots of examples outside health research, including one of special relevance to a lot of us: student evaluations.

Star ratings are ordinal; they usually get summarised as means, but that's the whole point at issue here. 

<hr>

<img src="images/Screenshot 2025-10-30 at 5.14.51 PM.png" alt="" width="90%"/>

And finally, the Beaufort Scale of wind intensity (as interpreted by a rigging company).  The Beaufort scale was initially based on rigging for Royal Navy sailing ships, along the same lines as the categories on the left.  It was then modified to use sea conditions (waves, spray), and then modified again for land (trees, leaves).  

The Beaufort Scale is somewhat different from the earlier examples in that there is an underlying ratio-scale measurement -- wind speed -- that just wasn't readily available in the old days. 


<hr><img src="images/Screenshot 2025-10-30 at 5.18.58 PM.png" alt="" width="90%"/>

These are all examples of ordinal variables. They have a clear ordering, but they don't have clear numbering, either because there isn't a preferred numerical scale underlying them or because there is a preferred numerical scale but we don't have access to it. 

Since you don't need to make your collaborators assign numbers to the levels it can look like the easy option.

<hr>

<img src="images/Screenshot 2025-10-30 at 5.24.44 PM.png" alt="" width="90%"/>

These are from a brief internet search on how people describe ordinal-scale data and its importance, and how to analyse it.

<hr>

<img src="images/Screenshot 2025-10-30 at 5.26.12 PM.png" alt="" width="90%"/>

If you actually look at Stevens (1946), he's less stringent about the protection of ordinal data than many people who invoke him

<hr>

<img src="images/Screenshot 2025-10-30 at 5.27.54 PM.png" alt="" width="90%"/>

The highlighted section is interesting. Stevens says means and standard deviations from ordinal data are "in error", rather than being "meaningless" or "in a state of sin".  He appears to be thinking of the psychological measurements under examination in the paper as like the Beaufort Scale, imperfect discretisations of an objective underlying ratio scale. 

This viewpoint doesn't fit the SF-1 or the DOOR health scale, and doesn't really fit restaurant ratings or student evaluations of teaching. 

<hr>

<img src="images/Screenshot 2025-11-03 at 5.23.45 PM.png" alt="" width="90%"/>

What does it actually take to respect the ordinal scale? These are some claims that people have made about what you need to do with ordinal data

The issue at the individual measurement level is related to group equivariance: ratio scales are equivariant under change of units with same zero, interval scales equivariant under change of units with different zero, nominal scales equivariant under complete relabelling. In this taxonomy,  ordinal data are equivariant under  monotone relabelling. That turns out to be much too strong for most purposes.

We can phrase the 'monotone relabelling' constraint in two ways:

- Strong form: it is meaningless to say one set of labels is better than another
- Weak form: there is a preferred set of numerical labels, but we may not know it or agree on it. 

<hr>

<img src="images/Screenshot 2025-11-03 at 5.27.23 PM.png" alt="" width="90%"/>

Rank tests would respect ordinal scale if we used ranks just within each sample -- but we'd lose all the information. 

<hr>

<img src="images/Screenshot 2025-11-05 at 1.05.24 PM.png" alt="" width="90%"/>

If, say, 
$${\textrm{logit}}\,P(Y\leq k)=\alpha_k-x'\beta$$
then by construction $x'\beta$ is a one-dimensional summary and the different categories only differ according to $\alpha_k$ in a way that can't cause problems.

Also, I'm talking about data here, not models. We will come back to models.

<hr>

<img src="images/Screenshot 2025-11-05 at 1.08.42 PM.png" alt="" width="90%"/>

Suppose you have the choice between two interventions

- Green moves one person from above average to a bit average
- Red moves one person from above average to pretty average

The unambiguous ordering on individual outcomes tells us Green is better

<hr>
<img src="images/Screenshot 2025-11-05 at 1.10.41 PM.png" alt="" width="90%"/>


- Green moves one person from above average to a bit average
- Red moves one person from a bit average to pretty bloody average

The unambiguous ordering on individual outcomes can't tell us which of these is better

<hr>

<img src="images/Screenshot 2025-11-05 at 1.12.53 PM.png" alt="" width="90%"/>


- Green moves three people from above average to a bit average
- Red moves one person from above average to pretty average

The unambiguous ordering on individual outcomes can't tell us which of these is better

An ordering on individual outcomes **doesn't** give us an ordering on samples or on distributions.

<hr>

<img src="images/Screenshot 2025-11-05 at 1.15.46 PM.png" alt="" width="90%"/>

Individual to group orderings is one problem. Another is going from orderings on a pair of groups to orderings on multiple groups.

Ignore equality for now (equality doesn't make the problem simpler). There are three possible pairwise comparisons and so `$2^3=8$` possible sets of pairwise comparison results. There are only six (`$3!$`) possible orderings, so two of the sets of pairwise comparison results don't lead to an ordering.

More generally, with `$k$` groups you have `$2^{k\choose 2}$` sets of pairwise comparisons and `$k!$` possible orderings. 

In this setting the other two sets of results are perfectly non-ordered "rock-paper-scissors" comparisons. 

<hr>

<img src="images/Screenshot 2025-11-05 at 1.21.10 PM.png" alt="" width="90%"/>

Rock-paper-scissors is a wonderful invention: it lets you do fair choices without a trusted source of random numbers. 

It has arisen in lots of societies around the world.  I particularly like the variant with $$\text{hero} \succ \text{tiger} \succ \text{hero’s mother} \succ \text{hero}$$

Obviously the rock-paper-scissors ordering can't happen with the t-test, because that orders distributions by their means, which is a perfectly ordinary linear preorder on numbers.  But can it happen with some tests?

<hr>

<img src="images/Screenshot 2025-11-05 at 1.29.46 PM.png" alt="" width="90%"/>

In the 1970s, Brad Efron invented a set of non-transitive dice. Martin Gardner popularised the idea in his *Mathematical Games* column in *Scientific American*. 

The dice in the picture (from Wikipedia) have the same number on the opposite hidden face as on each visible face. You can verify that Red beats Green with probability 5/9, Green beats Blue with probability 5/9, and Blue beats Red with probability 5/9.

The "beats at dice" comparison is the same as the statistic for the Mann-Whitney U-test. So the Wilcoxon/Mann-Whitney test says Red is higher than Green is higher than Blue is higher than Red.

Now, you may well not care about that *specific* comparison of distributions, but there is a broader implication. *Whatever* ordering on distributions you *do* care about, the Wilcoxon/Mann-Whitney test does not agree with that ordering. It is inconsistent with *all* orderings of distributions.

[Timothy Gowers and the internet](https://gowers.wordpress.com/2017/07/25/intransitive-dice-vi-sketch-proof-of-the-main-conjecture-for-the-balanced-sequences-model/) have a paper (a Polymath project) showing that this non-transitivity is in some sense the *generic* behaviour.  That is, if you generate `$n$`-sided dice by sampling their faces from `$1,\dots,n$`, the Wilcoxon/Mann-Whitney test will agree with the ordering by means if the means are different, but if the means are the same then 

`$$P(A\prec B\mid A\prec C, C\prec B)= 1/2+o(1)$$`

<hr>
<img src="images/Screenshot 2025-11-05 at 1.43.12 PM.png" alt="" width="90%"/>

What happens if you use the three-group Wilcoxon test (aka Kruskal-Wallis test) on the three distributions? It depends on the groups sizes.

Suppose A and B are the same size:

- If C is small, A beats B
- If C is about twice as big as A and B, it's a tie
- If C is four times larger than A and B, B beats A

<hr>

<img src="images/Screenshot 2025-11-05 at 1.47.10 PM.png" alt="" width="90%"/>

It's clear that a test based on a univariate real-valued summary for each group is transitive. The converse is almost true.

If you have a preorder (an ordering allowing for things to be the same) you can take equivalence classes to get a linear order. Any reasonable linear order can be embedded in the reals.  The fundamental result here is Debreu's theorem in economics, which says that any continuous preorder on a separable space is representable by a real-valued utility.

Distributions with the uniform ('Kolmogorov') norm are not a separable space, so Debreu's theorem doesn't apply out of the box, but it can be extended. 

One exception: suppose you order distributions on the lower quartile and then break ties using the upper quartile.  The ordering on all possible distributions is the same as the lexicographic ordering on `$(0,1)\times (0,1)$`, which is too big to be represented by reals. It's also a useless test -- it isn't consistent, because the ordering is too big.

There are three other things that can go wrong, all of which are set theory and unreasonable for statistics: your test ordering could contain a long line, an Aronszajn-like chain, or a Souslin chain.

So, any transitive test that is any use will be representable by a real-valued univariate summary statistic -- unlike most rank tests. 

<hr>

<img src="images/Screenshot 2025-11-05 at 1.56.22 PM.png" alt="" width="90%"/>

"We destroyed the data analysis in order to save it"

A theoretically coherent alternative, but not all that viable.

<hr>

<img src="images/Screenshot 2025-11-05 at 1.58.15 PM.png" alt="" width="90%"/>

The theory is fun, and Dan Gillen and I wrote a paper about it, but is this actually an issue?

Yes, actually it is actually an issue!

These are real choices and maths can't make them for you

<hr>

<img src="images/Screenshot 2025-11-05 at 2.44.52 PM.png" alt="" width="90%"/>

Stochastic dominance is quite reasonable for active vs control experiments in some settings. Some classic examples:  turning gene expression on/off, insecticide on flies, muscle relaxant for mice balancing on a rotor, anticoagulant to prevent clotting

It's less plausible for *active control* or for composite outcomes (two insecticides, two downstream gene expression levels, two muscle relaxants, clotting+bleeding outcomes from anticoagulant)

One-dimensional location-shift families are less plausible

<hr>

<img src="images/Screenshot 2025-11-05 at 2.46.57 PM.png" alt="" width="90%"/>

This was from a JASA commentary on the 100th anniversary of the t-test. 

To be fair to the distinguished statisticians involved, there was sort of an implicit context of location-shift comparisons.  It's true under location shift. There has been a lot of discussion in mathematical statistics about two-group comparisons under location shift, which has been valuable because it informed the understanding of statistical information and the efficiency of tests. 

Even so, 100 years after the t-test, questions of its robustness should go beyond adjusting the tails in a location shift model.   

If you don't assume a location shift the t-test and the Wilcoxon test don't have the same null and don't even need to agree in **direction** of departure from the null

<hr>

<img src="images/Screenshot 2025-11-05 at 2.50.56 PM.png" alt="" width="90%"/>

Zaremba (1962) is the earliest paper I know about that tackles the "test for the median" misinterpretation of the Wilcoxon/Mann-Whitney test, and it has this nice quote about being able to tell.

Scott Emerson is a former colleague from Seattle. 

<hr>

<img src="images/Screenshot 2025-11-05 at 2.53.49 PM.png" alt="" width="90%"/>

Savage's axioms are usually invoked by smug Bayesians against frequentist testing, because of the first part of the conclusion.

The second part holds even for Bayesians: coherence requires assigning numerical utilities to ordinal data. 

As with the first part, this doesn't necessarily imply that all analyses should assign numerical utilities to ordinal data, but it does mean that any successful approach must implicitly do so to some level of approximation. 

As with priors, you can try to look at decisions over a community of utilities, and you probably should, but that doesn't *solve* anything. The decisions will typically vary according to the utilities assigned. 

<hr>

<img src="images/Screenshot 2025-11-09 at 5.58.06 PM.png" alt="" width="90%"/>

`lm` and `glm` have what I call **robustness of interpretation** -- they can be taken as models for means no matter what the true distribution is.   I don't think we understand any of the ordinal models that well, and we know enough to be concerned. For example, the score tests for the proportional odds and proportional hazards models are rank tests that are not transitive.

There's [a recent paper](https://pubmed.ncbi.nlm.nih.gov/40997285/) says you don't need to worry much about proportional odds for two-sample tests, because proportional odds automatically holds under the null hypothesis that the two grouops are the same.

This is true, but it's true for the *strong* null hypothesis that the two groups are identical.  It's not true for the weak null hypothesis that neither group is better -- th weak null intrinsically requires defining "better".  A placebo-controlled trial *might* care mostly about the strong null, but an active-control trial doesn't.  And even in a  placebo-controlled trial a treatment might have both good and bad effects.


Now, we can always take a fitted ordinal model and just compute marginal distributions at covariate values of interest.  That's actually a good idea -- but it doesn't solve the ordering problem, it just exposes the problem.

<hr>

<img src="images/Screenshot 2025-11-09 at 6.12.33 PM.png" alt="" width="90%"/>

For the DOOR outcome I mentioned earlier, the stochastic dominance assumption doesn't seem especially like.  In fact, it seems quite plausible that novel antibiotics with more effectiveness might actually  be more toxic than the current standard.

For some trials, people have put more effort into thinking about whether a treatment is likely to affect all levels of the outcome in the same way.  They might also have looked at past datasets to see if comparisons between interesting subgroups of the data typically do satisfy stochastic dominance.

<hr> 
<img src="images/Screenshot 2025-11-09 at 6.58.03 PM.png" alt="" width="90%"/>

Ordinal data can be very valuable, but it's not the easy option.  

Binary data has a unique ordering, and for numeric (interval/ratio) data we are accustomed to choosing between orderings. A lot of traditional ordinal data approaches don't provide an ordering over distributions in any internally-consistent way without strong assumptions.

<hr>

<img src="images/Screenshot 2025-11-09 at 7.01.44 PM.png" alt="" width="90%"/>

##$# Issues that came up in questions or afterwards

- I should have made it clearer that it may not be the *statistician* who evaluates the tradeoff. For example, in medical treatment it would ideally be the individual patient. In government it may be the Minister rather than the official stats agency. The statistician's job is to make sure that people know evaluating the tradeoff is needed.
- This *is* a lot like other utility tradeoffs: eg equity vs number of people helped in public health. Someone needs to decide; the problem can't just delegated to maths.
- Someone (?Cameron Patrick) asked about how this differs from Frank Harrell's views and why.  I think (having given a version of this talk at his department and talked to him about this) that Frank regards failures of ordering as less important and less plausible than I do. He has also been more interested in ordinal scales as a way of pushing back against dichotomisation in medical statistics.