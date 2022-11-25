# joycefier
Nanogenmo entry for 2022


# Disclaimer
The text in moby_joyced.txt was automatically generated from Moby Dick using the script on the .ipynb file and it's over 100k words long.
It involves automatically choosing words from BPE vocabularies. I haven't read it all yet, and during generation the script might accidentally have included offensive words or slurs within.
If you find anything offensive let me know and I can fix it.

# Description

This is an experiment in trying to make a normal English text look like something out of Finnegans Wake, algorithmically.
To achieve this, BPE vocabularies (from the BPEmb library) in 4 languages (en, es, de, fr) were used. 
BPE vocabularies contain words and subwords that are frequent in a language. 
The vocabularies used have a size of 10k items, and have a good mix of full words and some subwords.

The (as of yet) ugly script splits words into chunks depending on their size, and operates on these chunks.
For all words in the text, whether the code decides or not to substitute a word is random, with different probabilities for different substitutions.

For words with a single chunk, the code may look up similar-ish (difflib fuzzy matching) words on the BPE vocabularies and substitute.
For words with multiple chunks, the first chunk maybe substituted by a word whose ending continues with the chunk.
For subsequent chunks, the difflib fuzzy matching is used again.

This gives you transformations such as (using only an english vocabulary for example)
circulation -> circustation
whenever -> whenevery
Manhattan -> Manhattoes

# Example paragraph
It doesn't have to be Moby Dick, but many people seem to use it for these projects. Might change it up later. Full text on moby_joyced.txt

Original:
> No, when I go to sea, I go as a simple sailor, right before the mast,
plumb down into the forecastle, aloft there to the royal mast-head.
True, they rather order me about some, and make me jump from spar to
spar, like a grasshopper in a May meadow. And at first, this sort of
thing is unpleasant enough. It touches one’s sense of honor,
particularly if you come of an old established family in the land, the
Van Rensselaers, or Randolphs, or Hardicanutes. And more than all, if
just previous to putting your hand into the tar-pot, you have been
lording it as a country schoolmaster, making the tallest boys stand in
awe of you. The transition is a keen one, I assure you, from a
schoolmaster to a sailor, and requires a strong decoction of Seneca and
the Stoics to enable you to grin and bear it. But even this wears off
in time.

Joycefied:
>   o,  got tot,  simplement sir,  rinight ore, 
  komplumb orchester,  alout anthere royle- . 
 ,  ther rathuer borde about, 
 ,  za grasspapier sin za ray meaown.  firesté, 
  ething plants enough.  touches ones’  sense ahonor, 
  particularly ol established mil, 
  uan Rensselaers,  adop,  Hardiclantes.  ond, 
  previous tot puting onto- ,  reven
  verlording contra schoolmaster,  making entallest bois estan
  wolf.  transition keinen,  surve, 
  schoolamster sailor,  requwire wa strhong decoction Seneca
  Stoices enable youth rine rit.  ute wears
  sin. 
