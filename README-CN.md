# Industries of the Caribbean

IOTC 加勒比海营造了一个出口导向的国营经济体系，你拥有工业、产业链与运输网络。在这个经济体系中，除非你出口货物，否则你不会因为运输而获得报酬。
你的岛屿拥有肥沃的土壤和丰富的石油和镍矿藏，但没有加工工业来生产有价值的产品。

（跳至[设计理念](#设计理念)）

## 货物运输图
![货物运输图](docs/cargo_chart.png)

#### 进出口方案
* 咖啡 -> 食品
* 糖 -> 石油
* 镍 -> 肥料
* 钴 -> 管道
* 雪茄 -> 化学品
* 游客 -> 机械装置

## 货物种类

与大多数 OpenTTD 工业 GRF 不同，在 IOTC 中运输货物的报酬不取决于运输距离，即运费为货物本身的价值。本项旨在模拟玩家控制着一个国营进出口经济体系，而不是单纯的运输公司。

#### 出口货物

These are exported to the Import/Export industry where they are traded for other cargos. These make significant profit.

#### Imported cargos

These are obtained in exchange for exported cargos at the Import/Export industry. They cost you money to transport, so don't import more than you need!

#### Domestic cargos

These are all other cargos, including Workers and intermediate cargos which travel between industries. They make a slight loss. The one exception is Mail, which makes a normal profit.

## General industry mechanics

Industries do not close or change production.

#### Primary industries

* Beach
* Coffee Plantation
* Hotel
* Nickel Mine
* Oil Wells
* Sugarcane Plantation
* Tobacco Plantation

These industries generate naturally, sometimes with with elevation or distance from town requirements. Many require a cargo to be delivered for their production like Pipe for Oil Wells and Food for Hotels. Also delivering a boost cargo will double production. Boost cargos are stockpiled and consumed during each production tick (8-9 times per month) to determine how much cargo is produced.

#### Secondary industries
* Cigar Factory
* Nickel Smelter
* Oil Refinery
* Rum Distillery
* Sugar Mill

These industries are funded by the player. They require one Worker for each unit of input cargo. If this seems like a lot, it is! Workers are the main production bottleneck and you'll need to both connect many towns to each industry, and deliver the necessary cargos to grow these towns.

Also, some of these industries have additional cargos, like Chemicals for the Nickel Smelter, which are required input cargos. The industry window lists the ratio of input cargo required for each unit of output cargo.

## Getting started

Initially, the only profitable cargo is coffee, which requires no processing before it is exported.

Start by exporting as much coffee as you can until you can afford your first processing industry: the sugar mill. After that, unlock new cargo chains by funding the proper industries, as governed by the cargo flowchart and the Import/Export trade deals.

Be careful, though, not to expand into a cargo chain before you have the required cargos — for example, the Nickel chain requires Chemicals, which are obtained by exporting Cigars.

Remember that imported cargos cost you money to transport — check the Cargo Payment Rates graph if you're unclear.

#### Recommended Settings

* News/Advisors: Warn if a vehicle’s income is negative: Off
* News/Advisors: Warn if a vehicle is lost: Off
* Environment > Industries > Company stations can serve industries with attached neutral stations: Off
* Environment > Cargo distribution: Manual

#### Recommended World Generation settings

* Climate: Sub-tropical
* Sea level: Medium
* No. of towns: High
* No. of industries: Low
* Desert coverage: 0%

#### Required NewGRFs

* ITL Houses 1.4.0 or later
  * (These houses don’t accept Workers or Food, keeping those cargos going only to your industries.)

#### (Optional) Suggested NewGRFs
My personal favorites, if you don't have your own.
* Iron Horse 2
* Termite (tracks)
* SHARK (ships)
* Mop Expanded Road Vehicles
* Unspooled (roads)
* Av9.8 Aircraft Set
* OpenGFX+ Airports
* Industrial Stations Renewal
* ISR-style Dock
* ISR/DWE-style Objects
* US Stations set
* Total Bridge Renewal Set
* Rainforest Ruins

## Credits
* Beach sprites: [Beach Objects](https://www.tt-forums.net/viewtopic.php?f=26&t=62258) by Quast65, GPL v3 license

## Translations
* English
* Simplified Chinese (chengdd1987)
* French (arikover)
* German (Fauleresel)

To add a translation, please create a Pull Request!

## 设计理念

Industries of the Caribbean is an experimental industry/economy mod which aims to radically rethink the OpenTTD economy by breaking common design patterns and reclaiming “useless” features to add interesting gameplay.

Before we get into what I’ve changed, let’s briefly recap how vanilla and most NewGRF economies are structured:

* Money is an early-game constraint, but by mid-game your company earns money faster than you can spend it. The constraint then becomes tile space for stations, junctions, and mainline throughput. OpenTTD would still be fun without money.
* Industries grow to immense production either through station rating-fueled production increases (vanilla), or boost cargos (FIRS). This high production usually requires double-track infrastructure, and don’t even dream of using road vehicles for cargo.
* Most production chains lead to town cargos which are delivered to “black hole” industries, such as Goods, Alcohol, or Vehicles. These are highly profitable, but by the time you complete the production chain to this extent, money is generally not a motivating factor.

The serious OpenTTD players I talk to tend to fall into two gameplay categories:

1. Players who build passenger networks using CargoDist to route passengers automatically and create network design and capacity challenges for gameplay interest.
2. Players who build cargo networks using a complex industry mod like FIRS Steeltown or XIS.

I have played both styles of game and have been frustrated and intrigued by features in each which fall short of interesting gameplay:

* Road vehicles are too low capacity to be useful outside niche roles like boost cargo distribution, feeder lines, or very short distance routes.
* Without daylength patches such as in JGRPP, most rail lines require double track. It would be nice to have some low-traffic branch lines in addition to the heavy trunk lines.
* Ships are so slow that unless you absolutely need them to reach Oil Rigs (vanilla) or Fishing Grounds (FIRS), using them instead of trains often feels silly.
* Passenger transportation gives you nothing but money (a “bad feature,” remember?) and its only gameplay interest comes from fighting to keep up with CargoDist and town growth...which is often more frustrating than fun.
* Endgame town cargos have no incentive to deliver them, and it’s just as profitable to dump them all in one place rather than distributing them across the map.
* Cargo aging and different values per cargo only matter in the early game.
* If you’re not playing with passengers or mail, towns are useless to you and just get in the way.

So, what ~~weird and ill-advised~~ interesting things can we do to change this?

* Primary industries have a fixed production much lower than FIRS, to encourage road vehicles and single-track rail lines to industries while still keeping enough production for busy trunk lines.
* Only primary industries spawn on map generation, and all secondary industries are funded by the player — more on this later. Industries never change production or close, and only Hotels spawn during the game.
* Secondary industries need an immense supply of Workers: one per unit of cargo converted. Funding them requires you to think about worker supply and once built, you’ll need to grow cities and run commuter trains from nearby towns and cities.
