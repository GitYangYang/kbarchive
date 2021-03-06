---
layout: page
title: "Q200591: PRB: 8570 Report Sections Do Not Match DataSource"
permalink: /kb/200/Q200591/
---

## Q200591: PRB: 8570 Report Sections Do Not Match DataSource

{% raw %}

	Article: Q200591
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0,2.1,2.5,2.6,6.0
	Operating System(s): 
	Keyword(s): kbADO200 kbDatabase kbDataBinding kbReportWriter kbVBp600 kbDataEnv kbGrpDSVBDB kbGrpDS
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Data Access Components versions 2.0, 2.1, 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use a Report Control that is bound to a Visual Basic Data Environment
	command object and perform a GroupBy, you receive the following error:
	
	  8570 Report sections do not match data source
	
	CAUSE
	=====
	
	One of the following has occurred:
	
	- The DataReport is bound to an ungrouped recordset.
	
	- The DataReport was created before binding the recordset.
	
	RESOLUTION
	==========
	
	The ADO Command object that the report is based on needs to be modified for
	grouping. Below is an example using Visual Basic 6.0's Data Environment and
	grouping in a report. Note that the command is doing the grouping, NOT the
	DataReport.
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Add a reference to Microsoft ActiveX Data Objects 2.x Library.
	
	3. Add a DataEnvironment.
	
	4. Configure the Connection1 properties to use OLE DB Provider for SQL Server
	  (SQLOLEDB) and the Northwind database (Nwind.mdb).
	
	5. Add a Command object off of Connection1.
	
	6. Configure the Command1 properties to use the Orders table and group by
	  OrderDate (under the Grouping tab).
	
	7. Add a DataReport to your project.
	
	8. Set the DataSource to DataEnvironment1.
	
	9. Set the DataMember to Command1_Grouping.
	
	10. Right-click on DataReport1 and choose Retrieve Structure.
	
	11. From the Summary Fields in Command1_Grouping, click and drag the OrderDate
	  field into the DataReport1 Group Header.
	
	12. Click and drag detail fields from the Detail Fields in Command1 into the
	  DataReport1 Detail section.
	
	13. Add a CommandButton to Form1.
	
	14. Add the following code to Form1:
	
	  Private Sub Command1_Click()
	      DataReport1.Show 1
	      Unload DataReport1
	  End Sub
	
	15. Run the project and click Command1.
	
	It is important that the report sections match the command object's structure. If
	the error continues to occur, try using the Retrieve Structure command on the
	DataReport to refresh the sections. Retrieve Structure will remove all fields
	that are currently in the DataReport.
	
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The example above assumes that you have a good understanding of how the
	DataEnvironment, DataReport, and ADO work.
	
	The key to fixing this problem is to make sure that the data sections match the
	DataSource exactly. The most reliable way to do this is to use the Retrieve
	Structure command on the DataReport.
	
	REFERENCES
	==========
	
	For more information on ADO, please refer to your Visual Basic documentation or
	visit:
	
	http://www.microsoft.com/data/.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbADO200 kbDatabase kbDataBinding kbReportWriter kbVBp600 kbDataEnv kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbADO250 kbMDAC260 kbADO260 kbmdac270 kbado270 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbMDACSearch kbMDAC200 kbMDAC210 kbMDAC250 kbMDAC260 kbMDAC270
	Version           : :2.0,2.1,2.5,2.6,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
