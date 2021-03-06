---
layout: page
title: "Q156902: STL Sample for deque::operator&#91;&#93; and deque::at Functions"
permalink: /kb/156/Q156902/
---

## Q156902: STL Sample for deque::operator&#91;&#93; and deque::at Functions

{% raw %}

	Article: Q156902
	Product(s): Microsoft C Compiler
	Version(s): 4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbVC420 kbVC500 kbVC600 kbDSupport
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ NET (2002) supported both the managed code model that is provided by the .NET Framework and the unmanaged native Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	The sample code below illustrates how to use the deque::operator[], deque::at,
	deque::empty, deque::push_back, and deque::end, STL functions in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     < deque>
	
	Prototype
	---------
	
	     const_reference operator[](size_type pos) const;
	     reference operator[](size_type pos);
	     const_reference operator[](difference_type _N) const;
	     reference operator[](difference_type _N) const;
	
	     const_reference at(size_type pos) const;
	     reference at(size_type pos);
	
	     bool empty() const;
	
	NOTE: The class/parameter names in the prototype may not match the version in the
	header file. Some have been modified to improve readability.
	
	Description
	-----------
	
	The member function operator[] returns a reference to the element of the
	controlled sequence at position pos. If that position is invalid, the behavior
	is undefined.
	
	The member function at returns a reference to the element of the controlled
	sequence at position pos. If that position is invalid, the function throws an
	object of class out_of_range.
	
	The member function empty returns true for an empty controlled sequence.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: -GX
	  // 
	  // deque.cpp :
	  // 
	  // Functions:
	  // 
	  //    operator[]
	  //    at
	  //    empty
	  //    push_back
	  //    begin
	  //    end
	  // 
	  // Written by Bobby Mattappally
	  // of Microsoft Product Support Services,
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  /* Compile options needed:-GX
	  */ 
	  #include <iostream>
	  #include <deque>
	
	  #if _MSC_VER > 1020   // if VC++ version is > 4.2
	     using namespace std;  // std c++ libs implemented in std
	     #endif
	
	  typedef deque<char, allocator<char> >  CHARDEQUE;
	
	  void print_contents (CHARDEQUE  deque, char*);
	
	  void main()
	
	  {
	
	      //create an empty deque a
	      CHARDEQUE  a;
	
	      //check whether it is empty
	      if(a.empty())
	          cout<<"a is empty"<<endl;
	      else
	          cout<<"a is not empty"<<endl;
	
	      //inset A, B, C and D  to a
	      a.push_back('A');
	      a.push_back('B');
	      a.push_back('C');
	      a.push_back('D');
	
	      //check again whether a is empty
	      if(a.empty())
	          cout<<"a is empty"<<endl;
	      else
	          cout<<"a is not empty"<<endl;
	
	      //print out the contents
	
	      print_contents (a,"a");
	
	      cout <<"The first element of a is  " <<a[0] <<endl;
	      cout <<"The first element of a is  " <<a.at(0) <<endl;
	
	      cout <<"The last element of a is  " <<a[a.size()-1] <<endl;
	      cout <<"The last element of a is  " <<a.at(a.size()-1) <<endl;
	
	  }
	
	  //function to print the contents of deque
	  void print_contents (CHARDEQUE  deque, char *name)
	
	  {
	
	      CHARDEQUE::iterator pdeque;
	
	      cout <<"The contents of "<< name <<" : ";
	
	      for(pdeque = deque.begin();
	          pdeque != deque.end();
	          pdeque++)
	          {
	              cout << *pdeque <<" " ;
	          }
	      cout<<endl;
	
	  }
	
	Program Output is:
	
	a is empty
	a is not empty
	The contents of a : A B C D
	The first element of a is  A
	The first element of a is  A
	The last element of a is  D
	The last element of a is  D
	
	REFERENCES
	==========
	
	Visual C++ Books On Line: Visual C++ Books:C/C++:Standard C++ Library Reference.
	
	Additional query words: STL STLSample deque operator[] at empty push_back begin end kbSTL kbTemplate
	
	======================================================================
	Keywords          : kbcode kbVC420 kbVC500 kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC500 kbVC600 kbVC32bitSearch kbVCNET kbVC500Search
	Version           : :4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
