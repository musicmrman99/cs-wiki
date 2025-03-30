# The 7 Cs

These are some of the most important high-level principles of information design that also apply to software.

| No. | Principal     | The System ...                                                          |
|-----|---------------|-------------------------------------------------------------------------|
|   1 | Correct       | Is true and accurate to the reality and/or vision                       |
|   2 | Comprehensive | Includes all concepts and details relevant to the reality and/or vision |
|   3 | Consistent    | Is in the equivalent form with least internal variation                 |
|   4 | Coherent      | Is useful for the purpose of the vision                                 |
|   5 | Concise       | Is in the equivalent form with least semantic content                   |
|   6 | Clear         | Is expressed in the most easily understandable way                      |
|   7 | Complete      | Is functional/usable in its current state                               |

---

## Knowledge Systems

A knowledge system is a system (a set of objects governed by a set of self-consistent rules in a given environment) in which:
- The objects are pieces of information or ideas
- The rules are how those ideas interact or allowed to interact

## Coupling & Cohesion

Coupling and cohesion are common metrics that support understanding of core design principles. They are commonly used in software design in relation to code, but apply in all knowledge systems, and to the full extent of each knowledge system.

- Coupling is generally about one thing being 'connected' to another. In SE, that translates to one thing being dependent on another, whether directly or indirectly. Coupling is about the effects of change - it's the answer to the question, "if you make a change in one place, what else must change to make the system correct, consistent and complete?"
  - for example, if the process for ordering a takeaway needs to be changed in a food company's app, then what else would need to change to make the system correct, consistent and complete? The definitions of an Order? The UI? The code tests? The code documentation? The app's user documentation? The staff training? The processes for ordering other things? The inventory system? The finance system?

- Cohesion is generally about one thing being 'related' to another. In SE, that translates to how closely one thing is associated with the domain concept another thing is associated with.

- Like all knowledge systems, coupling and cohesion operate in all S-G spaces, eg. lines of code, functions, modules, packages, applications, networks, teams, organisations and society.


- both coupling and cohesion are objectively identifiable at the code level
- **coherence** (one of the 7 Cs), is subjective and relates to how closely

---

- Modular - Break your system into parts that encapsulate knowledge (SOLID)
- Compositional - Systems can both use other components, and be used as components.
  - "always design a thing in its next larger context" - Eliel Saarinen (from Kevlin Henney)

---

- Constructivist vs. restrictivist -

---

- Domain-oriented
  - There is a design approach specifically named Domain-Driven Design (DDD), which does include many of the things I mention here, but is not specifically what I'm referring to here.

---

- SE should be:
  - Constructive  - Aim for a system that aligns with the domain (a 'system of meaning')
  - Collaborative - Everyone must discuss and agree on the language/words to use
  - Iterative     - Synthesis and analysis of the problem and solution in a repeating cycle
  - Segmented     - Cycles are short, so you can reflect on:
    - what has been learned
    - what remains to be learned
    - what cannot be learned, because it keeps changing

## Constructive

?

## Collaborative

- There are many different ways that people can misinterpret each other
  - Language is not the direct transfer of knowledge from one person to another
  - Context and experience are just as important as the symbols (often words) we use when deriving meaning

- Trying to have a conversation with another developer who believes very different things to you is like "trying to have a conversation with a flat-Earther." (Kevlin Henney)

- "People call the same things by many different names, and what's intuitive for one programmer seems strange to another."
  - BeauWilkinson (https://wiki.c2.com/?VeryLongDescriptiveNamesThatProgrammingPairsThinkProvideGoodDescriptions)

### Naming Things

- Excessively short and long names of concepts
  - https://wiki.c2.com/?VeryLongDescriptiveNamesThatProgrammingPairsThinkProvideGoodDescriptions
  - Bad Enterprise Tricks (Kevlin Henney) - https://www.youtube.com/watch?v=FyCYva9DhsI

  - If some part of the name are actually associated with a wider context, then you can factor it out into a parent module (this is the most common issue/solution)
  - If some parts of the name are 'filler' words like "data", "information", "handler", "manager", "helper", "compute", or "processor" (not an exhaustive list), then you may be able to remove them entirely - they're implied by the nature of a module (the implementation of a type). All modules contain data/information, handle things, manage something, and compute/process things, and many have supporting 'helper' functions in them. These terms describe any type/module, not just your type/module - focus on what makes yours unique among the other concepts you have.
  - Some concepts do just have long names, like 'HarmonFiddleWatleyAndSprung' (like the example internationalisation convention example in the above c2 wiki page)

In the above example, I would suggest you could structure the modules as follows:
```
your.app.namespace
\- internationalisation
   |- Convention
   \- conventions
      |- private HarmonFiddleWatleyAndSprung : Convention
      |- private GreblitchBorgAndFungal : Convention
      |
      |- harmonFiddleWatleyAndSprung : HarmonFiddleWatleyAndSprung
      \- greblitchBorgAndFungal : GreblitchBorgAndFungal
```

- `internationalisation` as a concept is likely to have things other than Conventions associated with it in your software, but it doesn't describe a type of thing (an interface), it describes a group of types of things (a package) related by a common context and purpose (or set of purposes).
- An `internationalisation.Convention` is a type of thing that isn't specific enough to be used directly (an abstract type).
- A static list of `internationalisation.conventions` is also included, which includes two types of conventions (they're probably made up). The 'type' and 'instance' of the conventions are separated in the above model because object-oriented languages often require it. Some languages don't, and in those languages, the behaviour should be directly embedded into the 'instances' of these types of `internationalisation.Convention`.

None of the above names are more than 30 characters long, which is a good general guideline for maximum length. That is not to say that names must not be longer than that, but rather that if they are longer than that, you should examine why they are as long as they are.

## Iterative and Segmented

- Synthesis/analysis of problem/solution in cycles

- When learning SE, it's often easiest to write small programs, as they allow for the fastest iterations. That means you can reflect on what you've built sooner, and learn what went wrong, why it went wrong, and a better way of doing the job.

- However, this can also be applied to larger systems. Modern agile development methodologies often emphasise creating smaller, well-defined pieces of work before starting them to allow for shorter iterations. This is so that at the end of each piece of work, you can reflect on what you've learned and to apply that knowledge into the future.

- Things to consider at 'points of completion':
  - what do we now know that we didn't before?
  - what do we now (or still) know we don't know?
  - what can we not know? what knowledge keeps changing?

- This is most useful for misunderstandings of the domain model

## ???

- A bit about how people perceive things as 'abstract'
  - People not familiar with maths or programming often consider them 'abstract', while people who are, often consider them 'concrete'. Why is this?
  - As a non-computing example, take physics. Considering only the maths of physics removes the *experience* of the world and turns it into 'abstract' symbols that merely represent the things we experience, which I believe is the source of the idea that the maths of physics is abstract. But if you ignore the maths, you remove the *details* of how the world works. Both of these are abstractions, just in different forms.
  - The same is true of programming - code abstracts away the resulting experience of using the software, while merely using the software abstracts away the implementation.

- Types of programs:
  - Requirements are not dependent on the context of use
    - The requirements never change

  - Requirements are uni-directionally dependent on the context of use
    - When the context changes, the requirements change

  - Requirements are bi-directionally dependent on the context of use
    - When the context changes, the requirements change
    - When the requirements change (and are implemented in the software), the context changes

  - As an interesting example of the last case
    - social media
      - the classic example of a system that modifies its own requirements due to its use

    - predictive systems
      - another, perhaps more recent example of a system that modifies its own requirements (ie. its predictions) due to its use (the interpretations of its predictions and actions based on them)
      - when computers begin using AI to predict the future, but the predictions change the future by people interpreting them and acting on them, is it really possible for them to predict the future?
      - This essentially boils down to the classic time-travel paradox: if you can change the future by knowing the future, then you didn't know the future to begin with.
      - The only solutions to this paradox are either that we can't know the future, or that we can't change the future (or both).
      - AI can't know the future, it can only guess based on trends of the present, so will never be perfectly accurate at prediction. Error is inherent.

## Wider Reading

- https://www.youtube.com/watch?v=ndnvOElnyUg
- https://mahb.stanford.edu/blog/beyond-computational-thinking-cloud-unknowing-21st-century/
