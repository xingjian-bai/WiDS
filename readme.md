## Pre-requisite
1. [Install conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)


## Build codebase locally
1. [Add a folder using the terminal, and open it](https://blog.csdn.net/biggercoffee/article/details/50752910)
2. `git clone https://github.com/xingjian-bai/WiDS`
   - Setting up Github account on terminal [tutorial 1](https://www.cnblogs.com/suihung/p/16087899.html), [tutorial 2](https://tonyscript.github.io/2017/12/17/2017-12-17-Using-GitHub-In-Terminal/)
3. `conda env create -f environment.yml`
    - environment.yml is the description file of the env。
4. `conda activate wids`
5. Pushing the repo.
   1. `git add .` 
   2. `git commit -m "some message"`
   3. `git push`

## Download data
- Download file from Kaggle, and put it into the root directory


# EDA resources
## [Code - EDA, WiDS Datathon-2023](https://www.kaggle.com/code/khsamaha/eda-wids-datathon-2023)
- 2 character feature: start date, climateregions_climateregion
	- Add new features “year”, “month” and “day”
- 8  Variables contain missing data
	- Impute Missing data with the mean of each variable that has NAs
- Plots on target against the start date
	> we have no sufficient evidence to say that this distribution is sampled from the Normal Distribution population
- Target distribution by Regions
> perhaps we would build a model for each Region separately and check the result!

- Target Variable and Relative Humidity Time series
	- high temp. --> low RH, low temp. --> high RH
	- some noise in this pattern, I might say it is the YEARS issue
- Target Variable and precipitation Time series
	- high temp. --> Low probability or no precipitation, low temp. --> high probability of precipitation
- Relative Humidity and Target variable relationship by Climate Region
	- ![[Pasted image 20230126091531.png]]
> 		I would do a lot of exploration for this Variable (Climate Region)


## [Simple basline - RMSE 1.14](https://www.kaggle.com/code/ducanger/wids-2023-simple-basline-rmse-1-14)
- catboost is the best so far
```
submit = pd.read_csv('/kaggle/input/widsdatathon2023/sample_solution.csv')
submit[target] = model.predict(X_test)
submit.to_csv('submission.csv', index = False)
```

## [different locations train/test SOLVED](https://www.kaggle.com/code/flaviafelicioni/wids-2023-different-locations-train-test-solved)
> The current notebook is based on [lgbm model](https://www.kaggle.com/code/iamleonie/wids-datathon-2023-forecasting-with-lgbm)
> Although a "location feature" was created in the original notebook from the latitude/longitude coordinates, different locations were obtained between the training and test data.

In this notebook, we have corrected this problem.
- **Insight 1**: For each date, we have 514 unique values. This means, we have 514 unique locations.
- **Insight 2:** We have different locations, between training and test data. But just slightly.
- SOLUTION: we truncate the data.
Now we have obtained the relationship between the locations in test and training set.

## [Forecasting with LGBM](https://www.kaggle.com/code/iamleonie/wids-datathon-2023-forecasting-with-lgbm)
- After EDA we found we should not fill in empty data with mean.
- [season encoding](https://colab.research.google.com/drive/10r73mOp1R7cORfeuP97V65a-rgwGyfWr?usp=sharing#scrollTo=c9ZkVb2aU-S7)
- [year sin cos encoding](https://colab.research.google.com/drive/10r73mOp1R7cORfeuP97V65a-rgwGyfWr?usp=sharing#scrollTo=c9ZkVb2aU-S7)
- w-and-b used in hyperparameter tunning
- loc-group: a deeper understanding
	- The training dataset is actually 514 * (365 + 366) = 465734 terms!!
			- from 2014 sth to 2016 sth
			- test set: 2020 to 2021 sth
## [Data Drift for Dynamic Forecasts](https://colab.research.google.com/drive/10r73mOp1R7cORfeuP97V65a-rgwGyfWr?usp=sharing#scrollTo=c9ZkVb2aU-S7)

