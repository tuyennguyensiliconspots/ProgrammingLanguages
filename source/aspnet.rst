===============
ASP.NET
===============

A.  Fundamentals
================

Section 1.1 Title TEST
---------------------------

Custom error
^^^^^^^^^^^^^^

Custom error
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add this to web.config::

    <configuration>
        <system.web>
            <customErrors defaultRedirect="ouch.htm" mode='On|Off|RemoteOnly'>
                <error statusCode="404" redirect="filenotfound.htm"/>
            </customErrors>
        </system.web>
    </configuration>

Get Unhandle Exception information
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Add this to Global.asax file::

    void Application_Error(object sender, EventArgs e)    
    {
        Exception x = Server.GetLastError();
        Response.Write(x.ToString());
        Server.ClearError();
    }

B. Advanced
========================

ASP.NET Security
---------------------------

Developer should know
^^^^^^^^^^^^^^^^^^^^^^

- If your website accepts user input, it may be vulnerable to attack.
- Two of the most common attacks against web applications
    - SQL Injection
    - Cross Site Scripting