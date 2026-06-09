# Portfolio Methodology

## Review Focus

My current focus is the bridge and cross-chain contract layer.

In practice, I mainly review:

- token-specific bridge paths
- gateway logic
- router behavior
- deposit and withdrawal flows
- finalize paths
- escrow and release logic
- token-pair checks
- token accounting assumptions
- bridge-specific deviations across different systems and forks

## Scope Boundary

My default scope is the application / contract layer between L1 and L2 or L3.

I do not treat deeper rollup internals such as Nitro, compression, prover logic, or lower-level messaging internals as the main scope by default.

## How I Review Code

I usually start from a concrete token path.

For example, I take the ERC20 bridge path and then break it into the main user flows:

- deposit flow
- withdrawal flow

From there, I read the functions inside those flows and separate them into different review layers.

## Review Layers

### Flow

I first identify the main flow itself:

- where the path starts
- how the message is constructed
- how the path crosses L1 and L2 or L3
- where the final credit or release happens

### Function-Level

Inside the flow, I review the key functions one by one:

- what the function does
- what assumptions it relies on
- what invariants it should preserve
- what part of the logic is security-critical

### Out-of-Flow

After the main flows, I review functions that are not part of the main user path but still affect the security model:

- support logic
- helper functions
- routing mutations
- admin-like behavior
- fallback or recovery branches
- init or upgrade surfaces

### Global

At the end, I summarize the system-level guarantees:

- token accounting
- token-pair assumptions
- routing model
- trust assumptions
- cross-chain message handling

## Review Workflow

My usual workflow is:

1. Choose a concrete bridge path, such as the ERC20 path.
2. Split it into the main flows, usually deposit and withdrawal.
3. Trace the main functions inside each flow.
4. Review the function-level logic and draft candidate invariants.
5. Review out-of-flow functions that still affect the bridge model.
6. Summarize the global assumptions and system-level guarantees.
7. Write the final review in a structured form.

## How I Use AI

I use AI as a support tool for:

- drafting candidate invariants
- improving structure
- clarifying wording
- helping turn notes into cleaner review writeups
- stress-testing reasoning

I do not treat AI output as final by default.

I manually verify candidate invariants, assumptions, and reasoning against the code, and I keep the final security judgment myself.
