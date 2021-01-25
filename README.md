# gun-stats-test

### The idea is to accumulate the performance statistics on a gun peer and periodically share those with other peers.

At first I had experimented measuring only peers running nodejs [see here.](https://github.com/amark/gun/compare/master...i001962:master) Nodejs peers are reporting performance stats already and storing them in stats.radata every 15 seconds. The default install has stats collected and overwritten(?), presumably to save disk space, as point in time snapshots vs aggregated performance.

This repo shows an example of capturing performance for a round trip on get soul. You may add whatever measurement you want instead but as of now you'll need to know the wire protocol which I don't at time of this writing. markn walked me through the getSoul function and setting the timestamps. 

Live (when it's working) Demo [here](http://plato.seallake.net/API/v1/data/gun-stats-test/plotHisto2/plotFiles.html)

Warning- When I added the observation slider I failed to initialize the chart so on first load...errrrrr Move the observations slider and you should see the chart. I never did get this to display in Firefox but Chrome seems to work. PRs welcome. *Even if the chart doesn't display you may inspect the performance histogram in the dev console where there are instructions.*

The performance observations are binned using [hdr-histogram](https://github.com/HdrHistogram/HdrHistogramJS).

Encoding the histogram and .put(ting) to gundb at regular intervals would enable sharing of peer performance.