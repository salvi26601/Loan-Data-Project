The original dataset of 10000 x 14 with an initial header containing ['id', 'issue_d', 'loan_amnt', 'loan_status', 'funded_amnt', 'term', 'int_rate', 'installment', 'grade', 'sub_grade', 'verification_status', 'url', 'addr_state', 'total_pymnt']
was preprocessed and cleaned in such a way that is suitable to gain insights using Machine Learning models or to implement visual representations.

The preprocessed data of 10000 x 17 contains a header of ['id', 'loan_amnt_USD', 'loan_amnt_EUR', 'funded_amnt_USD', 'funded_amnt_EUR', 'int_rate', 'installment_USD', 'installment_EUR', 'total_pymnt_USD', 'total_pymnt_EUR', 'exchange_rate', 'Issue_Date', 'loan_status', 'Term_months', 'sub_grade', 'verification_status', 'State_Address']

The changes made in the data:
* Firstly, the empty values are filled by the temporary mean of the respective numeric columns
* Empty values in string columns are filled by the worst values(CRM model).
* 'issue_d' - the month values in the issue date are represented by the respective month integers
* 'loan_amnt', 'funded_amnt', 'installment', 'total_pymnt' - Their values originally are in USD and they are converted to EUR by the exchange rates
* 'loan_status' - From the 9 unique values, according to regression model they are categorized as good financial condition(1) or bad financial condition(0)
* 'term' -  The empty values are filled by the worst value, i.e., the maximum term months
* 'int_rate' - The values are converted to percent values between 0 and 1
* 'grade' - This field is removed because sub_grade field values reveals the grade values
* 'sub_grade' - The empty values are substituted by the worst values of the respective grade and then the sub grades are converted to integers
* 'verification_status' - The 4 unique values are classified as good(1) or bad(0)
* 'url' - From the lengthy url, the common part is removed and only the last unique numbers are kept. The numbers are found to be same as the id so the url column is removed.
* 'addr_state' - All the unique state codes are classifed as west, south, midwest and east regions and are represented by integers

Thus, the changes are stored in a new file named loan-data-preprocessed ready to take meaningful insights from.
