# Mythrul

mythrul is a tool to predict carbon emissions caused by blockchain transactions.


Carbon Footprint

We calculate Bitcoin’s carbon footprint based on its total power consumption and geographic footprint. To determine the amount of carbon emitted in each country, we multiply the power consumption of Bitcoin mining by average and marginal emission factors of power generation. Our best guess is based on average emission factors, which represent the carbon intensity of the power generation resource mix, while marginal emission factors account for the carbon intensity of incremental load change.

We find that the annual global carbon emissions of Bitcoin range between 22.0 and 22.9 MtCO2, a ratio that sits between the levels produced by Jordan and Sri Lanka12 and is comparable to the level of Kansas City.13 22.0 MtCO2 is based on the footprint of the device IP method, and 22.9 MtCO2 assumes the footprint of the pool server IP method. Compared to the global annual energy demand of approximately 13,760 Mtoe (∼160 PWh) or the global energy-related CO2 emissions of more than 30 GtCO2 in 2016,21 this might seem small. Still, Bitcoin’s CO2 equivalent ranks between numbers 82 and 83 on the list of biggest emitting countries.


If we assume fossil fuels cover the additional load entirely, we find that annual emissions caused by Bitcoin mining could be as high as 51.0 MtCO2. On the contrary, assuming a higher share of clean power consumption decreases CO2 emissions.

Some have argued that miners do not operate continuously. We assume that miners run their hardware continuously throughout the year. A comparison of break-even electricity prices for ASIC-based mining systems shows that this assumption is valid for most fixed-rate retail tariffs and especially for regions with high mining activity. This is also the reason for ignoring potential additional sources of revenue from price volatility in the wholesale market or from the provision of load-balancing services, as these would not change the duration of mining operations.

In the long run, we can envision Bitcoin miners to increasingly establish their operations near large sources of renewable energy, which also triggers further development of renewable generation resources at the respective sites.27 Therefore, long-run emissions factors of the Bitcoin network might be lower than the current grid average.

So, what is the carbon footprint of Ethereum?

Its network hashrate has been hovering very closely to 300 TH/s the past month

At the time of this writing, the Ethereum network is still largely dominated by large GPU farms. It is likely that ASICs were privately being used by a handful of small teams with the necessary engineering and manufacturing talent (and capital), but direct-to-consumer ASIC hardware for Ethereum didn’t really show up until this summer.

There are an estimated 10 million GPUs churning up hashes for the Ethereum network, to replace those with ASICs will likely take more than a year… assuming price stability occurs (and coin prices are volatile and anything but stable).

For illustrative purposes, what if the entire network were to magically switch over the most efficient hardware -the Innosilicon A10 – released next month?

Innosilicon currently advertises its top machine can generate 485 megahashes/sec and consumes ~ 850 W.

So what is that math?

The Ethereum network is ~300 TH/s which is around 300,000,000 megahashes /sec.

Quick division: that’s the equivalent of 618,557 A10 machines.

Again, each machine is advertised to consume ~850 W.

in a single day one A10 consumes: 20.4 kWh
in a month: ~612 kWh
So what would 618,557 A10 machines consume in a single day?
– about 12.6 million kWh / day

And annually:
– about 4.6 billion kWh / year

That works out to be between Afghanistan or Macau.  However…

Before you say “this is nearly identical to Bitcoin Cash” keep in mind that the Ethereum estimate above is the lowest of lower-bounds because it uses the most efficient mining gear that hasn’t even been released to the consumer.

In reality the total energy consumption for Ethereum is probably twice as high.

Why is Etherum electricity usage likely twice as high as the example above?

Because each of the ~10 million GPUs on the Ethereum network is significantly less efficient per hash than the A10 is. 4  Note: an example of a large Ethereum mine that uses GPUs is the Enigma facility.

For instance, an air-cooled Vega 64 can churn ~41 MH/s at around 135 W which as you see above, is much less efficient per hash than an A10.

If the Ethereum network was comprised by some of the most efficient GPUs (the Vega 64) then the numbers are much different.

Starting with: 300,000,000 MH/s divided by 41 MH/s.  There is the equivalent to 7.32 million Vega GPUs generating hashes for the network which is more in line with the ~10 million GPU estimate.

one Vega 64 running a day consumes ~3.24 kWh
one Vega 64 running a month: ~77.7 kWh
If 7.32 million Vega equivalent GPUs were used:

in a day: ~ 23.71 million kWh
in a year: ~8.65 billion kWh
That would place the Ethereum network at around 100th on the electricity consumption list, between Guatemala and Estonia.



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
