# Weather and solar irradiance prediction


https://open-meteo.com/


Both are explained in [this July 2024 blog post](https://tryolabs.com/blog/solar-energy-predictions-with-ai-a-joint-case-study?utm_source=post_link&utm_medium=social_media&utm_campaign=blog_post_ocf) on Solar energy predictions with AI.

It describtes a project with Open Climate Fix (OCF), a British non-profit organization. "This project aims to create an open-source tool for predicting solar energy that is accessible and beneficial to all. It leverages data on the panel's location, specific characteristics, and various meteorological variables..."

It may however only be for the UK.  "Although the model can be applied globally, caution is advised when using it outside the training dataset’s geographical bounds, as different regions may exhibit unique patterns in solar radiation,"

They provide a [colab](https://colab.research.google.com/drive/1qKDFRpq4Hk-LHgWuDsz_Najc3Zq-GVNY?usp=sharing) example notebook.

![Solar](https://tryolabs.imgix.net/assets/blog/solar-energy-predictions-with-ai-a-joint-case-study/OCF1-fb07e5e01e.png?auto=format&fit=max&w=3840)


![alt text](solar_prediction.png)

The model seems to obtain weather forecasts from the Open-Meteo API, and then uses a neural network to predict solar irradiance.  
("Power (kw)", "Temperature", "Precipitation", "Cloud Cover (Low)", "Cloud Cover (Mid)",
                                    "Cloud Cover (High)", "Wind Speed (10m)",
                                    "Shortwave Radiation", "Direct Radiation"))


WHy better forecasting:

https://openclimatefix.org/projects/forecasting

Solar Photovoltaics (PV) is one of the most significant sources of uncertainty in the UK’s power forecasts. To mitigate against the risk of a large cloud sweeping across the country (and hence the grid losing Gigawatts of PV generation), the Electricity System Operator (National Grid in the United Kingdom) keeps lots of natural gas generators operating at less than full capacity, so they have headroom to ramp up quickly (spinning reserve).
‍
The physics of the grid dictate that - at every instant - supply must precisely match demand. So, any loss in PV supply must be immediately replaced. The spinning reserve, usually gas turbines, are kept idling because they take several hours to start up from cold, costing a lot of money and pumping out a lot of CO2.
‍
If National Grid had better PV forecasts, even for the next few hours, they could reduce the amount of spinning reserve required, and hence reduce emissions (by about 100,000 tonnes per year for the UK [Details]).

Really interesting blog post on data:

https://openclimatefix.org/post/lazy-loading-making-it-easier-to-access-vast-datasets-of-weather-satellite-data