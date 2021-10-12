---
title: Election Simulator
nav_order: 0
---

The President of the United States is not elected by a popular vote, but by a majority vote in the Electoral College. Each state, [plus DC](https://en.wikipedia.org/wiki/Twenty-third_Amendment_to_the_United_States_Constitution), gets some number of electors in the Electoral College, and whoever they vote in becomes the next President. Right before the 2016 election, [NPR reported](https://www.npr.org/2016/11/02/500112248/how-to-win-the-presidency-with-27-percent-of-the-popular-vote) that 23% of the popular vote would be sufficient to win the election, based on the 2012 election data. They arrived at this number by looking at states with the highest ratio of electoral votes to voting population. This was a correction to their originally-reported number of 27%, which they got by looking at what it would take to win the states with the highest number of electoral votes. But the optimal strategy turns out to be neither of these and instead uses an unlikely coalition of small and large states.

{{ site.modules | where: 'title', 'Election Simulator' | first }}

How might we identify the coalition of states with the minimum possible popular votes needed to win the Electoral College? So far, all of our programming experience has focused on solving problems that have only one solution (result or output) associated with each input. Sometimes, that solution is a collection type, but even a collection of data still represents only one solution, one coalition of states out of all of the possible combinations. Even generative recursive algorithms still only produce one solution per input, though the algorithm generating them uses randomness.
