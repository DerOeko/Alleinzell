tags:: Neuroscience, Hebbian Natural Abstractions, Hebbian Learning, Natural Abstractions Hypothesis, AI Alignment, Human values

- ---
- ![hebbiannaturalabstractions.webp](../assets/hebbiannaturalabstractions_1738438804081_0.webp){:height 270, :width 225}
- **TL;DR:** *This post discusses the pointers problem, its consequences for language and thought, and the potential for resolving it with the concept of 'natural abstractions'. It introduces a new perspective from classic philosophy and neuroscience, showing how the Hebbian learning rule may form a basis for the emergence of natural abstractions in real intelligent agents. The end goal is to provide empirical evidence for the so-called natural abstraction hypothesis and give a more mechanistic explanation for abstractions emergence.*
- With this sequence, we (Sam + Jan) want to provide a principled derivation of the [natural abstractions hypothesis](https://www.alignmentforum.org/posts/Nwgdq6kHke5LY692J/alignment-by-default#Unsupervised__Natural_Abstractions) (which we will introduce in-depth in later posts) by motivating it with insights from computational neuroscience.
- Goals for this sequence are:
	- show why we expect natural abstractions to emerge in biological brains,
	- provide empirical evidence and a mechanistic explanation for the emergence of natural abstractions in biology, and
	- spelling out implications of the emergence of natural abstractions in biology.
- *Author’s note: This is currently my (Sam’s) main research project, but my first nonetheless. Happy to receive any feedback! Some of the original ideas and guidance come from Jan. I don’t expect you, the reader, to have solid background knowledge in any of the discussed topics. So, whenever you get lost, I will try to get you back on board by providing a more high-level summary of what I said.*
- ---
- # Why are ‘abstractions’ relevant?
  
  As alignment researchers, the higher-level problem we are trying to solve is: ‘*How do we teach an AI what we value?*’. To simplify the question, we assume that we already know what we value[¹](((679e78b3-c16d-4db6-a784-6e31dc2b696e))). Now, we’ve got to teach an AI that we value “things out there in the world”, e.g. trees. Specifying “trees” should be easy, right?
  
  … o no …
  
  You: »*Yea, so… we value trees. These for example. *gestures wildly**«
  AGI: »*Of course! So you only value these trees in your backyard? Okay, I will just quickly measure the constellation of molecules in—*«
  You: »*No, no, no! Stop, that’s not what I meant! Not only those, but you know… the idea behind the trees?  I also value trees that aren’t present here and certainly not their constituting molecules. Look, let’s go over to my neighbors backyard. These are trees too.*«
  AGI: »*Huh, this tree seems to be made out of papier-mâché.*«
  You: »*Ahhh uups… Yea, humans are fallible. Don’t treat my best guess estimations as unfailing sources of truth. Please note that I care about the [territory](https://www.wikiwand.com/en/On_Exactitude_in_Science) - not just the map in my head that might be mistaken.*«
  AGI: »*Wh- What? How should I know about the relation between your map and the territory?*«
- In a similar vein, John Wentworth [spells out](https://www.lesswrong.com/posts/gQY6LrTWJNkTv8YJR/the-pointers-problem-human-values-are-a-function-of-humans) the **pointers problem**[²](((679e78b3-9f80-487c-b1c1-e462bd11d629))): *‘An AI should optimize for the real-world things I value, not just my estimates of those things’.* He formalizes the problem as follows:
- “What functions of what variables (if any) in the environment and/or another world model correspond to the latent variables in the agent’s world model”.
- Let’s apply JW’s definition to the trees example from above.
	- The concept of a ‘tree’ (that’s what JW calls a ‘*latent variable’*) is not directly observable and is only clear in your head.
	- To make the concept observable, you have to specify the correct relationship between the concept in your head and the observable objects in the world (that’s what JW calls ‘*functions of […] variables (if any) in the environment and/or another world model*’).
	- Eventually, you want to transfer something (the concept of a tree) in your map to the AGI’s map (that’s what JW calls ‘*agents world model*’).
	- There is also an analogous view on the pointers problem from classic philosophy, called the ‘[problem of universals](https://www.wikiwand.com/en/Problem%20of%20universals)’. Similar to our story, we face issues when pointing towards the ‘*universal* of a tree’. We will explain the problem of universals using an example:
- Let’s consider the thought process of the divine mind[³](((679e78b3-a519-4e4e-ace2-72ca05619a7d))) when creating trees. Trees come in very different shapes or differing branching patterns. Now, who imposed on them that they are ‘trees’? Did the divine mind already have a category in mind and created *trees from an existing idea of trees, [universalia ante rem](https://plato.stanford.edu/entries/universals-medieval/notes.html#note-4)* (‘universals before the thing’)? Is the idea of a tree *realized in trees, [universalia in re](https://plato.stanford.edu/entries/universals-medieval/notes.html#note-4)* (’universals in the thing’)? Or did *we* create the idea of a tree by examining trees and throwing away unnecessary properties? This would mean that we formed something like an abstraction, *universalia post rem* (’universals after the thing’).
- As we will see, the *natural* part in ‘natural abstractions hypothesis’ suggests that we should expect universals, *in the things*[⁴](((679e78b3-d5d3-4e1b-b88f-1fade90a294f))).
- # ‘Hebbian’ Natural Abstractions?!
  
  After having read the previous sections, we want to keep in mind that:
- ‘Problems’ with universals only come across when you happen to study philosophy. Normally, we don’t face issues when communicating concepts. You balance out the imprecision in my expressions. Since our maps are roughly similar, you can fill in the necessary gaps. Concepts like ‘tree’ don’t confuse you, even if we have differing cultural upbringings. I mean the green, leaf-y thing that is not a cabbage. The concept of a ‘tree’ formed in our heads by mere observation.
- The discrepancy between the *theoretical* pointers problem and the situation in the real-world has a curious implication: An AGI that derives its concepts in the same way that we do, might have a much easier time understanding what we mean when we specify trees.
- To belabor the point further, we of course don’t primarily care about trees, we care about the concept ‘human values’. We need a formal specification between the concept in our head and observables in the world. A superintelligent AGI without such a specification will misunderstand what we mean with e.g. a ‘happy person’[⁵](((679e78b3-f216-4de4-97fb-535de630f4d2))).
- So, how is it that our maps are so similar? Is this the way things generally *have* to be? Does the emergence of concepts like ‘tree’ involve things like genetics? Should we expect aliens or artificial intelligence[⁶]() to share the same understanding of trees? And what happens when they don’t understand us?
- All these questions have something to do with our brains and how it learns. With this sequence, we want to explore exactly these questions using the brain as a working example. We choose the simple⁷ and plausible Hebbian learning rule that models how the brain learns in an unsupervised  way. The goal of this sequence is to provide empirical evidence for the so-called natural abstraction hypothesis in real intelligent agents and give a more mechanistic explanation for how abstractions emerge. We supplement John Wentworth’s information-theoretic perspective with our perspective from neuroscience/biology.
- If you want to dig deeper into John Wentworth’s perspective and the relevance of abstractions, we refer to [John Wentworth's posts](https://www.alignmentforum.org/posts/cy3BhHrGinZCp3LXE/testing-the-natural-abstraction-hypothesis-project-intro).
  
  ---
  
  Future posts will talk about the [mathematics behind 'Hebbian' Natural Abstractions]([[Mathematical Foundations of "Hebbian Natural Abstractions"]]) and the empirical background.
  
  ---
- # Footnotes
- 1) To convince yourself that this is already hard enough, read the [sequences](https://www.lesswrong.com/rationality), [The Hidden Complexity of Wishes](https://www.lesswrong.com/posts/4ARaTpNX62uaL86j6/the-hidden-complexity-of-wishes), [Value is Fragile](https://www.lesswrong.com/posts/cSXZpvqpa9vbGGLtG/thou-art-godshatter) and [Thou Art Godshatter](https://www.lesswrong.com/posts/cSXZpvqpa9vbGGLtG/thou-art-godshatter)
  id:: 679e78b3-c16d-4db6-a784-6e31dc2b696e
- 2) Actually, I first read about the pointers problem in [Abram Demski’s posts](https://www.lesswrong.com/s/SBfqYgHf2zvxyKDtB/p/5bd75cc58225bf06703754b3). In a vague sense, other authors talked about the problem at hand as well. Though, John Wentworth is the first to spell it out in this way. If you want to dig deeper into the pointers problem, read [John Wentworth’s post](https://www.lesswrong.com/posts/gQY6LrTWJNkTv8YJR/the-pointers-problem-human-values-are-a-function-of-humans), [this](https://www.lesswrong.com/s/SBfqYgHf2zvxyKDtB), [this](https://www.lesswrong.com/posts/7Zn4BwgsiPFhdB6h8/the-pointers-problem-clarifications-variations) and [this](https://www.lesswrong.com/posts/nFv2buafNc9jSaxAH/siren-worlds-and-the-perils-of-over-optimised-search).  The issue goes back to the [wireheading](https://arxiv.org/pdf/1605.03143.pdf) problem. Here, we want to prevent a generally intelligent agent to realize that it can stimulate its sensors, so that it receives *greatest reward all the time*. To solve this issue, we have to tell the agent that it should optimize for our intended outcome, ‘the idea behind it’. Natural abstractions are ought to be a way to specify exactly what we value.
  id:: 679e78b3-9f80-487c-b1c1-e462bd11d629
- 3) Or which other being or event may have created them.
  id:: 679e78b3-a519-4e4e-ace2-72ca05619a7d
- 4) *Natural* here means, that we should expect a variety of intelligent agents to converge on finding the same abstractions. Thus, abstractions are somehow embedded in things, otherwise we would expect agents to find different abstractions, or universals.
  id:: 679e78b3-d5d3-4e1b-b88f-1fade90a294f
- 5) Definitely not a [rectus grin](https://www.wikiwand.com/en/Risus_sardonicus), but a genuine smile. It does not understand what we are pointing at. But you do.
  id:: 679e78b3-f216-4de4-97fb-535de630f4d2
- ‘6) Aliens’ or artificial intelligence might have completely different [computational limitations](https://arbital.com/p/solomonoff_induction/?l=1hh) compared to humans. How do abstractions behave then?
- 7) The model is imperfect, but a suitable abstraction (huh) to talk about the topic at hand.