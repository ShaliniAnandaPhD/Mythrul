# Mythrul

mythrul is a tool to predict carbon emissions caused by bitcoin transactions.

Participation in the Bitcoin blockchain validation process requires specialized hardware and vast amounts of electricity, which translates into a significant carbon footprint. Here, we demonstrate a methodology for estimating the power consumption associated with Bitcoin’s blockchain based on IPO filings of major hardware manufacturers, insights on mining facility operations, and mining pool compositions. We then translate our power consumption estimate into carbon emissions, using the localization of IP addresses. We determine the annual electricity consumption of Bitcoin, as of November 2018, to be 45.8 TWh and estimate that annual carbon emissions range from 22.0 to 22.9 MtCO2. This means that the emissions produced by Bitcoin sit between the levels produced by the nations of Jordan and Sri Lanka, which is comparable to the level of Kansas City. With this article, we aim to gauge the external costs of Bitcoin and inform the broader debate on the costs and benefits of cryptocurrencies.

Carbon Footprint

We calculate Bitcoin’s carbon footprint based on its total power consumption and geographic footprint. To determine the amount of carbon emitted in each country, we multiply the power consumption of Bitcoin mining by average and marginal emission factors of power generation. Our best guess is based on average emission factors, which represent the carbon intensity of the power generation resource mix, while marginal emission factors account for the carbon intensity of incremental load change.

We find that the annual global carbon emissions of Bitcoin range between 22.0 and 22.9 MtCO2, a ratio that sits between the levels produced by Jordan and Sri Lanka12 and is comparable to the level of Kansas City.13 22.0 MtCO2 is based on the footprint of the device IP method, and 22.9 MtCO2 assumes the footprint of the pool server IP method (we apply emission factors from the IEA21; the calculation can be found in Data S1: Sheet 3.1.). Compared to the global annual energy demand of approximately 13,760 Mtoe (∼160 PWh) or the global energy-related CO2 emissions of more than 30 GtCO2 in 2016,21 this might seem small. Still, Bitcoin’s CO2 equivalent ranks between numbers 82 and 83 on the list of biggest emitting countries.

Many have argued that clean surplus energy fuels Bitcoin to a significant degree. In the short run, which is relevant for our snapshot, curtailment rates of clean resources may be large in certain areas with Bitcoin mining activity. Especially in southwestern China, hydropower accounts for around 80% of the generated electricity in the provinces of Yunnan and Sichuan.22 Yunnan curtailed 31.2 TWh of hydropower in 2016, which equaled 11.6% of the total electricity generation in the province.23 However, mining activities can also be found in regions with coal-heavy power generation, such as in the province of Inner Mongolia.24 Pool regional statistics of BTC.com suggest a 58% versus 42% split between hydro-rich and coal-heavy regions in China. The ratio represents the computing power reported from Shenzhen (server location closer to hydro-rich regions) versus Beijing (server location closer to coal-heavy regions).25 If we weight the emission factors of Sichuan (265 g/kWh) and Inner Mongolia (947 g/kWh) accordingly, we obtain an adjusted emission factor of 550 g/kWh, which we use in our calculations to account for the special case of China.

If we assume fossil fuels cover the additional load entirely, we find that annual emissions caused by Bitcoin mining could be as high as 51.0 MtCO2. On the contrary, assuming a higher share of clean power consumption decreases CO2 emissions.

Some have argued that miners do not operate continuously. We assume that miners run their hardware continuously throughout the year. A comparison of break-even electricity prices for ASIC-based mining systems shows that this assumption is valid for most fixed-rate retail tariffs and especially for regions with high mining activity. The steadiness of the hash rate distribution in Figure 3 supports this assumption. This is also the reason for ignoring potential additional sources of revenue from price volatility in the wholesale market or from the provision of load-balancing services, as these would not change the duration of mining operations.

In the long run, we can envision Bitcoin miners to increasingly establish their operations near large sources of renewable energy, which also triggers further development of renewable generation resources at the respective sites.27 Therefore, long-run emissions factors of the Bitcoin network might be lower than the current grid average.

Please find some key equations used to calculate the effect of blockchain on carbon footprint:

![image](https://user-images.githubusercontent.com/50239203/132248312-f20abbc3-0aaa-485a-82cc-0295ee205a70.png)
![image](https://user-images.githubusercontent.com/50239203/132248353-58ac5433-29b8-421b-8699-14527333cb3d.png)
![image](https://user-images.githubusercontent.com/50239203/132248377-baf22a71-c8f3-450d-a135-a8878565f433.png)
![image](https://user-images.githubusercontent.com/50239203/132248422-e1caf6a3-72b0-4201-b796-efbc26ede559.png)
![image](https://user-images.githubusercontent.com/50239203/132248448-28fc5288-8be4-459c-a37b-98a189a006d1.png)
![image](https://user-images.githubusercontent.com/50239203/132248476-3ec8899b-eeac-47d5-861d-928850b30a83.png)
![image](https://user-images.githubusercontent.com/50239203/132248525-bbdb0402-4e94-4194-9b80-bc81215a723c.png)
![image](https://user-images.githubusercontent.com/50239203/132248559-3430c595-b833-4afd-9925-3583d757d2b5.png)


Compatibility

mythrul is compatible with:

NVIDIA GPUs that support NVIDIA Management Library (NVML)

Intel CPUs that support Intel RAPL
Slurm
Google Colab / Jupyter Notebook
Notes
