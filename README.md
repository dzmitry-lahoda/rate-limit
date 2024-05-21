# rate-limit

rate limiter possible spec updates #4460
dzmitry-lahoda started this conversation in Ideas

dzmitry-lahoda
on Feb 28, 2023
each side of rate limiter is mana pool
amount of mana never fells below some value (i.e. it refreshed instantly for some amounts).
as soon as transfer happens, mana was spent.
on each transfer, time from previous to current transfer is taken, and mana refreshed according some rate.
so there is no long hour window.
so logically mana refreshed little bit each block.
on transfer back, net flow, mana restored.
Replies:3 comments

dzmitry-lahoda
on Feb 28, 2023
Author
on maximal limit
store hourly buckets, human reaction time.
there would be 32 buckets, one for each hour.
each transfer ads value into 0h.
when window (here we use window) of hour lapses.
value added to next bucket (shifts array).
example can have 0, 42, 33, 44, 150, 42, 0(not yet filled), .. 0
from that array can form hourly changing strategy for limit.
biased to 8h/16h values, and yet 2h,4h still can have influence on cap increased.
so it will allow people do small money transfers even if there was big transfer taking all mana, because mana restored continuously. no each window.
mana restoration period can be taken e.g. 16 hours.
may be that can be tied to window of averages

rate limiter is based on the available liquidity on the source and destination layer. also can dynamic fee change depending also.
