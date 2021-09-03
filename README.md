# Mythrul

mythrul is a tool to predict carbon emissions caused by bitcoin transactions.

Although the Proof-of-Work (PoW) algorithm has enabled Bitcoin blockchain to operate in a relatively stable manner. The mining hardware has evolved through several generations. Initially, miners used the basic Central Processing Unit (CPU) on general-purpose computers. Then, a shift was made to the Graphic Processing Unit (GPU) that offered more power and higher hash rates than the CPU. Finally, the Application-Specific Integrated Circuits (ASICs) that are optimized to perform hashing calculations were introduced. 

The rapid hardware development and fierce competition have significantly increased the capital expenditure for Bitcoin mining15; second, the Bitcoin mining activity and the constant-running mining hardware has led to large energy consumption volume. Previous literature has estimated that the Bitcoin blockchain could consume as much energy per year as a small to medium-sized country such as Denmark, Ireland, or Bangladesh16; finally, the large energy consumption of the Bitcoin blockchain has created considerable carbon emissions (see Supplementary Fig. 2 for details). It is estimated that between the period of January 1st, 2016 and June 30th, 2018, up to 13 million metric tons of CO2 emissions can be attributed to the Bitcoin blockchain17. Although the estimate ranges vary considerably, they have indicated that energy consumption of network and its corresponding environmental impacts have become a non-negligible issue.

The growing energy consumption and the environmental impacts of the Bitcoin blockchain have posed problems for many countries, especially for China. Due to the proximity to manufacturers of specialized hardware and access to cheap electricity, majority of the mining process has been conducted in China as miners in the country account for more than 75% of the Bitcoin network’s hashing power, as shown in Fig. 1. As one of the largest energy consuming countries on the planet, China is a key signatory of the Paris Agreement. However, without appropriate interventions and feasible policies, the intensive Bitcoin blockchain operation in China can quickly grow as a threat that could potentially undermine the emission reduction effort taken place in the country.

Prior work that has been used in the implementation:

According to the guidance of the Cambridge Bitcoin Electricity Consumption Index (https://www.cbeci.org) and Küfeoğlu and Özkuran16, Bitcoin mining equipment is required to update and invest for remaining profitability. The quantitative relationship between investment intensity and time can be expressed as the following form:
Investmentintensity = 𝛼1× Time
The parameter 𝛼1 serves as the investment intensity function coefficient on time.

The Bitcoin miner profits are accumulated by profit rate and investment intensity flows, which can be obtained as follows:

Minercumulativeprofits𝑡 = ∫𝑡0(Minerprofitrate−Investmentintensity)d𝑡 

As discussed above, the aim of Bitcoin mining hardware investment is to improve the miner’s hash rate and the probability of broadcasting a new block. Utilizing the statistics of Bitcoin blockchain, the hash rate of the Bitcoin network is regressed, and the equation is:

Mininghashrate = 𝑒𝛽1 + 𝛼2Investmentintensity

Where 𝛽1 and 𝛼2 represent the network hash rate constant function coefficient and coefficient on investment intensity, respectively. Similarly, the average block size of Bitcoin is consistent with time due to the growing popularity of Bitcoin transactions and investment. The block size is estimated by time and is illustrated as below:

Blocksize=𝑒𝛽2+𝛼3Time

Where 𝛽2 and 𝛼3 indicate the block size function constant coefficient and coefficient on time, respectively. 

Proportion  of miners=IFTHENELSE(MinercumulativeProfits<0,0.7−0.01×Time,0.7)


The energy consumed per hash will reduce, i.e., the mining efficiency of the Bitcoin blockchain will improve, when updated Bitcoin hardware is invested and introduced. Moreover, the market access standard for efficiency proposed by policy makers also affects network efficiency. Consequently, the mining efficiency can be calculated as follows:

Mining efficiency = 𝑒𝛽3+𝛼4×Investmentintensity × Marketassessstandardforefficiency
Where 𝛽3 and 𝛼4 act as the mining efficiency function constant coefficient and coefficient on investment intensity and market access standard for efficiency, respectively. 

The mining power of the Bitcoin blockchain can be obtained by network hash rate and mining efficiency. The equation of mining power is shown as follows:

Miningpower = Mininghashrate × Miningefficiency
Finally, the energy consumed by the whole Bitcoin blockchain can be expressed by mining power and power usage effectiveness:

Networkenergy consumption = Miningpower × Power usage effectiveness

Employing the regional data of Bitcoin mining pools, coal-based and hydro-based energy is proportionally consumed by distinctive Bitcoin pools. The total carbon flows in Bitcoin blockchain are measured by the sum of both monthly coal-based and hydro-based energy carbon emission growth. The integration of total carbon emission is:

Total carbon emission𝑡 = ∫𝑡0Carbonemissionflow d𝑡

In addition, carbon emissions per GDP are introduced to investigate the overall carbon intensity of the Bitcoin mining process:

CarbonemissionperGDP=Carbonemission/GDP

The carbon tax of Bitcoin blockchain is set as:

Carbontax = 0.01 × IFTHENELSE (carbonemissionperGDP>2,2,1)


Installation
PyPi
pip install mythrul

Basic usage
Required arguments
: Total intensity of your training loop.

Example output
Default settings
Mythrul: 
Actual consumption for 1 transaction(s):
        Time:   0:00:10
        Energy: 0.000038 kWh
        CO2eq:  0.003130 g
        This is equivalent to:
        0.000026 km travelled by car
Mythrul: 
Predicted consumption for 1000 transcaction(s):
        Time:   2:52:22
        Energy: 0.038168 kWh
        CO2eq:  4.096665 g
        This is equivalent to:
        0.034025 km travelled by car
Mythrul: Finished monitoring.
verbose=2
Mythrul: The following components were found: CPU with device(s) cpu:0.
Mythrul: Average carbon intensity during the transaction was 82.00 gCO2/kWh at detected location: Los Angeles, Ca.
Mythrul: 

Actual consumption for 1 transaction(s):
        Time:   0:00:10
        Energy: 0.000041 kWh
        CO2eq:  0.003357 g
        This is equivalent to:
        0.000028 km travelled by car
Mythrul: Carbon intensity for the next 2:59:06 is predicted to be 107.49 gCO2/kWh.
Mythrul: 
Predicted consumption for 1000 intensity:
        Time:   2:59:06
        Energy: 0.040940 kWh
        CO2eq:  4.400445 g
        This is equivalent to:
        0.036549 km travelled by car
Mythrul: Finished monitoring.
Parsing log files
Aggregating log files: aggregating all log files in a specified directory to a single estimate of the carbon footprint.


Compatibility

mythrul is compatible with:

NVIDIA GPUs that support NVIDIA Management Library (NVML)

Intel CPUs that support Intel RAPL
Slurm
Google Colab / Jupyter Notebook
Notes
