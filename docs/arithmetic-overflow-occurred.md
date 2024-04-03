---
sidebar_label: 'Arithmetic Overflow Occurred'
hide_title: 'true'
---

## Arithmetic Overflow Occurred

When SAM attempts to process job starts and receives an arithmetic overflow

The following stack trace appears within the logs:

```

11/25/2022 08:22:41.762 Error in ExecuteNonQuery. Error: 8115: System.Data.SqlClient.SqlException (0x80131904): Arithmetic overflow error converting IDENTITY to data type int.
Arithmetic overflow occurred.
at System.Data.SqlClient.SqlConnection.OnError(SqlException exception, Boolean breakConnection, Action`1 wrapCloseInAction)
at System.Data.SqlClient.TdsParser.ThrowExceptionAndWarning(TdsParserStateObject stateObj, Boolean callerHasConnectionLock, Boolean asyncClose)
at System.Data.SqlClient.TdsParser.TryRun(RunBehavior runBehavior, SqlCommand cmdHandler, SqlDataReader dataStream, BulkCopySimpleResultSet bulkCopyHandler, TdsParserStateObject stateObj, Boolean& dataReady)
at System.Data.SqlClient.SqlCommand.RunExecuteNonQueryTds(String methodName, Boolean async, Int32 timeout, Boolean asyncWrite)
at System.Data.SqlClient.SqlCommand.InternalExecuteNonQuery(TaskCompletionSource`1 completion, Boolean sendToPipe, Int32 timeout, Boolean asyncWrite, String methodName)
at System.Data.SqlClient.SqlCommand.ExecuteNonQuery()
at SMASAM.DatabaseHelper.ExecuteNonQuery(String SQL, ISmaConnection conn)
ClientConnectionId:e2161aaf-33ce-4e32-a722-9f7ac3f4641c
Error Number:8115,State:1,Class:16
SQL = INSERT INTO SMASTER VALUES (44890, 90, 9, 1, 'SDAGGFTAGE_ESTR9920221125SDAGIX.L10', 'All-Days', 0, 1, 1, 0, 0, 34, 0, 0, 0, 0, 0, 0, 'A', 0, 'A', 90, 0, 0, 0, 0, ' ', 0, 1, 'SDAGGFTAGE', 'SDAGGFTAGE')
11/25/2022 08:22:41.762 Activating Reconnection Process...
11/25/2022 08:22:41.980 Connection has been restored...

```

This type of error occurs when the identity column of a table reaches the value of 2,147,483,647 (the size limit of that data type). This identity field is an internally tracked data value on the table and unrelated to the primary key, which is what the SQL database and the Opcon software uses to find a specific database entity. So reseeding a table back to a value of 1 will not affect database integrity or the software's ability to track down or locate information.

To start, run the following SQL query to determine the current seed of each table related to SMASTER.

```

DBCC CHECKIDENT ('AUDITRECS',RESEED);
DBCC CHECKIDENT ('AUDITRECSVIEW',RESEED);
DBCC CHECKIDENT ('ENSACTIONS',RESEED);
DBCC CHECKIDENT ('ENSGROUPS',RESEED);
DBCC CHECKIDENT ('ENSTRIGINFO',RESEED);
DBCC CHECKIDENT ('EscalationGroup',RESEED);
DBCC CHECKIDENT ('EscalationRecipient',RESEED);
DBCC CHECKIDENT ('EscalationRule',RESEED);
DBCC CHECKIDENT ('EscalationSequence',RESEED);
DBCC CHECKIDENT ('Escalation',RESEED);
DBCC CHECKIDENT ('FEEDBACKEVENTS',RESEED);
DBCC CHECKIDENT ('INSTANTMESSAGES',RESEED);
DBCC CHECKIDENT ('JEVENTS',RESEED);
DBCC CHECKIDENT ('MSGS_TO_NETCOM',RESEED);
DBCC CHECKIDENT ('MSGS_TO_SAM',RESEED);
DBCC CHECKIDENT ('NOTIFY',RESEED);
DBCC CHECKIDENT ('OPCONREQ',RESEED);
DBCC CHECKIDENT ('RPTPARAMS',RESEED);
DBCC CHECKIDENT ('Runner',RESEED);
DBCC CHECKIDENT ('Script',RESEED);
DBCC CHECKIDENT ('ScriptType',RESEED);
DBCC CHECKIDENT ('ScriptVersion',RESEED);
DBCC CHECKIDENT ('SERVICE_REQUEST',RESEED);
DBCC CHECKIDENT ('SERVICE_REQUEST_CATEGORY',RESEED);
DBCC CHECKIDENT ('ServiceRequestExecutions',RESEED);
DBCC CHECKIDENT ('SEVENTS',RESEED);
DBCC CHECKIDENT ('XMLFREQDATA',RESEED);

```