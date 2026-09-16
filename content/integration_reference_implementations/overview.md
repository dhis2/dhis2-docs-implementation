# Integration reference implementations { #integration_reference_implementations }

## Introduction { #iri_introduction }

A reference implementation is a working example that shows one way to solve a common integration problem. You can run it, explore how it's put together, and use it as a starting point for building your own solution. It is meant to be studied and adapted, not installed and used unchanged.

> **Note**
>
> A reference implementation is not ready-to-use software, and it is not officially supported the way a DHIS2 core product is. It needs to be reviewed and adjusted to fit your own systems, data, and security requirements before it can be relied upon.

Building an integration from scratch takes time and is easy to get wrong, especially when the same kinds of problems come up again and again across different implementations. A reference implementation gives your team a tested example to learn from, so effort goes into adapting the parts that are genuinely specific to your context, rather than re-solving problems that have already been worked out elsewhere.

## Common integration patterns { #iri_common_patterns }

These examples tend to cluster around a handful of recurring problems rather than being one-off curiosities. A common one is connecting DHIS2 to an external system that already holds information about a person — an identity registry, a civil registry, another health record — so that a health worker doesn't have to re-enter details that are already known elsewhere. Another is laboratory interoperability: exchanging orders and results with a laboratory information system so that specimen and test data move between DHIS2 and the lab without being re-entered on either side. A third is letting information move safely between different services and providers, using a shared way of identifying and authenticating someone, while still respecting who is allowed to see what.

Each reference implementation is built around one specific project's actual need, and some are more mature than others: some are documented, tested end-to-end examples meant to be adapted directly, while others are earlier, more exploratory demonstrations meant to show that an idea works before anyone commits to a specific design. Either way, the underlying pattern usually shows up well beyond the original project, which is exactly why it is useful as a shared example rather than something built again from scratch every time.

## Adapting a reference implementation for deployment { #iri_adapting }

Turning a reference implementation into something you can actually deploy is a process of deliberate adaptation, not a checklist to click through. It means:

- **Decide what to keep** as-is and what to replace with your own systems.
- **Adjust the example** to match the data you actually need to exchange, which will rarely be identical to what it started with.
- **Swap out example components** for the real systems in your environment, such as a different lab system or a different identity provider.

> **Tip**
>
> Keep the automated checks that ship with the example in place as you make changes. They give you a fast way to confirm your adaptation still works as intended, rather than discovering problems only after deployment.

## Who should be involved { #iri_who_should_be_involved }

This adaptation work is rarely something one person does alone, and it rarely happens in a single pass. It usually involves whoever owns the systems on the other side of the integration, the team responsible for data protection and information security, and the people who will end up supporting the result day to day.

Bringing them in early, while the example is still being explored rather than already locked into a deployment plan, tends to save time later: it's much easier to change direction on a working example than on something that has already gone live. Treating the reference implementation as a shared starting point for that conversation, rather than a finished answer to hand over, is usually what makes the eventual adaptation hold up.

## Confirming your adaptation is production-ready { #iri_production_ready }

Before treating an adapted reference implementation as production-ready, it's worth working through a short set of questions with that same group of people:

- Has someone reviewed it against your organization's own security and data protection requirements, not just the example's assumptions?
- Have you confirmed it handles your real data, including the messy, incomplete, or unusual cases the example data may not have covered?
- Have the example-only components — test systems, sample identity providers, demo data — been replaced with your actual systems?
- Do the automated checks that came with the example still pass after your changes, and have you added checks of your own where the adaptation introduced something new?
- Does your team understand the design well enough to support it going forward, rather than treating it as a black box inherited from the example?

## Conclusion { #iri_conclusion }

None of this is meant to discourage teams from using reference implementations — quite the opposite. They exist precisely because starting from a working, well-thought-through example is faster and safer than starting from a blank page, and the questions above are simply the difference between borrowing that head start responsibly and copying it blindly. Used this way, a reference implementation shortens the distance between having an integration problem and having a solution your organization actually trusts and owns.
