---
title: TAXII2 Groups &amp; Channels
---
# Groups and Channels in TAXII

In the TAXII 2.0 design we are discussing introducing the concept of "groups" and "channels".

## Group

A group is a collection of channels. When first presented, this was based on the idea of "trust groups", who can see what.
If you were a member of a "group" then you would have permission to see everything within that group.

## Channel

A channel is the place where TAXII messages are published and subscribed. It is the identifier of the "location" to which
messages are sent and received.

## Thoughts

If there are "groups" can or should there be groups within groups? In a filesystem, we are very familiar with this concept.
Directories bin items together, those items can be other directories or files. A directory is analogous to a TAXII group, and 
a TAXII channel is analogous to a document file. Directories and files have various permissions applied to them.

This sort of hierarchical arrangement is very common and widely seen in IT. Does TAXII need a similar hierarchy?

## Examples

/groups/mitre/bedford/m-building/third-floor/wi-fi_routers - could be a channel for all wi-fi routers at a location.

A system could then subscribe to /groups/mitre/bedford/**/wi-fi_routers to subscribe to all wi-fi routers channels
under the "bedford" hierarchy.

A subscription to /groups/mitre/bedford would receieve ALL channels under the bedford group. "bedford" acts an alias
for all of the channels under its hierarchy.

---

A question has arisen as to how the paths are represented.

  /group(s)
    /group1
      /group(s)
        /group2
        /group3
          /channel(s)
            /channel1
            /channel2
    /channel(s)
      /channel1
      /channel2
        
/group(s)
   [/group(s)]
     [{group-id}] ...
   [/channel(s)]
     [{channel-id}] ...

In this case, the item type, group or channel, is explicit in the path.

vs

/group(s)
  /group1
    /group2
    /group3
      /channel1
      /channel2
    /channel1
    /channel2
  
