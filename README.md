# REDCap API Library for C#
The REDCap API (Application Programming Interface) for REDCap, lets you:
1.  export/import/delete data in REDCap
2.  export/import/delete project information (e.g., field names and types) in REDCap

__Prerequisites__
1.  Local redcap instance instsalled (visit https://project-redcap.org) if you need to download files(assuming you have access)
2.  Create a new project with "Demographics" for the template, this gives you a basic project to work with.
3.  Create an api token for yourself, replace that with the tokens you see on the "RedcapApiTests.cs" files, and others
4.  You'll need to add a field type of "file_upload" so that you can test the file upload interface of the API
5.  Build the solution, then run the tests

__API METHODS SUPPORTED__
* ExportArmsAsync
* ImportArmsAsync
* DeleteArmsAsync
* ExportEventAsync
* ImportEventAsync  
* ExportFileAsync
* ImportFileAsync
* DeleteFileAsync
* ExportMetaDataAsync
* ExportRecordsAsync
* ImportRecordsAsync
* ExportRedcapVersionAsync
* ExportUsersAsync

__Usage__:

1. dotnet restore
2. Add reference to the library in your project, or download from nuget into project
3. Add "using Redcap" namespace
4. Add "using Redcap.Models" for convenience
5. Replace the demo api token with your test project

__Example__
```C# 

using System;
using Newtonsoft.Json;
using Redcap;
using Redcap.Models;

namespace RedcapApiDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Redcap Api Demo Started!");

            var redcap_api = new RedcapApi("3D57A7FA57C8A43F6C8803A84BB3957B", "http://localhost/redcap/api/");

            var result = redcap_api.GetRecordAsync("1", RedcapFormat.json, RedcapDataType.flat, ReturnFormat.json, null, null, null, null).Result;
            var data = JsonConvert.DeserializeObject(result);
            Console.WriteLine(data);
            Console.ReadLine();

        }
    }
}

```

__Install directly in Package Manager Console or Command Line Interface__
```C#
Install-Package RedcapAPI -Version 0.3.0-alpha  
```

```C#
dotnet add package RedcapAPI --version 0.3.0-alpha 
 ```

```C#
paket add RedcapAPI --version 0.3.0-alpha  
```

__Example Project__

A console project has been included with the source code to get started.

__Test Project__

A project with associated test cases is included. Make sure to change the api token