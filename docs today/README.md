Cryptocurrency Arbitrage

Arbitrage Cryptocurrency Determine best time to buy and sell crypto currencies by anaylzing data trends from multiple exchanges.

Technologies

Systems

conda 4.10.3 - Package manager, Environment Manager

python 3.10.1 64-bit-

JupyterLab - included in Python

Pandas - included in Python

Installation Guide must use JupyterLab to access the application file.

Additional installs are needed before running the program. Please install in terminal, in a dev environment:

conda active dev python -m ipykernel install --user --name dev conda install -c conda-forge nodejs conda deactivate

open JupyterLab by the following code:

conda activate dev jupyter lab

conda activate dev conda install pandas -y conda deactive Usage and Examples To use the cryptocurrency arbitrage strategy, the repository will need to be cloned from GitHub and into a local repository.

In the crypto_arbitrage folder, you will want to use the 'crypto_arbitrage.ipynb' file. Enter into the dev environment by commanding:

conda activate dev Next, use the code:

jupyter lab to run the file.

opening_repo

01_import

Collect the Data
In this section, both datasets from Bitstamp and Coinbase are pulled and sorted by date/time with the usage of index_col="Timestamp".

02_collect_data collectdata coinbase

Prepare the Data
In order to prepare the data, the use of the functions isnull(), duplicated(), and dropna() were essential in providing clean data to work with. Using isnull().mean() or isnull().sum() helps to understand how much of the dataset is affected by incomplete data.

04_Prepare_data_isnull

Code used to prepare/clean the data:

bitstamp.isnull() bitstamp.duplicated() bitstamp = bitstamp.dropna().copy()

03_prepare_data 03_prepare_data float

Analyze the Data capture abrbitrage spread
03_analyze close data

Summary statistics are ran to understand the data we are working with. To do this we use the describe() function.

03_analyze describe

Visualizations are also used to help analyze the data. To do this we use the the code:

bitstamp_sliced['Close'].plot( figsize=(30, 20), title="Bitstamp v. Coinbase", color="green", label="Bitstamp")

To plot two graphs on one plot, we state legend=True

bitstamp_sliced['Close'].plot(legend=True, figsize=(30, 20), title="Bitstamp v. Coinbase", color="green", label="Bitstamp") coinbase_sliced['Close'].plot(legend=True, figsize=(30, 20), color="orange", label="Coinbase")

This helps visualize the spread between the two exchange datasets. From there the calculation to see what percentage of return a person could earn is computed by taking the gain (loss) and dividing it by the price of the lower-priced exchange 'close' data.

Next, filter the data by only including the returns that give a positive return (>0), and ensuring that it meets the 1% threshold to cover cost.

The returns that met these requirements are then multiplied by the price of the lower-priced exchange to show what the profit would be for that day.

The profits are then graphed to give an idea of how much profit is earned during what time of day. With further analysis, it can be infered that the arbitrage opportunity has ended by the end of the dataset as Bitstamp's prices increase and closely move with the prices of Coinbase. The spread gap closes and there is little profit that can be made.

Contributors Phil Hills

License MIT License
