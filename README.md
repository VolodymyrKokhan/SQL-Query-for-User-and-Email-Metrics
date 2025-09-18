# **SQL Query for User and Email Metrics**
Writing an SQL query to gather data that will help analyze the dynamics of account creation, user activity from emails (sends, opens, clicks), and evaluate behavior within categories such as sending intervals, account verification, and subscription status

![Country and Email metrics](SQL-Query-for-User-and-Email-Metrics/Visualisation.PNG)



Visualisation at Looker Studio https://lookerstudio.google.com/u/0/reporting/0d4fc7a8-0754-438d-9f44-71f2ca7f7429/page/12TSF

The result of the query should contain a specific list of grouping fields—that is, categorical values (with which no calculations are performed). The main account metrics, as well as the main email metrics, should be calculated across the following dimensions:

* `date` - date (for accounts - the date the account was created; for emails - the email's sent date);
* `country` - country;
* `send_interval` - the sending interval set by the account;
* `is_verified` - whether the account is verified or not;
* `is_unsubscribed` - whether the subscriber has unsubscribed or not.

These dimensions apply to both account and email metrics. The necessary information is in the **account** table.

Query should calculate the following main metrics (across the listed dimensions):

* `account_cnt` - the number of created accounts;
* `sent_msg` - the number of emails sent;
* `open_msg` - the number of emails opened;
* `visit_msg` - the number of clicks from emails;

As well as the following additional metrics (calculated based on the main metrics):

* `total_country_account_cnt` - the total number of created subscribers across the country;
* `total_country_sent_cnt` - the total number of emails sent across the country;
* `rank_total_country_account_cnt` - the country's ranking by the total number of created subscribers;
* `rank_total_country_sent_cnt` - the country's ranking by the total number of emails sent.

Account and email metrics should be calculated separately to maintain unique dimensions for each and avoid conflicts due to the different logic of using the `date` field. Use **UNION** to combine the results. In the end, keep only those records where `rank_total_country_account_cnt` or `rank_total_country_sent_cnt` is less than or equal to 10.

**Dataset Structure**

The query should output the following columns:

* `date` - date;
* `country` - country;
* `send_interval` - sending interval;
* `is_verified` - whether the account is verified;
* `is_unsubscribed` - whether the subscriber has unsubscribed;
* `account_cnt` - number of created accounts;
* `sent_msg` - number of emails sent;
* `open_msg` - number of opened emails;
* `visit_msg` - number of clicks from emails;
* `total_country_account_cnt` - total number of created subscribers per country;
* `total_country_sent_cnt` - total number of emails sent per country;
* `rank_total_country_account_cnt` - country ranking by the number of created subscribers;
* `rank_total_country_sent_cnt` - country ranking by the number of emails sent.
