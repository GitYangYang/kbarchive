---
layout: page
title: "Q238116: PRB: Accessing Temporary SQL Server Table Result: DB_E_NOTABLE"
permalink: /kb/238/Q238116/
---

## Q238116: PRB: Accessing Temporary SQL Server Table Result: DB_E_NOTABLE

{% raw %}

	Article: Q238116
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 1.5,2.0,2.1,2.5,2.6,3.0,3.5,3.6,3.7
	Operating System(s): 
	Keyword(s): kbDatabase kbMDAC kbODBC kbSQLServ kbODBC300 kbODBC350 kbODBC360 kbGrpDSVCDB kbGrpDSMDA
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC Driver for SQL Server, versions 2000.80.194, 3.0, 3.5, 3.6, 3.7, included with:
	   - Microsoft Data Access Components versions 1.5, 2.0, 2.1, 2.5, 2.6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using the SQL Server ODBC driver with forward-only server-side cursors in
	trying to access a local temporary SQL Server table that was explicitly created
	using the same ActiveX Data Object (ADO) connection object, the application
	receives the following error message:
	
	  [Microsoft][ODBC SQL Server Driver][SQL Server]Invalid object name
	  '#temptable12'.
	
	The HRESULT obtained is:
	
	     DB_E_NOTABLE // 0x80040e37
	
	CAUSE
	=====
	
	The SQL Server ODBC driver does not support multiple active recordsets on the
	same connection when using the forward-only cursor. The OLE DB Provider for ODBC
	drivers attempts to work around this limitation by creating a second connection.
	Since temporary tables are only visible to the connection that created it, the
	application fails to find the table and returns a DB_E_NOTABLE HRESULT.
	
	RESOLUTION
	==========
	
	Use one of the following solutions to correct the problem:
	
	- Use ADO client-side cursors.
	
	- Use the Microsoft OLE DB Provider for SQL Server.
	
	- Insert a rs.Release() call in between two execute calls in the Visual C++
	  code, when using forward-only server-side cursors.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce this Error
	-----------------------------
	
	1. Create an empty WinConsole application.
	
	2. Insert the sample code below into a Visual C++ source code file.
	
	3. Set the appropriate values of Server, User ID, and Password to access the
	  default Pubs database on a SQL 7.0 Server.
	
	4. Compile and run the application.
	
	5. Uncomment either of the following lines:
	
	  // conn->CursorLocation = adUseClient;
	  //rs.Release();
	
	Visual C++ 6.0 Sample Code
	--------------------------
	
	  // Start of TempTbl.cpp
	  //  Database Type : SQL Server 7
	  //  Server: "ServerName" UID: "sa" PWD:""
	  //  This code checks lifetimes of temporary tables in SQL 7.0
	  //  Database : pubs
	  //  TableName: #temptable12
	  // The includes
	  #include <stdio.h>		// Needed for printf.
	  #include <tchar.h>		// Needed for _T() macro.
	  #include <conio.h>		// Needed for _getch().
	  #include <afxdisp.h>  // CString etc...
	  // The #import
	  #undef EOF
	  #import "C:\Program Files\Common Files\System\ADO\msado15.dll" rename_namespace("ado20")
	  #define CATCHCOM(hr)  if ( FAILED( hr ) ) throw( _com_error( hr, NULL ) );
	  // The BSTR's
	  _bstr_t connStrSQL("Driver=SQL Server;Server=ServerName;Database=pubs;UID=sa;PWD=;");
	  // The Coinitialize
	  struct HandleCOM
	  {
	     HandleCOM()  { ::CoInitialize(NULL); }
	     ~HandleCOM() { ::CoUninitialize();   }
	  } _HandleCOM_;
	
	  int main(void)
	  {
	     using namespace ado20;
	     _ConnectionPtr conn;
	     _RecordsetPtr rs;
	     _variant_t vra;
	     HRESULT hr;
	     try
	     {
	  	conn.CreateInstance(__uuidof(Connection));
	  	hr = conn->Open(connStrSQL,L"",L"",-1);
	  	//conn->CursorLocation = adUseClient;
	  	CATCHCOM(hr)
	  	rs =conn->Execute(_bstr_t("Select * into #temptable12 from authors"),&vra,-1);
	  	//rs.Release();
	  	rs = conn->Execute(_bstr_t("Select * from #temptable12"),&vra,-1);
	     }
	     catch (_com_error &ce)
	     {
	  	CString adoStr,msgStr,tempStr;
	  	// 
	  	// Trace COM error information.
	  	// 
	  	adoStr=_T("");
	  	TRACE( "\nCom Exception Information\n-----------------------------------------------\n" );
	  	TRACE( "Description : %s\n",   (char*) ce.Description()  );
	  	TRACE( "Message     : %s\n",   (char*) ce.ErrorMessage() );
	  	TRACE( "HResult     : 0x%08x\n", ce.Error() );
	  	// 
	  	// Trace ADO exception information only if connection is not null.
	  	// 
	  	if ( NULL != conn )
	  	{
	  	   TRACE( "\nADO Exception Information\n-----------------------------------------------\n" );
	   	   ado20::ErrorPtr err;
	  	   for ( long i=0; i<conn->Errors->Count; i++ ) 
	  	   {
	  		tempStr=_T("");
	  		err = conn->Errors->Item[i];
	  		TRACE( "Number      : 0x%08x\n", err->Number );
	  		TRACE( "Description : %s\n",	  (char*) err->Description );
	  		TRACE( "SQLState    : %s\n",     (char*) err->SQLState );
	  		TRACE( "Source      : %s\n\n",   (char*) err->Source );
	  		tempStr.Format("Ado Exception :\n===============\nDescription : %s\nSource : %s\n",(char*) err->Description,(char*) err->Source);  
	  		adoStr += tempStr;
	  	   } 
	  	}
	  	msgStr.Format("Com Exception :\n===============\nDescription : %s\nMessage     : %s\n%s",(char*) ce.Description(),(char*) ce.ErrorMessage(), (LPCTSTR) adoStr);  
	  	MessageBox(::GetDesktopWindow(),msgStr,"Error Message", MB_OK);
	     }
	     return 0;
	  }
	  // End of TempTbl.cpp
	
	REFERENCES
	==========
	
	SQL Server Books Online
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbMDAC kbODBC kbSQLServ kbODBC300 kbODBC350 kbODBC360 kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC210 kbMDAC210SP2 kbMDAC250 kbODBC370 kbMDAC260 kbmdac270 kbado270 
	Technology        : kbSQLServSearch kbAudDeveloper kbODBCSearch
	Version           : :1.5,2.0,2.1,2.5,2.6,3.0,3.5,3.6,3.7
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
