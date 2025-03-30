# Types

## Essential vs. Emergent (aka. Definition vs. Description)

### Key

In the following explantions:

- `O` is 'our' property/type (the thing being defined/described)
- `T` is 'their' property/type (the description that is used to define/describe `O`)
- `U` is the 'user' of the above properties/types (the person/computer doing the defining/describing)

### Explanations of the Terms

I would explain what I mean by 'essential' and 'emergent' as follows:

- If something (T) is **essential** to something else (O), then O must be/have T (or it wouldn't be O) - O is *defined* in terms of T. When something (O) is defined as something else (T), then it (O) is that thing (T) because you said it (O) was.

- If something (T) is **emergent** from something else (O), then O happens to be/have T - O can be *described* in terms of T (but doesn't have to be). When something (O) is described as something else (T), then it (O) is that thing (T) because it (O) matches the pattern of that thing (T) that is defined elsewhere.

### Implied Existence of Emergent Properties?

The first and most important thing to talk about in relation to these explanations is whether emergence makes properties/types necessarily come about. For example, if you assemble two wheels, several gears, a chain, handles, and a seat together, does it become a bicycle, whether you know what a 'bicycle' is or not, and whether you want it to become a 'bicycle' or not. Let's talk about these two points in turn.

First, if we don't know what a 'bicycle' is (ie. if we haven't *defined* it), then the above assemblage doesn't become a 'bicycle'. It remains 'something with two wheels, several gears, a chain, handles, and a seat that is a mode of transportation' (presuming we've defined all of those terms). This bicycle example may be slightly difficult to follow as a demonstration of this argument because you already have an *assumption* about what a 'bicycle' is - ie. you *have* defined it, if only implicitly from your *experience*. However, remember that while we often take the definitions of common concepts for granted in the real world, we can't in the software world - a computer can't know what anything is (including a 'bicycle') unless you tell it. If we pretend for a moment that the whole world knew that 'bicycle' was 'a spaceship with two rotating plates', then would the above assemblage of two wheels, several gears, a chain, handles and a seat be a 'bicycle'? Of course not.

This is what I call the **nominality argument** - that for something (O) to be *described as* something else (T), that something else (T) must first be *defined*.

Second, presuming that we go back to using the standard definition of 'bicycle' again, if we didn't want the above assemblage to be a 'bicycle', could we stop it from being one? To this, I would answer "no." In software, this is a useful property in some ways, and a problematic one in others, as it allows anyone (U) to describe anything (O) as anything else (T) so long as it (O) conforms to the description of that thing (T). But regardless of that, in software at least, there is another important argument here: just because it exists doesn't mean we care about it.

This is what I call the **usefulness argument** - that for something (O) to be *worth* being described as something else (T), that something else (T) must be useful to the user/software engineer/you (U).

### Main Differences

Here are some of the main differences between 'essential'/definitions and 'emergent'/descriptions that relate to software engineering:

- Time
  - If O is defined as Y and Z, then Y and Z must be defined before O has any meaning.
  - If O is described as Y and Z, then O exists independently from Y and Z, so they can be defined in any order.

- Ownership of Change
  - If O is defined as Y and Z, then for O to be defined as anything other than Y and Z, another property/type must be defined (X), O must be changed (re-defined) to include it, then others can use the new definition of O. Definition is done by O.
  - If O is described as Y and Z, then for O to be described as anything other than Y and Z, another property/type must be defined (X), then others can use it to describe O. Description is done by the user of O

- Orthognality (and therefore Multiplicity in general)
  - If O is defined as Y and Z, then things other than O may be defined as Y and/or Z, but O can only have one definition (of Y and Z).
  - If O is described as Y and Z, then things other than O may be described as Y and/or Z, and O may be described as things other than Y and Z.

## Other things

https://en.wikipedia.org/wiki/Strongly_typed_identifier
https://en.wikipedia.org/wiki/Domain-driven_design
