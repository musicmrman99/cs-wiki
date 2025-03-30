# Imperative vs. Declarative Style

- Styles
  - **Imperative** styled solutions define *how* to get to the desired result (as process): do A, do B, do C, done.
  - **Declarative** styled solutions define *what* the desired result is (as data), which then must be given to a *reconciler* that determines how to get to that result.

- In imperative style, actions are taken that result in a new state. Each action results in an intermediate state until the final action, which results in the final state.
- In declarative style, no action is taken and no intermediate state is reached/created. The final state is represented directly as data. No instructions of how to get to the final state exist in the declarative style.

This may seem confusing, as this implies that only components of systems written in the imperative style can *do* anything, and therefore reach the desired state. If you can't reach the desired state, how are declarative components useful? Components using the declarative style are often abstractions - they remove information irrelevant to the user, which allows them to focus on what is important to them. The *reconciler* is written in imperative style, and actually performs the operations that are needed to reach the state given in declarative style.

- Examples of imperative style
  - 

- HTML (excluding embedded JS), CSS (excluding imports), and Terraform/HCL are all examples of declarative languages.
- An *executor*, aka. [???] an interpreter, is a specific kind of reconciler.

- Examples of declarative style

  - The `render()` method in React is usually written in declarative style. You return an *object* that represents the desired state. React calls this method when it determines that it needs to (according to various rules that aren't relevant here). It *reconciles* the resulting object (the target state) and the current DOM (the current state) by determining what series of mutations to the DOM must occur for the DOM to be in the target state, then performs each mutation (producing an intermediate state each time) until the target state is reached.

  - The Terraform engine
