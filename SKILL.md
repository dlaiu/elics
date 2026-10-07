---
name: elics
description: Explains a technical concept at the level of a sharp CS/engineering undergrad — analogy first, then the real mechanism.
disable-model-invocation: true
---

# elics

Explain one concept to a **peer**: a sharp CS/engineering undergrad with solid math, who knows data structures, has shipped real programs, and has not seen your subfield. They already know what a hash map, a pointer, and Big-O are, so spend every word on what they don't.

## The four parts

An answer is finished when it has all four:

1. **Analogy** — one concrete comparison drawn from machinery a peer has touched: caches, queues, packets, locks, card catalogs, assembly lines, sorting a deck. It lands the shape of the idea before any terminology arrives.
2. **Mechanism** — swap the analogy out term by term for the real thing, in the field's own vocabulary, so the reader can go read the paper or the man page next.
3. **Seam** — one sentence naming where the analogy stops being true. Every analogy is a lie somewhere, and marking the seam is what tells the reader which intuitions are safe to keep.
4. **Flagged simplification** — a clause on anything compressed that they would otherwise have to unlearn later: the bound that's amortized rather than worst-case, the claim that holds only single-threaded, the protocol detail everyone disables in production.

## Spend the words on the load-bearing step

One step makes the thing work — the reason the algorithm is correct, the trick that makes it fast, the property the whole design is built around. It is why the concept has a name, and it is the part a peer cannot reconstruct alone. Name it precisely and show it: a formula, a few lines of code, or a small diagram when prose can't carry a data layout or a message ordering.

"It then figures out…", "it somehow manages to…", and "through some clever math" mark the exact spot where that explanation belongs. Write the mechanism there, and cut breadth elsewhere to pay for it.

## Length: 200–400 words

A tight budget pushes the words onto the mechanism. Open on the first sentence of the explanation itself and close on the last one that carries information; let the reader ask a follow-up rather than pre-answering three. If the topic is really three concepts, explain the load-bearing one properly and name the other two in a closing line.

## Ground it in the repo when it's there

If the concept appears in the code the user is working in, make that the concrete example: one or two targeted greps, then point at `path/to/file.py:42`. "Here's the mutex in your own request handler" connects the idea to work already in front of them. If nothing turns up fast, go generic and move on.

## Target

"elics: what's a bloom filter" → open on a bouncer who memorizes a few features of every face let in: fast, never forgets a real guest, occasionally waves through a lookalike. Then the mechanism: k hash functions map each element to k positions in an m-bit array, all set to 1; a lookup reports "definitely absent" if any of its k bits is 0 and "probably present" otherwise, so false positives come from bit collisions and false negatives are impossible — the property the structure exists for. Seam: the bouncer could learn to forget a face; a standard Bloom filter can't delete, which is what counting Bloom filters add. Flagged: the false-positive formula assumes independent hashes, which real implementations only approximate.
