Netrunner Datasuckers
=====================

The primary goal of Datasuckers is to decentralize the storage of Netrunner card data. The dispersal of this data across various servers will remove the need for tools and utilities to embed any copyrighted work and thus hopefully avoid a legal confrontation.

Datasuckers must implement a standardized REST API:
- /cards
- /card/$cardCode
- ... possibly more (API is under development)

Datasuckers must return JSON card objects (property types and names are under development):
<code>
card.code
card.title
card.agendapoints
card.baselink
card.cost
card.faction
card.factioncost
card.illustrator
card.imagesrc
card.influencelimit
card.memoryunits
card.mindecksize
card.number
card.maxperdeck
card.quantity
card.set
card.side
card.strength
card.subtype
card.text
card.trash
card.type
card.uniqueness
</code>

The Datasucker API represents the aboslutely smallest possible API needed to power external Apps.
Any search feature, sorting, querying, sub-queries, etc. must be built external to the Datasucker API.

This repository holds what you need to spin up your own Datasucker that is self-maintaining. (Instructions to follow)

The servers hosting this data will be private and not easily discoverable. The data that the servers are hosting is also freely available from the copyright owners and the storage of the data can be considered transient.


Currently there is a Parse.com Datasucker here.
( improved instructions coming soon )
<code>
To get it running, sign up for a free Developer account at Parse.com.
Create your first App and call it "Datasucker".
It's a "Cloud Code" App.
Follow the instructions to install the Parse command line tool.
At the command line, you'll do something like this:
parse new Datasucker
--> insert email / pass
--> Select the Datasucker project you created earlier (probably "1")
cd Datasucker
--> copy the main.js from this repo (Parse/cloud/main.js) to this directory in the same spot (cloud/main.js)
parse deploy

Next you'll want to go to your project on Parse and schedule the background job to refresh the data.
( Core -> Jobs -> Schedule a Job -> Select "refreshData")
Set it to repeat at a reasonable rate (once a day or week should be fine).
Click "Run Now". It will take ~6-7 minutes to populate your Datasucker.
</code>