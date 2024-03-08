# Pymaceuticals Data Cleansing #
Two datasets consisting of study results and mouse data were imported and read as CSV files. matplotlib.pyplot, pandas, and scipy.stats were imported as dependencies. The two files were merged; value_count and .loc was performed on Mouse ID and Timepoint to identify duplicate record. The duplicate record was dropped, resulting in 248 unique mouse IDs.

