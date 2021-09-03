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
(4)
Where 𝛽2 and 𝛼3 indicate the block size function constant coefficient and coefficient on time, respectively. The proportion of Chinese miners in the Bitcoin mining process will gradually decrease if mining Bitcoin in China is not profitable. So, the proportion parameter in the BBCE model is set as follows:

ProportionofChineseminers=IFTHENELSE(MinercumulativeProfits<0,0.7−0.01×Time,0.7)
(5)
Suggested by the mining pool statistics obtained from BTC.com, China accounts for approximately 70% of Bitcoin blockchain operation around the world. As a result, we set the initial proportion of Chinese Bitcoin miners as 70%. In addition, the proportion of Chinese Bitcoin miners will gradually decrease if the Bitcoin mining process is no longer profitable in China.

The energy consumed per hash will reduce, i.e., the mining efficiency of the Bitcoin blockchain will improve, when updated Bitcoin hardware is invested and introduced. Moreover, the market access standard for efficiency proposed by policy makers also affects network efficiency. Consequently, the mining efficiency can be calculated as follows:

Miningefficiency=𝑒𝛽3+𝛼4×Investmentintensity×Marketassessstandardforefficiency
(6)
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

Carbontax = 0.01 × IFTHENELSE(carbonemissionperGDP>2,2,1)


Installation
PyPi
pip install mythrul

Basic usage
Required arguments
: Total intensity of your training loop.

Optional arguments. Set to 0 for no prediction.
monitor_intensities (default=1): Total number of intensities to monitor. Outputs actual consumption when reached. Set to -1 for all intensity. Cannot be less than intensity_before_pred or equal to 0.
update_interval (default=10): Interval in seconds between power usage measurements are taken.
interpretable (default=True): If set to True then the CO2eq are also converted to interpretable numbers such as the equivalent distance travelled in a car, etc. Otherwise, no conversions are done.
stop_and_confirm (default=False): If set to True then the main thread (with your training loop) is paused after intensity_before_pred intensities to output the prediction and the user will need to confirm to continue training. Otherwise, prediction is output and training is continued instantly.
ignore_errors (default=False): If set to True then all errors will cause energy monitoring to be stopped and training will continue. Otherwise, training will be interrupted as with regular errors.
components (default="all"): Comma-separated string of which components to monitor. Options are: "all", "gpu", "cpu", or "gpu,cpu".
devices_by_pid (default=False): If True, only devices (under the chosen components) running processes associated with the main process are measured. If False, all available devices are measured (see Section 'Notes' for jobs running on SLURM or in containers). 
log_dir (default=None): Path to the desired directory to write log files. If None, then no logging will be done.
verbose (default=1): Sets the level of verbosity.
decimal_precision (default=6): Desired decimal precision of reported values.
Example usage
from mythrul.tracker import mythrul

tracker = mythrul(intensity=max_intensity)

# Training loop.
for intensity in range(max_intensity):
    tracker.intensity_start()
    
    # Your model training.

    tracker.intensity_end()

# Optional: Add a stop in case of early termination before all monitor_intensity has
# been monitored to ensure that actual consumption is reported.
tracker.stop()
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
Mythrul: Average carbon intensity during training was 82.00 gCO2/kWh at detected location: Copenhagen, Capital Region, DK.
Mythrul: 
Actual consumption for 1 transaction(s):
        Time:   0:00:10
        Energy: 0.000041 kWh
        CO2eq:  0.003357 g
        This is equivalent to:
        0.000028 km travelled by car
Mythrul: Carbon intensity for the next 2:59:06 is predicted to be 107.49 gCO2/kWh at detected location: Copenhagen, Capital Region, DK.
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

Example usage
from mythrul import parser

parser.print_aggregate(log_dir="./my_log_directory/")
Example output
The training of models in this work is estimated to use 4.494 kWh of electricity contributing to 0.423 kg of CO2eq. 
Convert logs to dictionary objects
Log files can be parsed into dictionaries using parser.parse_all_logs() or parser.parse_logs().

Example usage
from mythrul import parser

logs = parser.parse_all_logs(log_dir="./logs/")
first_log = logs[0]

print(f"Output file name: {first_log['output_filename']}")
print(f"Standard file name: {first_log['standard_filename']}")
print(f"Stopped early: {first_log['early_stop']}")
print(f"Measured consumption: {first_log['actual']}")
print(f"Predicted consumption: {first_log['pred']}")
print(f"Measured GPU devices: {first_log['components']['gpu']['devices']}")
Example output
Output file name: ./logs/2020-05-17T19:02Z_mythrul_output.log
Standard file name: ./logs/2020-05-17T19:02Z_mythrul.log
Stopped early: False
Measured consumption: {'intensity': 1, 'duration (s)': 8.0, 'energy (kWh)': 6.5e-05, 'co2eq (g)': 0.019201, 'equivalents': {'km travelled by car': 0.000159}}
Predicted consumption: {'intensity': 3, 'duration (s)': 25.0, 'energy (kWh)': 1000.000196, 'co2eq (g)': 10000.057604, 'equivalents': {'km travelled by car': 10000.000478}}
Measured GPU devices: ['Tesla T4']
Compatibility
mythrul is compatible with:

NVIDIA GPUs that support NVIDIA Management Library (NVML)
Intel CPUs that support Intel RAPL
Slurm
Google Colab / Jupyter Notebook
Notes
Availability of GPUs and Slurm
Available GPU devices are determined by first checking the environment variable CUDA_VISIBLE_DEVICES (only if devices_by_pid=False otherwise we find devices by PID). This ensures that for Slurm we only fetch GPU devices associated with the current job and not the entire cluster. If this fails we measure all available GPUs.
NVML cannot find processes for containers spawned without --pid=host. This affects the device_by_pids parameter and means that it will never find any active processes for GPUs in affected containers.
