# Module-9-Challenge-Surf-Icecream


### Resources
- Data source: hawaii.sqlite
- Software: Python 3.7.10, Jupyter Notebook 6.3.0


## Overview

This analysis was done for helping W.Avy with their due digillence regarding a surf shop & ice cream concept in Hawaii. Precipitation, temperatures and metrics recorded from Hawaii stations were used to identify whether the target spot would be suitable for the concept and move forward with investments. Additionally this analysis has to be scalable providing analysis for some other Hawaiian locations in case the project is successful and requires expansion. 

## Results


- 75%+ of the time the temperature will be +69ºF for June and December so temperature does not vary to much in Oahu
- In average June month are ~4ºF warmer than December but both with a +70ºF average temperature
- 68% of the time (2 std dev) the temperature will not vary more than +/-3.25ºF for June and +/-3.75ºF in December 

**June Temperature Stats**
![Oahu - June Temperatures](https://github.com/Mejikano/Module-9-Challenge-Surf-Icecream/blob/main/Resources/June_Temp_Stats.png)

**December Temperature Stats**
![Oahu - December Temperatures](https://github.com/Mejikano/Module-9-Challenge-Surf-Icecream/blob/main/Resources/December_Temp_Stats.png)


## Summary 

According to the analysis Oahu Temperature does not vary too much in Summer (June) and Winter (December) which will be ideal for ice cream before, after, or even during surfing the Waves! 

However to complete the analysis below queries would provide the precipitation results for both months under analysis: 

```

    results = session.query(Measurement.date, Measurement.prcp).\
                filter(extract('month',Measurement.date) == 6).all()
    
    results = session.query(Measurement.date, Measurement.prcp).\
                filter(extract('month',Measurement.date) == 12).all()

```

Finally, a temperature and precipitation summary throughout the year bolsters our conclusion. Oahu Weather is ideal for surf and icecream ALL YEAR LONG, although June has high precipitations the temperatures do not drop so being wet because of waves or rain would not make the difference for enjoying a good icecream and buy SURF STUFF!

Below queries aggregates by month temperature and precipitations providing min, max and average reads:

```
   results = session.query(extract('month',Measurement.date), func.min(Measurement.tobs),\
        func.avg(Measurement.tobs), func.max(Measurement.tobs)).\
        group_by(extract('month',Measurement.date)).all()
    df3= pd.DataFrame(results, columns=['Month','Min Temperature','Avg Temperature','Max Temperature'])
    df3


    results = session.query(extract('month',Measurement.date), func.min(Measurement.prcp),\
        func.avg(Measurement.prcp), func.max(Measurement.prcp)).\
        group_by(extract('month',Measurement.date)).all()
    df4= pd.DataFrame(results, columns=['Month','Min Precipitation','Avg Precipitation','Max Precipitation'])
    df4
```

Below Tables summarizes the results of suggested queries specified before.

**Oahu All Months Temperatures**
![Oahu - All Months Temperatures](https://github.com/Mejikano/Module-9-Challenge-Surf-Icecream/blob/main/Resources/AllMonths_Temps.png)

**Oahu All Months Precipitations**
![Oahu - All Months Precipitations](https://github.com/Mejikano/Module-9-Challenge-Surf-Icecream/blob/main/Resources/AllMonths_Precipitations.png)
