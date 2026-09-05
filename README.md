# Artur

I have been writing software for more than 20 years, 14 of them in Java. I work as a senior
backend engineer, and most of what I think about now is what changes when the model
writes the code, and what does not.

My current answer is that engineering discipline matters more than ever. A codebase
with clear boundaries, good types and real verification gets useful work out of an
agent. A codebase without them still gets an answer. It just looks right, which costs
more than being obviously wrong.

## Current work

An integration platform for the Polish national e-invoicing system, in Java 21 and
Spring. It generates FA(3) invoices, submits them online, runs the offline flow with
its queue and deadlines, handles technical and business corrections, and retrieves
status and official confirmations. Twelve Gradle modules with hexagonal boundaries
that ArchUnit checks on every build. The repository is private.

The parts I would defend in a review are the boundaries rather than the features.
Retries are bound to operations that are provably safe to repeat, so an invoice upload
never goes out twice on its own. A submission whose previous attempt is unresolved is
refused rather than retried, because unresolved is a state of its own and not a variety
of failure. Rate limiting honours the interval the server asks for instead of guessing
one.

The release candidate was verified end to end against the tax authority's official test
environment. A green local build was never accepted as evidence of compliance, because
it only proves the code agrees with my own mocks.

## What I write about

I publish on [LinkedIn](https://www.linkedin.com/in/arturprzychodzen/), for engineers and sometimes for managers. Three recurring threads now: how
code structure becomes context an agent can rely on, how you decide what is actually
safe to merge, and what pattern recognition still buys you once the first draft is free.

## Elsewhere here

Older public work: event sourcing in Java, and an agent project in Python. The current
work is closed source. The writing about it is not.
