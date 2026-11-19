# FDPS
### Fire Danger Point System

A simple, points-based model for describing fire-weather conditions using air moisture, wind gusts, and fine-fuel moisture.

FDPS has been in use by private fire-weather research organizations since 2015.

---

## How It Works

FDPS uses three inputs:

- **Relative humidity:** how dry the air is.
- **Wind gust:** how strong the gusts are, in miles per hour.
- **1-hour dead fuel moisture:** moisture content in fine dead fuels, expressed as a percentage of dry fuel weight.

Each input receives **1 to 6 points**. Add the three contributions for a score of **3 to 18**. Higher scores indicate more favorable conditions for ignition and fire spread.

```text
FDPS = Fuel Moisture Points + Gust Points + Humidity Points
```

## Input Scores

| Points | 1-Hour Fuel Moisture (%) | Wind Gust (mph) | Relative Humidity (%) |
| :---: | :---: | :---: | :---: |
| 1 | >=20 | <=5 | >=50 |
| 2 | 17 to <20 | >5 to 10 | 40 to <50 |
| 3 | 14 to <17 | >10 to 15 | 30 to <40 |
| 4 | 11 to <14 | >15 to 20 | 20 to <30 |
| 5 | 8 to <11 | >20 to 25 | 10 to <20 |
| 6 | <8 | >25 | <10 |

## Rating Scale

| Total Points | Rating |
| :---: | :--- |
| 3-5 | **Low** |
| 6-8 | **Moderate** |
| 9-11 | **High** |
| 12-14 | **Very High** |
| 15-18 | **Extreme** |

## Current and Projected Ratings

**Current FDPS** uses one coherent station observation. If multiple stations are available, use the designated primary station, falling back to the next station with all three required inputs.

For current conditions, when **RH is at least 75%** and **1-hour fuel moisture is at least 15%**, reduce the gust contribution by **one point**, with a minimum of **one gust point**. This reduces wind's influence when both air and fine fuels are moist.

**Projected FDPS** uses the lowest humidity, lowest 1-hour fuel moisture, and highest gust in the selected assessment window. These extremes may come from different times or stations. Use the same scoring tables, without the current-condition gust adjustment.

### Example

With **83% RH**, a **7 mph gust**, and **16.1% fuel moisture**:

```text
Fuel moisture: 3 points
Wind gust:    2 points, reduced to 1 for moist current conditions
Humidity:     1 point

Current FDPS: 5 points = Low
```

## Use and Limitations

If any required input is missing, report the rating as **unavailable**, not Low.

FDPS is a research and reference model, not an official fire-danger classification or a prediction that a fire will occur. It does not replace local warnings, burn restrictions, or professional judgment.

## Authors and Attribution

FDPS was jointly created by [DevRanger](https://github.com/DevRanger) and [mesocom](https://github.com/mesocom).

When sharing or adapting this documentation under CC BY 4.0, credit **both DevRanger and mesocom** as the co-creators of the FDPS model.

## License

The documentation in this repository is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You may share and adapt it, including commercially, with appropriate credit, a link to the license, and an indication of any changes. See [LICENSE](LICENSE) for the full terms.
