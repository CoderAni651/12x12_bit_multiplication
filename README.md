Traditional multiply-by-add methods generate partial products and then reduce them into the final product. This design:

Generates 12 partial product rows (one per multiplicand bit).

Uses a small Carry-Save Adder (CSA) tree to reduce partial products in stages (fast, no long carry propagation).

Uses a hybrid final adder to perform the final carry propagation with a balance of area and timing:

Ripple-Carry Adder (RCA) for least-significant chunk (smaller, low area).

Carry Lookahead Adder (CLA) (or small Carry-Select block) for upper/significant chunk (fast carry resolution).

Resulting product width: 24 bits.

This hybrid approach reduces critical-path delay vs. naive ripple adders while avoiding the area/complexity of a full wide CLA.
