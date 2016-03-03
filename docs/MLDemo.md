# Add Columns

*Add columns from one dataset to another*

Category: [Data Transformation\Manipulation](92B32033-F75F-4854-AC8F-9110B3FE7E09)

Module Overview
---------------

-   To concatenate columns from different datasets, the columns in each dataset must have an equivalent number of rows.

-   The number of columns in the new dataset equals the sum of the columns of both input datasets.

-   You cannot choose individual columns to add \-\- all the columns from each dataset are concatenated when you use [!INCLUDE[M_AddColumns](Token\M_AddColumns.md)]. If you want to add only a subset of the columns, use [!INCLUDE[M_ProjectColumns](Token\M_ProjectColumns.md)] to create a dataset with the columns you want.

-   If there are two columns with the same name in the input datasets, a numeric suffix is added to the name of the column from the dataset used in the right\-hand input. For example, if there are two instances of a column named     **legacyBold tag is not supported!!!!**
, the second column would be renamed     **legacyBold tag is not supported!!!!**

[!INCLUDE[M_AddColumns](Token\M_AddColumns.md)] concatenates two datasets by combining all columns from the two datasets that you specify as inputs, to create a single dataset.
* To concatenate columns from different datasets, the columns in each dataset must have an equivalent number of rows.
* The number of columns in the new dataset equals the sum of the columns of both input datasets.
* You cannot choose individual columns to add -- all the columns from each dataset are concatenated when you use [!INCLUDE[M_AddColumns](Token\M_AddColumns.md)]. If you want to add only a subset of the columns, use [!INCLUDE[M_ProjectColumns](Token\M_ProjectColumns.md)] to create a dataset with the columns you want.
* If there are two columns with the same name in the input datasets, a numeric suffix is added to the name of the column from the dataset used in the right-hand input. For example, if there are two instances of a column named **TargetOutcome**, the second column would be renamed **TargetOutcome (1)**
>[!NOTE] If you want to combine two datasets that contain a different number of rows, use [!INCLUDE[M_AddColumns](Token\M_AddColumns.md)]. If you want to add only a subset of the columns, use [!INCLUDE[M_Join](Token\M_Join.md)], which supports outer joins on a common key column.

Examples 

Concatenation of datasets is useful in many scenarios:

* You want to combine a column containing labels with a feature dataset. (See the [CRM](http://azure.microsoft.com/en-us/documentation/services/machine-learning/models/) example.)
* You have multiple results sets and want to concatenate them into one table. (See the [Sentiment Analysis](http://azure.microsoft.com/en-us/documentation/services/machine-learning/models/) example.)

Expected Inputs
---------------

<table>
<thead>
<tr>
<td>Name</td>
<td>Type</td>
<td>Description</td>
</tr>
</thread>
<tbody>
<tr>
<td>Left dataset</td>
<td>[!INCLUDE[T_DataTable](Token\T_DataTable.md)]</td>
<td>Left dataset</td>
</tr>
<tr>
<td>Right dataset</td>
<td>[!INCLUDE[T_DataTable](Token\T_DataTable.md)]</td>
<td>Right dataset</td>
</tr>
</tbody>
</table>

Outputs
-------

<table>
<thead>
<tr>
<td>Name</td>
<td>Type</td>
<td>Description</td>
</tr>
</thread>
<tbody>
<tr>
<td>Combined dataset</td>
<td>[!INCLUDE[T_DataTable](Token\T_DataTable.md)]</td>
<td>Combined dataset</td>
</tr>
</tbody>
</table>

Exceptions
----------

<table>
<thead>
<tr>
<td>Exception</td>
<td>Description</td>
</tr>
</thread>
<tbody>
<tr>
<td>[!INCLUDE[E_NullOrEmpty](Token\E_NullOrEmpty.md)]</td>
<td>Exception occurs if one or more of inputs are null or empty.</td>
</tr>
<tr>
<td>[!INCLUDE[E_InvalidColumnType](Token\E_InvalidColumnType.md)]</td>
<td>Exception occurs if one or more specified columns have type unsupported by current module.</td>
</tr>
</tbody>
</table>