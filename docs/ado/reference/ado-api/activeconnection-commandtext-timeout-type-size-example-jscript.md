---
title: Пример свойств хранимой процедуры (JScript) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- ActiveConnection property [ADO], JScript example
- CommandText property [ADO], JScript example
- Size property [ADO], JScript example
- Direction property [ADO], JScript example
- CommandTimeout property [ADO], JScript example
ms.assetid: ea74e2a3-c965-43aa-9076-26a084b48ad8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c9c474cfe2b1d38154129070cb11c91434ee4fad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921556"
---
# <a name="activeconnection-commandtext-commandtimeout-commandtype-size-and-direction-properties-example-jscript"></a>Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)
В этом примере для выполнения хранимой процедуры используются свойства [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md), [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md), [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md), [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md), [size](../../../ado/reference/ado-api/size-property-ado-parameter.md)и [Direction](../../../ado/reference/ado-api/direction-property.md) . Вырежьте и вставьте следующий код в Блокнот или другой текстовый редактор и сохраните его как **активеконнектионжс. ASP**.  
  
```  
<!-- BeginActiveConnectionJS -->  
<%@LANGUAGE="JScript"%>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
<head>  
    <title>ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body bgcolor="White">  
  
<%  
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));  
    // check user input  
  
    if (iRoyalty > -1)  
    {  
            // connection and recordset variables  
        var Cnxn = Server.CreateObject("ADODB.Connection")  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='pubs';Integrated Security='SSPI';";  
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");  
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");  
        var rsAuthor = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var filter, strMessage;          
  
        try  
        {  
            // open connection  
            Cnxn.Open(strCnxn);  
  
            cmdByRoyalty.CommandText = "byroyalty";  
            cmdByRoyalty.CommandType = adCmdStoredProc;  
            cmdByRoyalty.CommandTimeOut = 15;  
  
            // The stored procedure called above is as follows:  
                //    CREATE PROCEDURE byroyalty  
                //  @percentage int  
                //    AS  
                //  SELECT au_id from titleauthor  
                //  WHERE titleauthor.royaltyper = @percentage  
                //  GO  
  
            prmByRoyalty = Server.CreateObject("ADODB.Parameter");  
            prmByRoyalty.Type = adInteger;  
            prmByRoyalty.Size = 3;  
            prmByRoyalty.Direction = adParamInput;  
            prmByRoyalty.Value = iRoyalty;  
            cmdByRoyalty.Parameters.Append(prmByRoyalty);  
  
            cmdByRoyalty.ActiveConnection = Cnxn;  
  
            // recordset by Command - Execute  
            rsByRoyalty = cmdByRoyalty.Execute();  
  
            // recordset by Recordset - Open  
            rsAuthor.Open("Authors", Cnxn);  
  
            while (!rsByRoyalty.EOF)  
            {  
                // set filter  
                filter = "au_id='" + rsByRoyalty("au_id")  
                rsAuthor.Filter = filter + "'";  
  
                // start new line  
                strMessage = "<P>";  
  
                // get data  
                strMessage += rsAuthor("au_fname") + " ";   
                strMessage += rsAuthor("au_lname") + " ";  
  
                // end line  
                strMessage += "</P>";  
  
                // show data  
                Response.Write(strMessage);  
  
                // get next record  
                rsByRoyalty.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // clean up  
            if (rsByRoyalty.State == adStateOpen)  
                rsByRoyalty.Close;  
            if (rsAuthor.State == adStateOpen)  
                rsAuthor.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsByRoyalty = null;  
            rsAuthor = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="ActiveConnectionJS.asp">  
  <p align="left">Enter royalty percentage to find (e.g., 40): <input type="text" name="RoyaltyValue" size="5"></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
  
</body>  
  
</html>  
<!-- EndActiveConnectionJS -->  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойство ActiveCommand (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Свойство CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Свойство CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)   
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство Direction](../../../ado/reference/ado-api/direction-property.md)   
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)   
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Свойство Size (объект Parameter ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
