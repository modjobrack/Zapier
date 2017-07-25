# Zapier Take Home

Ingesting the data- Using pgAdmin I connected to the server and downloaded the data.

select user_id, account_id, tasks_used_per_day, date, date - lag(date) over (partition by user_id order by date) as difference into tasks_used_modj from tasks_used order by user_id, date;

Calculating the difference between dates allowed me to determine when a user was Active, in Churn, or Inactive.

The data did not contain the full month of June so I filtered the data to show only through May 31st, since that was the last complete month available.

After adding the new column of data I exported the file as a CSV and connected it to Tableau to continue to model and visualize the data.

The following calculation was used in Tableau to determine when a user was Active, in Churn, or Inactive:

Status: IF [Difference in Days] < 28 then "Active" ELSEIF [Difference in Days] < 56 then "Churn" ELSE "Inactive" END

The attached Tableau Packaged Workbook contains the visualizations. There are screenshots of the report as well.
Find packaged workbook here: https://www.dropbox.com/s/sqcw9vxlr90xwft/ZapierTakeHome.twbx?dl=0 


