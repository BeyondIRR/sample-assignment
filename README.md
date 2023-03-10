# BeyondIRR Task

Create a Django Application that manages the expenses of a family. Let's consider a family of 6 people, namely, a Father, a Mother, two children (Child1, Child2), set of grandparents (Grandfather and Grandmother). Goal of this tracker is to enable this family for the financial year of 2023-24 to save an `goal-amount` of their choice. This choice will vary for different families. 

### General Details

- Earning members of this family are considered to be the parents and the grandparents at the time of building the application (there may be more in the future).
- Sources of income for the earning members of the family maybe dynamic, i.e. there can be multiple sources of income to be considered for each individual earning member.
- Each individual member of the family bound by certain attributes:
    - Income they generate per month
    - Amount they will contribute in the `family-fund-expense-pool`
    - Personal Expense amount threshold 

Note: Each individual member is allowed to have a personal expense amount that they can spend without submitting as an expense in our tracker. For example, if the Father has spent Rs. 50 out his Personal Expense amount threshold of Rs. 20,000 then he may or may not add it as an expense in this tracker. The family member will however provide the overall amount spent out of his personal expense at the end of the month.

### Task Details
- Father has:
    - Income of Rs. 1,20,000 per month
    - Amount he will contribute to `family-fund-expense-pool` is 70% of his income
    - Personal Expense amount threshold is Rs. 20,000 per month
- Mother has:
    - Income of Rs. 1,50,000 per month
    - Amount she will contribute to `family-fund-expense-pool` is 70% of her income
    - Personal Expense amount threshold is Rs. 15,000 per month
- Granfather has:
    - Income of Rs. 40,000 per month
    - Amount he will contribute to `family-fund-expense-pool` is 15% of his income
    - Personal Expense amount threshold is Rs. 8,000 per month
- Granmother has:
    - Income of Rs. 20,000 per month
    - Amount she will contribute to `family-fund-expense-pool` is 10% of her income
    - Personal Expense amount threshold is Rs. 5,000 per month
- Child1 has:
    - Income of Rs. 0 per month
    - Amount they will contribute to `family-fund-expense-pool` is 0% of her income
    - Personal Expense amount threshold is Rs. 2,000 per month
- Child2 has:
    - Income of Rs. 0 per month
    - Amount they will contribute to `family-fund-expense-pool` is 0% of her income
    - Personal Expense amount threshold is Rs. 2,000 per month

### Explanation
Since the Father is earning Rs. 1,20,000 per month and he is contributing 70% of his income to the `family-fund-expense-pool` which amounts to be Rs. 84,000 the rest of his income Rs. 36,000 is then considered as `saved-money`. Similarly, the Mother is earning Rs. 1,50,000 per month and her share towards `family-fund-expense-pool` is Rs. 1,05,000 (70% of her income) she will save Rs. 1,50,000 - Rs. 1,05,000 which is Rs. 45,000 is then considered as `saved-money` just like every other family member respectively.

`family-fund-expense-pool` is used to spend on the total common spending of the family expenses (Rent, Electricity, you may add more). Personal Expenses are allocated from the `family-fund-expense-pool` like,
- Father is allocated Rs. 20,000 from `family-fund-expense-pool`
- Mother is allocated Rs. 15,000 from `family-fund-expense-pool`
- Granfather is allocated Rs. 8,000 from `family-fund-expense-pool`
- Granmother is allocated Rs. 5,000 from `family-fund-expense-pool`
- Child1 is allocated Rs. 2,000 from `family-fund-expense-pool`
- Child2 is allocated Rs. 2,000 from `family-fund-expense-pool`

The rest of the money is allocated to various expenditures that the family may incur during a month. The money after the expenditures is called `saved-money`, money leftover from the personal allocated amount is added to the `saved-money` attribute if they do not spend it fully.

## Application Specifications

### Project Details
- Create a project named `birr`
- Create three models:
    - `Accounts`: Store information about the family members.
    - `Expenses`: Store information about which family member from `Accounts` incurred an expense at which date.
    - `Billing`: Store extra information about the `Expenses` such as the bill of the expense.


## Design APIs
### GET Request
- **/api/accounts/** 
    - To attain all the objects accounts in the `Accounts` model
- **/api/accounts/{id}**
    - To attain single object accounts in the `Accounts` model
- **/api/expense/** 
    - To attain all the objects in the `Expense` model
- **/api/expense/{id}**
    - To attain single object in the `Expense` model
- **/api/billing/** 
    - To attain all the objects in the `Billing` model
- **/api/billing/{id}**
    - To attain single object in the `Billing` model

### POST Request
- **/api/accounts/** 
    - Add an object in the `Accounts` model with `json` payload
- **/api/expense/** 
    - Add an object in the `Expense` model with `json` payload
- **/api/billing/** 
    - Add an object in the `Billing` model with `json` payload

### PATCH Request
- **/api/accounts/** 
    - Update an object in the `Accounts` model with `json` payload where partial update is allowed
- **/api/expense/** 
    - Update an object in the `Expense` model with `json` payload where partial update is allowed
- **/api/billing/** 
    - Update an object in the `Billing` model with `json` payload where partial update is allowed


### DELETE Request
- **/api/accounts/** 
    - Delete an object in the `Accounts` model with `json` payload
- **/api/expense/** 
    - Delete an object in the `Expense` model with `json` payload
- **/api/billing/** 
    - Delete an object in the `Billing` model with `json` payload


### Additional APIs
- An API that shows the individual family member of how much more can they spend out of their personal allocated amount
- An API that checks if any family member as exceeded their personal allocated amount this month. 
- An API that shows how much more amount is needed to reach `goal-amount` in this financial year.

**NOTE:**
---------------
- Assign a superuser to any one of the accounts in the project
- Please document the code wherever possible
- Please use pep8 guidelines to complete this task

### Authors of this task
- [@shubdixit](https://github.com/shubdixit)
- [@sagar-birr](https://github.com/sagar-birr)
