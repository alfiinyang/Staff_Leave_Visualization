## STEP 1 — Converting to CSV

The document was an excel sheet having five columns: “S/N”, “NAME”, “ID.NO”, “START DATE” and “END DATE”, with a title as the document header. The first step was to convert the file to CSV format from within Excel. I did this by using the “Save as” feature from the “File” dropdown and selecting “CSV (Comma delimited)” option of the “Save as type” response.

![xx](https://user-images.githubusercontent.com/92611635/233744457-81e22e6f-f336-4564-820a-1d627ba37671.PNG)


## STEP 2 — Reading the CSV file

After importing the relevant python packages (Pandas, Matplotlib, and Numpy), the CSV file was read as a Pandas DataFrame using the “read_csv()” function with the following keys:

1. `index_col` = 0 (to set “S/N” as the index column),

2. `header` = 1 (to set the row containing column names as header), and,

3. `parse_dates` = [‘START DATE’, ‘END DATE’] (to parse the contents of the date columns as they were originally mixed format; needful for plotting the histogram).

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

staff_leave = pd.read_csv("C:\\Users\\XXXXX\\Downloads\\XXXXXX.csv", index_col = 0, header = 1, parse_dates = ["START DATE", "END DATE"])
```

## STEP 3 — Plotting the histogram

The data of interest were in the last two columns, `START DATE` and `END DATE`. Since this was a Pandas object, the interest columns were accessed using the square brackets with the syntax `pandas_object[‘column name’]`. Using either single square brackets (for pandas series) or double square brackets (for pandas dataframe) is acceptable at this point.

This was passed into the `hist()` function with the bin size and colour specifications. The x and y axes labelling and the chart titling was done with the `xlabel()`, `ylabel()`, and `title()` functions. Then the `show()` function was called to display the chart.

## STEP 4 — Plotting the second histogram

The `END DATE` distribution was plotted by repeating STEP 3, after clearing the previous plot with the `clf` method.

```
plt.clf
plt.hist(staff_leave["END DATE"], 12, color = 'red')
plt.xlabel("MONTH"); plt.ylabel("STAFF"); plt.title("LEAVE END DATES DISTRIBUTION")
plt.show()
```

Below are the outputs of both plots.

![Figure_1](https://user-images.githubusercontent.com/92611635/233743613-9c5e77bc-2b48-48a1-9a29-7b8801df9209.png)
![Figure_2](https://user-images.githubusercontent.com/92611635/233743695-be85a487-77cf-4d9c-adb4-2214847e0069.png)

It was evident that more staff preferred taking their leave about the first quarter of the year. I desired to understand why this was the case, but I was limited by the unavailability of data. More data, more insight.

If more data was available more understanding about employee decisions regarding their leave scheduling would have been realized.
