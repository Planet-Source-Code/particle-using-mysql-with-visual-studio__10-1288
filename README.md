<div align="center">

## Using MySQL with Visual Studio


</div>

### Description

If you're just wondering how to use MySQL with VS.NET or are having problems, give this a try.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Particle](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/particle.md)
**Level**          |Intermediate
**User Rating**    |4.7 (160 globes from 34 users)
**Compatibility**  |VB\.NET
**Category**       |[Databases](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases__10-5.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/particle-using-mysql-with-visual-studio__10-1288/archive/master.zip)





### Source Code

<font color="#0099CC"><b>Introduction</b></font><br>
&nbsp;&nbsp;&nbsp;&nbsp; Hello, my name's Geoff (aka Particle) and if you're
              here you're probably wondering how to get MySQL to
              work with Visual Studio.NET.&nbsp; I had the same
              problem this morning and it took hours to find
              everything I needed.&nbsp; Therefore, I thought I'd
              make a guide to save other people time.&nbsp; If
              you're completely new to MySQL, please visit <b>
              www.pcrpg.org/TRPGguides/mysqloledotnet.php</b> for
              complete instructions on how to install and
              configure MySQL, useful tools such as phpMyAdmin,
              and everything needed to make phpMyAdmin work.&nbsp;
              What I am posting here is just the last portion of
              the guide dealing with VS.NET itself.&nbsp; I'll
              leave the &quot;What You'll Need&quot; table from the
              beginning of the guide in tact (except for the web
              components and installing MySQL, etc--for those
              please visit the link above).&nbsp; Some of the
              links have been broken into two lines.&nbsp; Sorry
              about the links--it appears that due to some
              immaturity, hyperlinks can no longer be used so I'll
              just bold them.<br>
&nbsp;<table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse" width="100%" id="AutoNumber1">
               <tr>
                <td width="31%">MyOLEDB Driver</td>
                <td width="69%">
                <b>
                http://www.mysql.com/downloads/download.php?file=Downloads/<br>
                Win32/MyOLEDB3.exe&amp;pick=mirror</b></td>
               </tr>
               <tr>
                <td width="31%">Microsoft Visual Studio .NET</td>
                <td width="69%">
                <b>http://msdn.microsoft.com/vstudio/ </b> </td>
               </tr>
               <tr>
                <td width="31%">&nbsp;</td>
                <td width="69%">&nbsp;</td>
               </tr>
               <tr>
                <td width="31%">Other Stuff That's <i>Nice</i>
                to Have:</td>
                <td width="69%">&nbsp;</td>
               </tr>
               <tr>
                <td width="31%">.NET Framework 1.1</td>
                <td width="69%">
                <b>
                http://www.microsoft.com/downloads/details.aspx?FamilyID=<br>
                262d25e3-f589-4842-8157-034d1e7cf3a3&amp;DisplayLang=en</b></td>
               </tr>
               <tr>
                <td width="31%">.NET Framework SDK 1.1</td>
                <td width="69%">
                <b>
                http://www.microsoft.com/downloads/details.aspx?FamilyId=<br>
                9B3A2CA6-3647-4070-9F41-A333C6B9181D&amp;displaylang=en</b></td>
               </tr>
               <tr>
                <td width="31%">MDAC v2.7</td>
                <td width="69%">
                <b>
                http://www.microsoft.com/downloads/details.aspx?FamilyID=<br>
                9ad000f2-cae7-493d-b0f3-ae36c570ade8&amp;DisplayLang=en</b></td>
               </tr>
               </table>
							<p>&nbsp;&nbsp;&nbsp;&nbsp; Alright.&nbsp; As you
              can see, we'll be using MySQL 4.0, MDAC 2.7, and one
              of the many listed MyOLEDB drivers listed on MySQL's
              website.&nbsp; I'm not using VS.NET 2003, so if you
              have that product I cannot ensure that this guide
              will work (or is even necessary).&nbsp; If you were
              getting a message along the lines of &quot;MySQLProv was
              not registered on localhost&quot; then installing the
              MyOLEDB driver I linked to should fix that problem.</p>
							<p><font color="#0099CC"><b>Ok, Now I've Done All of
              That Crap--What About Visual Studio?<br>
              </b></font>&nbsp;&nbsp;&nbsp;&nbsp; If you have a
              database setup, you can proceed to work in Visual
              Studio.&nbsp; If not, use phpMyAdmin to create a
              database and a simple table.&nbsp; Usage of
              phpMyAdmin is rather straight-forward.&nbsp; If you
              need help, try the documentation for it above.&nbsp;
              Also, there are links named &quot;Documentation&quot;
              everywhere throughout phpMyAdmin that can point you
              to help.&nbsp; (Information on using phpMyAdmin is
              available at
              www.pcrpg.org/TRPGguides/mysqloledotnet.php)</p>
							<p>&nbsp;&nbsp;&nbsp;&nbsp; Now, assuming you've
              installed the MyOLEDB driver and your MySQL server
              is up and running, let's begin.&nbsp; I only cover
              VB.NET code, but the methodology is similar for C#
              as well.&nbsp; If you're programming and have come
              this far using C++, then you should be able to adapt
              this to your language.</p>
							<font SIZE="2">
              <p></font><font size="2" COLOR="#0000ff">Dim</font><font size="2">
              fdCon <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font>
              OleDb.OleDbConnection(&quot;Provider=MySQLProv;Data
              Source=<b>DATABASE</b>;User Id=<b>YOURSQLUSERNAME</b>;Password=<b>YOURSQLPASSWORD</b>;&quot;)</font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdCom
              <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font>
              OleDb.OleDbCommand(&quot;SELECT * FROM <b>TABLENAME </b>
              ORDER BY<b> DESIREDFIELD </b>ASC&quot;, fdCon)<br>
              <br>
              fdCom.Connection.Open()<br>
              </font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdRead
              <font COLOR="#0000ff">As</font>
              OleDb.OleDbDataReader =
              fdCom.ExecuteReader(CommandBehavior.CloseConnection)</font></p>
              <p><font size="2" COLOR="#0000ff">While</font><font size="2">
              fdRead.Read<br>
&nbsp;&nbsp;&nbsp;&nbsp; <font color="#008000">'Do what you want here.&nbsp;
              Below is code that will pop up a message box for
              every record.<br>
&nbsp;&nbsp;&nbsp;&nbsp; 'This code would work if your table had three fields.<br>
&nbsp;&nbsp;&nbsp;&nbsp; 'This database's first field is an auto-incrementing ID
              medium integer, second field is a<br>
&nbsp;&nbsp;&nbsp;&nbsp; 'VarChar, and the third is also a VarChar.&nbsp; This
              code displays each field on its own line.</font><br>
&nbsp;&nbsp;&nbsp;&nbsp; MsgBox(fdRead.GetValue(0) &amp; vbCrLf &amp; fdRead.GetValue(1)
              &amp; vbCrLf &amp; fdRead.GetValue(2))</font><font size="2" COLOR="#0000ff"><br>
              End</font><font size="2"> </font>
              <font COLOR="#0000ff"><font size="2">While<br>
              </font></font><font size="2"><br>
              fdCon.Close()</font></p>
              <p>&nbsp;&nbsp;&nbsp;&nbsp; You will need to change
              the bold parts to the appropriate information.&nbsp;
              For example, DATABASE should be the name of your
              MySQL database, YOURSQLUSERNAME is the username
              (probably root) for the database, and the same
              concept for YOURSQLPASSWORD.&nbsp; Change TABLENAME
              to the name of your table.&nbsp; It's a good idea to
              stay away from all capital names in SQL.&nbsp; You
              don't have to use the ORDER BY DESIRED FIELD ASC
              statement, but you can to sort the data.&nbsp; If
              you want to use it, change the DESIREDFIELD to the
              name of one of your fields.&nbsp; Sorting by an ID
              field if you've got one is always a good idea.&nbsp;
              ASC = ascending; DESC = descending.&nbsp; For more
              information on SQL commands, please visit a site
              such as:<br>
              <b>http://www.phpfreaks.com/postgresqlmanual/page/sql-commands.html</b><br>
              or for an explained easy-to-learn course of basic
              SQL commands such as INSERT, SELECT, UPDATE, and
              DELETE go to:<br>
              <b>http://www.developerfusion.com/show/48/1/ </b> <br>
              Once you've learned the stuff at Developer Fusion,
              the PHP Freaks page will come in handy as you'll
              understand it better.</p>
              <p>&nbsp;&nbsp;&nbsp;&nbsp; Now that you've learned
              basic data retrieval, let's go over a non-query.</p>
              <font SIZE="2">
              <p></font><font size="2" COLOR="#0000ff">Dim</font><font size="2">
              fdCon <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font>
              OleDb.OleDbConnection(&quot;Provider=MySQLProv;Data
              Source=<b>DATABASE</b>;User Id=<b>YOURSQLUSERNAME</b>;Password=<b>YOURSQLPASSWORD</b>;&quot;)</font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdCom
              <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font> OleDb.OleDbCommand(&quot;&quot;,
              fdCon)<br>
              <br>
              fdCom.Connection.Open()<br>
              </font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdRead
              <font COLOR="#0000ff">As</font>
              OleDb.OleDbDataReader =
              fdCom.ExecuteReader(CommandBehavior.CloseConnection)</font></p>
              <font SIZE="2">
              <p>fdCom.CommandText = &quot;INSERT INTO TABLENAME
              (FIELDNAME1, FIELDNAME2) VALUES (&quot;&quot;lookatme&quot;&quot;, &quot;&quot;newline!&quot;&quot;)&quot;<br>
              fdCom.ExecuteNonQuery()</font><font size="2" COLOR="#0000ff"><br>
              </font><font size="2"><br>
              fdCon.Close()</font></p>
              <p>Once again, replace TABLENAME and the FIELDNAMEx
              to appropriate values.&nbsp; You can have more or
              less fields (depending on what's in your table) or
              select one the fields you want.&nbsp; However, take
              notice of the order in which you list them as that's
              the order in which the VALUES will be placed.&nbsp;
              If you take notice, &quot;lookatme&quot; would be inserted as
              FIELDNAME1 and &quot;newline!&quot; would be inserted for
              FIELDNAME2.&nbsp; Using a double double-quote in VB
              acts as an escape character and actually inserts a
              real double-quote.&nbsp; It's always a good practice
              to either use that or a solitary single-quote around
              your variable names.&nbsp; If you were going to use
              the variables ImaVar1 and ImaVar2 with
              double-quotes, you could do it like this:</p>
              <font SIZE="2">
              <p></font><font size="2" COLOR="#0000ff">Dim</font><font size="2">
              fdCon <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font>
              OleDb.OleDbConnection(&quot;Provider=MySQLProv;Data
              Source=<b>DATABASE</b>;User Id=<b>YOURSQLUSERNAME</b>;Password=<b>YOURSQLPASSWORD</b>;&quot;)</font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdCom
              <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font> OleDb.OleDbCommand(&quot;&quot;,
              fdCon)<br>
              <br>
              fdCom.Connection.Open()<br>
              </font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdRead
              <font COLOR="#0000ff">As</font>
              OleDb.OleDbDataReader =
              fdCom.ExecuteReader(CommandBehavior.CloseConnection)</font></p>
              <font SIZE="2">
              <p>fdCom.CommandText = &quot;INSERT INTO TABLENAME
              (FIELDNAME1, FIELDNAME2) VALUES (&quot;&quot;&quot; &amp; ImaVar1 &amp;
              &quot;&quot;&quot;, &quot;&quot;&quot; &amp; ImaVar2 &amp; &quot;&quot;&quot;)&quot;<br>
              fdCom.ExecuteNonQuery()</font><font size="2" COLOR="#0000ff"><br>
              </font><font size="2"><br>
              fdCon.Close()</font></p>
              <p>Yes, that's three double-quotes together.&nbsp;
              That's the double double-quote inside of a quoted
              string.&nbsp; It stores an actual quote there.&nbsp;
              Now, to use single quotes you might do it like
              below:</p>
              <font SIZE="2">
              <p></font><font size="2" COLOR="#0000ff">Dim</font><font size="2">
              fdCon <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font>
              OleDb.OleDbConnection(&quot;Provider=MySQLProv;Data
              Source=<b>DATABASE</b>;User Id=<b>YOURSQLUSERNAME</b>;Password=<b>YOURSQLPASSWORD</b>;&quot;)</font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdCom
              <font COLOR="#0000ff">As</font>
              <font COLOR="#0000ff">New</font> OleDb.OleDbCommand(&quot;&quot;,
              fdCon)<br>
              <br>
              fdCom.Connection.Open()<br>
              </font><font size="2" COLOR="#0000ff"><br>
              Dim</font><font size="2"> fdRead
              <font COLOR="#0000ff">As</font>
              OleDb.OleDbDataReader =
              fdCom.ExecuteReader(CommandBehavior.CloseConnection)</font></p>
              <font SIZE="2">
              <p>fdCom.CommandText = &quot;INSERT INTO TABLENAME
              (FIELDNAME1, FIELDNAME2) VALUES ('&quot; &amp; ImaVar1 &amp; &quot;',
              '&quot; &amp; ImaVar2 &amp; &quot;')&quot;<br>
              fdCom.ExecuteNonQuery()</font><font size="2" COLOR="#0000ff"><br>
              </font><font size="2"><br>
              fdCon.Close()</font></p>
              <p>That's a single-quote on the inside of the string
              declaration quotes.&nbsp; ' &quot; and &quot; '
              accordingly--no spaces between them.&nbsp; I guess
              that about wraps it up.&nbsp; If you need help on
              something, fire off an email to <b>mysqlhelp@pcrpg.org</b> and I'll get back to you as
              soon as I can.&nbsp; Thanks for reading this
              tutorial--it's pretty long, I know.&nbsp; I could
              have spent a Saturday better ways, trust me!</p>

