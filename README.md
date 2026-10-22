# Sunrise Coffee: performance review, 2023 to 2024

My entry for the Onyx DataDNA challenge. The brief puts me in the seat of a commercial analyst reporting to the Chief Commercial Officer of a 60-store UK coffee chain. The CCO wants to know which stores and regions to prioritise for 2025 and whether the loyalty programme is worth more money.

It's a four-page Power BI dashboard. This README covers what I found, what I recommend, how I treated the data, and the parts of the brief that didn't fit on a page but still deserve an answer.

I treated the dataset as fictional, so I didn't hold it to real-world logic. For example, stores marked closed still trade for all 24 months, and I left that alone.

## The short version

**Headline recommendation:** put 2025 expansion into Shopping-Centre and Suburban High-Street sites, not London City-Centre. Hold loyalty spend flat until someone tests whether it brings customers back more often.

Five findings sit behind that:

1. **Every store sells about the same.** Average revenue is roughly £62k per store per month, in London (£62.2k) and everywhere else (£62.3k). Total revenue was flat too: £45.0m in 2023 and £44.7m in 2024. Net margin was 18.8% in both years.
2. **London is the weak spot, and it's a cost problem.** London's margin is 8.5% against 20.2% elsewhere. Rent takes about 19% of sales there, against about 9% elsewhere. Across all stores, rent has no link to how much a store sells (r = 0.03).
3. **Staffing doesn't flex with demand.** Weekend sales run 24% below weekdays and bank holidays 34% below, but staff hours stay flat at about 41.5 a day. Sales per staff hour fall from £53 on weekdays to £40 at weekends.
4. **Eight stores need a look.** They have 6 or more loss months out of 24, and five of the eight had more loss months in 2024 than 2023 (30 in total, up to 39).
5. **Loyalty doesn't clearly pay for itself.** Rewards cost £1.73m. My estimate of the extra gross profit from members' bigger tickets comes to between £1.28m and £1.56m, so the net is between -£0.17m and -£0.45m. That's an estimate with a big caveat (see below).

## What's on each page

| Page | Question it answers | Main visuals |
|---|---|---|
| **Overview** | Where does the business stand, and what should the CCO do? | Recommendation banner, margin by site type, monthly margin trend, status mix |
| **Cost drivers** | Why do stores that sell the same make different profit? | Where each £1 of sales goes (London vs rest), staffing against margin, sales per staff hour by weekday |
| **Stores to review** | Which stores and regions need attention? | The eight stores, loss months by region, 2023 vs 2024 comparison |
| **Loyalty ROI** | Does the programme pay for itself? | Waterfall from extra member spend to net value, adoption against margin |

There's also a hidden tooltip page that shows a store's 24 months of loss and deep-loss months when you hover over in the stores to review table.

## What I recommend

**Stores and regions for review**
- The eight stores on page 3. South London Corner has the most loss months (13 of 24) and is the only store that lost money over the full two years. Five of the eight are London stores where rent is the main gap, and three are staffing-driven (South London Corner, Manchester Collective, Derby Lounge).
- Margin by site type: Shopping-Centre 22.3% (12 stores), Suburban High-Street 20.3% (16), City-Centre outside London 18.4% (23), London City-Centre 8.5% (7).
- Margin by region: Northern Ireland 28.4% and West Midlands 24.5% are highest, but each has only 3 stores, so I'd pilot there, not scale. Wales (22.8%) and East of England (22.1%) are the strongest regions with a decent sample (6 stores each). London is last.
- Train-Station sites post 25.1%, but that's 2 stores. I'd test a third site before saying anything about the format.

**Loyalty**
- Don't cut it, don't grow it yet. Run a test that measures visit frequency, because that's the benefit this data can't show.

**Staffing and promotions**
- Match weekend and bank holiday staffing to demand. I haven't sized the saving, so I won't put a figure on it.
- There's no seasonal peak to plan around, so I wouldn't build promotions around the calendar. Weekends and bank holidays are the weak days, so that's where a promotion has room to work. That's a hypothesis, not a finding. The data can't test it.

## What I left off the pages, and the answers

The brief asks a lot of questions and a spacious dashboard can't hold them all. These are the ones that didn't get their own visual.

| Brief question | Answer |
|---|---|
| **Which regions to prioritise?** | See the regional margins above. Wales and East of England are the safest bets on sample size. London is the one to avoid. |
| **Is food share growing? Beans?** | No for food: 26.2% to 25.9%. Slightly for beans: 8.9% to 9.2%. Filter went from 19.0% to 19.3%. Espresso is steady at about 46%. Filter has the highest list margin of any category (88%). |
| **Do formats differ on footfall and sales per sq ft?** | Hardly. Daily footfall runs from 456 to 493 across site types and sales per sq ft from £48 to £54. Revenue mix is about the same in every site type too (espresso 45 to 46%, food 25 to 26%). |
| **Does adoption drive member revenue share?** | Yes, almost one for one (r = 0.998). That's partly mechanical, because the more customers use the app, the bigger the share of sales. It doesn't mean more members means a more profitable store: adoption and margin have no link (r = -0.01). |
| **Weekday vs weekend, and bank holidays by format?** | Weekends run about 24% below weekdays in every site type (Train-Station 27%). Bank holidays run about 34% below standard days for both High-Street and Transport-Hub stores, but the hub figure rests on 7 sampled days. |
| **Which stores improved or fell most?** | Biggest falls in net profit, 2023 to 2024: Bristol Station -£141k, South London Corner -£108k, Chester House -£92k. Biggest gains: Belfast Yard +£117k, Liverpool Collective +£116k, Cheltenham Quarter +£90k. 31 stores improved and 29 fell. |
| **Net value of loyalty per store?** | On my estimate, 37 of 60 stores come out negative. The brief's own definition (member revenue minus redemption cost) gives £28.0m, but that counts every member pound as won by the programme, so I treat it as a ceiling. |
| **Seasonal pattern?** | There isn't a repeatable one. November 2023 was the worst month for profit and November 2024 the best. Q3 was strong in 2023 and the weakest quarter in 2024. Monthly margin stays between 15.8% and 21.0%. |

## How I treated the data

- **Profitability status.** The dictionary says status comes from net margin, but the labels shipped with the data follow £ profit (cut-offs near £20k, £8k, -£2k and -£15k). They disagree on 600 of 1,440 store-months. I used the dictionary's margin rule and kept the shipped column for reference.
- **A loss month** is a net margin below -2%. **Review** means 6 or more loss months out of 24. That 6 is my call: 4 would flag 22 stores, 5 would flag 14, 7 would flag 7, and 8 would flag 4.
- **Formats.** The brief talks about High-Street, Retail-Park and Transport-Hub. The data has 58 High-Street stores and 2 Transport-Hub stores, and no Retail-Park. Format comparisons would be 58 against 2, so I compared site types (location type) and split London out of City-Centre.
- **The daily table is a sample.** It has 10,000 rows covering 8,910 of 43,800 possible store-days, and 1,006 of those are repeated. Weekday, holiday and mix figures come from it, so they're indicative. I never add it up against the monthly table, except in the loyalty estimate, which I label.
- **Product in the daily table is random.** The "top product" doesn't change that day's revenue, and Pumpkin Spice Latte is logged as top product 73 times before its own launch date. So I built no product ranking from it. Category margins come from the product table.
- **"Sales collapse"** is my own term, not the dictionary's: a month with sales below half of that store's own typical month. It flags 38 months, and 37 of them are loss months. Three of London's 49 loss months followed a collapse. Elsewhere it's 34 of 148.
- **The loyalty estimate.** Members' extra spend per visit is about 7 to 9% above non-members' (an estimate that mixes the monthly and sampled tables). I take that extra, assume it earns the estate's usual gross margin, and subtract the reward cost. Working store by store gives -£0.17m. Using one ratio for the whole estate gives -£0.45m.

## Other quirks in the data

- The date table ends on 30 December 2024, so it has 730 rows where two years should have 731. It has no `month_id`, and it carries a School-Holiday calendar value the dictionary doesn't list.
- `launch_date` is documented as never empty, but it's blank for 36 of 40 products.
- 119 store-months with rent between £9k and £10k are labelled Medium, where the dictionary says High. No Premium band exists.
- Four store-months have margins below -100%, outside the documented range.
- List margins in the product table (about 66 to 90%) run well above the roughly 62% the business actually earns.
- Cold drinks and merchandise have no revenue column in the daily table.
- A handful of store-months look planted. Manchester Collective's October 2024 revenue is exactly £8,000, for example.

## What this can't tell you

- **Whether loyalty brings people back.** The estimate only counts bigger tickets. If rewards bring extra visits, the result could flip. There's no before-the-programme baseline to measure it against.
- **Cause.** Staffing and margin move together, but a store might staff up because it's struggling.
- **Anything firm about small groups.** Eight flagged stores, regions with 3 to 7 stores, and 2 Train-Station sites are all small. "Five of eight got worse" is an observation, not a trend. Estate-wide loss months were flat (98 in 2023, 99 in 2024).

## How it's built

- Power BI, Star schema: store, product and date dimensions, with the monthly P&L as the main fact table and the daily table as the sample.
- Every number on the pages is a DAX measure, so slicers (year, site type, region) work and a reset button clears them. The only static text is verdicts and notes.
- A few measures deliberately ignore the year slicer, such as the movers and the 2023 vs 2024 comparison, and say so in the info panel on each page.
- Palette: white, light grey, night black and gold. Gold marks the thing to look at, and a gold bar always carries a label.


## Power BI Report Access

* [Click to download Power BI file](/Onyz%20Data%202026-10%20Power%20BI%20Representation.pbix)


##  Author

**Doobem**  
Data Analyst  

- LinkedIn: [doobemoguzie](https://www.linkedin.com/in/prosper-oguzie-54a706336) 
- GitHub: [Doobemoguzie](https://github.com/Doobemoguzie)
- Contact: [Prosperoguzie379@gmail.com](prosperoguzie379@gmail.com)


