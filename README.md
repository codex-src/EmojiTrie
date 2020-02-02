# EmojiTrie

This repo was originally built for handling emoji in the [Codex editor](). The constraints for this package were simplicity and speed.

A trie in computer science is also known as a DAG -- a [directed acyclic graph](). Effectively, a unidirectional tree where all child nodes can only ever point to more child nodes. This might sound confusing, but you can imagine a trie as a kind of nested switch statement expression:

```js
switch (v1) {
case 1:
	switch (v2) {
	case 2:
		switch (v3) {
		case 3:
			// ...
		case 4:
			// ...
		case 5:
			// ...
		default:
			// ...
		}
	case 3:
		// ...
	case 4:
		// ...
	default:
		// ...
	}
case 2:
	// ...
case 3:
	// ...
default:
	// ...
}
```

This is somewhat maddening but accurately demonstrates the use case for tries -- logical expressions modeled as a data structure _instead of_ statements.

The purpose of this package is to make accessing the next and previous emoji -- **any emoji** (Unicode 12.1 at the time of this writing) -- simple and as fast as possible.

You may be surprised to learn that for computers, emojis are not one character. [`💩`.length === 2](), for example. This is because emojis are represented in *code points*, and code points **do not** correspond to bytes. 

Other alternatives **do** exist to solve for this problem, using one technique or another, such as [regex]() and the [UAX #29]() algorithm, but I argue that such implementations are heavy-handed and convolute the the problem space.

