---
layout: post
title: Reading XML Fragments into ADO.NET DataSets
date: 2008-02-01 18:49
author: John
comments: true
categories: [All]
---
The DataSet.DataSetName is a cool property that is easily overlooked. Here is an example of where it comes in handy. <BR><BR>Let's say you want to load an XML fragment into a DataSet that was retrieved via SQL Server's FOR XML clause. You might try doing the following: <BR><BR> <FIELDSET><SPAN class="myCode">XmlReader oMyXmlReader = oCmd.ExecuteXmlReader(); <BR>oDs.ReadXml(oMyXmlReader, XmlReadMode.Fragment); </span></FIELDSET> <BR><BR>The problem with this code is that when you read the XML fragment the ReadXml method tries to match it against a schema. If it does not find a schema, then it ignores the XML. Your end result might be an empty XML document. One way to solve this is to add a schema to the DataSet. Here is one solution: <BR><BR> <FIELDSET><SPAN class="myCode">XmlReader oMyXmlReader = oCmd.ExecuteXmlReader(); <BR>oDs.ReadXmlSchema(oMyXmlReader ); <BR>oDs.ReadXml(oMyXmlReader , XmlReadMode.Fragment); <BR>oDs.DataSetName = "myRoot"; </span></FIELDSET> <BR><BR>Now the schema exists (it was inferred) and all of the fragments can be loaded. If I want to write the XML out to a stream, file or string I might want to wrap the XML fragment inside of a parent node (like "myRoot") so the XML is a well formatted XML document. To do this, you can use the oft overlooked property DataSetName. <BR>

