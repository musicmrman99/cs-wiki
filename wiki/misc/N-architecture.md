- architecture is how we:
  - structure
  - define
  - talk about

  software

- some people say architecture is best defined as "the stuff we need to get right", because it's the stuff that has the greatest impact on effectiveness and change down the line

- the boundaries between coding, design, and architecture are blurred
- 'architect elevator' (from engine room to board room)

1. Learn about the context
   - what is it that you want to achieve, where are you currently with it
   - scale (num. users), speed, security, availability, safety
     - and the other 'ility's
   - how fast and easy will it be to develop?

   - you need to build this as an architect - nobody can tell you
   - the goal here isn't to solve the problem
   - the less certain we are about something, the more flexible the design/architecture needs to be in that area to be able to change it later
   - the goal is to make a model of the system that can cope with being wrong about things

   - good to keep models at different levels of granularity

- your job after that is to evaluate, sense-check and update the state of the context

2. experiment
   - goal: rule out designs that don't work, and find the issues with the things that might work.
   - the goal is *not* to prove that something will work

   - if you try to get to 'perfect' (which doesn't exist), then you won't have time to build the thing in the first place
   - design, like development, must be iterative and risk-based

3. iterate
   - solve the problems you didn't know you needed to solve, or didn't know how to solve, as you go forward
   - optimise for learning and managing complexity

- "work now to minimise work later" - Dave Farley
- "work here to minimise work everywhere else" - me

## Wider Reading

- https://www.youtube.com/watch?v=wQYRl--58zM
