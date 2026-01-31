# requirements brainstorm
Most of what I (julien) have in mind, so we can start on the same page. These should not be taken as ready-to-submit as there's probably too much info and not well formated, but they should allow agreeing on what we want to keep

## the application
Think strava but for mountaineering/climbing.
Climbers want to be able to share the details of their adventures with others.
Climbers also want to be able to browse other people's climbs for information on conditions, difficulty, experience, and details of the route. 

My notes include info about why certain features are included. This info should not be transfered to the reqs we submit (e.g. "having entity A, B, C because we want an ISA")

![alt text](image.png)


* A climber is a generic user of the app. They go on climbs, sometimes as part of a roped party, post about their climbs.
  * a climber can follow other climbers on the app to be notified of their new climbs

* a roped party is a combination of two or more climbers (typically at most 6, but nothing prevents more people) that connect themselves via an alpine rope. This is typically done for any travels across exposed terrain that does not require special technique (i.e. no climbing). The rope allows to prevent terrain-related dangers like crevaces, cornice breaks, ice bridges, unstable slopes.
  * a roped party has at mot 1 lead. The lead is the first on the rope, and assumes heightened responsibilities, both technical ones (has to perform some special techniques, like installing snow anchors) and those related to a heightened exposure to terrain risks (typically the first to fall through crevaces...).

* mountain: an elevated region of terrain to climb. 
  * climbers want to be able to search the routes by mountain, as a single mountain may have multiple ways to be climbed (routes). 
  * a mountain  has a unique name

* checkpoint: a unique geographical point of interest; what the climbers try to reach, or pass by during their climbs. These are not necessarily the summit. Examples include the parking lot, base camp, camps number 1-n, the summit, the "lake of the clouds", the "midway cascade", etc.

* feature: a traversable segment of terrain (not a point; a line on a map) that possesses distinct characteristics, such that users benefit from specific information about this stretch of terrain. Examples include "5km glacier travel", users might want to know snow conditions, strength of the ice bridges, new crevaces;  "300m serac scramble", for cliff exposure, dislodged rocks; "700m alpine ridge" for presence of a cornice, depth of snow cover, wind speed and direction.
  * not every segment of the mountain is a feature. users might not need special information on a 3km flat gravel road. Features are parts of the mountain that require special care to traverse.
  *  Some features require additional technique and care to traverse. Unlike the above (glacier travel, ridge crossing), where technique is only necessary to prevent injury and not to advance, it is difficult or impossible to advance on technical terrain without proper technique. I can run across a glacier and possibly not fall into a crevace, I can't scale an ice waterfall without being roped up. 
     *  Technical features are a special category of features since they carry additional information; their difficulty is typically graded by official organizations. (see all the grades: https://en.wikipedia.org/wiki/Grade_(climbing)) 
  *  note to self: currently imo a non-covering ISA of "feature" (regular) and "technical feat." (child). could be a covering ISA with "easy peasy" (like a road), "medium" (ungraded, requires protection like glacier travel), "technical" (the current bullet point)

* a route: a sequential combination of checkpoints and features. 
  * a route has exactly one objective: one of the checkpoints. e.g. a route may go from parking lot, and end at the "lake of the cloud". note that a "checkpoint" can be the objective in one route, but not the objective in another. E.g. another route may pass by the lake of the cloud to get to the summit. The summit is the objective here, not the lake. 
  * A route happens on a mountain. Or multiple mountains?

* post


* checkpoint

* a route is a specific, ordered succession of features and checkpoints, on a particular mountain.
  * there may be multiple routes from 


* no longer sure about the pertinence of groups because they prevent useful ER patterns. could be included with a bit of complexity.

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