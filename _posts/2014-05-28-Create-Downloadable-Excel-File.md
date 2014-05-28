---
layout: post
title: Create Downloadable Excel file on MVC4
description: "Create Downloadable Excel file on MVC4"
tags: [ code, MVC4]
comments: true
---

Recently I had to create a downloadable excel file on the MVC4 website I was working on. Most tutorials gave partial pictures of what I had which frustrated me but adding the pieces together I was able to come up with a solution.

## Step 1 Create a Web Role MVC4 project using visual Studio
Below are the pictures showing you how to do that
<figure>
	<a href="http://lynnug.github.io/images/excel1.png"><img src="http://lynnug.github.io/images/excel1.png"></a>
	<figcaption><a href="http://lynnug.github.io/images/excel1.png
" title="Click create new project">Create new project</a>.</figcaption>
</figure>
Under Visual C sharp project , you'll see Cloud select, type appropriate project name and click ok. Make sure the .NET Framework selected is 4.
<figure>
	<a href="http://lynnug.github.io/images/excel2.png"><img src="http://lynnug.github.io/images/excel2.png"></a>
	<figcaption><a href="http://lynnug.github.io/images/excel2.png
" title="Add a web role">Add a web role</a>.</figcaption>
</figure>
Select the ASP.NET MVC4 Web Role
<figure>
	<a href="http://lynnug.github.io/images/excel3.png"><img src="http://lynnug.github.io/images/excel3.png"></a>
	<figcaption><a href="http://lynnug.github.io/images/excel3.png
" title="Created Web Role MVC4 Project">Created Web Role MVC4 Project</a>.</figcaption>
</figure>
Caption showing created project
<figure>
	<a href="http://lynnug.github.io/images/excel4.png"><img src="http://lynnug.github.io/images/excel4.png"></a>
	<figcaption><a href="http://lynnug.github.io/images/excel4.png
" title="Configure settings to connect to cloud storage">Configure settings to connect to cloud storage</a>.</figcaption>
</figure>
Open the cloud service in the soultion explorer, under it go to Role , then on the role created right click and go to properties. The section to go to is highlighted in the picture. Once there go to settings and add under settings add a new settings field with name "StorageConnectionString", type Connection String , for value click on the icon next to it and select the appropriate storage location. If you have an azure account enter details , else set up windows emulator storage.
<figure>
	<a href="http://lynnug.github.io/images/excel5.png"><img src="http://lynnug.github.io/images/excel5.png"></a>
	<figcaption><a href="http://lynnug.github.io/images/excel5.png
" title="Add a web role">Configure local storage</a>.</figcaption>
</figure>
Go to local storage and and create a new storage

## Step 2 create an excel file

I obtained code that was very helpful in creating an excel file , only work i did was to convert my list to a data set and pass it on to the method. Here's the link to that very helpful snippet of code. [link](http://mikesknowledgebase.azurewebsites.net/pages/CSharp/ExportToExcel.htm)

{% highlight csharp linenos %}
           Type elementType = typeof(T);
            DataSet ds = new DataSet();
            DataTable t = new DataTable();
            ds.Tables.Add(t);

            //add a column to table for each public property on T
            foreach (var propInfo in elementType.GetProperties())
            {
                t.Columns.Add(propInfo.Name, Nullable.GetUnderlyingType(propInfo.PropertyType)?? propInfo.PropertyType);
            }

            //go through each property on T and add each value to the table
            foreach (T item in list)
            {
                System.Diagnostics.Debug.WriteLine(item);

                DataRow row = t.NewRow();
                foreach (var propInfo in elementType.GetProperties())
                {
                    System.Diagnostics.Debug.WriteLine(propInfo.GetValue(item, null));
                    row[propInfo.Name] = propInfo.GetValue(item, null);

                }
                t.Rows.Add(row);
            }

{% endhighlight %}

