# requirements brainstorm
Most of what I (julien) have in mind, so we can start on the same page. These should not be taken as ready-to-submit as there's probably too much info and not well formated, but they should allow agreeing on what we want to keep

## the application
There is a large community of mountaineers that engages in the occasional climb of a mountain. The community has a friendly culture of informally sharing stories, details, and tips about their recent ascents to fellow climbers. This is both a social activity - it’s nice to share our adventures - and it is in large part a necessary phase of the mountaineering process. This information sharing is tremendously helpful when preparing for a climb; it helps to know the difficulty of the trail ahead, as well as the recent conditions on the trail - a trail may be practicable in the summer, but not in the winter due to ice and snow.

Our application allows climbers to share information about their recent ascents, as well as researching other climber’s ascents as a means to gather information on specific routes. 
Data Requirements
A climber is a generic user of the app. They ascend mountains, sometimes as part of a roped party, and post about their climbs.
A climber can follow other climbers on the app to be notified of their new climbs
A climber is uniquely identified by their email
A climber has a name, address, age, nationality, username, bio

A roped party is a combination of two or more climbers (typically at most 6, but nothing prevents more people) that connect themselves via an alpine rope. This is typically done for any travels across exposed terrain that requires protection (e.g. in case someone falls in a crevasse) or assistance (e.g. rock climbing).
A roped party has exactly 1 lead. The lead is the first on the rope, and assumes heightened responsibilities, both technical ones (has to perform some special techniques, like installing snow anchors) and those related to a heightened exposure to terrain risks (typically the first to fall through crevasses...).
A climber may change roped-party between climbs.
A climber may perform an ascent without being in a roped party

Mountain: an elevated region of terrain to climb. 
climbers want to be able to search the routes by mountain, as a single mountain may have multiple ways to be climbed (routes). 
A mountain has a unique name
A mountain has a location

Checkpoint: a unique geographical point of interest; what the climbers try to reach, or pass by during their climbs. These are not necessarily the summit. Examples include the parking lot, base camp, camps number 1-n, the summit, the "lake of the clouds", the "midway cascade", etc.
A checkpoint has a unique location. There cannot be 2 checkpoints with the same location… they would be the same checkpoint.

Feature: a traversable segment of terrain (not a point; a line on a map) that possesses distinct characteristics, such that users benefit from specific information about this stretch of terrain. Examples include "5km glacier travel", users might want to know snow conditions, strength of the ice bridges, new crevasses;  "300m serac scramble", for cliff exposure, dislodged rocks; "700m alpine ridge" for presence of a cornice, depth of snow cover, wind speed and direction.
Not every segment of the mountain is a feature. Users might not need special information on a 3km flat gravel road. Features are parts of the mountain that require special care to traverse.
Some features require additional technique and care to traverse. Unlike the above (glacier travel, ridge crossing), where technique is only necessary to prevent injury and not to advance, it is difficult or impossible to advance on technical terrain without proper technique. I can run across a glacier and possibly not fall into a crevasse, but I can't scale an ice waterfall without being roped up. 
Technical features are a special category of features since they carry additional information; their difficulty is typically graded by official organizations. (see all the grades: https://en.wikipedia.org/wiki/Grade_(climbing)) 
A feature has a starting location, an ending location, a non-unique name, an optional description

Route: a sequential combination of checkpoints and features.
A route has exactly one objective: one of the checkpoints. e.g. a route may go from the parking lot, and end at the "lake of the cloud". note that a "checkpoint" can be the objective in one route, but not the objective in another. E.g. Another route may pass by the lake of the cloud to get to the summit. The summit is the objective here, not the lake.
A route happens on at least one mountain.
A route has a non-unique name, an optional description. 

Ascent: an attempted completion of a route by a climber. 
An ascent is completed on a specific day, at a specific time.
An ascent has a duration.
A climber may ascend a route more than once
The ascent should record which roped party, if any, participated in the climb (i.e. was the climber part of a party as they made the ascent.)
The ascent can be Successful or Unsuccessful

Post: a climber that completes an ascent can post about their experience to comment on conditions of the route, features. 
A climber can only post about an ascent if they have participated in it.
The post includes information about the condition of the route ascended.
The post includes information about the condition of features within that route (optional, if we want more entities/relationships; I was a bit short as I wrote this)
The post includes the timestamp.
As it is important for climbers to keep track of the evolution of conditions, the past conditions of a route / features must be preserved. (this sounds trivial if the conditions are tied to the post or their own entity, not an attribute of the route / feature)
A single post can only have a single description of the feature conditions. The previous edits do not have to be remembered for that single post.
A single post can only have a single description of the route conditions. The previous edits do not have to be remembered for that single post.
Other climbers can comment on the post. Previous comments should be preserved. (optional, removing this removes entities if we need space, does not break anything)

### 




### note to self
just brainstorm stuff

key constraint: route has at least one feature

participation constraint: every cordee must have at least one member

bold arrow: a post must have exactly one author

isa: feature can be technical feature, where it has an official grade

weak rel: checkpoint name -> mountain id

bin rel: climber membertOf roped party

tertiary rel: unsure for now

aggregation: climber climbs route. aggregation climb -> \<authors\> -> post
  the author of a post must have completed the route during a climb