# Science & Technology

Science infrastructure built at Stars contribute to the overall research amount per tick for the chosen technology that is being researched. More Science infrastructure increases the speed of which new technology is researched.

Open the Research screen to view the current research and set the next research. 

The types of technologies are as follows:

![The Research menu](img/research-menu.png)

The science amount needed to complete a research `level` is given by the formula:

- Standard: `50 * expenseConfig * level`
- Exponential: `50 * expenseConfig * growthFactor ** (level - 1)`

Where `expenseConfig` is:

- `1` for cheap costs.
- `2` for standard costs.
- `4` for expensive costs.
- `8` for very expensive costs.
- `16` for crazy expensive costs.

Where `growthFactor` is:

- `1.25` for soft growth.
- `1.50` for medium growth.
- `1.75` for hard growth.

## Scanning

Improves the visible area star a star can see. The higher your scanning, the further you can see. 

The equation is `(scanning + 1) * lightYear`.

> Note: A `lightYear` distance unit is `50`.

## Hyperspace Range

Improves the distance a carrier can travel in between each waypoint. 

The equation is `(hyperspace + 1.5) * lightYear`.

> Note: A `lightYear` distance unit is `50`.

## Terraforming

Improves the natural resources at Stars to make infrastructure upgrades cheaper. 

The equation for terraformed resources is `floor(naturalResource + (5 * terraforming))`.

The equation for infrastructure cost is `max(1, floor((baseCost * expenseConfig * (current + 1)) / (terraformedResources / 100)))`.

Where `baseCost` is:

- `50` for Warp Gates.
- `2.5` for Economy.
- `5` for Industry.
- `20` for Science.
- `10` for Carriers.

Where `expenseConfig` is:

- `1` for cheap costs.
- `2` for standard costs.
- `4` for expensive costs.
- `8` for very expensive costs.
- `16` for crazy expensive costs.

## Experimentation

Grants a `50` bonus points per level to a random technology each production.

The equation is:

- Standard: `experimentation * 50`
- Experimental: `(experimentation * 50) + (0.15 * experimentation * totalScience)`

## Weapons

Improves the amount of enemy ships destroyed per combat step. Each step, an amount of enemy ships exactly equal to the effective weapons level is destroyed.

## Banking

Earns extra credits every production cycle. 

The equation is:

- Standard: `(banking * 75) + (0.15 * banking * totalEco)`
- Legacy: `banking * 75`

## Manufacturing

Increases ship production rate on all stars. 

A star produces `industry * (manufacturing + 5) / tickPerCycle` ships per tick.

## Specialists
Increases the number of specialist tokens awarded at the end of a galactic cycle, these are used to hire specialists. 

The equation is:

- Standard: `tokens = tech level`
- Experimental: `ceil(min(star count * tech level * 0.1, tech level))`
