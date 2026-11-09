Fix leakage in coffee notebook, split by lot and compare models with CV

 Move median imputation out of the EDA part. It was filling NaNs on the
  whole dataset before the split, now only the pipeline does it
 Keep certification as its own "None" category instead of dropping it
  (61% missing probably just means no certification)
 Split train/test with GroupShuffleSplit on lot_id so the same lot can't
  end up on both sides, and print the number of shared lots as a check
 Add a quick check in the data quality cell to see if repeated lots are
  exact copies
 Add LinearRegression to the model comparison
 Add 5-fold GroupKFold CV on the training set and pick the best model
  from CV instead of the test set
 Clean up the imports and remove the old "messy imports" comment
 Drop the unused label argument in evaluate(), fix the DROP_COLS comments
  and a few typos in the section titles
 Outputs are cleared from the missing values section onward, rerun the
  notebook to refresh them
