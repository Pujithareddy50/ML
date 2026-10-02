why after the PDF calculation graphs are different for before scaling and after scaling using standardscalar() values
Thought for a second

PDF/KDE changed because:

Before scaling, Age and Salary have very different ranges.
Age values are small, like 20–60.
Salary values are large, like 15000–180000.
So before scaling, Age curve looks squeezed near one side.
After StandardScaler(), both Age and Salary come to a common range, mostly around -3 to +3.
So after scaling, both curves become clearly visible.
The data pattern is almost same, but the scale of x-axis changed, so the PDF/KDE graph looks different.
how is the KDE/PDF calculated?
Thought for a couple of seconds

KDE/PDF is calculated like this:

Take all values of one column, for example Age.
Age = [20, 25, 30, 35, 40]
KDE puts a small smooth curve around each data point.
Then it adds all those small curves together.
The final smooth curve shows where values are more concentrated.
If many values are near 30, KDE curve becomes high near 30.
If only few values are near 60, KDE curve becomes low near 60.

Simple meaning:

KDE/PDF tells:
Where is the data more crowded?
Where is the data less crowded?

For example:

High curve  = more data points in that range
Low curve   = fewer data points in that range

In your graph, KDE is showing the density/distribution of Age and EstimatedSalary.

blue and orange lines are for?
Why one attribute density is high and others is very less?
Thought for a couple of seconds

In your code:

sns.kdeplot(X_train['Age'], ax=ax1)
sns.kdeplot(X_train['EstimatedSalary'], ax=ax1)

Usually:

Blue line   = Age
Orange line = EstimatedSalary

Because Age is plotted first, so it gets blue color.
EstimatedSalary is plotted second, so it gets orange color.

To clearly see this, add labels:

sns.kdeplot(X_train['Age'], ax=ax1, label='Age')
sns.kdeplot(X_train['EstimatedSalary'], ax=ax1, label='EstimatedSalary')
ax1.legend()

Why one density is high and another is very less?

Because density depends on how spread the values are.

Simple idea:

Less spread data  = high density curve
More spread data  = low density curve

Example:

Age: 20 to 60
Salary: 15000 to 180000

Age values are in a small range, so the curve becomes tall.

Salary values are spread across a very large range, so the curve becomes flat/low.

Important:

High density does not mean high value.
High density means more data points are crowded in that region.