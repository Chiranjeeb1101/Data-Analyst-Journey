# Problem Framing & Issue Tree Deconstruction

> **Structuring complex, ambiguous business problems using MECE (Mutually Exclusive, Collectively Exhaustive) issue trees.**

---

## 🌳 The MECE Issue Tree Methodology

When presented with a high-level business challenge, an analyst uses an issue tree to break the core question down into non-overlapping, comprehensive sub-components.

### Example: Deconstructing Revenue Loss

```text
                               ┌── Drop in Order Volume ──┬── Drop in Active Customer Base
                               │                          └── Drop in Purchase Frequency
Total Revenue Decline (Q3) ────┤
                               │                          ┌── Drop in Units Per Order
                               └── Drop in Average Order ─┤
                                   Value (AOV)            └── Drop in Average Unit Price
```

---

## 📐 Steps for Effective Problem Framing

1. **Define the Core Business Problem Clearly**: Quantify the metric change, time frame, and baseline comparison.
2. **Deconstruct Mathematically**: Break the core metric into its exact mathematical constituents.
3. **Formulate Sub-Questions**: For each branch, create a testable sub-question.
4. **Prioritize Branches**: Use 80/20 intuition—focus exploration on branches with the largest volume or variance potential.
5. **Assign Data Tests**: Map each sub-question to specific database tables and SQL queries.
