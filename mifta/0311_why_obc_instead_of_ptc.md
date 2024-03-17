# Why do we need to use Obc instead of PTS in the first place
- Convert High level programming instructions written in Pipit into executable code for embedded devices, ensuring the code can run in real-time without needing external inputs for undefined variables (free context).
- A recursive expression is a way to define an operation in terms of itself, which is tricky because it needs a starting point to avoid going into an infinite loop. The passage describes a method to handle this by initially assigning a default value (bottom value ⊥τ) to kick-start the recursion.
- So basically, Pipit/F* uses pure arrays, and it's converted to C which uses imperative arrays. And Pure transition System used to do the conversion can only convert pure arrays in one language to pure arrays in another language, but cannot work with imperative arrays at all. This results in - everytime an array needs to be altered, new memory needs to be allocated  

[1] Pipit on the Post: Proving Pre- and Post-conditions of Reactive Systems, Section 5

