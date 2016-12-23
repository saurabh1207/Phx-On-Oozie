# Phx-On-Oozie
Example Oozie action to run Apache Phoenix commands in Hadoop.

Currently Oozie does not provide in-built action to run queries in Apache Phoenix as it does for Hive.
Apache Phoenix can be accessed using JDBC drivers and SQLLine.
E.g.:  /usr/hdp/current/phoenix-client/bin/sqlline.py <zoo-keeper-address>:2181:/hbase-unsecure

We can use JDBC drivers of Phoenix to execute JAVA action in Oozie and access Phoenix through Oozie workflow.
Only external jar required to run JAVA action is : <b>phoenix-client.jar</b>
You can get the jar from the bin folder of phoenix installation.

In above workflow.xml, you can see that class sqlline.SqlLine is used in JAVA action.
3 important arguments are passed to this class:
<br/>1) -d org.apache.phoenix.jdbc.PhoenixDriver (This is the class name)
<br/>2) -u jdbc:phoenix:localhost:/hbase-unsecure (This is the URL to Habse zoo-keeper)
<br/>3) --run=oozie.sql (This is SQL file with all commands which you want to run in Phoenix)

Also you can see that phoenix-client.jar path is also provided under archive tag. This is jar with all the required classes.
