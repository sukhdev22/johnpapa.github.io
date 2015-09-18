---
layout: post
title: Find a Column, Find a Table in SQL Server
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
<P>OK, so this isn’t rocket science, but then again some of the best things are the simplest. You can do a lot with the information_schema views in SQL Server. </P> <P>Here is a short stored procedure that you can use to find:</P> <UL> <LI>a table by its full name <LI>a table by partial name <LI>a column by its full name <LI>a column by its partial name</LI></UL> <P>&nbsp;It comes in handy for me when I am looking for a field in related tables, or a spec I am reading refers to a field by name but not by the table it is in. Like I said, it is simple, but I have used this type of a proc for a long time. </P> <FIELDSET><LEGEND>Table or Column Finder</LEGEND><PRE><SPAN style="FONT-SIZE: 9pt; COLOR: black; FONT-FAMILY: Arial"> <SPAN style="COLOR: blue">CREATE PROCEDURE</SPAN> prFindTableOrColumn ( @table_name <SPAN style="COLOR: blue">VARCHAR</SPAN>(128) = <SPAN style="COLOR: gray">NULL</SPAN>, @search_data <SPAN style="COLOR: blue">VARCHAR</SPAN>(128) = <SPAN style="COLOR: gray">NULL</SPAN> ) <SPAN style="COLOR: blue">AS</SPAN> <SPAN style="COLOR: blue">DECLARE</SPAN> @search1 <SPAN style="COLOR: blue">VARCHAR</SPAN>(128) <SPAN style="COLOR: blue">SET</SPAN> @search1 = <SPAN style="COLOR: red">'%'</SPAN> + @table_name + <SPAN style="COLOR: red">'%'</SPAN> <SPAN style="COLOR: blue">IF</SPAN> @search1 <SPAN style="COLOR: blue">IS</SPAN> <SPAN style="COLOR: gray">NULL</SPAN> <SPAN style="COLOR: blue">SET</SPAN> @search1 = <SPAN style="COLOR: red">'%'</SPAN> <SPAN style="COLOR: blue">DECLARE</SPAN> @search2 <SPAN style="COLOR: blue">VARCHAR</SPAN>(128) <SPAN style="COLOR: blue">SET</SPAN> @search2 = <SPAN style="COLOR: red">'%'</SPAN> + @search_data + <SPAN style="COLOR: red">'%'</SPAN> <SPAN style="COLOR: blue">IF</SPAN> @search2 <SPAN style="COLOR: blue">IS</SPAN> <SPAN style="COLOR: gray">NULL</SPAN> <SPAN style="COLOR: blue">SET</SPAN> @search2 = <SPAN style="COLOR: red">'%'</SPAN> <SPAN style="COLOR: blue">SELECT</SPAN> c.table_name, c.column_name, c.data_type, c.character_maximum_length, c.numeric_precision, c.numeric_scale <SPAN style="COLOR: blue">FROM</SPAN> information_schema.columns c <SPAN style="COLOR: blue">INNER</SPAN> <SPAN style="COLOR: gray">JOIN</SPAN> information_schema.tables t <SPAN style="COLOR: blue"> ON</SPAN> c.table_name = t.table_name <SPAN style="COLOR: blue">WHERE</SPAN> c.table_name <SPAN style="COLOR: gray">LIKE</SPAN> @search1 <SPAN style="COLOR: gray">AND</SPAN> c.column_name <SPAN style="COLOR: gray">LIKE</SPAN> @search2 <SPAN style="COLOR: gray">AND</SPAN> t.table_type = <SPAN style="COLOR: red">'BASE TABLE'</SPAN> <SPAN style="COLOR: blue">ORDER BY</SPAN> c.table_name, c.column_name </SPAN></PRE></FIELDSET> <BR></SPAN>
